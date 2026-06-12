---
title: "import troubles in Octave"
date: 2008-04-11
forum: Education &amp; Science
---

### Post by Ryan Swanson on 2008-04-11
Hi there,

I've recently started using Octave (within the last 3 months), and I'm having what is probably a beginners problem.  I have a series of data saved in a tab delimitted .dat file, and I want to fit a series of Gaussian functions to it.  Is there any way to import the data in this file in such a way as to be compatible with both Octave and Matlab (I'm writing an m-file for someone who uses Matlab)?

Many thanks to whoever can help!  

Ryan

---

### Post by Ryan Swanson on 2008-04-11
Nevermind; I just figured it out.  It turns out I had a typo in my code.

---

### Post by thisismalhotra on 2008-04-11
Most of the matlab functions(if you know them ofcourse) should also work in Octave for file read except for functions specially made for excel, like dlmread(I don remember the name)...

But you should be able to use fopen in Octave to read you .dat fil as a matrix and the use it row by row or column by column or the whole matrix.

Use the octave manual online for that. Here is the link to fopen function details: -

[http://www.gnu.org/software/octave/doc/interpreter/Opening-and-Closing-Files.html#index-fopen-687](http://www.gnu.org/software/octave/doc/interpreter/Opening-and-Closing-Files.html#index-fopen-687)

Look at this too : -

[http://www.gnu.org/software/octave/doc/interpreter/Simple-File-I_002fO.html#Simple-File-I_002fO](http://www.gnu.org/software/octave/doc/interpreter/Simple-File-I_002fO.html#Simple-File-I_002fO)

EDIT: Sorry too late !!

---

### Post by Ryan Swanson on 2008-04-11
Thanks Malhotra,

When I said I figured out my problem, fopen is what I was talking about.  I wasn't sure what the big endian and little endian architecture formats were, so I wasn't giving them much regard, but ,having which is which, I am now implementing the correct one.

Thanks for you help,
Ryan

---

