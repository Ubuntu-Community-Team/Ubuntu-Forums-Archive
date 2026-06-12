---
title: "Making sure new layout configurations stick on the Mini 9"
date: 2009-01-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by magicfab on 2009-01-15
If anyone has problems changing the keyboard layout on Dell Mini 9 and having it stick after reboot, you may want to try this, after having configured any keyboard layout you want to use:

1) Go to System > Preferences > Sessions
2) Click on "Add"
3) Under "Name" enter "Keyboard layout setup"
Under "Command" enter /usr/bin/setxkbmap
Under "Comment" enter any comment 
4) Click on "OK" (don't press Enter), then "Close"
5) The new entry won't show up in the list. Go again to System > Preferences > Sessions and make sure it's listed there.
6) Click "Close"

I'd appreciate if anyone can confirm this works on the Mini 9 version of Ubuntu.

---

### Post by ex.pat on 2009-01-23
Hi Fab,

I have tried this and it seems to have worked so far. You are fantastic if this was the problem all along as I was getting somewhat annoyed with it continually resetting to US layout.

ex.pat

---

### Post by Seejayuu on 2009-02-26
Thanks Magicfab. Works for UK as well. delboy1 pointed me to your thread. Problems with " £ @
See: [http://ubuntuforums.org/showthread.php?p=6803093&highlight=Dell+Mini+keyboard+Layout=United+Kingdom+%22%A3@](http://ubuntuforums.org/showthread.php?p=6803093&highlight=Dell+Mini+keyboard+Layout=United+Kingdom+%22%A3@)

---

### Post by vickoxy on 2009-07-12
Thanks magicfab-it works well under Ubuntu 9.04 as well!

---

### Post by vickoxy on 2009-07-12
NOT SOLVED.

So, after restart, there is another Language option in keyboard layout, but as soon i start to type with external keyboard (apple) it dissapears.

Any clue?

---

### Post by Karan Sharma on 2011-10-10
type  sudo dpkg-reconfigure console-setup 
then select the language of keyboard

---

