---
title: "Xmame in hoary is OLD..."
date: 2005-04-09
forum: Gaming &amp; Leisure
---

### Post by leech on 2005-04-09
The Hoary version of xmame/xmess is now at 0.86, the newest version is 0.95, and even the Debian Sid version is at 0.94.  Any ideas when this will be updated?  For a while there, I was just using the Sid packages, but it'd be a lot easier if I could just update them through Synaptic.

Leech

---

### Post by sinbad782 on 2005-04-10
Yup - I agree. I also can't seem to find the gxmame frontend in any of the regular repositories

PJS

---

### Post by leech on 2005-04-10
Well, that's the other thing, gxmame currently has issues.  You can add 'deb [http://anarxia.dyndns.org/debian/](http://anarxia.dyndns.org/debian/) ./' to your sources, but it will always crap out if you try to use your joystick/gamepad.  Because the xmame-sdl itself only supports joytypes 1 and 5, but the UI, when selecting SDL joystick, thinks it's only 4.  I had gotten around this by changing the config file, but that trick doesn't seem to work anymore.  

You can also go to the sourceforge.net page for it and get the cvs version of gxmame, then use dpkg-buildpackage.  Like so....

```
sudo apt-get install cvs
cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/gxmame login
```
Just hit enter when it asks for a password.  It probably will tell you you don't have a .cvspass, just do the command again and it should work fine.  Then; 
```
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/gxmame co -P gxmame
```

And finally;
```
cd gxmame
sudo dpkg-buildpackage
```

Afterwards you should have a gxmame_0.35beta2-1_i386.deb

Just do a ```
sudo dpkg -i ../gxmame_0.35beta2-1_i386.deb
```

Leech

---

