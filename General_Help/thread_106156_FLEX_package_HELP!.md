---
title: "FLEX package?? HELP!"
date: 2005-12-20
forum: General Help
---

### Post by Prudentissimus on 2005-12-20
> checking for X... no
checking for flex... no
checking for lex... no
checking for yywrap in -lfl... no
checking for yywrap in -ll... no
checking for :... no
checking for flex... no
checking for lex... no
configure: error: no suitable lex found. Please install the 'flex' package.

Configure failed, aborting install.
prudens@lin:~/Desktop/wine-20040615$



What is FLEX package?

---

### Post by invalid on 2005-12-20
```
sudo apt-get install flex
```

---

### Post by wwfn on 2006-04-11
i just wanted to say thank. i was looking on how to install flex.

---

### Post by jkeyes0 on 2006-04-11
[QUOTE=Prudentissimus]What is FLEX package?[/QUOTE]

From [http://dir.filewatcher.com/d/Ubuntu/i386/devel/flex_2.5.31-31_i386.deb.256136.html](http://dir.filewatcher.com/d/Ubuntu/i386/devel/flex_2.5.31-31_i386.deb.256136.html)

> flex - A fast lexical analyzer generator.

flex is a tool for generating scanners: programs which recognized lexical patterns in text. flex reads the given input files for a description of a scanner to generate. The description is in the form of pairs of regular expressions and C code, called rules. flex generates as output a C source file, lex.yy.c, which defines a routine yylex(). This file is compiled and linked with the -lfl library to produce an executable. When the executable is run, it analyzes its input for occurrences of the regular expressions. Whenever it finds one, it executes the corresponding C code.


Hope this helps (along with the apt-get mentioned earlier)

---

### Post by hezuo on 2008-07-22
great! thx alot, i was looking for this. now i can install wine 1.1

---

