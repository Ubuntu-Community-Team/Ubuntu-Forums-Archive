---
title: "gfortran will not compile .f"
date: 2009-05-20
forum: General Help
---

### Post by nutu on 2009-05-20
hello everybody,

i am trying to compile some fortran code using gfortran but i have unfortunately run into some issues.

using:

```

program test
write(*,*)'Hello world!'
end program test

```i can compile and run the code if i end it with a .f90:

[I]gfortran -o test.exe test.f90
./test.exe[/I]

the output i get is:

```

Hello world!

```however, when i try to end the file using .f:

*gfortran -o test.exe test.f*

the output i get is:

```

test.f:1.1:

program test                                                            
 1
Error: Non-numeric character in statement label at (1)
test.f:1.1:

program test                                                            
 1
Error: Unclassifiable statement at (1)
test.f:2.1:

write(*,*)'Hello world!'                                                
 1
Error: Non-numeric character in statement label at (1)
test.f:2.1:

write(*,*)'Hello world!'                                                
 1
Error: Unclassifiable statement at (1)
test.f:3.1:

end program test
 1
Error: Non-numeric character in statement label at (1)
test.f:3.1:

end program test
 1
Error: Unclassifiable statement at (1)

```

i get the aforementioned error message and gfortran will not compile the .f file. for some reason .f90 works but .f doesn't. i need both types to work (and do not see why it shouldn't as i have had this work on windows before but not on ubuntu).

can anybody help me please? 

thank you.

---

### Post by nutu on 2009-05-20
update: when i indent my .f code 3 times (~6 spaces) then:
 
```

gfortran -o test.exe test.f
./test.exe

```
 
works.
 
 
 
does this mean i have to indent every single program 3 times before even beginning to write? what happens if i have a program which i would like to open that is already written and several hundred lines long?

---

### Post by StuartN on 2009-05-20
According to man gfortran:

```
-ffree-form
-ffixed-form
Specify the layout used by the source file.  The free form layout was introduced in Fortran 90.  Fixed form was traditionally used in older Fortran programs.  When neither option is specified, the source form is determined by the file extension.
```

So I guess a .f90 extension allows free use of whitespace and .f requires strict use, but the gfortran -ffreeform option will permit free use in a .f source file.

---

### Post by nutu on 2009-05-20
> **StuartN said:**
> According to man gfortran:
 
```
-ffree-form
-ffixed-form
Specify the layout used by the source file.  The free form layout was introduced in Fortran 90.  Fixed form was traditionally used in older Fortran programs.  When neither option is specified, the source form is determined by the file extension.
```
 
So I guess a .f90 extension allows free use of whitespace and .f requires strict use, but the gfortran -ffreeform option will permit free use in a .f source file.
 
thank you so much. now when i write:
 
```

gfortran -ffree-form -o test.exe test.f

```
 
it compiles!!! :D

---

