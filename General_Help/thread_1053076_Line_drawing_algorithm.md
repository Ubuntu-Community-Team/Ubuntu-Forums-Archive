---
title: "Line drawing algorithm"
date: 2009-01-28
forum: General Help
---

### Post by chhama on 2009-01-28
This is more of a general Linux question.

I'm trying to implement DDA and bresenham's line drawing algorithm. The code is from the book "Computer Graphics" by Donald Hearn and M.Pauline Baker. I am able to run the program using the old Turbo C compiler but I am unable to do so in gcc as there is no device.h files. How can I implement these algorithms, Is there any header file in gcc which can perform the operation of Turbo C's device.h?

---

### Post by Simian Man on 2009-01-28
Not really no.  The simplest thing would probably be to port the code to SDL which provides simple framebuffer graphics.

---

