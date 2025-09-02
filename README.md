# Interpreter Pattern in Java

The **Interpreter Pattern** is a behavioral design pattern that defines a grammatical representation for a language and provides an interpreter to deal with this grammar.  

It is often used to evaluate sentences in a language (like SQL parsing, mathematical expressions, or business rules).

---

## 📖 Pattern Explanation

- **Expression (interface)** → Declares the `interpret` method.  
- **TerminalExpression** → Implements the interpretation for terminal symbols in the grammar.  
- **Non-terminal Expressions (AndExpression, OrExpression)** → Combine terminal expressions using grammar rules.  
- **Context** → The input string that needs to be interpreted.  

---

## 📝 UML Diagram

```mermaid
classDiagram
    class Expression {
        +boolean interpret(String context)
    }

    class TerminalExpression {
        -String data
        +TerminalExpression(String data)
        +boolean interpret(String context)
    }

    class OrExpression {
        -Expression expr1
        -Expression expr2
        +OrExpression(Expression, Expression)
        +boolean interpret(String context)
    }

    class AndExpression {
        -Expression expr1
        -Expression expr2
        +AndExpression(Expression, Expression)
        +boolean interpret(String context)
    }

    Expression <|.. TerminalExpression
    Expression <|.. OrExpression
    Expression <|.. AndExpression
