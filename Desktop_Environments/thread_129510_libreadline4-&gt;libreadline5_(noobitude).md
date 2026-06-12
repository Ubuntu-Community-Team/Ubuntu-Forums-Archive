---
title: "libreadline4-&gt;libreadline5? (noobitude)"
date: 2006-02-13
forum: Desktop Environments
---

### Post by Horza on 2006-02-13
Is it possible to replace libreadline4 with libreadline5, given that so much depends on libreadline, and aptitude wants to uninstall all of it.  Can this be done without a functioning internet connection?  The purpose is to upgrade something else (Python 2.4->2.42) which requires libreadline5.

 - Micro$erf wandering around on the other side of the fence

---

### Post by emersony on 2006-11-12
Actually, I have libreadline4 and libreadline5 both installed on Hoary and Breezy. Both of those systems are working fine. 

On Dapper however readline-common (which is not on the other two) conflicts with libreadline4, and thus breaks the system, or at least requires manic updating e.g. mysql (4) which is looking for readline.so.4 -- presumeably mysql 5 will be happy with libreadline5?

And in Dapper EVERYTHING depends on readline-common. 

-Emerson

---

