---
title: "Fortran"
date: 2012-08-08
forum: Education &amp; Science
---

### Post by Lingadharini on 2012-08-08
I am trying to do some Fortran programming. Mine is ubuntu 10.04
Suggest what all files I have to install related to Fortran. How to and where to run the Fortran programs?
I am new to Fortran. So I need help badly..
Please help..:(

---

### Post by xadder on 2012-08-09
Not sure what you want, but if you google fortran f90 tutorial you get some good links. Avoid f77 sites. There are some now dealing with f2003, but despite the 2003 label this variant is not 100% supported yet (afaik, I haven't checked for ages, and most codes I see are f90/f95.)

All you need is a compiler. I use gfortran, it is free, available on all machines, and good.

---

### Post by Lingadharini on 2012-08-10
Thanks, but what should I do to run my fortran code? I am really new to fortran, and I have only the book on how to write a Fortran code, I dont know how to compile fortran or what commands or such sort I have to use for that.

---

### Post by bouncingwilf on 2012-08-10
Fortran seems to be reasonably well supported in Linux - check out this link for "how to's" 

[http://gcc.gnu.org/wiki/GFortran](http://gcc.gnu.org/wiki/GFortran)

I've also found the GTK+ fortran works well as does DISLIN if you want GUI programming.


Bouncingwilf

---

### Post by Eezyville on 2012-08-30
I make fortran programs all the time in Ubuntu. You need a compiler first. so google how to download gfortran or get the free version of intel fortran, the non-commercial use version. Now to compile the programs you first have to make them. Use a text editor to make the program and just type in a terminal thats in the same directory as the file gfortran *name_of_file*.f90 and it will create an *a.out* file. Now in the terminal type ```
./a.out
``` and the code will run.

---

### Post by Senplanet on 2012-09-18
Install gfortran:
```

sudo apt-get install gfortran

```create your fortran file (ex. test.f90)
Example:
```

program test
write(*,*)'Hello Lingadharini'
end program test

```Compile and build:
```

gfortran test.f90 -o test

```This will produce executable file 'test'

to run the program:
```

./test

```It should give you result:
```

Hello Lingadharini

```Good Luck ! :)

---

