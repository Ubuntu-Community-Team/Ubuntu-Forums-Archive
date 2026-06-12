---
title: "Compiz problem"
date: 2006-08-10
forum: Desktop Environments
---

### Post by lesemi on 2006-08-10
I've been using Ubuntu since the warty days - so far i have no complaints.  I've recently done a clean install of dapper on my secondary drive and updated with Kubuntu.  I've also followed this tread for compiz:

[http://www.ubuntuforums.org/showthread.php?t=186200&highlight=install+xgl](http://www.ubuntuforums.org/showthread.php?t=186200&highlight=install+xgl)

Everything seems to work - windows are wobbly etc.  My problem is the other functions of compiz - i can't get to them - i've tried several shortcuts from the suse and gentoo forums - but nothing seems to work.
I've attempted to play with gset-compiz - still no luck.

anybody out there with the same prob?

Note: I'm using a dual core amd 64bit - Nvidia card - and installed Dapper i386

---

### Post by adam.tropics on 2006-08-10
looking at what gets installed on that guide, have you tried, from terminal, running gconf-editor? Settings are in apps>>compiz>>plugins

---

### Post by lesemi on 2006-08-10
No i didn't - i tried gset-compiz and i really didn't quite see how i can change the shortcuts and i did go through: app/compiz/plugins... however i didn't know how to change the configuration.  I didn't run the gconf-editor.  
I'm at work at the moment - i will have to give it a go later.

---

### Post by lesemi on 2006-08-10
ok - got gconf-editor up -
maybe i'm having a dense moment - what keys do i need to push to create a cube, i just can't seem to make sense out of the config.

another q. is the <Super> key the windows key?

---

### Post by zachtib on 2006-08-10
> **lesemi said:**
> another q. is the <Super> key the windows key?

yes

---

### Post by lesemi on 2006-08-10
thanks for the answer re: the Super key 

anyone can help me with the command to execute the cube plugin?

---

### Post by murataht on 2006-08-10
you can rotate cube with:
alt+ctrl+left/right arrow....

you can find more shortcut settings from:
[http://en.opensuse.org/Compiz](http://en.opensuse.org/Compiz)

for personal shortcut setting you should ckeck with gset-compiz. there is shortcut setting tool. 

good luck. 

PS: when i first heard about compiz, i tried it on kde. but not very lucky...
then i changed to gnome, and i am happy with both gnome and compiz+aiglx. things may have changed a lot. so hope you succeed.

---

### Post by lesemi on 2006-08-10
Thanks - 

compiz is working on my desktop (kde) it's wobbly - however what is the actual command to get the cube going - rotating it will come after.

---

### Post by MarkSheely on 2006-08-10
It should be enabled by default.  Try alt+ctrl+left/right arrow just to see if it works.  

--Mark

---

