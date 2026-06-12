---
title: "what does yy stand for inyin,yylex,yyparse..."
date: 2009-06-08
forum: General Help
---

### Post by himagiri19 on 2009-06-08
hello everyone,
could u plz tell me what does yy stand for in yyin yyout,ets

---

### Post by tempo on 2009-06-25
> **himagiri19 said:**
> hello everyone,
could u plz tell me what does yy stand for in yyin yyout,ets

The yy is to remind you that it refers to yacc.  Quoting: > The Yacc parser uses only names beginning in ``yy''; the user should avoid such names. from [http://dinosaur.compilertools.net/yacc/]("http://dinosaur.compilertools.net/yacc/").  That way you can have a symbol called parse, yacc can have a symbol called yyparse and everyone is happy.

   tempo

---

