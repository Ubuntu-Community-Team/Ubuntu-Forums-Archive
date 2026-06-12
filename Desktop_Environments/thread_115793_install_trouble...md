---
title: "install trouble..?"
date: 2006-01-11
forum: Desktop Environments
---

### Post by donnym on 2006-01-11
I've been trying to install Ubuntu 5.10 off & on over the last couple of days.. When I install the disk in the drive & reboot it doesn't automatically start ,how do I install this from the disk ..? .. What am I doing wrong..?

I've did a search & read 100's of these forums none were any help..

---

### Post by kaamos on 2006-01-11
Did you burn the cd as an image? [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)
Did you set your BIOS to boot from the cd?

---

### Post by canadianwriterman on 2006-01-11
[QUOTE=kaamos]Did you burn the cd as an image? [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)
Did you set your BIOS to boot from the cd?[/QUOTE]

I agree. The first stp is to determine if you burned the CD correctly from the ISO you downloaded. To check that, open the install CD and look at the files on it. If there is only one (the ISO file), then you need to reburn the install CD as an image.

Then you can check to ensure that the CD is set for booting in the system BIOS.

---

### Post by frodon on 2006-01-11
Here his a nice guide about installing ubuntu, you will find in most of needed informations (including how to force your BIOS to boot on the CD) : [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by donnym on 2006-01-11
I didn't burn the CD..I received 5 CD's in the mail .. And tried to install 1... It said on the package to reboot and it will automatically install..

---

### Post by Thirsteh on 2006-01-11
Enable CD boot in your BIOS. If you don't know how, get a friend who knows to do it. There's 80% certainty that that's what you need to do.

---

### Post by J77 on 2006-01-11
You need to burn the CD as a 'bootable CD/DVD'

ie. Nero does this if you enable the 'advanced' options layout to their gui.

Once your CD is **bootable**, you can then go into the BIOS menu to tell it to boot from CD first.

---

### Post by donnym on 2006-01-11
Ok I will try that .. This came with 2 CD's 1 is a live CD to test try the program..the other CD is an install CD that says it will automatically install ..

---

### Post by J77 on 2006-01-11
[QUOTE=donnym]Ok I will try that .. This came with 2 CD's 1 is a live CD to test try the program..the other CD is an install CD that says it will automatically install ..[/QUOTE]mmm... If you received physical CDs (ie. didn't download and burn the yourself) I guess they should be bootable already.

Like above, go into the BIOS options (F12 on my machine when on initial splash screen) and change boot order...

---

