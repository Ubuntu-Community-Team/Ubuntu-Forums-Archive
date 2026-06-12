---
title: "F9 first impressions"
date: 2008-05-14
forum: Fedora/RedHat and derivatives
---

### Post by orbital on 2008-05-14
1. Couldn't login with a user account at all (only with root). Changing pw didn't help.

2. Resolution on ATI Mobility Radeon x1400 was no good. After driver updates I got it up to 1280x800, but the login screen resolution was still low.

3. Everytime I selected Appearance from the System menu resolution dropped to the level of unusability. Strange stuff.

4. Had a lot of problems getting WLAN to work properly.

5. When I tried to update packages with the Update tool it didn't do nothing. I got F9 updated using the command line.

6. Couldn't enable Desktop Effects.

Everything above worked perfectly when I installed Ubuntu 8.04. So, I'm not too impressed with F9. Very buggy.

---

### Post by karellen on 2008-05-14
I tried the livecd today and it worked fine. I like the overall look and feel, and it detected my video card and set the resolution properly. it automatically detected my cable connection, I have no wireless at home so I can't speak about this matter. anyway, as I use Fedora 8 (together with Vista) I was expecting enthusiastically this new release
before you apply labels as "buggy", think about different hardware out there. if it doesn't work for you doesn't mean it's buggy ;)
my 0.02$

---

### Post by igknighted on 2008-05-14
> **orbital said:**
> 1. Couldn't login with a user account at all (only with root). Changing pw didn't help.

2. Resolution on ATI Mobility Radeon x1400 was no good. After driver updates I got it up to 1280x800, but the login screen resolution was still low.

3. Everytime I selected Appearance from the System menu resolution dropped to the level of unusability. Strange stuff.

4. Had a lot of problems getting WLAN to work properly.

5. When I tried to update packages with the Update tool it didn't do nothing. I got F9 updated using the command line.

6. Couldn't enable Desktop Effects.

Everything above worked perfectly when I installed Ubuntu 8.04. So, I'm not too impressed with F9. Very buggy.

The xserver shipped is a pre-release version, please file bugs on it.  Even if you don't plan on staying with Fedora, this xserver will ship with the next ubuntu so you don't want that bug still floating around then either.

Can you log in as a user via the CLI?  The new GDM has had some issues, so I wonder if it is that.  Also, make sure your username is spelled properly, that has gotten me a few times.

---

### Post by orbital on 2008-05-15
> **igknighted said:**
> Can you log in as a user via the CLI?  The new GDM has had some issues, so I wonder if it is that.  Also, make sure your username is spelled properly, that has gotten me a few times.

I'll try logging in using CLI later today. And yes, I'm sure the username is spelled properly.

---

### Post by Cybie257 on 2008-05-17
Well, today I gave Fedora 9 a try. Like most linux explorers, I began with Red Hat. Since Fedora took over the (red hat) open source/free downloadable OS, I've tried the past few releases.

Beginning with Ubuntu 6, I've found that installing Ubuntu to be simpler, faster, and overall more functional 'out-of-the-box' that any other distribution, including Kubuntu, which I find strange. Release 7 proved to be much more laptop friendly, but still had issues. Release 8 has proven to be overall solid for laptop use. 

Comparing something that I utilize over and over, VMWare Workstation, for testing OS's, Fedora 9 became a headache. First, because I had the VMNet cards disabled during install, it required me to start all over with a fresh install to ge the network working. I experienced the same issue with Ubuntu, disabled VMNet cards, but re-enabling them and re-starting network services allowed a solid Netowrk connection. This is the first thing I notice when installing Distro's as a install all the updates right away. Fedora 9 began to lose interest quickly.

So, before giving up, I decided to try a few other things such as installing VMWare Tools. Hmmm. First, the RPM package failed to install, then the shell install failed because it would'nt attach to the src directory, saying it was the wrong kernel, which were the latest install/updated files. Since I couldn't get these things working without going through hassles (others have same problems from reading within Fedora forums), I decided to delete this Fedora and Install a fresh 8.04 Ubuntu into VM Workstation. Results: Not only did it install 3 times faster, but everything worked, and to my surprise, the VMWare Tools, or at least being able to freely move the mouse pointer from and to Ubuntu VM from Windows XP, without any need to install the tools. Are they pre-installed? I have yet to confirm that as bedtime calls. :)

For me, it looks like Ubuntu is an overall winner of Linux Distros and I can't wait to see what improvements will be in Release 9. Everything seems to work great with 8. Now, some may say that I didn't give Fedora much of a chance. My opinion is, is that if an OS can't be installed without tweaking things and have the basics working on first reboot, there's not going to be much interest in migration from Windows. Ubuntu invites change by working 'right-out-of-the-box'.

On a last note... Why would I continue to use Windows? As a student in college, most of the courses taken are based in a Windows environment adn ust makes things easier, but I do have 2 laptops with Ubuntu on them as Base OS's and VMWare XP installs. I plan to do the same scenario with my tower when this term ends. 

