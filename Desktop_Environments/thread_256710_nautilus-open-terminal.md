---
title: "nautilus-open-terminal"
date: 2006-09-13
forum: Desktop Environments
---

### Post by gibbylinks on 2006-09-13
Hi

I'm running XGL with Compiz. I had nautilus-open-terminal installed to let me right click on my desktop and open a terminal. This was working fine but has now stopped working for some reason. I've tried removing it and re-installing it with no joy.

Does anyone have any ideas ?

Thanks

---

### Post by ciscosurfer on 2006-09-13
These will help you out:
[https://help.ubuntu.com/community/NautilusScriptsHowto](https://help.ubuntu.com/community/NautilusScriptsHowto)
[https://help.ubuntu.com/community/Nautilus_Scripts](https://help.ubuntu.com/community/Nautilus_Scripts)

---

### Post by Lunar_Lamp on 2006-09-13
Or you can just:

"sudo aptitude install nautilus-open-terminal"

I think nautilus needs to restarted, and maybe X, after installing this.  I can't quite remember.

---

### Post by gibbylinks on 2006-09-13
Thanks for help. Used a script to do it instead of the nautilus-open-terminal

---

### Post by gibbylinks on 2006-09-14
Ah, another problem. I've got the script working, but I can't copy and paste text into the terminal window ?

I used to be able to. I can still do this in gedit.

Any ideas

Thanks

---

### Post by ciscosurfer on 2006-09-14
key combo: Control-Insert or Control-V should do the trick

---

### Post by gibbylinks on 2006-09-15
Thanks ciscosurfer, but that's what has stopped working. Yet it works in other packages ?

---

### Post by ciscosurfer on 2006-09-15
And I assume you've logged out and logged back in or rebooted if necessary to get these functions back?

---

### Post by gibbylinks on 2006-09-16
Yes done that.

---

### Post by DoktorSeven on 2006-09-16
Don't think it's possible to use copy/paste keyboard shortcuts in most terminals (CTRL-C ends a running program, for example, so that's right out).  In gnome-terminal, you can right-click and use Copy and Paste instead, or do it the real Linux way and highlight text to copy, middle-click to paste.

---

### Post by 3rdalbum on 2006-09-16
Does copying and pasting into the terminal work when you select them from the Edit menu?

---

### Post by gibbylinks on 2006-09-17
That's my problem. I used to be able to right click and select paste. Now when I right click I just get a white band across the open window.

I get the same if I try it in root terminal.

Also I've tried installing the "open-terminal nautilus" using apt. It loads OK and I get it on my desktop as a right click option, but when I select it nothinh happens.

Thanks guys for continuing to think on this one.

---

### Post by DoktorSeven on 2006-09-17
Which X terminal are you using?  Is it gnome-terminal, or another one?  Some terminals (xterm, Eterm) don't have a Windows-like "copy" and "paste" function.  (If you don't know what you're using, I would think that the nautilus-open-terminal would use whatever is set in your Preferred Applications [Preferences->Preferred Applications->System->Terminal Emulator from the panel menus].  If this isn't set to gnome-terminal, I think that's what you want to run.  If you're using a script instead of nautilus-open-terminal, I'd find out what it's trying to run.  Not sure what script you're using.)

Otherwise, you're better off using highlighting what you want to copy and middle-click to paste in terminals other than gnome-terminal.

---

### Post by gibbylinks on 2006-09-17
I think I've found part of the problem. I haven't got gnome-terminal installed. When I try to install it synaptic gives me this error message

gnome-terminal:
  Depends: gnome-terminal-data (=2.14.2-0ubuntu1) but 2.14.2-0ubuntu3 is to be installed

Thanks

---

### Post by ciscosurfer on 2006-09-17
Install it with Aptitude and it will grab all dependencies necessary, so```
sudo aptitude update && sudo aptitude install gnome-terminal
```Remember also that there are many ways to copy/paste into a terminal, including middle-click, Control-V, Shift-Insert...to name a few...you can also assign a specific key-combos.

---

### Post by dwfox2002 on 2007-03-20
I paste into the gnome terminal with Sift+Control+V.  Works exery time!

---

