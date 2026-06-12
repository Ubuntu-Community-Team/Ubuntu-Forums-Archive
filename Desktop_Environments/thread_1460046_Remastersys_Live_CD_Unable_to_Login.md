---
title: "Remastersys Live CD Unable to Login"
date: 2010-04-22
forum: Desktop Environments
---

### Post by deeptiman.panda on 2010-04-22
Hi All
 
I have been using Ubuntu since 8.10. From time to time, I have used Remastersys to preserve my customizations and reinstall it when something goes wrong.
 
Recently I have upgraded to 10.04. Now, I am trying to save all the updates and my customizations using Remastersys. Everything goes fine and I am able to create a custom CD. But when I try to run this live CD, it is asking for a log in.
 
I have no idea what that login could be. I tried some standard logins like - custom/custom or my own user name and password from the installed Ubuntu, but nothing seems to be working. 
 
Now, I am worried, that if something goes wrong, then I have to redo the installation + upgrades and my customization.
 
Any help is much appreciated. Also, please let me know, if anyone else is also experiencing this issue.
 
Thanks
Deeptiman

---

### Post by rogerdean on 2010-05-06
same story here. can anyone help please?
cheers

---

### Post by SocialNetwork123 on 2010-05-07
> **deeptiman.panda said:**
> Hi All
    But when I try to run this live CD, it is asking for a log in.
  

Yes, I get the same problem. :mad:

I have just installed Ubuntu Lucid on my PC, solely with the view of  creating a customised LiveCD Distro for friends. 

Remastersys offers a great solution and it is a shame something is not  quite right, I am being  asked to:

Log in and Submit a password and this seems very strange and I hope remastersys has  not been compromised and consequently my own PC. I have been puzzled why I could not install  it directly from within Ubuntu's Software Centre etc.

I note the developer posted here:

