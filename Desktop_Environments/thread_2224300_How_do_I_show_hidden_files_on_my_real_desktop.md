---
title: "How do I show hidden files on my real desktop?"
date: 2014-05-15
forum: Desktop Environments
---

### Post by sanssadness on 2014-05-15
How can I show hidden files on the real desktop of Ubuntu 14.04? Right now, I can see hidden files only by browsing to my desktop's directory manually, but this is a waste of time. Is there a setting somewhere that lets me see hidden files on my actual desktop?

---

### Post by keratos2 on 2014-05-15
You can do this; but it depends on which desktop you are using:

XFCE?
Unity?
PlasmaKDE?
MATE? 
Cinnamon?
etc...

---

### Post by sanssadness on 2014-05-15
To be honest I really don't know. I am a Linux noob. What desktop comes default with Ubuntu 14.04? If I had to guess, I'd say Unity.

---

### Post by papibe on 2014-05-16
Hi sanssadness.

Open Nautilus (the file manager). Either hold the Alt key, or put the mouse over the top bar so you can get to the menus. Select:
```
Edit -> Preferences
```
A new windows will open> Go to the 'View' tab, and check the box 'Show hidden and backup files'.

I hope that that is what you are looking for. Let us know how it goes.
Regards.

---

### Post by keratos2 on 2014-05-16
he probably doesn't know if he's using nautilus or not
probably better off editing his .config/.. files

---

### Post by bapoumba on 2014-05-16
From the OP, I understood they wanted to see hidden files on the desktop, no in a file manager. I looked around a bit but have not found how to do this (there is a config for the Finder in OSX that allows to show .files directly on the desktop for ex).

---

### Post by keratos2 on 2014-05-16
> **bapoumba said:**
> From the OP, I understood they wanted to see hidden files on the desktop, no in a file manager. I looked around a bit but have not found how to do this (there is a config for the Finder in OSX that allows to show .files directly on the desktop for ex).
nautilus can manage the desktop

we need to know what desktop he's using - unity seems the obvious candidate, but as a time served s/w engineer with 35+ years experience behind me - I never assume anything in S/W !:-)

---

### Post by bapoumba on 2014-05-17
> **keratos2 said:**
> nautilus can manage the desktop

we need to know what desktop he's using - unity seems the obvious candidate, but as a time served s/w engineer with 35+ years experience behind me - I never assume anything in S/W !:-)
Thanks :)
Yes I know that but after looking around I did not find a quick way to do it. May be my search-fu failed me. Then looked for PCManFM that I am using, just to learn as I prefer an empty desktop. So i'll follow here.

---

### Post by 3rdalbum on 2014-05-17
When you are on the desktop (i.e. with no other programs in front) press Control-H to toggle hidden files.

---

### Post by sanssadness on 2014-05-19
bapoumba is right. I'm trying to view hidden files on my real desktop, and not just with Nautilus; yes, I do know what Nautilus is.

If there's no way to do this, then there's no way to do it. I don't think your search-fu failed you bapoumba. Sometimes something just doesn't exist, and that's that.

---

### Post by bapoumba on 2014-05-19
@sanssadness : if you installed the regular Ubuntu, without explicitly choosing [one of the flavors]("https://wiki.ubuntu.com/UbuntuFlavors"),  you are probably using unity, does it look like this ? [https://unity.ubuntu.com/about/](https://unity.ubuntu.com/about/)

Thing is, different flavors or desktop environments manage the desktop different ways.

I was referring to the Finder for Mac OSX which can do this for ex (there is a screenshot) : [https://discussions.apple.com/message/25426964#25426964](https://discussions.apple.com/message/25426964#25426964)
I suppose this is what you want to set up. If it is possible, some people here will most probably know about it :)

Edit : reading your previous post over, if you ever want to run a graphical application as root, please use gksudo and not sudo : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sanssadness on 2014-05-19
Yep! I took a look at your screenshot, and there is no doubt I am using Unity. Thanks! If you couldn't find a way to show hidden files on Unity's desktop, it probably doesn't exist. By the way, I also Googled quite extensively for this information before I posted here. I only asked for help after I had exhausted all the results on these forums and probably a number of other top results.

There's still one piece of information I have to investigate though. 3rdalbum mentioned that Ctrl + H can toggle the view of hidden files. I'm trying to find a hidden file right now so I can test whether it works for Unity, and whether the toggled setting sticks after a reboot.

Edit: I just finished a very simple test. Ctrl + H doesn't work on Unity desktop. I created a Test.txt~ file on Unity desktop, which immediately disappeared from view. It was still visible in Nautilus, so I know it exists. But Ctrl + H on my desktop failed to bring it back. Ctrl + H does toggle hidden files in Nautilus though; I managed to hide and then bring back the test file when in Nautilus.

---

### Post by bapoumba on 2014-05-19
> **sanssadness said:**
> Yep! I took a look at your screenshot, and there is no doubt I am using Unity. Thanks! If you couldn't find a way to show hidden files on Unity's desktop, it probably doesn't exist. By the way, I also Googled quite extensively for this information before I posted here. I only asked for help after I had exhausted all the results on these forums and probably a number of other top results.

There's still one piece of information I have to investigate though. 3rdalbum mentioned that Ctrl + H can toggle the view of hidden files. I'm trying to find a hidden file right now so I can test whether it works for Unity, and whether the toggled setting sticks after a reboot.

<ctrl> H will work with most file managers. It allows to show hidden files. It will be remembered until you hit <ctrl> H again to turn it off :)

---

