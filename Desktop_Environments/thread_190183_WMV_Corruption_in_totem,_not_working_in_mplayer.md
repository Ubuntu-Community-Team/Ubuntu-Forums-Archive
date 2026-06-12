---
title: "WMV Corruption in totem, not working in mplayer"
date: 2006-06-05
forum: Desktop Environments
---

### Post by cleary on 2006-06-05
Apologies if this has been covered, I tried searching but either got an unuseably large amount of results or none :(

I've installed mplayer via apt-get as per usual in Ubuntu, I then copied the mplayer essential codecs to /usr/lib/codecs/
When I double clicked on a wmv file it opened in totem, but the image picture was interlacedwith each second line offset the width of the normal video so it looked like two really grainy versions of the same video playing side by side in one totem window.
When I tried to open the same video in mplayer, it didn't display anything, but the controls window popped up.
I then tried copying the contents of the mplayer "all-codecs" pack into /usr/lib/codecs/ but it didn't change the situation.

I can play the same video in Kubuntu 6.06 (on my laptop) in mplayer without any problems. I believe I followed the same install procedure.
I tried dl-ing another wmv file from a completely different source and had the same trouble.

Any ideas?

---

### Post by jstroot on 2006-06-06
I have the exact same problem. I have not found a solution yet.

---

### Post by cleary on 2006-06-06
[QUOTE=jstroot]I have the exact same problem. I have not found a solution yet.[/QUOTE]

I posted this on another forum - the suggestion there was that it was an overlay issue or a video driver issue. 
I currently don't have access to the machine to test, but I'm using Xgl/Compiz so I should test with them switched off. 
Are you using Xgl as well? Can you try it firstly with compiz turned off, then with Xgl disabled?

---

### Post by u-blunt-2 on 2006-06-06
Same problem here, with mplayer running Xgl and compiz. I think it might be hardware related as I messed with alot of configuration files to get the eye candy working. My glxinfo output looks like this :
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.5814 (8.25.18)

```
The Xfree stuff isin't there without Xgl. I also have problems with java GUI's since switching to Xgl. Anyone have an idea ?

EDIT: the java gui was fixed with an automatic system update...

---

### Post by elomire678 on 2006-06-10
Switch mplayer to gl2 output and wmv will work fine, there's something messing up .wmv when it outputs through xv in Xgl it seems.

---

### Post by jdusablon on 2006-06-14
[http://ubuntuforums.org/showthread.php?t=196035]("http://ubuntuforums.org/showthread.php?t=196035")

---

