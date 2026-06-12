---
title: "Help connecting to Linux box from Windows!!!"
date: 2005-12-19
forum: General Help
---

### Post by winProLinuxNoob on 2005-12-19
Ok folks, here is my dilemma... I have Ubuntu and XP dual boot on my laptop, but unfortunately, I cannot get my wireless to work in Ubuntu (IPW 2200), and none of the posts here ACTUALLY get it working for me. I also have Ubuntu and XP dual boot on a box elsewhere in my house which is on a LAN. I use XP as a print server for the rest of the computers in the house, and I am slowly learning to do this efficiently in Ubuntu, so here is what I decided I want to do:  _I would like to be able to log into the Ubuntu box, from XP on my laptop (because wireless works on laptop in XP). _ Any help would be greatly appreciated. I am really new to linux so please do not be to vague. I would like to be able to have a complete remote desktop (gnome), but if I can only get terminal, that would be ok. Thanks all.

---

### Post by out180 on 2005-12-20
Simple, the best solution IMO is FreeNX.  Follow the howto linked below.

[General - HOWTO: Install FreeNX]("http://www.ubuntuforums.org/showthread.php?t=97277&highlight=freenx")

This will give you a complete remote desktop solution that is ~fast~.  You can download the client application from the [www.nomachine.com](www.nomachine.com) website.

The seveas repository seems to be lagging at the moment.  If you have trouble with the 'apt-get update' step hanging just wait for a little bit and try again.  It will work once they get the repository back up.

---

### Post by winProLinuxNoob on 2005-12-20
I will check that out, thank you very much. BTW, is this a common thing that I am trying to do? I would think it would be just because Unix/Linux is very popular for servers, and I am sure I am doing this somehow when I connect to my school terminal.

---

### Post by out180 on 2005-12-20
Very common.

---

### Post by BathroomNinja on 2005-12-20
Common enough that I use it sometimes.

---

### Post by out180 on 2005-12-20
I also wanted to let you know that if you continue to have trouble with the seveas repository you can use the one below instead.

deb [http://free.linux.hp.com/~brett/seveas/freenx/](http://free.linux.hp.com/~brett/seveas/freenx/)  ubuntu-seveas freenx

You'll get GPG errors on apt-get update unless you import the key.  You can ignore the errors if you want, it will still work.

---

