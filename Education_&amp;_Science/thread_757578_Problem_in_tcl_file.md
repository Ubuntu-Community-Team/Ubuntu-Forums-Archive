---
title: "Problem in tcl file"
date: 2008-04-17
forum: Education &amp; Science
---

### Post by hsanda on 2008-04-17
Hi All,
After do the installation and set path. i did the validation.
then it gave the following msg.

validate overall report: all tests passed

then i check the ns and after that i tried to compile a tcl code.
but a problem became as the file does not exit.
but the file is in the correct location.
Pls help to solve this.

hsanda@HS:~/NS2/ns-allinone-2.33/ns-2.33$ ns
Usage: host [-v] [-a] [-t querytype] [options] name [server]
Listing: host [-v] [-a] [-t querytype] [options] -l zone [server]
Hostcount: host [-v] [options] -H [-D] [-E] [-G] zone
Check soa: host [-v] [options] -C zone
Addrcheck: host [-v] [options] -A host
Listing options: [-L level] [-S] [-A] [-p] [-P prefserver] [-N skipzone]
Common options: [-d] [-f|-F file] [-I chars] [-i|-n] [-q] [-Q] [-T] [-Z]
Other options: [-c class] [-e] [-m] [-o] [-r] [-R] [-s secs] [-u] [-w]
Special options: [-O srcaddr] [-j minport] [-J maxport]
Extended usage: [-x [name ...]] server [name ...]]

//********************ERROR****************
hsanda@HS:~/NS2/ns-allinone-2.33/ns-2.33$ ns example2.tcl
example2.tcl does not exist, try again

hsanda@HS:~/NS2/ns-allinone-2.33/ns-2.33$

---

### Post by yasirimteyaz on 2009-08-06
mine after successful installation......
while running simple.tcl, it gives following errors:


_o5 cmd line 1)
invoked from within
"_o5 cmd at 1 “puts “Hello World!””"
invoked from within
"catch "$self cmd $args" ret"
invoked from within
"if [catch "$self cmd $args" ret] {
set cls [$self info class]
global errorInfo
set savedInfo $errorInfo
error "error when calling class $cls: $args" $..."
(procedure "_o5" line 2)
(SplitObject unknown line 2)
invoked from within
"_o5 at 1 “puts “Hello World!””"
("eval" body line 1)
invoked from within
"eval $scheduler_ at $args"
(procedure "_o3" line 3)
(Simulator at line 3)
invoked from within
"$ns at 1 “puts \“Hello World!\””"
(file "simple.tcl" line 2)




did anyone come across with the same problem?
If anyone know,could you help me.
thank you

---