Thanks, Ubuntu for making Linux a friendly environment thats easy and fast to install and begin working within. :)

-Cybie

---

### Post by Antman on 2008-05-17
Isn't it great to have choices...:KS

---

### Post by toni_uk on 2008-05-17
Installed Fedora 9 on my laptop yesterday, actually only to try persistant live USB. Still waiting for the stcik to be delivered by post but it has given me a bit of time to play around with F9. 

Things that haven't gone well:

--Grub - though I specified that Ubuntu boots from sda1 it does not pick it up. Some 'bad file error' - too much of a novice to fix it. Not sure how.

--WLAN - took me half a day to find out why it permanently disconnects. The channel on the Wireless setting in Fedora has to be the same as the channel set by the router to be stable. Never experienced that with any other distro before.

Otherwise I love Fedora 9 - it recognised my hardware much better than Ubuntu. My new Canon Ixus 70 which Ubuntu 8.04 did not even recognise was found immediately. A total relief. I will see whether I can fix this on Ubuntu, otherwise I will switch my wifes PC straight to F9 - no downloading of pictures from Camera = no Linux on her PC. Can't have that!

---

### Post by cb951303 on 2008-05-17
actually I find F9 really fast and stable on my hardware ... I even thought to stick with it :twisted: But as mentioned earlier X.org is prerelease and nvidia doesn't have drivers for it yet... also I can't give up apt-get. I just can't.

---

### Post by Infra on 2008-05-17
> **cb951303 said:**
> actually I find F9 really fast and stable on my hardware ... I even thought to stick with it :twisted: But as mentioned earlier X.org is prerelease and nvidia doesn't have drivers for it yet... also I can't give up apt-get. I just can't.

nvidia has already released "beta" drivers for Fedora9 and the prerelease Xorg. You can find them from livna or freshrpms repos

---

### Post by Istonian on 2008-05-17
Just tried out F9 today and I did not like it. I don't like packagekit. I like big repos and I don't feel that F9 has a big enough one yet.

---

### Post by orbital on 2008-05-18
I will give F9 another go today, and will post later how it went this time.

---

### Post by Antman on 2008-05-18
> **orbital said:**
> Everything above worked perfectly when I installed Ubuntu 8.04

> **orbital said:**
> I will give F9 another go today, and will post later how it went this time.
If everything worked perfectly while using Ubuntu, why would you try F9 again? My experience is the reverse of yours:

I normally use Fedora 8 on my subnotebook that I have connected to a TV in my living room; using it as a video media center type device. I figured I would try Hardy on it. 

This subnotebook doesn't have a CDrom drive so I first had to make a LivecdUSB install of Hardy. I had to go to the pendrivelinux site and follow the 20+ steps there in order to make a Livecd usb stick. After that I had a working LiveCDUSB stick of hardy.

I installed it on my subnotebook and prepared the system (updates, codecs, etc). When my son and I started to watch a movie, X crashed and rebooted (yes, desktop effects are off).:mad:
After logging in again, the movie was able to play fine. After that movie was over we watched another one and than X crashed again. My son said, "Dad, why did you change the system? The other one was working fine."
lol... I guess I need to stop tinkering with the media center laptop. 

Oh well, I setup a Fedora9 LiveCD usbflash using the included livecd-to-usb script on the Fedora9 iso. Typed in the command and had a working fedora9 LiveUSB stick in about 2 minutes. ;)
Again I went through the process of setting up the system with updates, codecs, etc.
&#8203;
End result: Fedora9 is working great so far as my video media system on this subnotebook (IBM Thinkpad  X41).

---

### Post by cardinals_fan on 2008-05-18
> **Antman said:**
> 
End result: Fedora9 is working great so far as my video media system on this subnotebook (IBM Thinkpad  X41).
You're using an X41 as a media center PC?!?!?!  Blasphemy!

---

### Post by Antman on 2008-05-18
> **cardinals_fan said:**
> You're using an X41 as a media center PC?!?!?!  Blasphemy!
LOL... the battery is dead and I don't feel like getting a new one. So until I do, it's stuck as a media pc. Maybe I'll find a cheap ebay battery and liberate it. ;)

---

### Post by djhyland on 2008-05-20
> **toni_uk said:**
> 
--Grub - though I specified that Ubuntu boots from sda1 it does not pick it up. Some 'bad file error' - too much of a novice to fix it. Not sure how.

Can you access your Ubuntu partition from Fedora?  If so, mount it up and open Ubuntu's /boot/grub/menu.lst with your text editor of choice.  Copy the boot entries for Ubuntu, then (as root) open Fedora's /boot/grub/menu.lst and paste Ubuntu's entries in and save.  You may want to back up Fedora's menu.lst first, just in case...  Anyway, it worked beautifully for me, and I'm happily dual booting Fedora 9 and Ubuntu 8.04.

Good luck!

---

### Post by wolfen69 on 2008-05-30
> **Antman said:**
> If everything worked perfectly while using Ubuntu, why would you try F9 again? 

exactly. isnt that the point? if something works perfect, stick with it. why create headaches for yourself?

---

