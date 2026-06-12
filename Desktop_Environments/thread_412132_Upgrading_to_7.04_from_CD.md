---
title: "Upgrading to 7.04 from CD"
date: 2007-04-17
forum: Desktop Environments
---

### Post by Magiczero on 2007-04-17
Hi

I have a question about upgrading to 7.04 on Thursday.  If I put the ISO on a flash drive & then burn it to a cd, Is there a way I can just upgrade to 7.04 from a cd?  If so, do I need the alternitave CD & what is the link to the download?

Thanks

---

### Post by phidia on 2007-04-17
In synaptic you can select Edit>Add CD-ROM
You would then need to comment out your repos in sources.list unless you want the upgrade to pull from there too. (I do it that way because I have a really slow internet connection)
"Mark all upgrades" "Apply" in synaptic should begin the upgrade from cd.
Or with apt  > sudo apt-cdrom add
> sudo apt-get update && sudo apt-get dist-upgrade
 
The download links should be here [http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)

---

### Post by Mana82 on 2007-04-20
where can i find this sources list ?

---

### Post by sethmahoney on 2007-04-20
> **Mana82 said:**
> where can i find this sources list ?

/etc/apt/sources.list

---

