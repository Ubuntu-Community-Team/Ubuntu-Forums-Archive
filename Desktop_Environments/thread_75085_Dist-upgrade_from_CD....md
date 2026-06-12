---
title: "Dist-upgrade from CD..."
date: 2005-10-13
forum: Desktop Environments
---

### Post by scorpio2002 on 2005-10-13
Hi there! I just dist-upgraded from a Cd and it went quite fine. There are some small issues I'd like to slove: first, even if i installed the usplash, I can't see any spalsh screen at the bootstrap.

Secondly, I'd like to substitute the old hoary repos with the new breezy repos...

---

### Post by scorpio2002 on 2005-10-13
one more thing: the openoffice implementation just looks awful: the icons in the toolbar are huge and don't seem to be the standard ones. 

The beta I got from an how-to in this forum that I used to use with hoary was really good.

---

### Post by Mustard on 2005-10-13
Here is a copy of breezy repos....

[http://paste.ubuntulinux.nl/2325](http://paste.ubuntulinux.nl/2325)

---

### Post by scorpio2002 on 2005-10-13
Well, they don't seem to be such complite repository with extras and so on, anyway for the moment I'm fine with them.

I noticed that dist-update didn't actually upgraded everything. For example, I'm still using the old kernel and I can't fine the new one in the repository... what a mess! :D

And again, usplash isn't working :|

---

### Post by nobby_trussin on 2005-10-13
i just did exactly the same. installed using upgrade (which went fine) and lo and behold i'm using the old kernel and X and Gnome and just about everything to be honest *sigh*

ah well, looks like i'll have to do a complete reinstall. oh goody. unless there's something i can do to get it to upgrade properly????

---

### Post by scorpio2002 on 2005-10-13
Yeah, distro-update doesn't work as it should. I guess it's better if they give up with it. Never heard about a successfully dist-update so I'm wondering what's the sense in carrying on something that's buggy and troublesome.

---

### Post by nobby_trussin on 2005-10-13
to be honest though mate, i only just looked at the date 5.10 was released. it was today. maybe they're still putting all the updates up. if you use ubuntu update manager and go to properties, the 5.10 stuff isn't even in the list. 

maybe in a few days?? i really can't be arsed reinstalling all my stuff

---

### Post by chanders on 2005-10-13
I noticed that you said that the splash is not working. One reason this can happen is if you have options passed to your kernel at boot time such as

 vga=xxx

to be more precise. If you do, try removing it and see if that helps.

---

### Post by scorpio2002 on 2005-10-14
Well, today I found a huge synaptic update (almost 200 paks). And now My ubuntu is working greatly: I've got the latest kernel, and the latest Gnome (even if the about dialog says I still have 2.12.1) and all the latest pakages: everything's working just fine. I'm sorry for criticizing dist-update, eventually it worked really fine I just had to wait :-)

Thank you for the great job guys :-) Ubuntu's the best!
bye,
Donato

---

### Post by ranf on 2005-10-14
[QUOTE=scorpio2002]Yeah, distro-update doesn't work as it should. I guess it's better if they give up with it. Never heard about a successfully dist-update so I'm wondering what's the sense in carrying on something that's buggy and troublesome.[/QUOTE]
I successfully upgraded from Warty and from Hoary to Breezy now. I wouldn't want Ubuntu if it was just another SUSE :-)

---

### Post by foxiness on 2005-10-14
[http://ubuntuforums.org/showthread.php?t=75414&highlight=usplash](http://ubuntuforums.org/showthread.php?t=75414&highlight=usplash)

---

