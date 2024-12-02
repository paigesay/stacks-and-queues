// Paige Saychareun
// CWID: 884902354

#include <iostream>
#include <string>
#include <vector>
#include <utility>
#include <algorithm>

// Add class Stack here
class Stack {
private:
    void push(std::vector<std::pair<char, int > >& a, std::pair<char, int> b) {
        a.push_back(b);
    }

    std::pair<char, int> top(std::vector<std::pair<char, int > >& a) {
        if (a.empty()) {
            return std::pair<char, int>(0, 0); // Return null equivalent for char and int
        }
        return a.back();
    }

    void pop(std::vector<std::pair<char, int > >& a) {
        a.pop_back();
    }

    bool match(char a, char b) {
        return (a == '(' && b == ')') || (a == '[' && b == ']') || (a == '{' && b == '}');
    }

    bool isOpen(char a) {
        return a == '(' || a == '[' || a == '{';
    }

    bool isClose(char a) {
        return a == ')' || a == ']' || a == '}';
    }

public:
    void validPara(std::string pairs) {
        std::vector<std::pair<char, int > > stack;
        for (int i = 0; i < pairs.size(); i++) {
            char ch = pairs[i];
            if (isOpen(ch)) {
                push(stack, std::pair<char, int>(ch, i));
            } else if (isClose(ch)) {
                if (!stack.empty() && match(top(stack).first, ch)) {
                    pop(stack);
                } else {
                    std::cout << "Invalid\n";
                    return;
                }
            }
        }
        std::cout << (stack.empty() ? "Valid\n" : "Invalid\n");
    }

    int indexError(std::string pairs) {
        std::vector<std::pair<char, int > > stack;
        for (int i = 0; i < pairs.size(); i++) {
            char ch = pairs[i];
            if (isOpen(ch)) {
                push(stack, std::pair<char, int>(ch, i));
            } else if (isClose(ch)) {
                if (!stack.empty() && match(top(stack).first, ch)) {
                    pop(stack);
                } else {
                    return i;
                }
            }
        }
        return stack.empty() ? -1 : stack[0].second;
    }

    void minPara(std::string pairs) {
        std::vector<std::pair<char, int > > stack;
        for (int i = 0; i < pairs.size(); i++) {
            char ch = pairs[i];
            if (isOpen(ch)) {
                push(stack, std::pair<char, int>(ch, i));
            } else if (isClose(ch)) {
                if (!stack.empty() && match(top(stack).first, ch)) {
                    pop(stack);
                } else {
                    push(stack, std::pair<char, int>(ch, i));
                }
            }
        }
        std::cout << stack.size() << "\n";
    }

    void scorePara(std::string pairs) {
        std::vector<std::pair<char, int > > stack;
        int score = 0;
        for (int i = 0; i < pairs.size(); i++) {
            char ch = pairs[i];
            if (isOpen(ch)) {
                push(stack, std::pair<char, int>(ch, i));
            } else if (isClose(ch)) {
                if (!stack.empty() && match(top(stack).first, ch)) {
                    pop(stack);
                    score++;
                }
            }
        }
        std::cout << score << "\n";
    }
};

// Add class Queue here
class Queue {
private:
    std::vector<std::string> queue;

    std::string pop() {
        auto a = queue[0];
        queue.erase(queue.begin());
        return a;
    }

    std::string reverse(std::string s) {
        std::string a = "";
        for (int i = s.size() - 1; i >= 0; i--) {
            a += s[i];
        }
        return a;
    }

public:
    void enqueue(std::string s) {
        int chunkSize = 8;
        for (int i = 0; i < s.size(); i += chunkSize) {
            std::string chunk = s.substr(i, chunkSize);
            queue.push_back(reverse(chunk));
        }
    }

    void processMsg() {
        std::string result = "";
        while (!queue.empty()) {
            result += reverse(pop());
        }
        std::cout << result << "\n";
    }
};

// Main function
int main() {
    Stack s1;
    s1.validPara("(([]))");
    s1.minPara("(([]))");
    s1.scorePara("(([]))");
    s1.validPara("(([])");
    std::cout << s1.indexError("(([))") << std::endl;
    s1.minPara("(([])");
    s1.validPara("(([{}))");
    std::cout << s1.indexError("(([[}])") << std::endl;
    s1.minPara("(([{}))");
    s1.scorePara("(([{}))");
    std::cout << s1.indexError("({}[]()[)") << std::endl;
    s1.validPara("(([))");
    s1.minPara("(([))");
    std::cout << s1.indexError("[({)]") << std::endl;
    s1.validPara("(([{[{({})}]}]))");
    s1.minPara("(([{[{({})}]}]))");
    s1.scorePara("(([{[{({})}]}]))");
    s1.validPara("(([[{[{({})}]))");
    s1.validPara("(([[{[{({})}]}])]))");
    s1.scorePara("(([[{[{({})}]}])]))");
    std::cout << s1.indexError("(([[{{({})]}])]))") << std::endl;
    s1.validPara("(())");
    s1.validPara("(())");
    s1.validPara("void function(){}");
    s1.scorePara("void function(){}");
    s1.validPara("void function(");
    s1.minPara("void function(");
    s1.validPara("void function(std::string expre){if(expre){return 1;}else{return 0;}}");
    s1.scorePara("void function(std::string expre){if(expre){return 1;}else{return 0;}}");
    s1.validPara("void function(std::string expre){if(expre){return 1;}else{return 0;}");
    s1.validPara("void function(std::string expre){if(expre){return 1;else{return 0;");
    s1.minPara("void function(std::string expre){if(expre){return 1;else{return 0;");
    std::cout << s1.indexError("void function(std::string expre){if(expre){return 1;else{return 0;") << std::endl;

    Queue q1;
    q1.enqueue("This is a secure message.");
    q1.processMsg();
    q1.enqueue("The product I received is damaged. What should I do?");
    q1.processMsg();
    q1.enqueue("I need assistance with setting up my new device");
    q1.processMsg();
    q1.enqueue("The website is not loading properly on my browser.");
    q1.processMsg();
    q1.enqueue("I accidentally placed the wrong order. Can it be canceled?");
    q1.processMsg();
    q1.enqueue("This is your project3. Have a happy thanksgiving!!! Hahaha");
    q1.processMsg();
    q1.enqueue("I forgot my password and can't reset it. Help, please! Do you provide technical support for mobile devices?");
    q1.processMsg();
    q1.enqueue("The software update is causing issues on my computer. The response time on your website is very slow.");
    q1.processMsg();

    return 0;
}
