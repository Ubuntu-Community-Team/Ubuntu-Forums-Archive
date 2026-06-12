---
title: "Desktop Launcher for Urban Terror??"
date: 2007-05-07
forum: Gaming &amp; Leisure
---

### Post by ianb72 on 2007-05-07
I am trying to make an Desktop Launcher for Urban Terror, in Terminal I type this:
[HTML]cd /home/ian-m3gxx/Linux-i386 && ./ioUrbanTerror.i386[/HTML]

But if I copy this into the launcher it doesn't work, any ideas??

---

### Post by Perfect Storm on 2007-05-07
Either you should make a script (/as a file) for it and pinpoint the launcher for it or try with 

sh -c "cd <distination> && ./ioUrbanTerror.i386"

---

### Post by crane on 2007-05-07
Just point the launcher straight to the sh file.
so if you UrT is installed to:
/home/ian-m3gxx/Linux-i386 then point the shortcut to 
/home/ian-m3gxx/Linux-i386/ioUrbanTerror.i386.

 Another example.
 I installed mine to my ioquake3 folder so my shortcut points to:

/usr/local/games/ioquake3/ioUrbanTerror.i386

I will double check the command when I get home but I am almost positive that is it. I will be online later(probably playing Urban Terror) if you need further help.

---

### Post by crane on 2007-05-08
Here is my launcher:

---

