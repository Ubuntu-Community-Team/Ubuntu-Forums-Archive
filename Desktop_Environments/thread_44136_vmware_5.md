---
title: "vmware 5"
date: 2005-06-24
forum: Desktop Environments
---

### Post by somuchfortheafter on 2005-06-24
well i just got a copy of vmware workstation 5 however I have not had a chance to install the software yet.. My main question is, can I use itunes in vmware to keep my ipod maintained/update/etc ?

---

### Post by flankk on 2005-06-24
[QUOTE=somuchfortheafter]My main question is, can I use itunes in vmware to keep my ipod maintained/update/etc ?[/QUOTE]

Yes you can, but you might find it easier to just use native Linux software.

---

### Post by somuchfortheafter on 2005-06-24
well xp pro is now installing under vmware and well i would use gtkpod with crossover office but it still doesnt solve my problem of listening to the music so i am attempting to correct it with the use of vmware, so far everything is running smoothly , there was an error about a sound server but that im sure can be fixed with little trouble...

---

### Post by kassetra on 2005-06-24
[QUOTE=somuchfortheafter]well i just got a copy of vmware workstation 5 however I have not had a chance to install the software yet.. My main question is, can I use itunes in vmware to keep my ipod maintained/update/etc ?[/QUOTE]

Yes you can.  You have to enable usb support in vmware (it's best to have your iPod plugged in before booting the guest system... so that the usb drivers are loaded as windows loads), but as long as windows/vmware sees the iPod, iTunes can take care of it just fine.

You *are* using a usb iPod, right?

---

### Post by kassetra on 2005-06-24
[QUOTE=somuchfortheafter]well xp pro is now installing under vmware and well i would use gtkpod with crossover office but it still doesnt solve my problem of listening to the music so i am attempting to correct it with the use of vmware, so far everything is running smoothly , there was an error about a sound server but that im sure can be fixed with little trouble...[/QUOTE]

Listening to music through iTunes -> winxp as guest of -> vmware running on a -> linux system is ... shaky at best.

My iTunes sound pretty bad, and little spikes in activity (i.e. moving from vmware to another desktop or opening an app) ... causes your music to stop / skip / etc.  And the quality is nothing to write home about, having to go through all of those layers.

If you want to listen to your music, have iTunes in winxp guest sync up to your iPod, and then just plug your speakers into your iPod... honestly.  (legally)

---

### Post by somuchfortheafter on 2005-06-24
how did you get past the dsp error in ubunt about the sound system already running?
 besides killall esd?

---

### Post by shapelessplanet on 2005-09-19
Sorry to dig this up, but were you able to sync your USB iPod with itunes in vmware? 

The way I understood it was that you had itunes installed in XP installed in VMware installed in linux. Were you able to sync the ipod? I'm totally tired of gtkpod, and I can't get itunes to manage my library through a samba share, so I want to just use VMware.

Thanks!
Shapeless Planet

---

### Post by jgomo3 on 2005-09-19
Ok, i don´t have an ipod and i didn´t thik to buy one becouse I thought it couldn´t be listened on ubuntu, until i was told rhythmbox supports it. My question is: does it or not?

excuse my english.

---

### Post by wmcbrine on 2005-09-19
[QUOTE=somuchfortheafter]i would use gtkpod with crossover office[/QUOTE]Huh? gtkpod is native. You don't need Crossover Office for it.

As for esd, I ditched it early on, for other reasons. It gave me nothing but trouble.

---

### Post by zenwhen on 2005-09-19
[QUOTE=wmcbrine]Huh? gtkpod is native. You don't need Crossover Office for it.

As for esd, I ditched it early on, for other reasons. It gave me nothing but trouble.[/QUOTE]


He probably meant iTunes. I used gtkpod when I had an iPod and it worked really well for my needs.

---

