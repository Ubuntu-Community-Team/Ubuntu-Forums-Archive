---
title: "pkgs vm under 15mb based on Ubuntu for my class"
date: 2008-12-08
forum: General Help
---

### Post by scoobynooby on 2008-12-08
Hi I am not really a noob around Linux but I am to Ubuntu.
I have two questions regarding setting up.
First do we use debs or is Ubuntu like some other distros out that have some pkgs like Pix or Dsl?
Also I was thinking of working with my class on a project using a mini Linux under vm with the goal of building up only to what his/her own needs are.
I don't have the time to reduce so do any of you know of a iso under say 15mb thats based on Ubuntu and no I don't need any wm or fancy graphics?
I will look forward to you replies.):P

---

### Post by MarblePanther on 2008-12-08
Based on Ubuntu *and* under 15mb ;)

that's a mighty tall task considering the heavily stripped DSL is ~50mb

good luck with that one  (a kernel itself for Ubuntu is around 15 mb)

Go with something not based on Ubuntu like a floppy-distro


[http://www.linuxlinks.com/Distributions/Floppy/](http://www.linuxlinks.com/Distributions/Floppy/)

---

### Post by albinootje on 2008-12-08
1) Ubuntu uses deb packages.
2) Ubuntu has a mini install iso available :
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

There also the business-card Debian install iso which is about 35 Mb.
[http://www.debian.org/CD/netinst/](http://www.debian.org/CD/netinst/)

But perhaps you wanted a Linux Live-cd under 15 Mb ?

---

### Post by scoobynooby on 2008-12-10
Hi I was looking and found Slitaz that is under 30mb and can run the Knoppix kernel but it's api is not like Ubuntu or Debian , Floppix that runs on 2 floppy's and is based on Debian and is very similar to what I'm looking for but it has no way of installing new pkgs or installing to any drive other then floppy and I also checked out Lepton by the makers of MuLinux but its not very stable and has no update-ability according to the site, however that might work.
I looked at the installers you mentioned but thees install the base systems usually over 200mb according to most sites.
I don't see any Debian, Ubuntu or even Knoppix floppy distros yet.
What do you think it might take to tern Debian, Ubuntu or Knoppix into a floppy distro?
I think it saddening that BL3 can get so much on 2 floppy's using Slackware and Debian based has no viable floppy distro to compare yet.
What ever I use I'd like to keep using the deb packages.
> 
But perhaps you wanted a Linux Live-cd under 15 Mb?

I am looking for a Live-cd or any thing that I can run under VM's such as Qemu, Vmware or virtualbox.
Any recommendations?

---

### Post by nc_jed on 2008-12-10
> First do we use debs or is Ubuntu like some other distros out that have some pkgs like Pix or Dsl?

I'd suggest using Synaptic or apt-get for installing additional software, but DEBs are the preferred method of installing additional software (dpkg or gdebi if you like GUI and have Gnome dependencies installed).  Alien is also available for installing RPMs.  Of course, there is the good old 'compile it yourself' method.

> Also I was thinking of working with my class on a project using a mini Linux under vm with the goal of building up only to what his/her own needs are.
I don't have the time to reduce so do any of you know of a iso under say 15mb thats based on Ubuntu and no I don't need any wm or fancy graphics?

Although this is not your specific question, you might consider getting the Alternate Install CD for one of the Distros (I used Xubuntu 8.04).  There is a command line install option in the menu, that will install a command line system.  From there, you can apt-get the additional packages you need for window managers, software, etc.

BTW, that was the installation method I used for the machine I'm writing ths on (P2 233 MHz).  Later versions of Xubuntu were too bloated to be effective on this hardware, so I did what I described above.

See this guide:  [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)  If I recall, I based my experience on it.

-Jed

---

### Post by scoobynooby on 2008-12-10
> 
Also I was thinking of working with my class on a project using a mini Linux under vm with the goal of building up only to what his/her own needs are.
I don't have the time to reduce so do any of you know of a iso under say 15mb thats based on Ubuntu and no I don't need any wm or fancy graphics?

Although this is not your specific question, you might consider getting the Alternate Install CD for one of the Distros (I used Xubuntu 8.04). There is a command line install option in the menu, that will install a command line system. From there, you can apt-get the additional packages you need for window managers, software, etc.


Ya I was trying to get more then one question in before I started in with Ubuntu.
So since I will be using VM's such as Qemu, Vmware or virtualbox and would like the small size can you tell me what a command line systems size might be so I know if I should go that rout?
I am interested if anyone has a iso of such a system ready for download to use under a VM?

---

### Post by nc_jed on 2008-12-10
Sorry Scoob, It's been a couple months since I did it and am not sure what the basic install size was of the command line system.  With XFCE 4.4 and a lot of apps it's just over 1 GB, but that doesn't tell you much.

I can say that it is going to be larger than 15 MB.

- Jed

---

### Post by snowpine on 2008-12-11
Hi there, I think you will find this thread helpful: [http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

The distros  are listed by the size of the ISO, and you'll see there are several choices under 15mb. The smallest Ubuntu-based distro on the list is the GTK remix at 187mb.

Good luck with your project!

---

### Post by scoobynooby on 2008-12-12
From what I gather DSL 50mb and up or command line install of Debian or Ubuntu ~120mb and up are the smallist to install debs with the possible exception of Slitaz 25mb if you think that it installs debs correctly.
I still don't know if Lepton can be made stable or if it even installs debs do you know?
If I must use DSL then I will need to know a quick way to reduce it down to command line and some pkg tool only.
I'd love to know what next?

---

### Post by scoobynooby on 2008-12-16
Hi I got back frome a trip and landed on ubuntutrinux.
I havn't had moch time to play yet but it looks good.
[http://code.google.com/p/ubuntutrinux/]("http://code.google.com/p/ubuntutrinux/")
has less ansures then I'd like to see but it is small about 9.5mb.
I don't know though about mounting or pkgs as no commands of the sort used under moste Debian based systems seem to be runnable aka mount -t ext3 /dev/hda1 /mnt/hd won't work even after creating the dir and I see no pkg tools like apt-get.
All though the site sayes it can mount and install debs I don't know how yet.
I looked for any info on ubuntutrinux but I don't see any.
So will any of you be willing to try it out and see what you can do?:popcorn:

---

