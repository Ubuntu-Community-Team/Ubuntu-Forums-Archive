---
title: "Wagic install?"
date: 2010-03-21
forum: Gaming &amp; Leisure
---

### Post by MTeVil on 2010-03-21
I'm newish to linux (ubuntu karmic) and am having issues running the wagic binaries... well, to say i'm having issues is a bit of a misstatement: I have absolutely no idea how to run binaries in linux. What should i be doing?

---

### Post by Perfect Storm on 2010-03-21
Right click on "Wagic.linux.static" and choose properties.

Enable "executable".
You can now just click it to launch it.

---

### Post by Rustybolts on 2010-03-21
To run a bin file if you right click on file go into properties click on permissions tab and click the ticky box after execute to Allow executing file as program, click close. The bin will auto execute once clicked on. Just pick run in terminal.
 *edit* was beaten to it was downloading said file -- as above--*

---

### Post by MTeVil on 2010-03-21
the program attempts to launch and crashes.

edit: when i attempt to run via the terminal i get this error:
 WARNING: Application calling GLX 1.3 function "glXCreateWindow" when GLX 1.3 is not supported!  This is an application bug!
failed to create drawable
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  136 (XFree86-DRI)
  Minor opcode of failed request:  7 ()
  Resource id in failed request:  0x3c00005
  Serial number of failed request:  33
  Current serial number in output stream:  33

does anyone know what that means? thanks to all.

---

### Post by spark82 on 2010-05-13
I just had the same problem. Installing 'nvidia-glx-185' solved the problem.
I am using ubuntu 9.10.

---

