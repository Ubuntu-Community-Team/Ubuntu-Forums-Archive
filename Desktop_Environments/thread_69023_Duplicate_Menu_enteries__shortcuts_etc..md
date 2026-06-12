---
title: "Duplicate Menu enteries / shortcuts etc."
date: 2005-09-25
forum: Desktop Environments
---

### Post by uthfull on 2005-09-25
I recently installed amaroK.
It installed all the dependencies.

But it still wudnt play with gstreamer.
I decided to install xine.

After a lot of effort.... I was able to install amaroK with xine.... but it installed XMMS amaroK-arts n gstreamer again with it.

Now if I remove XMMS.... which freezes n doesnt play ne files.... it tells me that all dependencies.... xine etc.. will b removed.
Now how do I remove it safely.

Also, the sound output in amaroK is perfect while its distorted in all players instaleld by default n even the sound notifications in gaim r distorted.

Further... while installing amaroK... synaptic messed up gaim. It did something to the package gaim-data.

Now it wudnt download or update it or gaim.

So I download the .autopackage from the gaim website.
It reinstalled Gaim to the newest version successfully. 
But now two gaim enteries appear in Applications -> Internet.

I navigated to /usr/share/applications and tried to move one shortcut to trash... but it said I didnt have the required persmissions?

Now how do I do it.
Also how do I delete files n folders frm the command line which have names with spaces like "I Love You" ??

Thanks.

---

### Post by uthfull on 2005-09-25
nebody there?!

---

### Post by uthfull on 2005-09-26
Thanks everybody for yer replies!!
:(

---

### Post by FLeiXiuS on 2005-09-26
Why not install them via aptitude? 

Apt-get is your friend!  Be patient, the answers are out there! :-)

---

### Post by uthfull on 2005-09-27
dude gives errors too for most upgrades.

Like it won;t upgrade my gimp... n chooses to "keep it back".

---

### Post by brentoboy on 2005-09-27
I have had problems with synaptic if I don't have all the sources selected for each of the servers.
In the repositories area of the synaptic setup, make sure for each source you have main restricted universe multiverse.  It seems like some of the dependencies are not always in the Fully supported list for some stuff.

Then, in your synaptic settings area, tell it that you want recommended options to be treated as dependencies, I have noticed that if something is recommended, then the app that *could* use it only semi functional without it.

Once I started polling from all their sources, and requiring recommended packages to be installed, synaptic became my new best friend.

Oh, almost forgot - once you make those changes, any app that gives you a hard time, do a complete removal of it, and then reselect it.  That should fix most any package.

---

