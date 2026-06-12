---
title: "[SOLVED] Dell Latitude C600 and Ubuntu 7.04"
date: 2007-09-08
forum: Dell  Ubuntu Support
---

### Post by TaoBoogie on 2007-09-08
I've read the suggested thread on this problem, but none quite the same as mine.
I have an old Dell Latitude C600 running XP Pro, and I'm thinking of installing some flavour of Linux on it. It has a 20 gig HD, 750 MHz Pentium 3 processor and 256 MB of RAM.

I have tried to run ubuntu 7.04 Live disk but it seems to hang when loading. It takes a half hour go get to the stage were there are icons on the desktop, then freezes when I click on "Install". I get to the "Installation Options" stage to choose the language then it freezes. I have waited for over two hours for the installation to continue but it never gets any further than this. The cd is still running and the processor light flickering away all through.

Is this simply a case of me expecting too much from the old Dell to be able to handle a Feisty Fawn install? I intend to write over XP and use the whole drive for the new install.
If this is the case I am checking the Linux site for more suitable distros.
Cheers

---

### Post by KCPokes on 2007-09-08
I can't offer much in the area of why you are having the problem, but I can say that I don' t think it is a matter of your machine not being able to handle the install.  I've installed Feisty Fawn on a PII 233Mhz laptop without issues, other then it was really slow.  Your machine should be more then adequate to handle it.

---

### Post by Hells.Tears on 2007-09-08
I have a C510/610 and i had exactly your problem running off the live disc / installing 

What you need to look at is using Xubuntu or invest in more memory since that is the problem that your having at the moment. 

Xubuntu is just the ubuntu for older pc's/laptops that don't have that much memory, It's what i've had to go for.

If you be looking at more memory, i would suggest looking on Ebay for SDRAM PC133 up to 521MB, to run Ubuntu you would be looking at prehaps getting 2x256MB set with the set up on the system board you have at the moment.

---

### Post by CREEPING DEATH on 2007-09-08
I ran 6.06 SP1 on a C610 (1ghz, 256mb) without any problems.  Try the alternate CD, or just install Debian 4.0 R1.

CD

---

### Post by TaoBoogie on 2007-09-08
Thanks for the thoughts and advice, it really is appreciated.
It's interesting to know that Feisty Fawn has been successfully installed and run on a laptop with lower spec's than mine.

I have a feeling that it must be the computer itself, it's not had an easy life and you're right, it could do with more RAM. I have a feeling that could be rather expensive.
I've updated most of the important drivers and BIOS. I think the modular hard drive may be running slow.

I'm off to check out a Xubuntu download and also look at Debian 4.0 R1.
I'm wondering if wiping the HDD before I try another install would help the process?
I'll keep you updated on my progress.
Tao

---

### Post by strabes on 2007-09-08
Wiping the HDD before trying another install won't make a difference. Just try the alternate CD, it's easier anyway.

---

### Post by TaoBoogie on 2007-09-08
Thanks strabes that makes sense

---

### Post by TaoBoogie on 2007-09-12
Well that was an interesting adventure. I downloaded kubuntu and ran it successfully as a live disk. I had problems on trying to install it though. I got as far as formatting the drive and received the message;
> The ext3 file system creation in partition 2 of IDE1 master (hda) failed.
I was then prompted to start the partition again. I'm sorry to say my knowledge of this in Ubuntu is very limited, so I tried again but received the same message. So the installation failed.
I slept on the problem and the next morning tried Ubuntu again, this time in "Safe Mode" To my surprise the installation went well, but I could only use it in 800x600 mode. This gave me an idea to retry the Ubuntu installation in the normal way and it worked. I'm thinking that having already converted the file system in my previous installation must have helped the process.

The only difficulty I had to overcome was not being able to see the full installation screen, the "forward, back" buttons being hidden by the bottom panel. To overcome this I moved the top and bottom panels to the sides so now I could see all the  information on the installation screen.

I have now connected to the internet through a wireless connection that took a fair bit of configuring for me (because I am not used to the Ubuntu system) but I eventually managed it and I am now posting this with that connection.

My main problem now is that my CD-ROM does not work properly. Every time I put a CD in the (removable) drive it starts to run and then  stops. after a minute or so I get the message "Cannot eject volume"
I get this with all types of CD-ROM music, data etc. I also cannot eject the CD manually. I have to restart the laptop and go into "setup" to give me time to manually eject the CD.

This is why I had a lot of fiddly oroblems connecting the the net as I could not install the software that came on CD with it (I chose this particular wireless LAN cardbus as it had driver support for Linux Redhat, Fedora, Debian  and SuSe.

Any ideas or thoughts on how I can get my CD-ROM working?
It is listed in my Device Manager under IDE Device (master) as (Samsung CD-ROM SN-124) Which I thought was odd as my HDD is also set as (master).
Also should I start a new thread for this as my initial problem is more or less solved.
Your thoughts gleefully received.

---

### Post by notwen on 2007-09-12
First off congratz on getting your install to work and welcome to Ubuntu. =]  That said if your current problem(cd-rom) does not involve your previous problem, then it would be suitable to create a new thread in the appropriate sub-forum.  Again welcome to the UBuntu community and don't hesitate on posting any issues here on ubuntuforums.

---

### Post by TaoBoogie on 2007-09-12
Ok thanks notwen, I'll mark this one as "solved" and start another thread.

---

### Post by memeyou on 2007-11-16
Sorry for flogging this dead/solved horse - this is for all you googlers out there.

I have a C600 and kept trying to install ubuntu/xubuntu and got the locking up on install issue, like described in the initial post.  I figured out that by adding "noapic" to the startup options fixed it right up.

---

