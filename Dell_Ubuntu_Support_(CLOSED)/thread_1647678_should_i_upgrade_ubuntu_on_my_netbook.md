---
title: "should i upgrade ubuntu on my netbook?"
date: 2010-12-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zander1013 on 2010-12-17
hi,

i have an inspiron 910 running oem dell 8.04.

i am having trouble viewing flash content and so-forth. updates from the channels don't solve the problem.

should i upgrade to a newer version of ubuntu?

can you advise on the path to take please?

vanilla ubuntu methods do not seem to apply to dell ubuntu without breaking stuff because of the dell channels are different.

thank you.
;)

---

### Post by garvinrick4 on 2010-12-17
#Dell has proprietary drivers is the problem I can only see. You have choice of doing a fresh install from downloading and burning a disk, 9.04 is unsupported also.
#There is a Dell forum here to check out your cards for any problems and drivers.
#If it is just flash have you tried to download from Adobe.
#Here are different Ubuntu versions still supported:
[Main Page -]("http://ubuntuguide.org/wiki/Main_Page")

---

### Post by ugm6hr on 2010-12-18
The Inspiron 910 is the Mini 9, isn't it?
If so, you should definitely upgrade to standard (32-bit) Ubuntu 10.10 (Maverick)
It works flawlessly, including suspend.
Wifi needs a (very) minor tweak: [http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)
There was a post somewhere here about how to save and restore the fluendo codecs (not open source) - but I just use the standard methods available for vanilla ubuntu.
I haven't tried the Netbook Remix, but think the standard desktop is cleaner (I just remove 1 of the panels).

---

### Post by zander1013 on 2010-12-18
ty ugm6hr,

yes i have an early mini 9.

can you recommend a upgrade path to 10.10 please?

i believe that somehow i have lost the fluendo codecs. :(

i do not believe that my mini 9 shipped with a restore disk. but i still have the original carton and so-forth i will double check.

i am trying to download an install iso from the link given by gravenrick4 but it seems to take way to long or times out..

subsequently i am going to download 10.10 and attempt to install as usual.

can i just run "apt dist upgrade"?

please advise.

thank you. :)

---

### Post by trinitydan on 2010-12-18
I second that about 10.10 desktop.  I was excited to try Ubuntu Netbook Remix on my HP Mini, but I personally found there is a lot still to be desired.  10.10 Desktop is great though.  It runs very smoothly on my netbook.  I kept both the panels but set them to autohide to maximize screen-space.  

Also while you can use apt-get dist-upgrade, when I am downloading large files like Distros from Firefox, I find it works much better if i use the DownThemAll add-on.  If there is a timeout error, you can easily resume from where it timed out as opposed to starting your whole download over.

[https://addons.mozilla.org/en-US/firefox/addon/201/](https://addons.mozilla.org/en-US/firefox/addon/201/)

---

### Post by zander1013 on 2010-12-18
hi,

i have burned a reinstall iso from the image here...
[http://linux.dell.com/files/ubuntu/hardy/iso-images/](http://linux.dell.com/files/ubuntu/hardy/iso-images/)


the docs on how to do the reinstall seem to have no bearing on how to do this with regards my mini 9 running 8.04.

specifically the reinstall disk will not mount when i boot the machine even after what i perceive to be selecting the cd/dvd rw as the boot device.

this is using a usb dvdrw that is "designed for dell" purchased at the same time as the mini 9 on the suggestion of the dell web site. this "designed for dell" dvd/rw has never mounted on the mini 9 despite the "designed for dell" assurance.

the dvdrw works fine on other vanilla ubuntu machines (ibm t60)  but not on the dell.

over all i am displeased with this dell ubuntu product in general.

ty for all your help and patience.

please advise.

thank you.

---

### Post by zander1013 on 2010-12-18
okay,

i think i have it working now the "!" prevents a device from booting.

so for completeness i have downloaded ubuntu 10.10 and made a bootable usb stick with it. then i have disabled the hdd from booting (shift+1). so there is a "!" next to the hdd boot option. then i booted to the usb stick plugged into my local internet router and it appears i can now do a fresh install of 10.10.

i will assume that the advice given on getting the wifi to work is good and mark the thread solved.

thank you everyone. :popcorn:

---

### Post by ugm6hr on 2010-12-19
Sorry, I should have been clearer.
When I said "upgrade" I meant do a fresh install with vanilla 10.10 desktop. This is easily done from a LiveUSB, which it appears you have created.
Don't worry about the codecs - you don't need them.

---

### Post by davepoth on 2010-12-20
Just make sure to back up your home directory first. 

Everything here works flawlessly on 10.10 on a Mini 9.

---

### Post by fjgaude on 2010-12-20
> **davepoth said:**
> Just make sure to back up your home directory first. 

Everything here works flawlessly on 10.10 on a Mini 9.

Do you have a video camera built-in? Curious!

---

### Post by ugm6hr on 2010-12-21
> **fjgaude said:**
> Do you have a video camera built-in? Curious!

The Mini 9 has a video cam, which works just fine.
Why so curious?

---

### Post by davepoth on 2010-12-21
> **fjgaude said:**
> Do you have a video camera built-in? Curious!

No, I specced mine without one because I'm so ugly. :D

---

### Post by fjgaude on 2010-12-21
> **ugm6hr said:**
> The Mini 9 has a video cam, which works just fine.
Why so curious?

Does it work with Ubuntu 10.10? You don't have the 1366 x 768 screen like I have on my mini 10? I'm down to trying one more thing to get all working correctly, including the video cam.

---

### Post by davepoth on 2010-12-22
Mini 9 has 1024 x 600.

---

