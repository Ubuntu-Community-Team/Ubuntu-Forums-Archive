---
title: "Which version should I use? 32bits or 64bits???"
date: 2008-12-09
forum: General Help
---

### Post by alex_kent_18 on 2008-12-09
Hi,

I have a laptop equipped with AMD64 Dual Core Processor. I used to use virtual machine such as running flex builder and other development tools that run only on windows system. I used to have 64bit version of ubuntu and as other have, I have run into troubles with Java, Skype and so on. Therefore, I would like to request for a suggestion which version of ubuntu should I use? Should I still stick to 64bit or just downgrade to 32bits version?

Thanks so much indeed....

Alex Kent

---

### Post by em4r1z on 2008-12-09
If you have problems on 64 bit running some applications you need, how are we supposed to help you? We could argue the whole day about the benefits of a 64 bit system, yet you'd still complain about Sun's Java, Skype, Abode's Flash, etc. You already made a decision.
I'd use 64 bit on anything capable of running it, though.

---

### Post by OneSeventeen on 2008-12-10
I have just started using the 64 bit version, and haven't had any real problems without work-arounds.

Things are much nicer now that I've installed Sun Java 6 Runtime instead of gcj.

Of course, YMMV, and if you are having massive problems with 64 bit, I'd switch to 32 and see if that resolves your problems.  I would guess that more software will become more 64 bit friendly as time passes, but 32 bit is probably still more widely supported.

---

### Post by alex_kent_18 on 2008-12-10
Thank you guys for your prompt reply. If it is possible, I dun want to move back to 32bits. I also have Sun Java 6 and it is running fine but I still have some problems as follow:

1) I cannot use Java Applet based web-applications which can be found mostly on bank websites and government websites. It runs into the serious infinite loop whenever I go into those websites.

2) my skype is not detecting my sound input and output devices well. So now i can't possibly chat with my family with pc-to-pc call.

If you guys have the work-arounds for that two problems, I'll be very happy to receive it.

---

### Post by aurelieng on 2008-12-10
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by Ayuthia on 2008-12-10
> **alex_kent_18 said:**
> Thank you guys for your prompt reply. If it is possible, I dun want to move back to 32bits. I also have Sun Java 6 and it is running fine but I still have some problems as follow:

1) I cannot use Java Applet based web-applications which can be found mostly on bank websites and government websites. It runs into the serious infinite loop whenever I go into those websites.

2) my skype is not detecting my sound input and output devices well. So now i can't possibly chat with my family with pc-to-pc call.

If you guys have the work-arounds for that two problems, I'll be very happy to receive it.

Have you tried using icedtea?  I found that it worked better for me in accessing java based sites.

As for skype, are you saying that that you are not seeing any devices under Options->Sound Devices or are you not getting the sound and microphone to work?

---

### Post by alex_kent_18 on 2008-12-11
I do have icedtea by default on my firefox. Note that I am running 64bits version. is there any specific modification to get worked for that plugin?

---

### Post by fragos on 2008-12-11
There may be some measurable reasons for running a 64 bit OS. In my experience I've not seen any perceivable benefits of 64 bit over a 32 bit OS. Some things don't work well with a 64 bit OS without special handling if at all. As a desktop user with a focus on application use the generic 32 bit OS serves me better.

---

### Post by nzadLithium on 2008-12-11
sudo apt-get install icedtea

you will probably need to remove any existing java plugins you have.

As for skype, i think you'll find your problem is not 64bit specific, and if you were to 'downgrade' to 32bit you would still have the problem.

First step is killall pulseaudio

pulseaudio is a pig when it comes to sound recording, if I have it started most apps can't access my microphone.

Go into the sound mixer, make sure your playback options are loud enough you can hear them in other apps, and check your mic boost +20dB id on and that your mic recording volume is full. Make sure nothing is muted either.

By now you should be able to hear other people, and hopefully can talk to others as well. If not try this (from ubuntu community docs - skype page)
> 2. Skype Audio Device

If your audio levels are properly configured and you can hear audio in Skype but your contacts cannot hear your input, you may need to change Skype's input device. From the Skype menu, choose Tools->Options and select Hand/Headsets in the dialog that opens. Experiment with different Calls selections, if they are available. 

If its still not working take a look here [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

if it still doesn't work post back and we'll see what we can do :D

---

### Post by alex_kent_18 on 2008-12-28
I am still having problem with icedtea. where can i test whether it works? For the sites, I tested are all failed; just end-up with an infinite loop.

Please help

---

