---
title: "trouble setting up a link in alacarte"
date: 2006-08-30
forum: Desktop Environments
---

### Post by MakLeod on 2006-08-30
So I've been trying to figure out how to set up Warcraft in alacarte.  When I open up the terminal (already in home folder), I type in:

cd wow

wine wow.exe -opengl

What do I put into the alacarte link box to make it work exactly how I type it into the terminal?  Thanks.

---

### Post by xtknight on 2006-08-30
In the command box for the shortcut type this:

wine /home/username/wow/wow.exe -opengl

---

### Post by MakLeod on 2006-08-30
ahh so you have to put the name of the program first, then the directory where the target file is.  Thanks a lot!

---

### Post by xtknight on 2006-08-30
> **MakLeod said:**
> ahh so you have to put the name of the program first, then the directory where the target file is.  Thanks a lot!

Yup.  Wine is a command.  The first argument it takes is the full filename of the application to execute.  The second argument passes -opengl to the Windows application by adding it to its argument list.

---

