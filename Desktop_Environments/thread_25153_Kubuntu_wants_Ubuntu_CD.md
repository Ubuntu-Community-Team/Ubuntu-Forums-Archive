---
title: "Kubuntu wants Ubuntu CD?"
date: 2005-04-09
forum: Desktop Environments
---

### Post by Breepee on 2005-04-09
Hey everybody,

After using warty experimentally I decided to try out KDE, Kubuntu Hoary off coure :) I've just downloaded the iso and burned. When I put it in and boot, it says it can't find the Ubuntu CD and can't add it to it's sources... Well, of course it can't find it, it's Kubuntu. I've searched to forums for a solution, but I couldn't find a similar experience so I'm asking, what must I do?

---

### Post by scottlc on 2005-04-09
[QUOTE=Breepee]Hey everybody,

After using warty experimentally I decided to try out KDE, Kubuntu Hoary off coure :) I've just downloaded the iso and burned. When I put it in and boot, it says it can't find the Ubuntu CD and can't add it to it's sources... Well, of course it can't find it, it's Kubuntu. I've searched to forums for a solution, but I couldn't find a similar experience so I'm asking, what must I do?[/QUOTE]
 There's no need to download the Hoary ISO to upgrade. Switch the Warty repositories with the Hoary ones then:

sudo apt-get dist-upgrade

---

### Post by Breepee on 2005-04-09
[QUOTE=scottlc]There's no need to download the Hoary ISO to upgrade. Switch the Warty repositories with the Hoary ones then:

sudo apt-get dist-upgrade[/QUOTE]
I'm installing onto a new (clean) computer.

And the question still stands. How does one install Kubuntu 5.04 from CD (since it asks for the Ubuntu CD)? Or was that done on purpose and must I download both CD iso's?

---

### Post by dermotti on 2005-04-09
My kubuntu cd never asked that.

---

### Post by Breepee on 2005-04-09
It says it's detected a non-Ubuntu disc to be precise... I downloaded the iso straight from the UK mirror and burning went OK.

---

### Post by scottlc on 2005-04-09
[QUOTE=Breepee]It says it's detected a non-Ubuntu disc to be precise... I downloaded the iso straight from the UK mirror and burning went OK.[/QUOTE]
Did you make sure that the checksum matched? If it does match, you might want to try reburning at a lower speed. If it doesn't, then you'll have to redownload.

---

### Post by Breepee on 2005-04-10
Checksum is OK, I burned it at the lowest speed setting, no luck. By the way, I've never ever burned a faulty disc on that burner I use, at any speed.

The CD just checks out. I think it's a bug of some kind?

---

### Post by Breepee on 2005-04-10
Anyone?

---

### Post by Breepee on 2005-04-11
Burned on another disc a the lowest speed setting; exactly the same error. Precisely the same bit wrong is p<0.00001 so it's software related I think.

---

### Post by Breepee on 2005-05-11
[QUOTE=Breepee]Burned on another disc a the lowest speed setting; exactly the same error. Precisely the same bit wrong is p<0.00001 so it's software related I think.[/QUOTE]
 Is this fixed yet?

---

### Post by arbearce on 2005-05-11
I downloaded the ISO image for x86 and amd64 though bittorrent and didn't have any problems with the install. Though this doesn't help you with your problem but I never had a problem with the Kubuntu cds I've burned.

---

### Post by Kurse on 2005-05-11
You could just install Ubuntu, then apt-get kubuntu-desktop to install KDE

---

### Post by bt300td on 2005-06-26
hello,

I had the same problem; burning with nero as disc-at-once/96 instead of disc-at-once solved the problem for me.

regards
bt300td

---

