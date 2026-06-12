---
title: "Zsnes installation problem"
date: 2007-04-16
forum: Gaming &amp; Leisure
---

### Post by mr.derp on 2007-04-16
I am getting a error when using the make command. It say this:

make: *** No rule to make target 'tools/depbuild.cpp', needed by 'tools/depbuild'. Stop

I have installed the required packages like SDL, NASM, and zlib. Does anyone know whats wrong here? Thanks in advance.

---

### Post by BoyOfDestiny on 2007-04-16
> **mr.derp said:**
> I am getting a error when using the make command. It say this:

make: *** No rule to make target 'tools/depbuild.cpp', needed by 'tools/depbuild'. Stop

I have installed the required packages like SDL, NASM, and zlib. Does anyone know whats wrong here? Thanks in advance.

try 
*./autogen.sh*
then 
*make*

Make sure you have installed build-essential, autoconf, automake (1.9 works fine.)

You are trying to compile 1.51 right?

Hope that does it. :)

---

### Post by mr.derp on 2007-04-16
Yes its 1.51

I installed those packages but I still get the same error message. What else could possibly be wrong?

On a side note does anyone know how to configure the keyboard for snes9express? Since that is the reason I'm trying to use Zsnes in the first place.

---

### Post by Perfect Storm on 2007-04-17
See if our guide solve your problem: [http://gaming.gwos.org/e107_plugins/content/content.php?content.38](http://gaming.gwos.org/e107_plugins/content/content.php?content.38)

---

### Post by surfjdh on 2007-04-17
just use gsnes9x, it freakin roxors

---

