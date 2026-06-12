---
title: "Xubuntu Thunar Segmentation Fault (core dump)"
date: 2007-05-31
forum: Desktop Environments
---

### Post by ubuntumaybe on 2007-05-31
Hi,

I successfully loaded Xubuntu but I have not application menu displayed. Also whenever I attempt to open the file manager, Thunar,  I recieve a Segmentation fault (core dump) message. What is the problem? Thanks.

---

### Post by afoglia on 2007-06-05
Can you try running Thunar from a Terminal?  What error messages do you get?

---

### Post by ubuntumaybe on 2007-06-06
Hi,

When I attempt to access the file manager from the icon on the desktop nothing happens. So I tried to access it from the terminal and that is when I see the segmentation fault error.

---

### Post by afoglia on 2007-06-06
Hmmm... Then I'm sorry I responded.  I got no ideas.  If no one else suggests anything, try using rox (package name, rox-filer).  It's the file manager that used to be packaged with XFCE before Thunar was ready.  Or try xffm (package name, xffm4).

What terminal program are you using?  I'm wondering if it's a low level XFCE issue.  Can you use Terminal?  Mousepad?

Is there anything odd in your .xsession-errors file (in your home directory)?

As for the application menu,can you get it if you right-click on the desktop background?  Have you tried manually adding it to your panel?  The panel item name is XFCE menu.  (The usual settings are Button title: Applications, Show title in button: checked, Use default desktop menu file, and the icon is /usr/share/pixmaps/xubuntu-logo.png, and Show icons in menu is checked.)

I've noticed my Applications menu will occasionally disappear if I have to force a restart, so I just readd the item manually.

---

### Post by ubuntumaybe on 2007-06-09
Hi,

I no longer get the segmentation error. Thunar is working but I still have no appliication menu. When I right click on the desktop nothing happens. I have been able to lauch application using the application launcher. I cannot locate the XFCE panel that you spoke of. I have looked in the supplied documentation and there is no mention of regenerating a menu. THanks.

---

### Post by rykel on 2008-02-20
> **afoglia said:**
>  Can you use Terminal?  Mousepad?


Hi,

I am facing a similar situation... when I try to run Mousepad, it gives me a "Segmentation Fault (core dumped)" error.

I purged Mousepad and reinstalled it to no avail.

Any way i can revive Mousepad?

---

### Post by afoglia on 2008-02-21
> **rykel said:**
> 
I am facing a similar situation... when I try to run Mousepad, it gives me a "Segmentation Fault (core dumped)" error.

I purged Mousepad and reinstalled it to no avail.

Any way i can revive Mousepad?

Are you trying to run Mousepad from a Terminal (or xterm or other terminal application)?  If not, try it from there, and see if you get more error messages.  (If you run it from the XFCE/Applications Menu, or another graphical program launcher, check the file .xsession-errors in your home directory both before and after you launch the program and see if any new lines were added.)

---