[http://ubuntuforums.org/showthread.php?p=9219675](http://ubuntuforums.org/showthread.php?p=9219675)

and here:

"I am currently investigating an issue that has come up.  As a security measure I have disabled the repositories and downloads until I have fully investigated everything and verified it all."
[http://webcache.googleusercontent.com/search?q=cache:2tRefwg5ECEJ:www.geekconnection.org/remastersys/+remastersys&hl=en&gl=uk](http://webcache.googleusercontent.com/search?q=cache:2tRefwg5ECEJ:www.geekconnection.org/remastersys/+remastersys&hl=en&gl=uk)
It is a snapshot of the page as it appeared on 3 May 2010 04:32:14 GMT

The website is now offline. On one of it's pages it did suggest using  the sourceforge versions of remastersys. I did this, though I was  puzzled why it also required an additional 26 packages...

I got my version of remastersys via: [http://sourceforge.net/projects/remastersys/](http://sourceforge.net/projects/remastersys/)

I have posted a note of this post direct to the developed tb6517 At yahoo dOT com

---

### Post by rogerdean on 2010-05-07
looks like he uploaded a new version to sourceforge yesterday

[http://sourceforge.net/projects/remastersys/files/](http://sourceforge.net/projects/remastersys/files/)

---

### Post by aysiu on 2010-05-07
You actually pick the username during the remastersys backup process. I believe if you don't pick one, the default username is *custom*.

The password should be blank (just hit Enter; don't type anything).

---

### Post by SocialNetwork123 on 2010-05-07
Yes 'custom' is the default user, but I can't get my Log in authenticated, even when I just press return. It would be nice if this login screen just did not display, as it the case for most livecd distros.

---

### Post by aysiu on 2010-05-07
> **SocialNetwork123 said:**
> Yes 'custom' is the default user, but I can't get my Log in authenticated, even when I just press return. It would be nice if this login screen just did not display, as it the case for most livecd distros.
This may be a recent bug. When I used Remastersys last year, it just autologged in.

When I used it last week, it prompted me for a login. I picked the default username and hit Enter and it worked.

Not sure what's wrong in this particular situation, though.

---

### Post by Fragadelic on 2010-05-07
2 main issues for login problems on the livecd are:

1) - autologin was chosen during initial install of the system being remastered.  This won't work.  The gdm.conf file needs to be defaulted back to standard and then remaster again.

2) - users on the system are messed up or not created properly - you should not use an existing group id of <1000 for any users on the system. If you do and they are out of sync you will have problems.

To check for additional user or group problems you can use the following 2 commands from a terminal prompt:

sudo pwck

and

sudo grpck

---

### Post by SocialNetwork123 on 2010-05-07
I have removed and reinstalled Ubuntu and remastersys and I did not use the automatic log-in option, but the same problem still presents itself. 

                 IE: **A password is requested to login**. 

Maybe the problems are caused by the newer Lucid version of Ubuntu. I am attaching a screen shot of the input box that has to be completed to install Ubuntu, though it gives few options.

---

### Post by Fragadelic on 2010-05-07
pass "break=bottom" to the live boot line and then when it stops take a look at the casper.log to find out why it isn't creating the user or setting up the login.

---

### Post by SocialNetwork123 on 2010-05-07
> **Fragadelic said:**
> pass "break=bottom" to the live boot line and then when it stops take a look at the casper.log to find out why it isn't creating the user or setting up the login.

I am a complete newbie to Ubuntu and whilst I have been able to work most things out, this is something beyond my ability. I have tried with 3 new Ubuntu installations, on top of a new Vista installation for good measure, but the same log-in/password request is still being prompted. 

I have spent half-a-day on this now and now is time for some respite, I would be glad to hear from those who also had similar problems, mentioned herein, whether they have sorted things out and how.

---

### Post by Fragadelic on 2010-05-08
If none of you can do the break=bottom I can't help you.

I just reinstalled 10.04 final and ran remastersys dist.  It booted fine to the desktop.  I then installed all updates to today(46 of them) and rebooted.  After it came back up I created another remastersys dist and then tried that and it booted up fine to the desktop.

Something you are installing or doing is causing the problem and I need to see the casper.log info to help you.  Since I can't duplicate your problem I need you to test and report.

---

### Post by Fragadelic on 2010-05-08
I also need to see the remastersys.log from your system.

---

### Post by SocialNetwork123 on 2010-05-08
Dear [Fragadelic]("http://ubuntuforums.org/member.php?u=386921"),

Can you advise how I can extract the log file, on a step-by-step basis, being a newbie I am unsure how to locate find and save!

Thanks

---

### Post by Fragadelic on 2010-05-08
In order to boot with break=bottom, you need to edit the first entry when the graphical boot menu from the livecd comes up.

Before the word quiet, insert "break=bottom" without the quotes.

When it stops at the busybox initramfs prompt, the casper.log file should be right there.

If you are using a virtual machine, you can take screenshots of the pages of the casper.log and send them to me.  If not, write down the error messages pertaining to the live user creation and/or gdm setup.

either one of the following will let you view the file:

less casper.log

or

more casper.log

---

### Post by SocialNetwork123 on 2010-05-08
Thanks, but I am so unfamiliar with these processes I am like to get stuck.

I have just download VirtualBox, to see whether that may be easier to test things out and see if I can do what you request, but I imagine a steep learning curve.

 I will also post a copy of the customised .iso file (800+ MB) online and would be grateful if you could consider testing it out for me and giving feedback here, so other can benefit from your unique knowledge base. I will send the url to your email address.

I am seeking to learn how to create customised LiveCD's for friends and once I am more competent, to provide such to a wider public audience.

I am glad to here ([http://ubuntuforums.org/forumdisplay.php?f=11](http://ubuntuforums.org/forumdisplay.php?f=11)) you have secured your own .com domain and I look forward to seeing your new website. In terms of web design, I have found useit.com a useful resource.

> **Fragadelic said:**
> In order to boot with break=bottom, you need to edit the first entry when the graphical boot menu from the livecd comes up.

Before the word quiet, insert "break=bottom" without the quotes.

When it stops at the busybox initramfs prompt, the casper.log file should be right there.

If you are using a virtual machine, you can take screenshots of the pages of the casper.log and send them to me.  If not, write down the error messages pertaining to the live user creation and/or gdm setup.

either one of the following will let you view the file:

less casper.log

or

more casper.log

---

### Post by Fragadelic on 2010-05-08
PM me the link to your iso and I'll take a look at it.

---

### Post by SocialNetwork123 on 2010-05-09
SOLVED!

I used a wiped hard disk, with a new Vista install and things worked first time. 

Though I have a newer issue on how make sure a specific folder I have added on my Ubuntu installation, is transferred to the new custom iso. I will ([have]("http://ubuntuforums.org/showthread.php?p=9269624#post9269624")) post a new thread on this issue to prevent confusion and possible help other user of remastersys.

EDIT: URL for new support request on issue above:
           [http://ubuntuforums.org/showthread.php?p=9269624#post9269624](http://ubuntuforums.org/showthread.php?p=9269624#post9269624)

Thanks, I tried  a free webhost but it does work well with large files.

> **Fragadelic said:**
> PM me the link to your iso and I'll take a look at it.

---

### Post by SocialNetwork123 on 2010-05-09
Sorted out folder/doc issues via:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=6866924](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=6866924)

> **SocialNetwork123 said:**
> SOLVED!

I used a wiped hard disk, with a new Vista install and things worked first time. 

Though I have a newer issue on how make sure a specific folder I have added on my Ubuntu installation, is transferred to the new custom iso. I will ([have]("http://ubuntuforums.org/showthread.php?p=9269624#post9269624")) post a new thread on this issue to prevent confusion and possible help other user of remastersys.

EDIT: URL for new support request on issue above:
           [http://ubuntuforums.org/showthread.php?p=9269624#post9269624](http://ubuntuforums.org/showthread.php?p=9269624#post9269624)

Thanks, I tried  a free webhost but it does work well with large files.

---

### Post by @ddus3r on 2010-05-30
Hi All!

I have another problem. For me it creates successfully the image file, but when I try to boot it gives me an error:

[I]boot:
Loading /casper/vmlinuz&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;
Could not find ramdisk image: /casper/initrd.gz
boot: [/I]

I tried to switch from ISOLINUX boot manager to GRUB, but there is no difference. Also I checked the iso file and there no such file indeed.

Any ideas? :)

---

### Post by n213978745 on 2010-05-30
I have similar problems before, I wasn't be able to boot from the Live Disc that I create with remastersys

But I knew where is my problem: If you choose "require password to login and decrypt my home folder" this options during installation, you may have difficult to login.  So the way I do it, is to reinstall the whole OS.

Also if you can't create backup with your user data.  Try to create a distro, it will backup all of your system update and the software you have installed so far.

I hope my reply can help some of the people

---

### Post by ydristi on 2010-07-18
hey ih've got something interesting
i've also got the same problem 
the customised iso which i made using remastersys was asking for username and password to login
after much effort i got a solution 
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
in the above page there are instructions to customize a standard ubuntu live cd
instead of using standard live cd i used the customised cd generated by remastersys & it worked well...
i omitted the sections named customizations & advanced customizations

---

### Post by paris_l87 on 2010-07-23
I have the same problem with the Live-CD auto login.
i tested on VirtualBox,run break=bottom and then cat casper.log and got this:

---

### Post by Bibbleycheese on 2010-09-06
> **aysiu said:**
> You actually pick the username during the remastersys backup process. I believe if you don't pick one, the default username is *custom*.

The password should be blank (just hit Enter; don't type anything).

THANK YOU! :D
Just what I was looking for.

---

### Post by paulohbsousa on 2010-11-04
Hello guys, I have the following issue:

[http://img255.imageshack.us/img255/8532/errorau.jpg]("http://img255.imageshack.us/img255/8532/errorau.jpg")

I would appreciate your help, thanks.

---

