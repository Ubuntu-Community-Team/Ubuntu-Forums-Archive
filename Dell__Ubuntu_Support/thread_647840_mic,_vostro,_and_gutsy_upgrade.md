---
title: "mic, vostro, and gutsy upgrade"
date: 2007-12-22
forum: Dell  Ubuntu Support
---

### Post by ayu on 2007-12-22
Hello,
Hoping it will fix my mic problem while not breaking anything else (not true!), I finally decided to upgrade to Gutsy from Feisty.  However, to my disappointment, after upgrading, and after trying many suggested fixes on the forums here, my microphone still does not work.  I'm now at the point that I have no idea what's driving my sound (not really the linux expert here, still learning a lot from these very useful forums), so I'll list what I've done in the past.
After my fresh Feisty install on: followed the instructions on [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly)
(basically added "options snd-hda-intel model=3stack" to /etc/modprobe.d/alsa-base, and modprobe snd_hda_intel).  I might have played around with some settings when upgrading the kernel to 2.6.22-10, but I don't have any successful results recorded from that.
After my upgrade to Gutsy, speakers/headphones still work, but mic does not. So I tried "sudo apt-get install linux-backports-modules-generic."  No noticeable results.  Realizing my audio sometimes doesn't work after suspend, I tried creating the script on [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Audio_Failure_On_Resume](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Audio_Failure_On_Resume)
Anyways, what sort of information should I provide to help troubleshoot this problem? 
Many thanks in advance, as I really hope to be able to use my mic soon. :)

---

### Post by ayu on 2007-12-27
Does anyone with a Vostro have their microphone working?

---

### Post by ayu on 2007-12-30
I should also note that there is no "Digital Input Source" checkbox in Volume Control preferences.

---

### Post by viniciusandre on 2008-01-09
I had my mic working with my Dell Vostro one time. Before that I didn't even know bout this so-known bug. I used it to speak on Skype and stufff, normally.

But now after a reboot (I don't remember, either don't know wich) my mic stop working. My Dell Vostro never met windows or other distribution, only Ubuntu Gutsy.

I remember to be playing around with some gstreamer dependent software installations after I installed Gutsy by the first time.

Still looking for a solution. I already tried everything.

I build a kernel for my system with [this patch]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153963"), and it didn't worked as well.

Anyone have this damn mic working? I really need skype.
Thanks!

---

### Post by ayu on 2008-01-15
Hm Gutsy is starting to seem more unreliable to me than Feisty.  Things are randomly breaking here and there.  Good to hear that it worked at least once.  Hopefully we can get it working all the time.

---

### Post by ayu on 2008-02-02
Bump! :) Does anybody else have their mic working?

---

### Post by Spam Banjo on 2008-02-08
Bump. Vostro 1700 with no mic at all.

Either internal or external would be fine.

Got no Headphones either.

:( Saaad Spam.

On the bright side, World or Warcraft runs like a dream

:guitar:

---

### Post by viniciusandre on 2008-02-08
It seems people here are managing to make it work:
I still have to try,

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153963](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153963)

---

### Post by Spam Banjo on 2008-02-11
> **viniciusandre said:**
> It seems people here are managing to make it work:
I still have to try,

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153963](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153963)

Thanks for that one my man!! Seems I missed that.

It's actually my buddies Laptop so I'll get tweaking next time I see him and let you all know how it went.

---

### Post by ayu on 2008-02-15
:confused: :confused: :confused:
Trying dell's solution at [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work) by installing the lpm seemed to make things worse!  I still don't have the mic working (no options in "Digital input source", and three(!) other "Input Source" options all with the same "mic, front mic, line"), and worse, sound doesn't work anymore until I resume from suspend!!! How do I debug this problem?  What on earth is my computer doing?  Any help will be much appreciated

---

### Post by Spam Banjo on 2008-02-20
> **ayu said:**
> :confused: :confused: :confused:
Trying dell's solution at [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work) by installing the lpm seemed to make things worse!  I still don't have the mic working (no options in "Digital input source", and three(!) other "Input Source" options all with the same "mic, front mic, line"), and worse, sound doesn't work anymore until I resume from suspend!!! How do I debug this problem?  What on earth is my computer doing?  Any help will be much appreciated

Same here dude... popper nightmare.

I tried several different walkthroughs reguarding ALSA setup. I got my sound working... even in wine, which wasn't finding any sound devices even after Ubuntu/VLC/etc started making noises for me. I can't get either the mic port or the built in mic to work... which for the record, doesn't actually work in Vista either :S... on either of the 2 identical Laptops (only 1 has Ubuntu).

As fundamentally a windows user I'm finding this VERY confusing in deed!!!

This is exactly the type of thing that is gonna stop newbies, convinced to try Ubuntu cus of how gawd damn easy to use it is, ever using Linux again. Which is Baaaad... cus 'buntu rocks.

---

### Post by ayu on 2008-03-16
Hope Heron fixes these issues! Just one more month.... :)

---

### Post by zeddock on 2008-03-25
Mine started to work after this...
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work)

---

### Post by viniciusandre on 2008-03-25
Yes, but what about AMD64 users?

---

### Post by ayu on 2008-03-26
> **zeddock said:**
> Mine started to work after this...
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work)

Hi, I've tried that already, but in general my audio was already working before that attempted fix. May I ask if your audio worked at all before doing that, and what version you are using + clean install or upgrade? Thanks!

---

