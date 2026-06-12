---
title: "How do I launch Penumbra after installation?"
date: 2007-05-10
forum: Gaming &amp; Leisure
---

### Post by KIAaze on 2007-05-10
How do I launch the game?

I have just finished installing it by using the shellscript as indicated [here]("http://frictionalgames.com/forum/showthread.php?tid=685"), but I can't find any launcher.

In my home directory, I have:
> >ls *umbra*
PenumbraDemo-Beta3.sh

PenumbraEp1Demo:
arch.tar


OS: Ubuntu Gutsy Gibbon

edit:
[Website]("http://frictionalgames.com/penumbra")
[The bittorrent link]("http://tracker.outoforder.cc/").
[http://frictionalgames.com/forum/showthread.php?tid=685]("http://frictionalgames.com/forum/showthread.php?tid=685")

---

### Post by aidanr on 2007-05-10
```
chmod +x PenumbraDemo-Beta3.sh
./PenumbraDemo-Beta3.sh
cd ~/PenumbraEp1Demo
./penumbrademo
```

---

### Post by KIAaze on 2007-05-10
Yes, but my problem is that I don't have the "penumbrademo" in the penumbra folder, even though the installer says that the installation was succesful...
I only have an "arch.tar", which is empty when I open it with the archive manager.

---

### Post by KIAaze on 2007-05-10
Aah, I'm blind!
I missed this:
> chcon: lib/libSDL-1.2.so.0: No such file or directory

Stupid GUI installer which hid my dropdown console and stupid me for not paying more attention to the console than to the GUI...

However, I'm still stuck:
libSDL-1.2 seems to be installed according to synaptic...

edit:
I think I found my problem:
> Ok, ok, I've finally found why the installer didn't work.. This is because my /tmp partition is only 256MB.. I ran the installer by changing the "--target" for uncompressing temporally files elsewhere.

Maybe Nixtaller should tell something when it doesn't succeed with the files extraction.
[http://frictionalgames.com/forum/printthread.php?tid=685]("http://frictionalgames.com/forum/printthread.php?tid=685")

> > df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             3.0G  2.7G  298M  91% /
varrun                220M  120K  220M   1% /var/run
varlock               220M  4.0K  220M   1% /var/lock
procbususb            220M  172K  220M   1% /proc/bus/usb
udev                  220M  172K  220M   1% /dev
devshm                220M     0  220M   0% /dev/shm
lrm                   220M   26M  195M  12% /lib/modules/2.6.20-9-generic/volatile
/dev/hda6              12G  9.3G  1.9G  84% /home
/dev/hda1              10G  8.6G  1.5G  86% /media/hda1
/dev/hda5             6.9G  6.7G  222M  97% /usr
/dev/hdc              4.4G  4.4G     0 100% /media/cdrom0


However, I am not willing to free any space right now to verify that this is the cause...
The official system requirements seem to be 400MB HD space.

re-edit:
No luck, after an apt-get clean:
> df -h /tmp
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             3.0G  1.3G  1.7G  44% /

And still no launcher.
A symbolic link to the libSDL 1.2 in /usr/lib from /lib also didn't do anything... :(

---

### Post by aidanr on 2007-05-10
see if the symlink /usr/lib/libSDL-1.2.so.0 exists, if not make it, for eg.
sudo ln -s /usr/lib/libSDL-1.2.so.0.11.0 /usr/lib/libSDL-1.2.so.0

the demo is pretty short, but awesome :-D, i'll buy it as soon as the linux build is done

---

### Post by KIAaze on 2007-05-11
It does exist, I already checked that. :(

---

### Post by weblordpepe on 2007-05-11
Theres gonna be a Linux build? Rad! It runs under Wine on nVidia cards anyway. At least on my 7600GT + AMD cpu.

---

### Post by aidanr on 2007-05-11
KIAaze, can't you try it on feisty, surely you're not running gutsy as your main/only os?

---

### Post by KIAaze on 2007-05-11
Yes, it's my main OS, otherwise I probably wouldn't be testing it much. ^^
I could try it on Debian though if I have enough space left on its partition.

But it's not catastrophic either if I don't play Penumbra now.

---

### Post by IamAcoconut on 2007-05-16
Same issue here! Though I'm using** Edgy Eft**
```
chcon: lib/libSDL-1.2.so.0: No such file or directory

```
Please, help us :(

---

