---
title: "KBFX question"
date: 2006-07-07
forum: Desktop Environments
---

### Post by srunni on 2006-07-07
OK, so I installed KBFX (sudo apt-get install kbfx) and downloaded a theme that I want to use. My question is, how exactly do I start KBFX? There seems to be no icon for it in the KMenu or anywhere, or do I even need to start it?

Thanks in advance.

---

### Post by srunni on 2006-07-07
Anybody know?

---

### Post by llamakc on 2006-07-07
I don't know how KDE adds programs to its menu (or where) but this I do know:

If you open a terminal window and type:

dpkg -L NAMEOFPACKAGE

like:

dpkg -L kbfx

it will spit out to the screen all of the files that were installed with that .deb. I usually look for whatever ends up in /usr/bin and just run that from the terminal with:

kbfx &

Also, I install menu with each Debian|Ubuntu install.

apt-get install menu

Good luck.

---

### Post by east_lander on 2006-07-07
I think you have to go the panel and add the kbfx applet:)

---

### Post by lefty.crupps on 2006-07-11
I have added the KBFX "button" to my panel.  But clicking on this "button" does nothing except a quick flash of an outline of what could be a menu.  It seems that more needs to be done?  What to do to get this to be a real button which works?

---

### Post by opticyclic on 2006-07-31
I get this as well.
Maybe it is something to do with the version of kbfx in the repos being a bit behind.
Have you tried the latest version?
There is a step by step guide to installing it here
[http://ubuntuforums.org/showthread.php?t=70282](http://ubuntuforums.org/showthread.php?t=70282)

---

### Post by srunni on 2006-08-02
Well, I got KBFX in my KMenu, and I can just use that. Also, once you have it set up, it's autoloads on login. Something else you can try is using Katapult to launch it. Hit alt+space and you can type the name of any program you want to start. Try that with KBFX and see if it helps.

---

### Post by srunni on 2006-08-02
oops...double post

---

### Post by opticyclic on 2006-08-02
KBFX has to be added as an applet to the panel, not run as an application.

I managed to fix the problem though.
If you goto Configure -> Misc -> Menu Type and select vistabar or xp menu you should get the effect.
It is just the kmenu option that doesn't appear to work with this version.
And the thing about the themes not selecting properly, but thats a different post... ;)

---

### Post by lefty.crupps on 2006-08-30
It has since began working.  I also have a KBFX Settings program in my Lost and Found.  I don't love it like i had hoped; it feels clunky.

---

