---
title: "Splash screen problem *I think*"
date: 2008-03-07
forum: Desktop Environments
---

### Post by jose158 on 2008-03-07
Well, I installed Ubuntu Tweaks, and tried to get a new Splash Screen on my Mint Linux. For some reason, then next time I logged in, I had to login via command prompt. Then type "startx", then when it starts up, nothing is in my desktop (home folders, computer, etc.) What's wrong?

---

### Post by uberlube on 2008-03-07
I believe that the problem has to do with ubuntu tweaks. It is a program meant for ubuntu and not mint, they are set up differently.

---

### Post by jose158 on 2008-03-07
Hmm. Didn't think about that... But how do I remove it?

---

### Post by angry_johnnie on 2008-03-09
> **jose158 said:**
> how do I remove it?


How did you install it?  Did you download a .deb package?  Did you use synaptic? (although, I don't remember ubuntu tweaks being in there).  

In any case, you would have to

```
sudo apt-get remove --purge ubuntu-tweaks
```
or whatever the package is called.

If you downloaded something other than a .deb package (like a .tar.gz) then refer to the 'readme' file that came with it (if it did), or to the page from where you got it.

If you want to change the splash screen, you could download gnome-splashscreen-manager.
It's in your repositories, so you just have to

```
sudo apt-get install gnome-splashscreen-manager
```

It's still rather strange that you ended up with no desktop just for changing the splash screen.  Did you change anything else?  Can you reset it to its default state?

Hope it works :-)
Good luck

---

### Post by jose158 on 2008-03-14
Well I removed Ubuntu Tweaks, but I still have the same problem... Has to be something else. Here is a screen shot of my desktop. [IMG]http://i201.photobucket.com/albums/aa311/jose158_2007/Screenshot-1.png[/IMG]
There is no Home Folder or Computer. I can't right-click either. Please Help.

---

### Post by dage on 2008-03-16
try this :
_ run gconf-editor
_ in gconf-editor : apps -> nautilus -> desktop then enable the home_icon_visible

---

### Post by angry_johnnie on 2008-03-16
> **jose158 said:**
> 
There is no Home Folder or Computer.


You mean on the desktop?  If you want icons on the desktop you have to go to your control center and select Mint Desktop.  Then you can check the boxes of all the things for which you want a desktop shortcut.

Edit:  I noticed this > Well I removed Ubuntu Tweaks, but I still have the same problem..

Does that mean you still have to login from a terminal screen?  Do you still have to startx?

If so, try this:

Find an option called Services in you control center, and once you're in there, find GDM, and make sure it's selected.

---

### Post by jose158 on 2008-03-17
> **hitomi_doaxbv@hotmail.com said:**
> try this :
_ run gconf-editor
_ in gconf-editor : apps -> nautilus -> desktop then enable the home_icon_visible
It's already enabled.> 
If so, try this:

Find an option called Services in you control center, and once you're in there, find GDM, and make sure it's selected. It's already enabled. Yes I do have a Home Folder and Computer, but to access it I had to install Konqueror or use Firefox to view them.

---

### Post by jose158 on 2008-03-18
Ugghh! This is really annoying, I can't do a lot with this problem. I have to do more work just to get something done! All I want to do is get this to work. Hopefully I won't have to reinstall Mint :(

---

### Post by jose158 on 2008-03-20
Hello?:confused:

---

