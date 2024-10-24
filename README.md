#include <iostream>
#include <stack>

using namespace std;

void insertAtBottom(stack<int>& s, int element) {
    if (s.empty()) {
        s.push(element);
    } else {
        int top = s.top();
        s.pop();
        insertAtBottom(s, element);
        s.push(top);
    }
}

void reverseStack(stack<int>& s) {
    if (!s.empty()) {
        int top = s.top();
        s.pop();
        
        reverseStack(s);
        
        insertAtBottom(s, top);
    }
}
void printStack(stack<int> s) {
    while (!s.empty()) {
        cout << s.top() << " ";
        s.pop();
    }
    cout << endl;
}

int main() {
    stack<int> s;
    
    s.push(31);
    s.push(30);
    s.push(29);
    s.push(28);
    
    cout << "原始堆疊: ";
    printStack(s);
    
    reverseStack(s);
    
    cout << "反轉後的堆疊: ";
    printStack(s);
    
    return 0;
}
