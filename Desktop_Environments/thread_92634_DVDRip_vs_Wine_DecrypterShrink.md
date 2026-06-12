---
title: "DVD::Rip vs Wine Decrypter/Shrink"
date: 2005-11-20
forum: Desktop Environments
---

### Post by Stambo00 on 2005-11-20
Iv'e always had a little trouble burning with Decrypter/Shrink. 

Is DVD::Rip a good alternative? 
Can it burn protected material? 

This is the only thing stopping me from blowing away my Windows partition. :p

---

### Post by bionnaki on 2005-11-20
I heard good things about xdvdshrink - havent tried tho.
I use dvdbackup>dvdshrink>k3b - it's multistep, but works great.

---

### Post by Stambo00 on 2005-11-20
Thanx for the info, I'll give it a try and post back how it went. :smile:

---

### Post by manicka on 2005-11-20
DVD Shrink now works without problem (for me anyway) with the wine 0.9 beta release.

I use it to  make an iso then burn k3b for the burning step to backup dvd's

[http://doc.gwos.org/index.php/DVD_Shrink_Breezy](http://doc.gwos.org/index.php/DVD_Shrink_Breezy)

---

### Post by Stambo00 on 2005-11-20
I thought I would try the DVD Shrink wine option again first.

DVD Shrink wont recognise my drives even though i followed the instructions directed by the link provided. 

Any help?

---

### Post by Stambo00 on 2005-11-20
Please ignore my last post, my friend helped me solve it. Seems to be working so far!

---

### Post by Stambo00 on 2005-11-20
I was able to make the ISO from DVD Shrink in wine but when I open it up in K3b I get an error "not an Iso9660 image". I continue to burn anyway and the disc doesnt work. Any ideas what I could be doing wrong?

---

### Post by oskude on 2005-11-20
[QUOTE=Stambo00]I was able to make the ISO from DVD Shrink in wine but when I open it up in K3b I get an error "not an Iso9660 image". I continue to burn anyway and the disc doesnt work. Any ideas what I could be doing wrong?[/QUOTE]
i never burned dvd images, but
[QUOTE=http://en.wikipedia.org/wiki/Dvd]DVDs contain a file system, called UDF, which is an extension of the ISO 9660 Standard used for CD-ROMs.[/QUOTE]

---

### Post by manicka on 2005-11-20
[QUOTE=Stambo00]I was able to make the ISO from DVD Shrink in wine but when I open it up in K3b I get an error "not an Iso9660 image". I continue to burn anyway and the disc doesnt work. Any ideas what I could be doing wrong?[/QUOTE]

Try burning it with nautilus, by right clicking on the iso and choosing 'write to disc'

---

### Post by Stambo00 on 2005-11-20
I tried that too but nautilus tells me its an invalid disc image. Could I need to change any settings in DVD Shrink?

---

### Post by GazaM on 2005-11-20
Stambo00: how did you solve the problem with it not listing any of your drives? I have the same problem and cannot solve it :(

---

### Post by Stambo00 on 2005-11-20
[QUOTE=GazaM]Stambo00: how did you solve the problem with it not listing any of your drives? I have the same problem and cannot solve it :([/QUOTE]
I solved it by clicking file, then open, then my computer and then selected the appropriate drive (which in my case was F:)

---

### Post by fergus on 2005-11-20
Gaza,

I had a similar problem.  By default, when you add a drive to wine it thinks its a hard drive and not a cd-rom.  Try going into winecfg and to the devices tab.  Then enable the Advanced options and select your dvd drive.  It might be listed as a hard drive, change that to cd-rom and then DVD Shrink should pick it up.

---

### Post by manicka on 2005-11-20
Thanks fergus, I've added this tip to the main DVD Shrink / Wine how-to

[http://doc.gwos.org/index.php/DVD_Shrink_Breezy](http://doc.gwos.org/index.php/DVD_Shrink_Breezy)
[http://ubuntuforums.org/showthread.php?p=424283](http://ubuntuforums.org/showthread.php?p=424283)

---

