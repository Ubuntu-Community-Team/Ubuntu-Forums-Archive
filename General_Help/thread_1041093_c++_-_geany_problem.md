---
title: "c++ - geany problem?"
date: 2009-01-16
forum: General Help
---

### Post by Len Tyree on 2009-01-16
trying to learn C++ using "sams teach yourself c++ for linux in 21 days" but have run up against a wall.

in creating/deleting objects in the free store application, code as shown in book 
class simplecat
{
public:
    simplecat(();
    ~simplecat();
private:
    int itsage;
}

simplecat::simplecat()    this statement causes this error "new types may not be defined in a return type" 

does anyone have a take on this?
Thanks for any help I can get.  Len Tyree.  
  [http://ubuntuforums.org/images/icons/icon5.gif](http://ubuntuforums.org/images/icons/icon5.gif)

---

### Post by jespdj on 2009-01-16
Look closely at this line:
```
simplecat(();
```
There is an extra opening brace.

---

### Post by Len Tyree on 2009-01-16
thanks jespdj.

typo, mine, when I typed the statements into this problem instead of copying them from geany.

sorry. should read:
simplecat::simplecat();   

can we try again??
Thanks len.

---

### Post by Len Tyree on 2009-01-16
problem solved by "johnsfine" on the linuxquestions forum

a missing ";" after the "}" at the end of a class statement...

thanks to johnsfine, and to all that looked.  len tyree

---

### Post by Len Tyree on 2009-02-04
solved

---

### Post by Len Tyree on 2009-03-02
SOLVED.  typeing error!!!   Thanks.

---

