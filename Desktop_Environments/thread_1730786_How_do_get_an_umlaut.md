---
title: "How do get an umlaut ?"
date: 2011-04-16
forum: Desktop Environments
---

### Post by Orange Kingdom on 2011-04-16
Hi,

I have some songs with umlaut characters in it but they show as little questionmarks in Nautilus and in the terminal.

How do i get the correct characters with umlauts?

I am using the US int. keyboard layout.

---

### Post by Enigmapond on 2011-04-16
Without changing the keyboard layout, just right-click on the top or bottom panel/Add to Panel/Character Palette. This gives you choices of all different characters. Hope this helps.

Cheers!

---

### Post by Orange Kingdom on 2011-04-16
thnx, but this does not give me a listing with the umlauts in Nautilus.

for example :  Die Sch&#65533;ne M&#65533;llerin D795 - Wohin.flac 

must be an o- umlaut and an u- umlaut.

Or do i have to change all this characters manually?

---

### Post by Enigmapond on 2011-04-16
Right this way you would have to go character by character. If you need to make it more permanent, you would need to add German to the System Language Support and Keyboard Layout.

---

### Post by Krytarik on 2011-04-16
I don't have German language support installed, and the few umlauts I have are displayed correctly. But I had those issue some years ago. I believe the clue was/is to mount the concerning partition/s with the option "utf8", similar to this:
```
/dev/disk/by-uuid/107C-26F4  /media/Data     vfat    user,utf8,umask=007,uid=1000,gid=46 0       0
```[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://manpages.ubuntu.com/manpages/maverick/en/man8/mount.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/mount.8.html)

Greetings.

---

### Post by Orange Kingdom on 2011-04-16
I have in /etc/default/locale  already  LANG="en_US.UTF-8"
Is that the same?

---

### Post by Krytarik on 2011-04-16
> **Orange Kingdom said:**
> I have in /etc/default/locale  already  LANG="en_US.UTF-8"
Is that the same?
Nope, please read the guide. It's about filesystem mount options, not language support.

---

### Post by sonoftherighthand on 2011-11-11
Check out the compose key. Go to System->Preferences->Keyboard, go to the Layouts tab, click Options…, and expand Compose key position (at least, this is what it is in Meerkat). 

After defining the compose key, you can use the handy chart over here ([http://en.wikipedia.org/wiki/Compose_key](http://en.wikipedia.org/wiki/Compose_key)) to make all sorts of symbols.

For umlauts, though, press compose + " followed by the desired vowel.

---

