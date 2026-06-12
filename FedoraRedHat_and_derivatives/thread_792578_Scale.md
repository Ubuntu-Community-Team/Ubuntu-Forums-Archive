---
title: "Scale"
date: 2008-05-13
forum: Fedora/RedHat and derivatives
---

### Post by ryan80 on 2008-05-13
Hi All,
I'm new here and I'm new in the Linux World :)

I have this problem where I am trying to divide 2 txt files to output in a another txt file. However the output is an integer. I am trying to output to 8 decimal places. Here is the code:

scale=8
paste -d\/ TotExec.txt NoExec.txt | bc -q > Final.txt

Output is still an integer :( Can anyone help me with this please?

Thanks.
Ryan

---

### Post by Phil Airtime on 2008-05-13
This sounds suspiciously like homework.

---

### Post by ryan80 on 2008-05-13
Actually its a little project i'm working on to gather some db2 statistics. I need to divide Total Execution time of a query by number of connections to check sql statement's result.

---

