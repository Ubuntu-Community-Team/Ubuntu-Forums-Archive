---
title: "i think wubi screwedup my wireless"
date: 2009-01-04
forum: General Help
---

### Post by wkuace on 2009-01-04
I had a problem with my wireless in wubi. Here is the short and sweet version of what happened and the long version follows if its more help. OK.

 My RTL8187B card isn't friends with ubuntu, but it worked in live cd and for a few days in wubi. tonight it stoped and i couldn't establish connecions. had the same problem in vista. reinstalled the card driver in vista, now ubuntu won't load. is my wireless safe now in vista? I think i'm going to reinstall wubi to fix the boot problem.

i know that ubuntu and my RTL8187B wireless card don't have a great history. It worked just fine in the live cd. I then installed wubi as a baby step towards a duel boot. i've been using it lightly for a couple of days with now problems. Tonight i was surfing for a couple hours when proformance got slugish. i would click the network and reset connection, and close firefox and wait. it worked ok but the problem came back.after a few times of this i figured it was my router acting up. reset the router twice. same problem. about 30 min later internet just stops working. I try the same thing and get "cannot establish connection" (it still reads signal strength and network name) . i try several times even reboot, still nothing. i go to vista to try to ask a question on here and vistas wifi doesn't work either. (it detects signal strength, but cannot connect). i even move right next to my router. i go back to ubuntu and internet works. back to vista with fingers crossed no wifi. back to ubuntu download windows wifi card driver to flashdrive. back to vitsa and install driver. back to ubuntu which now works and check forums for help. reboot vista wifi works i tell forms everythings ok. back to ubuntu but now ubuntu won't boot. at the progress bar screen i press ctrl+alt+f2 to load(it freezes at about 3 blocks alot somebody told me about ctrl+alt+f2) it said somthing about a usb error( the wifi card is an internal usb) and won't boot past guess it doen't recgonize the "new" hardware and cant boot. i'm thinking reinstall wubi and pray this doesn't happen again. should i?
i'm going to a full duel boot as soon as i can find someone local to walk me though it (i would like to have someone next to me when partioning etc. for the first time). that should keep the drivers separate right?

sorry if it got a little confusing any help would be appriciated. thank you

ok i tried again to restart here is most of the error message i got i tried to write it on my arm and its dark so i didn't get a part of it.

[42.076046]usb-8(i think) device destination read/64 error-(somthing)  it keep repeating this with increasing values in the first brakets about 4-5 times before i shut it off

i don't know much but from what i saw and having just reinstalled the usb internal wireless card driver i'm guessing it cant find the card its looking for and cant go on till it finds it? would re-installing wubi fix this problem

---

### Post by x58 on 2009-01-04
Problem is; UPDATE MANAGER have next update: Network time protocol daemon and utility programs (Size:431 KB).If you make this upgrade, then you will have Internet connection problems.I cannot figure out what do too yet, but I working on it. I just reinstall everything from back up files and it working again.I just don't install now that upgrade, before problem is resolved.

---

### Post by PanicIRAQ on 2009-01-05
> **x58 said:**
> Problem is; UPDATE MANAGER have next update: Network time protocol daemon and utility programs (Size:431 KB).If you make this upgrade, then you will have Internet connection problems.I cannot figure out what do too yet, but I working on it. I just reinstall everything from back up files and it working again.I just don't install now that upgrade, before problem is resolved.

You're absolutely right.  I just installed ubuntu using Wubi and everything was working fine.  Internet, email, applications, etc. but then it said I needed to update so I figured, like MS Windows it would handle every update okay, well it didn't.  I've narrowed it down to two updates that will mess up your wireless connection thanks to your information:

avahi-autoipd
avahi-daemon

DO NOT INSTALL THESE UPDATES!!

---

