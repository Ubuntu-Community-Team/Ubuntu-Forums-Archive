---
title: "running java (newbie)"
date: 2007-08-22
forum: Dell  Ubuntu Support
---

### Post by arvadawest on 2007-08-22
Hi,
I am a newbie to Ubuntu Linux.  I cannot get Java to run while on Firefox.  Keep in mind that I am a newbie on this.  How can I get Java to run on my desktop?  Thank you so much!

---

### Post by saru411 on 2007-08-22
what version of ubuntu are you running? 32 or 64 bit?

---

### Post by arvadawest on 2007-08-22
I am not sure.  I just purchased the Dell 410N XPS with ubuntu desktop ed 704.

---

### Post by saru411 on 2007-08-22
type this in terminal and copy the output here

> uname -a

---

### Post by arvadawest on 2007-08-22
hi,
2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

---

### Post by saru411 on 2007-08-22
you are definitely running 32bit. i run 64bit and had to install sun java5 with 32bit firefox. i followed this thread [http://ubuntuforums.org/showthread.php?t=202537&highlight=amd64+java+flash](http://ubuntuforums.org/showthread.php?t=202537&highlight=amd64+java+flash)
i dont think this is what you need. if you have a dual core processor i would recommend installing 64bit feisty. good luck

---

### Post by arvadawest on 2007-08-22
Saru,
Thanks.  I am a newbie and am lost.  do you mean i would have to reinstall a new 64 bit OS?  thanks.

---

### Post by arvadawest on 2007-08-22
I do have a dual-core on this Dell XPS 410.  Oh well, I didn't realize how dumb I am until I purchased this system with ubuntu.  I am truly lost.

---

### Post by saru411 on 2007-08-22
really, dont worry. there are plenty of people to help you. step back take a deeeep breath and maybe a cup o coffee and then download ubuntu feisty fawn amd64. when its done downloading write it to disc and install ubuntu 64bit. once you are up and running start looking around the 64bit section. you will get alot of help. i did the same thing about 6 monthes ago. i had some major issues but i kept going. you will make it im sure. i'll continue to help. check your private messages ;)

---

### Post by spier on 2007-08-22
Prior trying to reinstall ubuntu, as your problem is related to firefox and java, check if you have java plugin installed:

Open Synaptic Package Manager (System >  Administration >  Synaptic ...

Click Search button;
Type `java plugin`
Click Search.

Search for something like sun-java5-plugin or sun-java6-plugin. If they are not checked, mark  one accordingly your java version then  click Apply button to (Re)install.

---

### Post by saru411 on 2007-08-22
i agree, no need to do a reinstall just yet. i would recommend it later when you get more comfortable with ubuntu/linux.

---

### Post by cheetaux on 2007-08-22
I had a similar problem (Java plug-in not working in Firefox) and simply installed the java plug-in to fix it.  To do this, simply open a terminal window (Applications/Accessories/Terminal) and enter the following:

```
sudo apt-get install j2re1.4-mozilla-plugin
```

Hope this helps.

---

### Post by arvadawest on 2007-08-22
> **spier said:**
> Prior trying to reinstall ubuntu, as your problem is related to firefox and java, check if you have java plugin installed:

Open Synaptic Package Manager (System >  Administration >  Synaptic ...

Click Search button;
Type `java plugin`
Click Search.

Search for something like sun-java5-plugin or sun-java6-plugin. If they are not checked, mark  one accordingly your java version then  click Apply button to (Re)install.

Thanks to all of you.  I took these instructions here and it worked.  I still get confused about marking software and then installing it.  I need to find the proper instructions on what, how to look for, mark and then install.  Thank you!

---

### Post by Rick Z on 2007-08-24
I had the same problem with Java display on the firefox.  I will try all the suggestions.  thx a lot!

---

