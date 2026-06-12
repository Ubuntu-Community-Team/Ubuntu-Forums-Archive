---
title: "Compiz question: Where'd the config go?"
date: 2006-08-22
forum: Desktop Environments
---

### Post by LeftyAce on 2006-08-22
Hi all,
I am new to the forums (and to Ubuntu), and so far like what I see in Ubuntu.  My primary reason for switching from Debian to Ubuntu was to get XGL and Compiz, as I had heard that installing these was very easy in this distro.  I heard right, and initial installation went smoothly.

Now I want to enable some more effects (rain hitting the screen, etc) and went into gconf-edit to edit the /applications/compiz variable and its not there.  I ve been through the whole tree and don't see any folder called compiz, and searching turns up nothing (except the occasional crashing of gconf-edit).  I'm doing this all through sudo.  

Can anyone tell me how to get to the active_plugins variable? I followed the instructions in [this link]("http://www.ubuntuforums.org/showthread.php?t=133427") for the install, and have tried to replicate the steps to get to the variable.  It seems not to exist!  

Any help much appreciated.

Thanks in advance,

Lefty.

---

### Post by lazyd2 on 2006-08-22
Maybe you should take a look in the [Compiz forum]("http://www.compiz.net/index.html").

---

### Post by LeftyAce on 2006-08-22
Aha! Thanks, will post there.

---

### Post by LeftyAce on 2006-08-23
Hmm. I posted there last night, and now I can't even load the compiz.net site.  Maybe it'll be back later, but in the meantime, anyone know of a way to create the active_plugins variable and the folder it belongs in?

---

### Post by PathSpace on 2006-08-23
Hmmm...all those effects were enabled by default on my installation.  Are you sure that you downloaded all the necessary packages?

Note:  I use AIGLX instead of GLX.  That may or may not make a difference.

---

### Post by LeftyAce on 2006-08-23
I'll try uninstalling it and re-installing it.  The howto I followed didn't have those effects enabled, but I can't even see the opitions I _did_ enable...

I'll remove and re-install when I get home, and hopefully that'll do the trick.

---

### Post by PathSpace on 2006-08-23
Maybe you should try installing "gset-compiz" from here:

[http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/](http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/)

Dunno, but it *could* help...

---

### Post by LeftyAce on 2006-08-23
Tried installing gset-compiz, but the binaries don't support amd 64 bit processors :-(

I did however get to see the compiz key in gconf-editor! I had to run 
```
sudo gedit /usr/share/xsessions/compiz.desktop
``` and simply re-save the existing document.  Then gconf-editor showed the key.

EDIT: Apparently gconf-editor should NOT be run as root, otherwise the compiz options will not appear.

Another problem has cropped up though.  When I add a value to the active_plugins key, I hit ok and see the value in the key list.  But if I close and restart gconf-editor, the new value disappears.  The plugin I'm trying to activate is water, and needless to say it doesn't run even before I close gconf-editor.

Any idea why my edits aren't sticking?  

EDIT: Because I don't have the plugins installed. How to install??....

Thanks for your help so far,

Lefty

---

