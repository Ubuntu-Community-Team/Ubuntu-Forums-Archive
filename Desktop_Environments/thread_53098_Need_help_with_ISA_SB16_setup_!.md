---
title: "Need help with ISA SB16 setup !"
date: 2005-07-30
forum: Desktop Environments
---

### Post by kjelland28 on 2005-07-30
Hi !
I have installed Kubuntu on an old Compaq deskpro it has a very old SB card
and it does not give me a single beep in Kubuntu but in Mandriva i can set it up with sndconfig. 
How will i get it to work under Kubuntu ?
i tested something from the forum 
modprobe snd-sb16;modprobe snd-pcm-oss and got the answer back
fatal: error inserting snd_sb16 (path to module): no such device
fatal: error install command for snd_sb16
Please help me with this !
thanks in advance Kjell Andersson

---

### Post by heimo on 2005-07-30
How about *modprobe sb*?

---

### Post by kjelland28 on 2005-07-30
Nope didn't work  i dont think there were such module or something !

---

### Post by heimo on 2005-07-30
Hmm... I do have sb module (but it's not in use). You could install isapnptools and run pnpdump to get some more information. Does is it show any information of the card?

---

### Post by az on 2005-07-30
Alsa sound is muted by default. Run alsamixer in the console to unmute your sound


[https://wiki.ubuntu.com/forum/hardware/OldSoundCard](https://wiki.ubuntu.com/forum/hardware/OldSoundCard)

---

### Post by jeff2292000 on 2005-07-30
On the point of installing isapnptools, how does one do that? I've tried:
sudo apt-get install isapnptools

but get an error:
E: Couldn't find package isapnptools

Jeff




[QUOTE=heimo]Hmm... I do have sb module (but it's not in use). You could install isapnptools and run pnpdump to get some more information. Does is it show any information of the card?[/QUOTE]

---

### Post by heimo on 2005-07-30
Oh! It's in universe. You need to add extra repositories:
[http://www.ubuntuguide.org/#repositories](http://www.ubuntuguide.org/#repositories)

---

### Post by moopere on 2005-07-30
[QUOTE=kjelland28]Hi !
I have installed Kubuntu on an old Compaq deskpro it has a very old SB card
and it does not give me a single beep in Kubuntu but in Mandriva i can set it up with sndconfig. 
How will i get it to work under Kubuntu ?
i tested something from the forum 
modprobe snd-sb16;modprobe snd-pcm-oss and got the answer back
fatal: error inserting snd_sb16 (path to module): no such device
fatal: error install command for snd_sb16
Please help me with this !
thanks in advance Kjell Andersson[/QUOTE]

Do you know what sort of sound blaster you have?  Is it PnP or not?  This post might help you if its really old and _not_ PnP:

[http://www.ubuntuforums.org/showthread.php?t=24586&highlight=sound+blaster+16](http://www.ubuntuforums.org/showthread.php?t=24586&highlight=sound+blaster+16)

Go down to post number 8.

Cheers,
Craig

---

### Post by jeff2292000 on 2005-07-30
Thanks.... isapnptools successfully added.

---

