---
title: "OpenOffice.org-3.0"
date: 2008-11-12
forum: Desktop Environments
---

### Post by Pengwyn44 on 2008-11-12
I have installed OpenOffice-3.0 on 8.04 Hardy. All works OK except Base.
The error message says that my Java Runtime Environment is out of date.
However it is the latest from the Ubuntu depositary.
How can I upgrade because the Sun Java site only offers a Linux bin file?
Pengwyn44

---

### Post by binbash on 2008-11-12
you can remove the java then install it via bin file.

---

### Post by Pengwyn44 on 2008-11-13
Thank you for the suggestion but after downloading Java and doing ./ which ran OK I don't know how to do the next step. Can you help with that please?

---

### Post by binbash on 2008-11-13
accept the license.(just follow the instructions at terminal , press enter etc)

after that (java installed)

$ sudo update-java-alternatives -l
see the javas installed and select it : 

sample : 

$sudo update-java-alternatives -s java-6-sun


OR you can install it via repo (i guess mediubuntu repo has latest java)

---

### Post by Pengwyn44 on 2008-11-13
Many thanks for your help. Success!

---

