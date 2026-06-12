---
title: "warning  kernal 2.6.19 has problems with ide cd/dvd drives."
date: 2007-01-15
forum: Development CD/DVD Image Testing
---

### Post by ronacc on 2007-01-15
some motherboard and chipsets have problems with IDE cd or dvd drives under kernal 2.6.19 . this will cause the boot/install to fail after the initial menu. I have 1 box with an msi k8tneo2 amd 64 3000+ that will boot feisty herd2  and an msi k9vgm that wont , same ide dvd in both systems . distros other than those with a 2.6.19 kernal will boot on that box . installing a sata dvd drive allows feisty to boot on that box. see the sabayon linux forums for other mobo/chipsets that have problems with 2.6.19 as their new version has the same problem. this is a real stopper because most cd/dvd drives currently are ide and having ubuntu uninstallable on many systems would be a real disaster.

---

### Post by Sef on 2007-01-15
Thanks for that message.  Have a problem installing fiesty and if that is what is causing the problem.

Update:  Ran it a couple of more times and notice it fails when it says "Checking for CD-Rom."

---

### Post by ronacc on 2007-01-16
yep thats it, try the disk in another box , if it boots there you'll know for sure.

---

### Post by Sef on 2007-01-16
I have downloaded two different isos and both of them stop at the same spot.   Just wait till it is a little more updated and the problem fixed.

---

### Post by pochu on 2007-01-16
Hi.

The latest images have 2.6.20-rcX, and not 2.6.19.

So please search for that bug at Launchpad and if it hasn't been filed, do it. And if it has been, confirm it and write your problems/hardware/logs.

Thanks
Pochu

---

### Post by ronacc on 2007-01-16
you are right , I just checked with uname -r , reply is  2.6.20-5 generic  . Now this gets even more bizzare . after installing a sata dvd drive in the box that wouldn't boot feisty off of the ide dvd drive it now WILL boot from the sata dvd and the ide dvd both ??? 

I had made several attempts to boot from the ide dvd prior to installing the sata dvd and it would not boot the same cd that is now booting . the only change was that I also had a straight cd only drive on the same ide cable that I removed to open up a bay for the sata dvd . I wonder if that was causing the problem ? I'm too busy tonight to reinstall the cd drve and see what happens , 

my statement above still holds though , there are other reports of this no boot from ide cd/dvd in some systems so this could still be a real problem , as soon as I have more info  I will file a bug report.

PS I am neither drunk nor crazy .

---

### Post by pochu on 2007-01-16
> **ronacc said:**
> PS I am neither drunk nor crazy .
:D

---

### Post by DeeZiD on 2007-01-16
> **pochu said:**
> :D

Me either :D

---

### Post by DeeZiD on 2007-01-16
> **pochu said:**
> 
>  Originally Posted by ronacc  View Post
PS I am neither drunk nor crazy .:D

Me either :D

---

### Post by ronacc on 2007-01-16
by that I ment that I was correctly reporting the sequence of events. and that there is a problem , I just am not sure now what to ascribe it to.     as in my first post .

 box 1
msi k8tneo2 amd athalon 64 3000+  2 dvd drives (1 aopen SL  1 liteon DL) both ide both on same cable. .
2 ide  hd's both on same cable . 2 sata hd's . nvidia fx5200 128 mb . 2 gb ddr

this box would boot either feisty herd 2 or sabayon 3.26  right from the start

box 2
k9vgm athalon 64x2 3800+   1 dvd 1 cd  ( liteon DL , btc)  both ide on same cable
2 ide hd's both on same cable . 1 sata hd . nvidia nx7300le 128 mb . 1 gb ddr2.

 this box would not boot either feisty herd2 or sabayon 3.26  in this configuration using the same cd (feisty herd2 live/install) or dvd ( sabayon linux 3.26 )  that would boot on box 1. 

simply removing the btc cd drive and installing a sata dvd drive (samsung sh-s183) allows box 2 to boot . the cd drive (read only not a burner) is not defective , it will read cd's . also box 2 would boot edgy , suse 10.2 , puppy (several dots) , and sabayon 3.2 in the original configuration. it would not boot any distro that I tried that had a kernal later than 2.6.18 series. 

why simply removing the ide cd drive and installing a sata dvd drive would allow the IDE dvd drive to boot  >2.6.18 kernals is what is in question. I could understand if only the sata booted them , it is not the presence of 2 drives on the cable box 1 has 2 dvd drives and no sata(dvd) and does boot feisty etc. is it the combination of one dvd and one cd ? is it the presence of the sata dvd ?

I do know there are other posts in the ubuntu and in the sabayon forums describing exactly the same problem so it is not just me . When I have the chance to spen some time on it I will try several different configs ( IDE dvd only)(ide dvd ide cd +sata dvd) (2 ide dvd + sata dvd). and at that point file a bug report when I can give a better description than wont boot.

I keep mentioning sabayon because I first ran across this problem with it ,and I decided to try feisty to see if it was distro specific or a more general problem , I had intended to wait until feisty went beta.

---

### Post by pochu on 2007-01-17
Thanks for your test ronacc, but please, don't forget to report a bug at Launchpad, and provide all the info you can.

Regards
Pochu

---

### Post by ronacc on 2007-01-22
its been a couple of days but I finaly got a chance to try swaping some drives. it appears that it was the read only cdrom on the ide cable that was causing the problem.
removing the sata dvd and leaving the cdrom off of the ide cable , the ide dvd would boot feisty ok. putting the cdrom back on the ide cable would cause feisty not to boot even though distros with kernals 2.18 and earlier would boot (including edgy). the cdrom seems to be ok (it reads cds) so I have no idea why it causes problems with later kernals. when I get another chance Ill try a second ide dvd on that cable to try to determine wheather it is 2 devices on the cable or just the combo of a dvd and cd.

---

