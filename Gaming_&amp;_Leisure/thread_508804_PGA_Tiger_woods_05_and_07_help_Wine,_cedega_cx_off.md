---
title: "PGA Tiger woods 05 and 07 help Wine, cedega cx office."
date: 2007-07-24
forum: Gaming &amp; Leisure
---

### Post by bobbymcsteels on 2007-07-24
Hi
Right my friend is trying to get me to switch from Dual booting Windows and linux, mainly using Windows to just using Linux (actually he trying to get me to buy a mac but hey). But my main argument is that most apps I want to work or use in Linux don't run.
So i have been trying to install Tiger woods pga tour both 2005 and 2007 using Wine, Cedega and CX office and not having any success with any of the progs.
Cedega:-
I thought cedega is prolly the best choice to use as it is meant for gaming but When I try to install TW07 using Cedega The installer gets so far and then asks me to install directx 9.0c which fails to install thus making the rest of the installation fail. TW05 ask to install Directx 8.1 i think it is and i selected cancel and it started to install and got on to the 2nd disc and got halfway through that disc and then failed.

Wine:-
Neither games worked

CX Office:-
Same as Cedega.




All the other games I have wanted to install seem to be working fine but TW just doesn't want to work and the cedega forums is taking way too long to get an answer. And preferably i would like TW06 to work but I'm not really too fussed which one I can get working.
So any help with this would be great and thanx in advance:D

---

### Post by bobbymcsteels on 2007-07-25
can anyone help?

Bump

---

### Post by tsav87 on 2007-07-26
I was never able to get any windoze platform game to install from a disk, especially a multi disk game.  I used Steam, as you saw on the other post, and it downloads and installs all at once and doesn't give any problems.

The only draw back here is that you already bought the game from a store, you will have to buy it again from Steam.

---

### Post by hikaricore on 2007-07-26
> **tsav87 said:**
> I was never able to get any windoze platform game to install from a disk, especially a multi disk game.  I used Steam, as you saw on the other post, and it downloads and installs all at once and doesn't give any problems.

The only draw back here is that you already bought the game from a store, you will have to buy it again from Steam.

I wasn't aware that Steam supported Tiger Woods games O.o

Anyway... heh

The only Tiger Woods titles I can find on the [WINE Application Database]("http://appdb.winehq.org") are:

Tiger Woods '99: [http://appdb.winehq.org/appview.php?iVersionId=2047](http://appdb.winehq.org/appview.php?iVersionId=2047)

and

Tiger Woods '00:[http://appdb.winehq.org/appview.php?iVersionId=980](http://appdb.winehq.org/appview.php?iVersionId=980)



It looks like Woods '99 runs /w WINE, the other one doesn't.
It's more than likely that you will not be able to play the newer games with anything WINE based, but I could be wrong.

---

### Post by tsav87 on 2007-07-26
Your right, they don't, I just assumed.

---

### Post by bobbymcsteels on 2007-07-26
Yeah I have steam with dods that I installed from the disc and i have installed it by downloading via steam a while ago. But  I have a couple of games installed  that I have installed from disc as well, all using cedega.

But is there anyway for me tell or trick cedega into thinking that I have Directx 9.0c installed? As I think i tried with an earlier version of cedega and had it installed without having to install DX9.0c

---

### Post by hack_benjamin on 2007-07-27
Cedega *has* D3D9 (their own version), check that d3d9.dll and d3d8.dll are in <fake C>:/system32/

If they're not there then you can probably get it from *cough* FileHippo*cough* (sorry, I'm not sure whether they redirect you to MSDN for validation - if this is a bad thing then I hope the admin blur it out, I'm not too sure on the rights on distributing DX) and perform something like:

```
 
cedega -install "The Game That Needs IT" /Path/To/directx<version>redist.exe 

```

then try and install it again.

This is for everyone except Bobby (I am the friend in question :KS), and this Tiger Woods thing is the only problem I've ever had with gaming on linux, so persevere, and you'll be rewarded.

---

### Post by hack_benjamin on 2007-07-27
It seems that if you run it from the command line as above then either it will install DX cleanly or it will have a problem with ddraw16.dll, which I'm going to work on.

But for now I sleep.

I'll keep you posted

---

### Post by atomkarinca on 2007-07-27
i once tried this and worked without hacking anything apart from cedega. under edit > global settings > general tab change winver from winxp to win2k (if doesn't work try win98). this works in most cases.

---

### Post by hack_benjamin on 2007-07-28
Works flawlessly on my xubuntu (partitioned mac os to try it)

Seems there is something wrong with your cedega (and I used win98)

---

