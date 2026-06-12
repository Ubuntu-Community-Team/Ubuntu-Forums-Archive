---
title: "how to write malloc function"
date: 2007-11-15
forum: Education &amp; Science
---

### Post by mthalis on 2007-11-15
I'm in big trouble. I want to write malloc() function in language C. I want to write 'new malloc' function it do same thing in original malloc function do. This is my question

Write your own replacements for the memory allocation/deallocation routines malloc() and free(). Name these two new functions NewMalloc() and NewFree(). These two functions should be implemented in a file called newmalloc.c. Make sure to use the exact spellings as given above for the functions as well as the file. NewMalloc() allocates memory for each call from an array of fixed size. This array is an array of 50,000 characters. All the data structures that you declare to manage this 50,000 bytes memory area must reside within that memory area. The memory allocated using NewMalloc() can be freed with NewFree(). You cannot use malloc() or free() to write these two new functions. If memory cannot be allocated using the available memory a suitable error value must be returned. The funtion prototypes of NewMalloc() and NewFree() should be the same as of malloc() and free(). 

This is my original question if  anyone give some answer it's great help to me. I want it as soon as posible.

---

### Post by akniss on 2007-11-15
> **mthalis said:**
> I'm in big trouble. I want to write malloc() function in language C. I want to write 'new malloc' function it do same thing in original malloc function do. This is my question

Write your own replacements for the memory allocation/deallocation routines malloc() and free(). Name these two new functions NewMalloc() and NewFree(). These two functions should be implemented in a file called newmalloc.c. Make sure to use the exact spellings as given above for the functions as well as the file. NewMalloc() allocates memory for each call from an array of fixed size. This array is an array of 50,000 characters. All the data structures that you declare to manage this 50,000 bytes memory area must reside within that memory area. The memory allocated using NewMalloc() can be freed with NewFree(). You cannot use malloc() or free() to write these two new functions. If memory cannot be allocated using the available memory a suitable error value must be returned. The funtion prototypes of NewMalloc() and NewFree() should be the same as of malloc() and free(). 

This is my original question if  anyone give some answer it's great help to me. I want it as soon as posible.

Which class is this for? :)

---

### Post by mthalis on 2007-11-15
it header include only <stdio.h> thats what I want but if can't use it you can use anything you want. please send anser less than one hour.

---

### Post by David Corrales on 2007-11-17
Haha... earn your grade :p

---

### Post by akniss on 2007-11-17
> **mthalis said:**
> please send anser less than one hour.
That's my favorite part!  #-o

---

### Post by slimdog360 on 2007-11-18
I have an answer


DO YOUR OWN HOMEWORK

---

### Post by jatos on 2007-11-19
If you going to try this trick, leasst make sure it doesn't sound like its for homework...

---

