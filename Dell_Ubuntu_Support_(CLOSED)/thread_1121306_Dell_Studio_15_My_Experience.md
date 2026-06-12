---
title: "Dell Studio 15: My Experience"
date: 2009-04-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Maheriano on 2009-04-09
A lot of people wanted me to post my experience with the install once I got my machine. Well I received it today and here are the specifications:

2.0 gigahertz T6400 CPU
4 gigs 800 megahertz RAM
ATI 3450 Radeon HD video card with HDMI out
slot load DVD
backlit keyboard
built in Bluetooth
Wireless B/G/N

So far I've downloaded and burned the Ubuntu 9.04 Beta release twice and each time it freezes on the LiveCD menu screen. I can't get it to install.

---

### Post by Maheriano on 2009-04-09
I had K3B verify the data on the disc after burning and everytime it fails. There's something wrong with the iso.

---

### Post by knattlhuber on 2009-04-10
Do a checksum

```
md5sum /path/to/iso/file
```

and compare it against

[http://releases.ubuntu.com/releases/9.04/MD5SUMS]("http://releases.ubuntu.com/releases/9.04/MD5SUMS")

---

### Post by Maheriano on 2009-04-10
> **knattlhuber said:**
> Do a checksum

```
md5sum /path/to/iso/file
```

and compare it against

[http://releases.ubuntu.com/releases/9.04/MD5SUMS]("http://releases.ubuntu.com/releases/9.04/MD5SUMS")
Did that, it's the same. I even downloaded it from the Ubuntu.com page and it still failed. I'm wondering if it's locking up because of the ATI HD video card in it.

---

### Post by knattlhuber on 2009-04-10
Maybe try the alternative installation CD:
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by applecake on 2009-04-10
Have you tested the stable 8.10..?

---

### Post by superm1 on 2009-04-10
> **Maheriano said:**
> Did that, it's the same. I even downloaded it from the Ubuntu.com page and it still failed. I'm wondering if it's locking up because of the ATI HD video card in it.
This shouldn't stop the install from working.  The ATI HD card is supported minimally by the open source driver, and fully by the closed source driver.  It sounds like it hasn't even started the boot process when it's freezing.

I'd recommend installing from a USB stick if you are still having troubles with CDs.

---

### Post by Maheriano on 2009-04-11
Looks like the burner in my desktop finally bit the dust after 4 years. I downloaded and burned the 9.04 Desktop, 9.04 Alternate and 8.1 Desktop CD, they all failed on the write verification at the same spot. This burner came on my machine, it and the card reader are the only 2 original parts that I haven't upgraded. Looks like it's time to finally upgrade to a DVD burner.....they make those now right? I joke.
I'll have to get a friend to burn this and I'll try the install again tomorrow. Way too tired after snowboarding in the Rockies all day.

---

### Post by Maheriano on 2009-04-11
I ended up staying up last night and doing the install from a LiveUSB and it worked perfect. I got 9.04 installed on the machine and everything for now seems to be working perfect. There's only 2 problems I have so far though:
1. It hasn't prompted me for the proprietary ATI driver like it does for the nVidia driver on my desktop. Do I have to go download it manually?
2. When it was installing, it said it was preparing an ext3 filesystem for /. Shouldn't this be ext4?

---

### Post by knattlhuber on 2009-04-11
Successful day for you: Snowboarding in the Rockies AND a working Ubuntu install :p

1. Have you checked under System > Administration > Hardware Drivers?
2. I think ext4 is only optional at this point.

---

### Post by pdcox on 2009-04-12
ext4 is optional you have to select the option to manualy divide the partitions, when i was instaling i forgot and i am to lazy to install all again. maybe one day

---

### Post by Maheriano on 2009-04-13
> **pdcox said:**
> ext4 is optional you have to select the option to manualy divide the partitions, when i was instaling i forgot and i am to lazy to install all again. maybe one day
I never saw any mention of this in the install. I can reinstall tonight if that's the case, where do I find this option?

---

### Post by knattlhuber on 2009-04-13
During setup, when the partition manager comes up, choose 'Manual' and then, when editing your partitions, choose to format as 'ext4'.

---

### Post by Maheriano on 2009-04-13
I remember seeing Manual as an option. I'll do that tonight, thanks. So much for configuring Compiz just how I liked it. Good thing I didn't transfer any files to it yet.

---

### Post by pdcox on 2009-04-14
Were u able to format in ext4 ?

---

### Post by Maheriano on 2009-04-14
> **pdcox said:**
> Were u able to format in ext4 ?

Ya, I actually split it into 3 partitions:

15 gig = / = ext4
8 gig = swap
290 gig = /home = ext4

Working great! All of the features of the laptop are working, the proprietary ATI driver went on smoothly, Compiz is soaring in all its glory and the backlit keyboard is a gift straight from the gods. I really like this thing.

The funniest part was when I booted it up for the first time and it asked me if I agree to the Microsoft license. I tried to click NO so I could reboot into the LiveCD to install 9.04 but there was no option for it! The only option was YES, I had to hold down the power button.

---

### Post by pdcox on 2009-04-16
is everything going fine ?
is the ext4 much faster ? i am in doubt if i should format again or not

---

### Post by Maheriano on 2009-04-16
I honestly have no idea, it's like trying to tell the difference between 32 bit and 64 bit.

It does have its advantages though, we're reaching the limit for NTFS at work with one of our storage racks, I think it's 16 terabytes or something. I proposed we switch to EXT4 because it can handle some crazy amount like over 100 terabytes.

But yes, the laptop is cruising along and no, I can't notice a difference.

---

### Post by Supersquirrel on 2009-04-16
How long does the battery last?

---

### Post by Maheriano on 2009-04-17
About 2.5 hours on default settings. You'll get more if you customize it.

---

### Post by AtlantaBob on 2009-04-24
Out of curiosity, does it have the Broadcom Wireless adapter? I had to play with a Studio 17 with 8.04 earlier and it definitely wasn't working out-of-the-box. I was wondering if it would be worth it to upgrade to 8.10 or 9.04. Thanks!

---

### Post by Maheriano on 2009-04-24
Broadcom, not sure. I can't remember if I got the Intel wireless or the Dell wireless, I think it's the Dell B/G/N. Either way it worked as soon as I installed 9.04 and then the proprietary wireless driver. No problems so far.

---

### Post by Yehudah on 2009-04-24
I have the same laptop with 9.04 running.  How did you get your bluetooth to work?

---

### Post by Maheriano on 2009-04-25
I haven't tried the Bluetooth yet but the light is on and the icon is on my taskbar. I assumed it worked, are you saying it doesn't?

---

### Post by Yehudah on 2009-04-25
I haven't been able to get it to work....  but I could be doing it wrong.:confused:

[edit]
I got the lappy to see the headset and the phone.. they both paired.  I wasn't able to get the headset to work though, using Rhythmbox.  And I couldn't transfer or see files on the phone.
[/edit]

---

### Post by stringkarma on 2009-04-25
I have become a big fan of the blueman package. I think its much better than the gnome standard.

Add this [PPA]("https://launchpad.net/~blueman/+archive/ppa") and update and install blueman.

I have a little description on my blog [http://joelslinux.blogspot.com](http://joelslinux.blogspot.com)

I have a Studio 15 and I have liked it completely as far as OS goes. I don't like the media buttons and I am not the biggest fan of the touchpad, but the linux support is great.

---

### Post by Yehudah on 2009-04-25
Hey Joel.  I installed Blueman.. How do I created and edit the file you talked about?

I'm a Ubuntu noob, sorry.  But like you, I have a Dell 1536 that I just got and dumped Vista.... would really love to get my bt headset working. 

I see in Blueman my headset and phone.... when I try and start the a2d service, it fails... probably the fil update.


Yehudah

---

### Post by jrd2 on 2009-04-30
I have a question for you, Maheriano, if you (or others who can help) could kindly answer.

I too have a Dell Studio 15 with the same ATI 3450 graphics card. However, under Jaunty, this card doesn't appear under the Restricted Driver Manager. Does it for you?

I have tried installing the flgrx driver from the repository which works with limit success.

1) Compiz runs rather sluggish
2) Switching to fullscreen in Totem while playing movies causes a black screen (probably related to poor 3d performance)

Any suggestions? Did you have to do anything special?

Cheers


For others who are curious, beside the above issue, everything else has worked flawlessly for me. This includes the built in webcam and mic.

---

### Post by Maheriano on 2009-04-30
I did a scan for hardware drivers and the ATI driver popped right up. I installed it and Compiz runs beautifully. I didn't do anything else.

---

### Post by stringkarma on 2009-06-15
Sorry it took me so long to notice your post. What file do you need to edit? Have you added the PPA? Have you installed blueman?

Let me know, I'll try to help.

---

### Post by greenie9 on 2009-06-15
Hi all,

first time ive seen this thread, i am having an issue with my Dell Studio 15

the brightness keys just dont want to work, can anyone help me out?
thread with information can be found here:
[http://ubuntuforums.org/showthread.php?t=1187617](http://ubuntuforums.org/showthread.php?t=1187617)

Thanks heaps

---

### Post by Maheriano on 2009-06-16
> **greenie9 said:**
> Hi all,

first time ive seen this thread, i am having an issue with my Dell Studio 15

the brightness keys just dont want to work, can anyone help me out?
thread with information can be found here:
[http://ubuntuforums.org/showthread.php?t=1187617](http://ubuntuforums.org/showthread.php?t=1187617)

Thanks heaps

Just posted a suggestion for you.

---

