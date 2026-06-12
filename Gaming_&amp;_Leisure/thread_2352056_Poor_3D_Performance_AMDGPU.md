---
title: "Poor 3D Performance AMDGPU"
date: 2017-02-09
forum: Gaming &amp; Leisure
---

### Post by sparkzer56 on 2017-02-09
Alrighty, first off I would like to say hello!! I'm not new to the forums, but I had to make a new account since it's been so long since I've been on. Anyways, I have installed the 4.10 RC7 kernel in Ubuntu 16.10 along with the latest Mesa 17.1-devel through the padoka ppa. While I am getting excellent 2D performance in Undertale. However, I am getting terrible 3D performance in anything that involves 3D rendering. TF2, Runescape, ETC. However, I have seen some of the Phoronix benchmarks using the exact same kernel and mesa version. Yet, their FPS are 20x higher than mine. I understand that they are either using 1 generation newer, or older than my card. Does anyone know why I am getting terrible 3D performance? Thanks!!

Here are my specs.
AMD FX 8350 OC'd to 4GHz
16GB DDR3 RAM
AMD R9 380x 4GB

Output from grep
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tonga XT / Amethyst XT [Radeon R9 380X / R9 M295X] (rev f1)

Article
[http://www.phoronix.com/scan.php?page=article&item=mesa171-pro60-nvidia&num=4](http://www.phoronix.com/scan.php?page=article&item=mesa171-pro60-nvidia&num=4)

---

### Post by wildmanne39 on 2017-02-09
If you would like to get back to being able to use your old account please read this thread.
[https://ubuntuforums.org/showthread.php?t=2230004](https://ubuntuforums.org/showthread.php?t=2230004)

---

### Post by sparkzer56 on 2017-02-09
I'll be fine. :P Ironically my old forumn account is actually older than yours. lol Think I joined back in 06? Not sure don't really remember. I forgot the email I used for it too.

---

### Post by mastablasta on 2017-02-09
what does the OS see as GPU?: [https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

does it load the drivers propperly? anything in dmesg?

some initial troubleshooting and suggestions: [https://wiki.archlinux.org/index.php/AMDGPU](https://wiki.archlinux.org/index.php/AMDGPU)

Ubuntu page is sitll under construction...

---

### Post by sparkzer56 on 2017-02-09
grep says says the correct cards. :-/

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tonga XT / Amethyst XT [Radeon R9 380X / R9 M295X] (rev f1)

---

### Post by QIII on 2017-02-09
Hello!

Are you using the AMDGPU driver or AMDGPU-PRO?

And yes, the Ubuntu pages are still under construction because I have been busy with other things.  :)

---

### Post by sparkzer56 on 2017-02-09
No, I am still using the opensource amdgpu drivers. I have tried the amdgpu-pro drivers before but I kept getting a black screen, even with the 4.4 kernel.

---

### Post by QIII on 2017-02-09
How did you attempt to install the driver?

I am running it in 16.10 with a 4.8 kernel.

---

### Post by sparkzer56 on 2017-02-09
I added the padoka ppa.
```
[COLOR=#333333]sudo add-apt-repository ppa:paulo-miguel-dias/mesa[/COLOR]
```

Then I did
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Then I installed the Linux Kernel 4.10 RC7.

---

### Post by QIII on 2017-02-09
So you have two possible points of failure:

1.  A PPA.

2. An rc kernel.

Might I suggest using the 4.8 kernel shipped with 16.10 and the AMDGPU-PRO driver provided by AMD on their website?

I'm going to be straight up: over all the years I have been helping people with drivers, I have found that driver PPAs are more effective at stroking the maintainer's ego than providing anything of value that could not be gained by just doing things properly to begin with.

---

### Post by sparkzer56 on 2017-02-09
> **QIII said:**
> So you have two possible points of failure:

1.  A PPA.

2. An rc kernel.

Might I suggest using the 4.8 kernel shipped with 16.10 and the AMDGPU-PRO driver provided by AMD on their website?

Ok,will do.

---

### Post by QIII on 2017-02-09
Given the romance between AMD and Canonical since AMD bought ATI in 2007, it is likely that the AMDGPU-PRO driver will show up in the Canonical repo in an upcoming release.

---

### Post by sparkzer56 on 2017-02-09
> **QIII said:**
> So you have two possible points of failure:

1.  A PPA.

2. An rc kernel.

Might I suggest using the 4.8 kernel shipped with 16.10 and the AMDGPU-PRO driver provided by AMD on their website?

I'm going to be straight up: over all the years I have been helping people with drivers, I have found that driver PPAs are more effective at stroking the maintainer's ego than providing anything of value that could not be gained by just doing things properly to begin with.

haha!! Yeah, I understand. I've done that in the past but I've also had performance gains by using ppas. :P Sadly if I just use the stock Ubuntu 4.8 kernel I have to use nomodeset just so I can boot. :-/ If I don't I get a black screen and that doesn't do anything. If I use a newer kernel and use the padoka ppa I can boot into Ubuntu just fine but I get poor 3D acceleration. Installing the AMDGPU-PRO driver now.

---

### Post by sparkzer56 on 2017-02-09
Well now I just get a black screen once I get passed grub and my gpu fan is at max speed. Ill try booting with nomodeset again.

EDIT
Tried using 2 different kernels and still nothing. :-/ Just a black screen and max gpu fan speeds. Have to boot into nomodeset just to boot.

---

### Post by QIII on 2017-02-09
Did you uninstall the driver, remove the PPA, update and dist-upgrade?

---

### Post by sparkzer56 on 2017-02-09
> **QIII said:**
> Did you uninstall the driver, remove the PPA, update and dist-upgrade?

I did all of that and still nothing. :-/

---

### Post by QIII on 2017-02-09
OK.  I'll do some research a little later.  I'm running an R9 380X with AMDGPU-PRO on 16.10 without any complaint at all.

---

### Post by sparkzer56 on 2017-02-09
Ill see if I can just reinstall Ubuntu 16.10 and see what happens.

---

### Post by QIII on 2017-02-09
Usually I don't like to recommend blasting off and nuking from orbit, but if you don't have much invested it wouldn't hurt.

The problem is that it would be hard to determine the detailed state of your installation at this point.

---

### Post by sparkzer56 on 2017-02-09
> **QIII said:**
> Usually I don't like to recommend blasting off and nuking from orbit, but if you don't have much invested it wouldn't hurt.

The problem is that it would be hard to determine the detailed state of your installation at this point.

Lol Sorry, I thought it would be easier just to reinstall and start from scratch. That way it would be easier to troubleshoot.

---

### Post by QIII on 2017-02-09
Oh, I agree with that!

---

### Post by sparkzer56 on 2017-02-09
> **QIII said:**
> Oh, I agree with that!

NVM Ubuntu didn't wan't to boot with unetbootin this time. :-/ Back on Kernel 4.9 and running mesa again. So far this is the only way I can boot into Ubuntu.

---

### Post by sparkzer56 on 2017-02-10
Here is my dmesg, hopefully this helps a little more.
[http://pastebin.com/ftgL2xyR](http://pastebin.com/ftgL2xyR)

---

