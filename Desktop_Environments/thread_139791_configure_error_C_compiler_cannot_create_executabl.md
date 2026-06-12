---
title: "configure: error: C compiler cannot create executables
check `config.log' for details"
date: 2006-03-04
forum: Desktop Environments
---

### Post by white_tiger_daniel on 2006-03-04
an error message comes up when I try to install stuff (see below)

configure: error: C compiler cannot create executable
check `config.log' for details.

any gurus got fixes

thanks

---

### Post by taurus on 2006-03-04
Did you install "build-essential" and how did you try to build that program from source???

---

### Post by white_tiger_daniel on 2006-03-07
ok this is really lame but what is build-essential and i just did the stuff that it says in the install guides eg. 
./configure
make 
make install 
but it comes up with an error for those too rrrrrrrrrrr:confused: :confused: :confused: :confused: :evil:

---

### Post by nicholaspaul on 2006-03-10
build-essential is all the crap you need to compile and install packages. 
Open a terminal and type:```
sudo apt-get install build-essential
```.

---

### Post by cobralgato on 2006-03-30
i have build-essential instaled and get the same error ...so there must be something else ..by the way i have the 64 bit version of Dapper

---

### Post by art on 2006-03-30
Did you try installing gcc-3.4 and then:
CC = gcc-3.4 
export CC

---

### Post by crusher2001 on 2007-06-05
> **nicholaspaul said:**
> build-essential is all the crap you need to compile and install packages. 
Open a terminal and type:```
sudo apt-get install build-essential
```.

Thanks for posting this information.  It solved my issue which was the same error the other member was having.

---

### Post by crom on 2007-08-01
> **crusher2001 said:**
> Thanks for posting this information.  It solved my issue which was the same error the other member was having.

Yup, solved mine too :) Thanks

---

### Post by ljohnston on 2007-08-04
It helped my issue, too!  Thanks!

---

