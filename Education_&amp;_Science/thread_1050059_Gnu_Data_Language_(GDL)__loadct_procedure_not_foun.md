---
title: "Gnu Data Language (GDL) : loadct procedure not found"
date: 2009-01-25
forum: Education &amp; Science
---

### Post by acl123 on 2009-01-25
I've just downloaded GDL to have a play with it as an alternative to IDL.
It all works OK and I've managed to do some basic stuff, but it is telling me that the "loadct" procedure is not found.
According to various sites out there loadct should be implemented. Does anyone know why it might not be working?

---

### Post by slayoo on 2009-05-20
Hello,

> **acl123 said:**
> ... it is telling me that the "loadct" procedure is not found...

Please check if the IDL_DIR (or GDL_DIR) env. variable is set and points to a directory with GDL library files (those in the src/pro directory of the source package). Some of the GDL library routines are implemented in GDL language (or partly in GDL, as in the case of LOADCT). Mac ports, for example, automatically place these library files under ${prefix}/share/gnudatalanguage/pro.

Regards,
Sylwester

---

### Post by sfa2560 on 2009-09-22
Hi I have a similar problem but with reading image:

GDL> im = read_jpg('~/Desktop/image.jpg')
Function not found: READ_JPG
% Function not found: READ_JPG
% Execution halted at: $MAIN$

is this what you got with loadct?

if so please post the directory to the IDL_DIR (or GDL_DIR) and what exactly to do for the fix from the second post. :)

---

### Post by shanex on 2010-04-13
I am having this same loadct problem. I tried to find the GDL_DIR variable and cannot find it. Does anyone have any more specific instructions available?

---

### Post by jonnymccullagh on 2011-04-03
I just happened upon this old post and I found the solution myself so I thought I would post it to help others. Change jonny below to your own username:

To ensure the libraries above are available to GDL when you run it, you can make use of the GDL_STARTUP environment variable. Set it as follows (bash):

export GDL_STARTUP=/home/jonny/.gdl_startup

Or add that line to your .bash_profile file so it is run automatically on log in
Now that we have set the GDL_STARTUP variable to point to a file we need to create that file: Use vi, gedit or any other text editor to create the file: /home/jonny/.gdl_startup
and add the following contents:

!PATH=!PATH + ':/usr/share/doc/gnudatalanguage/examples/pro/'
!PATH=!PATH + ':/usr/share/doc/gnudatalanguage/examples/pro/dicom/'

---

