---
title: "skype 2.0 for Linux"
date: 2009-06-09
forum: General Help
---

### Post by chebbie on 2009-06-09
hey guys i've downloaded [http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/) and choose the Ubuntu Package since I've an Ubuntu Release 9.04 (jaunty) GENOME 2.26.1 and I think a 64bit version.  sorry for all these details but i'm just new.
so, i've downloaded the .deb file and tried to install it but it's giving as error: Wrong architecture 'i386'.
what does that suppose to mean?
can't I never install Skype for use on my ubuntu?

---

### Post by whitethorn on 2009-06-09
You just need to add the medibuntu repository.  Here's the webpage with the howto

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then just type

```

sudo apt-get update && sudo apt-get install skype

```

---

### Post by chebbie on 2009-06-09
I past the following in the Terminal:




Ubuntu 9.04 "**Jaunty** Jackalope": 
sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list


Then, add the **GPG** Key: 
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

then the code you gave me.

but nothing is working.

---

### Post by zcecc22 on 2009-06-09
Can you post an error message or something?

---

### Post by chebbie on 2009-06-09
well there's is nothing that happens or appears. and neither is skype found in the internet section or in any other section.
nothing nothing.

---

### Post by Chronon on 2009-06-09
Did the install command execute properly (with no errors)?  What happens if you run "skype" from a shell?

---

### Post by merlinus on 2009-06-09
You need the 64-bit version.  Filename is

skype_ubuntu-2.0.0.72-1_amd64.deb

Search for it at the skype website, as there does not appear to be a direct link.

---

### Post by aysiu on 2009-06-09
Are you using i386? What kernel are you using?

If you don't know, paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
uname -a
``` and then post the output back here.

---

### Post by nmaster on 2009-06-09
you can force it to install the i386 package

sudo dpkg -i --force-architecture <name.deb>

For jaunty, there are other skype problems tho: CPU leaks, audio problems, etc.  Its very disappointing.  

I'm going to try running skype through a windows xp virtual machine.  If anyone else has tried it, post your results.  It seems like a promising endevour but I'm still waiting to get my WinXP ISO.

---

### Post by mikewhatever on 2009-06-09
> **neal.m.master said:**
> ...
For jaunty, there are other skype problems tho: CPU leaks, audio problems, etc.  Its very disappointing. ...

Very true, but, at least in my case, all the said problems were related to pulseaudio. I tried fixing and tweaking to no avail, then gave up and removed PA. Not suggesting anything, just sharing.;)

---

### Post by nmaster on 2009-06-14
> **mikewhatever said:**
> Very true, but, at least in my case, all the said problems were related to pulseaudio. I tried fixing and tweaking to no avail, then gave up and removed PA. Not suggesting anything, just sharing.;)

I recently remove pulseaudio and got esound.  It fixed all my skype problems and I haven't experienced any negative repercussions (yet).  For new users, you can look here to see exactly what I did: [http://ubuntuforums.org/showthread.php?t=1127056&highlight=skype+cpu&page=5](http://ubuntuforums.org/showthread.php?t=1127056&highlight=skype+cpu&page=5)  I'm post #42.

---

