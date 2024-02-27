# KXI Compiler
Using Python and SLY
## Lexer
### Lexical Specification
#### Abbreviations
alpha &emsp;&emsp;&emsp; &emsp; = [A-Za-z]  
digit &emsp; &emsp;&emsp; &emsp; = [0-9]  
end_line &emsp;&emsp;&emsp; = [\r\n]+  
unescaped_char = ASCII 32-126 except `"`, `'`, and `\`  
escaped_char &emsp; = \\[\rtn]  
char &emsp;&emsp;&emsp;&emsp;&emsp; = \<unescaped_char> | \<escaped_char>  

#### Keywords
`bool` `break` `case` `class` `char` `cin` `cout` `default` `else` `false` `for` `if` `int` `new` `null` `public` `private` `return` `static` `string` `switch` `this` `true` `void` `while`

#### Punctuation
`;` `{` `}` `(` `)` `[` `]` `,` `:`  

#### Operators
`=` `==` `!=` `>=` `<=` `>` `<` `&&` `||` `!` `+` `-` `*` `/` `+=` `-=` `*=` `/=` `<<` `>>` `.` 

#### Other 
identifier = (\<alpha> | _) (\<alpha> | \<digit> | _)*  
char_lit = '(\<char> | \\' | ")'  
string_lit = "(\<char> | \\" | ')\*"  
int_lit = \<digit>+  
comment = // .\*(.\*|[\<end_line>]*)
unknown = .

#### Corresponding Tags
- Keywords: Same letters but capitalized
- Punctuation: `SEMICOLON` `LCUR` `RCURL` `LSQR` `RSQR` `LPAR` `RPAR` `PERIOD` `COMMA`
- Operators: `ASSIGN` `EQUAL` `NOTEQUAL` `GREATEQ` `LESSEQ` `GREAT` `LESS` `AND` `OR` `EXCLAIM` `PLUS` `MINUS` `TIMES` `DIVIDE` `ADDASSIGN` `SUBASSIGN` `TIMESASSIGN` `DIVIDEASSIGN` `INSERT` `EXTRACT`
- Other: `ID` `CHARLIT` `STRINGLIT` `INTLIT` `UNKNOWN`

#### SLY implementation
- KXILexer is a subclass of sly.Lexer  
- There is no COMMENT tag. This project uses SLY to ignore all comments. (Same regex is used, but a COMMENT Token will not appear in Token Stream)  

### Required/Libraries
- Python 3.6+
- Pytest (pip install pytest)
- SLY (pip install sly)
