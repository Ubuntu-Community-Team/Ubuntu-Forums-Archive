---
title: "New nVidia driver + Beryl install = blue screen of death. :("
date: 2007-02-17
forum: Desktop Environments
---

### Post by four o two on 2007-02-17
I'll try to explain everything as thoroughly as possible to make my problem easier to understand. I've had 6.10 Edgy Eft running before along with Beryl with no problems, so I've done it *before*, but now I seemed to have made a mistake somewhere along the way. I got a new HD so I figured I'd install Ubuntu/Beryl on it. So, after installing 6.10 from the CD and letting it do all the updates it found, I installed the nVidia driver (0.8.1-0ubuntu6) from this site: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Rebooted, and everything was fine. Then, I followed this exact walkthrough on installing Beryl: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia) ("installing Beryl on Ubuntu Edgy with nVidia")

After I did that, I rebooted and got a blue screen that told me basically that something was wrong with xorg.conf and "no screens were found."

Anyone have any ideas on how to fix this? BTW, I have a 6800GT video card, in case it matters.

---

### Post by ickyfeet on 2007-02-17
I use a package called Envy from   [here]("http://albertomilone.com/nvidia_scripts1.html").  It's easy to install and takes care of everything.  I've used it several times to install the most current nvidia drivers then get beryl running with no headache at all.

---

### Post by four o two on 2007-02-17
> **ickyfeet said:**
> I use a package called Envy from   [here]("http://albertomilone.com/nvidia_scripts1.html").  It's easy to install and takes care of everything.  I've used it several times to install the most current nvidia drivers then get beryl running with no headache at all.
That's the site I used. :KS

---

### Post by kvonb on 2007-02-17
From what you posted earlier, you installed the Ubuntu drivers.

Run Envy again, and install the official Nvidia driver.

It is a 14 meg download, but well worth it.

Then follow this guide for the Beryl installation:

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

Skip over STEP2 as envy would have done all that for you (I've done 3 of these installs over the Internet and it works a treat!).

Good luck :)

---

### Post by four o two on 2007-02-17
Thanks kvonb - reinstalled nVidia using envy and it boots up fine now. Running Beryl seamlessly (so far) as well. :)

---

### Post by kvonb on 2007-02-17
> **four o two said:**
> Thanks kvonb - reinstalled nVidia using envy and it boots up fine now. Running Beryl seamlessly (so far) as well. :)

Glad to hear it :)

Alberto did a FANTASTIC job with "envy", it solves so many problems in one fair swoop!

Kev :)

---

