---
title: "Convert SCILAB code to C/C++"
date: 2008-05-06
forum: Education &amp; Science
---

### Post by sandeep3181 on 2008-05-06
Dear All,

Is there a way to convert Scilab to C/C++, without using Matlab as an intermediate? If possible kindly let me know.


Regards,
Sandeep

---

### Post by thisismalhotra on 2008-05-06
> **sandeep3181 said:**
> Dear All,

Is there a way to convert Scilab to C/C++, without using Matlab as an intermediate? If possible kindly let me know.


Regards,
Sandeep

I dont know of one yet but you might want to ask this question on scilab mailing lists as that is a better place for this type of question...:KS

---

### Post by sandeep3181 on 2008-05-07
"thisismalhotra" could you guide me to the link of the "mailing lists" ,  i am not able to locate it.

Regards,
Sandeep

---

### Post by thisismalhotra on 2008-05-07
> **sandeep3181 said:**
> "thisismalhotra" could you guide me to the link of the "mailing lists" ,  i am not able to locate it.

Regards,
Sandeep
I think Technical area on the top then mailing list

[http://www.scilab.org/contactus/index_contactus.php?page=mailing_lists](http://www.scilab.org/contactus/index_contactus.php?page=mailing_lists)

---

### Post by Togras on 2008-06-01
as far i remember you have to download the help with all (source)contents and then you are able to view the sourcecodes of the blocks then copy paste and the right compiler...:)
hope this helps

---

### Post by Bou_bou on 2009-08-05
Hello,

I am new in the forum and I have the same question, I didn't find an answer on Scilab mailing lists.

Togras, would you detail your method, how can I download the help with all (source)contents, and how it works ?

Thank you in advance.

_
Bou

PS : Excuse my English ..

---

### Post by Bou_bou on 2009-08-18
Re,

Could someone explain to me the method suggested by Togras please ? I will be very grateful to him/her.
I have a program that takes a lot of time in Scilab, I really need to have the results quickly.

Thanks.

---

### Post by Togras on 2009-11-26
Sry for my late reply 

if you have install all of the scilab documentation you can look in the help which code stands behind

e.g modulo 

```
**Name**
modulo — symetric arithmetic remainder modulo m

pmodulo — positive arithmetic remainder modulo m
Calling Sequence
i=modulo(n,m)
i=pmodulo(n,m)

**Parameters**
n,m
integers

**Description**
modulo computes i= n (modulo m) i.e. remainder of n divided by m (n and m integers).
i = n - m .* int (n ./ m). Here the answer may be negative if n or m are negative.
pmodulo computes i = n - m .* floor (n ./ m), the answer is positive or zero.
```

so you can't translate your code automatically as matlab did if you have the right modules and a visual compiler (only pro version)

you have to rebuild the functions in c and change your source code to c or even better c++ because scilab is objekt orientated an other way would be to call smaller scilab scripts out of your c code but there i know only the possibility in windows with system calls i try this also under linux but i got permission problems...

Togras

---

