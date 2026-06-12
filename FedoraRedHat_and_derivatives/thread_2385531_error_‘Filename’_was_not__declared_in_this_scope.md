---
title: "error: ‘Filename’ was not  declared in this scope"
date: 2018-02-21
forum: Fedora/RedHat and derivatives
---

### Post by jimenright on 2018-02-21
error: ‘Filename’ was not declared in this scope : gcc-c++


spinning my wheels on this one - have checked out 6 or 7 similar issues through
google searches but nothing seems related.  have simplified the issue for this post:


1. have a header file, CCDSFileManagerLNX.h, that is included by my main.cpp pgm:


#include <stdio.h>


class CDSFileManagerLNX{
public:
    char* FileName;
    char* FileMode;
 
    FILE* pFile;
    
    void FileOpen();
};


2. have a cpp file, CCDSFileManagerLNX.cpp, that has been added to the project source files as it should:


#include "/home/test/cds/ClassLibrary/CCDSFileManagerLNX.h"


void CCDSFileManagerLNX::FileOpen(){
FILE* pFile = fopen(Filename,FileMode);
}


3. when i attempt to runi get this:


../../cds/ClassLibrary/CCDSFileManagerLNX.cpp:4:21: error: ‘Filename’ was not 
declared in this scope
 FILE* pFile = fopen(Filename,FileMode);
                     ^


WHAT THE .... er hey???


using netbeans ide on centos 7.4 and gcc - c++ compiler.  thanks in advance for any
insight.

---

### Post by coffeecat on 2018-02-21
> **jimenright said:**
> using netbeans ide on centos 7.4 

*Thread moved to **Fedora/RedHat and derivatives**.*

---

### Post by oldos2er on 2018-02-21
Centos support forums are here: [https://www.centos.org/forums/](https://www.centos.org/forums/)

---

### Post by steeldriver on 2018-02-21
Isn't it just a typo? File[COLOR=#ff0000]**n**[/COLOR]ame is not the same thing as File**N**ame

---

### Post by QIII on 2018-02-21
^^That appears to be it.

Remember that case matters in c++.

---

### Post by jimenright on 2018-02-21
doooooooooh - might you have something i can shoot myself with?  appreciate your help!

---

