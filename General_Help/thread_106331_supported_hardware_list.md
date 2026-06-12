---
title: "supported hardware list??"
date: 2005-12-20
forum: General Help
---

### Post by jezjones on 2005-12-20
Hi there everyone,

I have had several problems over the years with linux and hardware, most recently with sound in breezy 5.10.....

When posting to forums more than one reply from a more experienced linux person than me has chidded me on not checking whether the hardware was supported before purchase.

I am now starting to get really annoyed by this as there is no list of supported hardware.... do a google for it and all you find is out of date info from last century.

I am very impressed (mostly) with ubuntu, but still there is no decent list that basically says... use this hardware and you are unlikely to have problems.

Is this so hard? It would save me loads of time and quite possibly loads of money on wasted hardware.

Jez

---

### Post by mgor on 2005-12-20
hm, have you looked at [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport) ?

---

### Post by yanik on 2005-12-20
What is your soundcard?

---

### Post by SickTwist on 2005-12-20
Here is a list of supported hardware on the Ubuntu wiki: [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

For notes about printer support, check out [http://www.linuxprinting.org/](http://www.linuxprinting.org/)

Here is a wiki featuring *in*compatible hardware: [http://www.leenooks.com/](http://www.leenooks.com/)

More notes about Linux hardware support: [http://www.tldp.org/HOWTO/Hardware-HOWTO/](http://www.tldp.org/HOWTO/Hardware-HOWTO/)

In addition, if you're planning to purchase something specific (e.g. HP Deskjet 940c, Linksys BEFSR41 Router, etc) search in the Ubuntu forums to see if there are lots of posts regarding problems using that device. Less posts usually mean there are less problems.

Lastly, you could always *ask* the forum about something specific before purchasing it (e.g. "I am considering purchasing an iRiver iFP-899, has anyone managed to get it to work with Ubuntu?"). Always search the forum first though to see if someone has already asked your question.

Also, if you have trouble finding information online about Linux support for a specific piece of hardware and you purchase it anyway, please update wikis/forums/whatever as applicable to let others know how it has worked for you. It is the little contributions like this that make the Free Software community work. :)

---

### Post by jezjones on 2005-12-22
Thanks for your replies...

My soundcard is AC97 intelICH6, which is kinda supported.
Most of the hardware on my laptop is supported out of the box, except the 5 in 1 card reader, but i can live without that.

The reason i started this thread was because i had problems with my own sound card, and i should have done some of the things you suggested like checking the forums for problems and things, but i thought intel sound does have pretty good support.

Anyway, someone asked me to help them get their sound working on their desktop, someone who was a complete newbie and had no idea outside of windows. Since the card was not detected and installed properly i had to describe and troubleshoot installing new drivers.
This was not a problem, but it made me realise how much of a process it is!!
When you have a problem with hardware in windows you are usually told to update drivers, which is a download and install program.

Now on linux you can either wait for a package to be put together, or you can try and do it yourself. If you want for example the latest ALSA drivers, you will wait a fair amount of time for a package or you will get into a bit of a mess if things dont go right.

Of course this is part of what linux is, getting your hands dirty and knowing the system a lot better. But what if it doesnt go well.... you stuck.


~~~

About the links listed.... 
Do a search on ubuntulinux.org for 'hardware support' and you get alist of pages...

> 
Search results

Did you not find what you were looking for? Try the Advanced Search for more precise search options.
85 items matching your criteria. RSS Feed

 LaptopTesting [100%] by Matthew Garrett, 2005-05-12 11:10 PM
    = Providing totally rad laptop support =
 Certified Hardware [95%] by 815, 2005-09-07 11:19 AM
    An official endorsement by the Ubuntu project of a computer hardware product, backed by a validation and testing process conducted by Canonical to ensure ...
 SupportedHardware [95%] by Joachim Durchholz, 2005-04-25 08:23 PM
    We cannot list all hardware that's compatible with Ubuntu - the list alone would be several megabytes, and it's growing constantly.



Then click on the link that says supported hardware and you get this...

> 
SupportedHardware/view

This page does not exist yet. You can create a new empty page, or use one of the page templates. Before creating the page, please check if a similar page already exists.
Create new empty page



So how did you get to the [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport) page??


I guess that i am just not happy that i cannot get my sound working and there seems to be alot of conflicting information on how to do this.
Also the attitude of distros is to manage it all for you, but they give no clue about how to work outside of it....

---

### Post by jezjones on 2005-12-22
I have just checked your helpful link to the hardware support and it says that my sound card is both autodetected and supported.... great i bought the right one..... so why cant it make it work?? ... 

apparently there is some problems with the ALSA driver for this and a later version of the driver will work... but i found it tough to install the new driver.
Not tough to get it download, make install etc, the tough bit was at that point where i needed to know what driver was being used, what driver was getting loaded at boot time, the bit between installing the driver and making it work.... and work in a way that ubuntu would know about so that if i do anything automatic like upgrade, it wont be messed with.

---

