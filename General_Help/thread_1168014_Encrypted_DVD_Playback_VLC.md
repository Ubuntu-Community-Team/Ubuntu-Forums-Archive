---
title: "Encrypted DVD Playback VLC"
date: 2009-05-23
forum: General Help
---

### Post by BslBryan on 2009-05-23
Hello, everyone. :-)

I suppose I've a rather odd case, because it seems that VLC works for just about everyone for encrypted DVDs, but Totem does not.  For me, Totem works fine, but VLC is terrible.  

The reason I'd like to use VLC from now on is because it's menu compatible, which could be of real use.  

So, I installed, a very long time ago, debhelper, build-essential, fakeroot, and libdvdcss2.  The reason I'd need the first three packages is because I've got an AMD64 processor (though I may not even need it, it was unclear whether I'd have to have those packages to run on a 32-bit OS...  It's okay, though, I need them as a hopeful MOTU. :-) ).

Does anyone have any ideas?  Or even, is there an application that will help Totem support menus?

---

### Post by mc4man on 2009-05-23
**If** you are still running **8.04 and vlc 0.8.6** then it should work very well with dvd movies with the rare exception of some structured protected titles.

Some of those can be dealt with by bumping up your libdvdnav4 to the 4.1.2-3 version (will install cleanly, just use the intrepid ver.
[http://packages.ubuntu.com/intrepid/libdvdnav4](http://packages.ubuntu.com/intrepid/libdvdnav4)

Another thing to check is the launch command. Go right click on Applications -> edit menus, highlight Sound & Video, then right click on vlc -> properties.
If the command is vlc %U then change it to 
```
vlc %f
```

Otherwise start vlc from a terminal, open a disc and post output.

A more verbose description of issues wouldn't hurt either

---

### Post by BslBryan on 2009-05-23
Mc4man, the issues I was having were mainly related to the general pixelated blotchiness of encrypted videos.  

Vlc %f fixed it.  Thanks a lot! :-)

---

