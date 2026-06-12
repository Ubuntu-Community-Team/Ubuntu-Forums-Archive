---
title: "how to know bitsize  of integer variable in gmp library?"
date: 2010-03-21
forum: Desktop Environments
---

### Post by kishorebjv on 2010-03-21
How to know the size of a declared variable in GMP??or how can we decide the size of an integer in GMP?


mpz_random(temp,1);
in manual it  is given that this function allocates 1limb(=32bits for my comp) size to the "temp"....
but it is having 9 digit number only..
SO i dont think that 32 bit size number holds only 9 digits number..

So please help me to know the size of integer variable in GMP ..


thanks in adv..

---

### Post by VernonA on 2010-03-22
The largest value that can be stored in 32 bits is 0xFFFFFFFF which when printed as an unsigned decimal number is 4,294,967,295. Since the top digit position can only range between 0 and 4 (or -2 to 2 if you are using signed values), it is normal to say that only 9 digits are really available for storing decimal values.

---

### Post by kishorebjv on 2010-03-23
@ vernonA ... THANK YOU.. :)

yea.. you are right... i got it..

But how can i know bit size of a particular  integer variable  in GMP library..

can u code for displaying  bitsize of variable in gmp??

---

### Post by VernonA on 2010-03-24
One of the main purposes of the the GMP library is to use integers whose size grows according to the values they contain. When you create an **mpz_t** int, you are actually creating a structure which contains, amongst other things, a pointer to some memory created using malloc, plus variables to hold the size of this block, the number of digits in the block and so on. The internals of how this "integer" is used are hidden from you. In practice, you can go through the header files and deconstruct the internal workings if you want. However, if you really do need to keep track of the bitwise size of an int, you can tell the library to stop using malloc and instead use a function which you supply yourself, using the mp_set_memory_functions() call.
If you write a function like:
```
void * myCleverAllocFn(size_t alloc_size)
{
    printf("Creating a var of length %d bits\n", alloc_size*8);
    return malloc( alloc_size );
}

```and tell the library to use this when creating ints, you will get a printout of their size.

---

### Post by kishorebjv on 2010-03-24
@ VernonA

oooh... lil bit tough ..but very nice reply...


thank youuu...  :)

---

