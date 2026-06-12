---
title: "Best (Beagle) does not start"
date: 2005-07-01
forum: Desktop Environments
---

### Post by Nonno Bassotto on 2005-07-01
I've just installed Beagle, but when I try to launch best (Beagle GUI) I get this message:

** (/usr/lib/beagle/Best.exe:11122): WARNING **: The following assembly referenced from /usr/lib/beagle/Tiles.dll could not be loaded:
     Assembly:   gecko-sharp    (assemblyref_index=8)
     Version:    1.0.0.0
     Public Key: ccf7d78a55e9f021
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/beagle).


** (/usr/lib/beagle/Best.exe:11122): WARNING **: The class Gecko.WebControl could not be loaded, used in /usr/lib/beagle/Tiles.dll (token 0x0100003c)

** ERROR **: file class.c: line 2119 (mono_class_setup_parent): should not be reached
aborting...
Abortito

What does this mean? Is there a way to make beagle work?
Thank you
Andrea

Sorry, I just found another similar post. I had searched only in the desktop forum. This is the post
[http://ubuntuforums.org/showthread.php?t=40244&highlight=beagle](http://ubuntuforums.org/showthread.php?t=40244&highlight=beagle)

---

### Post by jshein on 2005-07-02
There are good, step-by-step instructions here:

[http://beaglewiki.org/Ubuntu_Installation](http://beaglewiki.org/Ubuntu_Installation)

---

