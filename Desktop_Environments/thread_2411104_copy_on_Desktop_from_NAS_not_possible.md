---
title: "copy on Desktop from NAS not possible"
date: 2019-01-24
forum: Desktop Environments
---

### Post by heidelxyz on 2019-01-24
[ATTACH=CONFIG]282307[/ATTACH]
Hi there,
i installed Xubuntu 18.04.1 an connected two NAS, not via fstab but via file manager thunar and alternatively via caja. Read/Write acess on the nas (FritzBoxNAS and XigmaNAS) functions properly. But i cannot copy files from/to nas e.g. to/from desktop or other directories. It´s possible to copy single files, but not whole folders. The process stops always after one file (see attached screenshot). Copying via gnome-commander (not in su mode) is no problem. And the same process functions also correctly e.g. in ubuntu mate, but not in xubuntu. I reinstalled and tried several times. Because i am a newbie in this issue i have no idea what i made wrong or what i should to:(. I also know, that there has been a similar post two years ago, but without functioning solution - but maybe someone has got a good idea!
 It would be very great, if someone could help me -thanks very, very much.:)

---

### Post by Autodave on 2019-01-25
For what its worth, I actually had a similar problem.  It lasted for 2 days.  Without reason, I could not copy or move files from my desktop, but then after a couple of days it statrted working again.  You may want too check for updates and also try rebooting the machine.

---

### Post by sawozny on 2019-01-26
I have also been having NAS difficulties since installing Ubuntu 18.04.  I'm going to post a more detailed question about it now that I have something I can consistently repeat, but I was looking at general NAS weirdness problems in the forum and yours seems to qualify.  I have no help to offer, but I feel your pain.  :)  Perhaps you can try the steps I put in my post and see if you have the same issue as I do.

---

### Post by heidelxyz on 2019-01-27
Thanks very much, i already did so, but it didn´t function. I think i´ll stay by ubuntu mate, an try xubuntu again sometime later.

---

### Post by him610 on 2019-01-27
I have had a fileserver running freenas v0.7 for about 8 or 9 years now, mostly trouble free. 
Which nas operating system software are you using?
Which sharing protocols (cifs/smb or nfs) do you have configured on FritzBoxNAS and XigmaNAS?
What do you enter into the address bar in Thunar to get to either of your two nas devices? Mine looks like this, *smb://freenas0/fileserver/* with *freenas* being name I have given my nas device and *fileserver* being top level directory.

Added - I just discovered that XigmaNAS is successor to nas4free. Website: [https://www.xigmanas.com/index.php?id=17]("https://www.xigmanas.com/index.php?id=17")

---

