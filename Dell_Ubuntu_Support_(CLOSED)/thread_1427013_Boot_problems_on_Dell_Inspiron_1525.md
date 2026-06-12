---
title: "Boot problems on Dell Inspiron 1525"
date: 2010-03-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by skoutariotis on 2010-03-11
I thought I was smart by installing ubuntu on my flash drive while in my Dell.
Well, that caused the dell to 'try' to boot to my flash drive and that's ok.
Then I realized the flash drive is ONLY ubuntu, not recognized by vista, so I formated the flash drive while in vista.
Now I cannot boot to my Dell.
it says...
GRUB loading
error: no such disk
grub rescue>
 
I just want my Dell back w/vista and I can boot ubuntu using a CD and later I'll install it on my older Dell Lattitude.
 
Even if I use the f12 key to boot to internal HD it still goes to grub. About the only thing I can do is boot to my ubuntu CD.
Even if I change my bios to boot to internal HD it still goes to grub.
 
If anyone can help will be greately appreciated!
 
Thank you in advance for any assistance.

---

### Post by mikewhatever on 2010-03-11
This is a common mistake people make, installing Ubuntu on an external device, and not changing the default location of Grub. Anyway, no worries, you Vista should still be intact, and all you have to do is restore its boot loader to the MBR of the hdd. I won't pretend I know anything about Vista, but here are some suggestions by others.
[http://members.iinet.net.au/%7Eherman546/p18.html#Vista_Recovery_CD_Method](http://members.iinet.net.au/%7Eherman546/p18.html#Vista_Recovery_CD_Method)
[http://ubuntuforums.org/showthread.php?t=482798&highlight=grub](http://ubuntuforums.org/showthread.php?t=482798&highlight=grub)

---

