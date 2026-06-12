---
title: "Wireless problem on Dell inspiron 1545"
date: 2009-11-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Mayniac18264 on 2009-11-07
Hi everyone

I'm an absolute beginner to linux, and for college level computing, decided to get kubuntu (easier for scripting than windows).
I'm running the newest version of kubuntu (9.10, I think), and it hasn't been able to connect to my home wifi. I've spent hours on google, forums etc, and solutions either don't work or are too complex.
Any help would be appreciated- I don't especially want to be rebooting my computer into windows 7 every time I want to use the internet.

Thanks

(p.s. I think this may have something to do with driver compatibility, but I'm too much of an amateur for a decent diagnosis)

---

### Post by soni1770 on 2009-11-07
what happens when you try to conect?

does it see the network?

maybe it's sending out the wrong type of security code,

try enter your wirelesskey with all the secutiry options, 

wpa

etc, 

what happens?

---

### Post by Togezo on 2009-11-08
Yeah, what exactly is going wrong?

I have a Dell 1545 myself, and Ubuntu 9.04 (though I also hae KDE installed), and for both desktops wireless is absolutely flawless.

---

### Post by bobcollard on 2009-11-08
You might want to use the Dell recovery disk for Ubuntu 9.10 then add Kubuntu desktop.  Here's the URL: [http://en.community.dell.com/wikis/linux/building-base-ubuntu-factory-iso.aspx](http://en.community.dell.com/wikis/linux/building-base-ubuntu-factory-iso.aspx)  I did it this way because of problems with my drivers too.  See my signature for the results, it works fine.

---

### Post by Mayniac18264 on 2009-11-08
It's not allowing me to use wireless connections at all- I've given my user permission to use them (it was unchecked originally) but it still won't acknowledge my home wifi.

I also tried entering my wifi's details, and it still refused to connect

\\edit  I had ubuntu for a few days before I changed to kubuntu, and under propriety drivers, there were no drivers listed. May be relevant, I'm not sure

---

### Post by Togezo on 2009-11-08
Try enabling and disabling the driver a few times, that may well work.

---

### Post by bobcollard on 2009-11-08
Check to see if your F2 button was not depressed to lock out access to the Internet for airplane use.

---

### Post by Mayniac18264 on 2009-11-08
I tried bobcollard's first solution and I got an error when installing the recovery package- still working on it

And I have tried the f2 button repeatedly, it was one of the first things I did. No luck.

---

### Post by bobcollard on 2009-11-08
Which method of recovery did you use?  The second one works better if you are already hooked up with an ethernet cable, it fixes the problems with language updates.  The button will show up as uavailable at the connection in your taskbar if it has been depressed.  What kind of errors are you showing?

---

### Post by Mayniac18264 on 2009-11-08
I got this error while trying to install the .deb file

Error: Dependency is not satisfiable: python-gtk2

Any idea on what this means or why it is happening?

---

### Post by bobcollard on 2009-11-08
Sorry, which .deb file?  My reference was for the full recovery disk.

---

### Post by bobcollard on 2009-11-08
Download the .iso from the site, burn it to a DVD.  Install the second choice,  right click on the unplugged cable icon in the taskbar to setup your wireless in Ubuntu.  Then run "sudo apt-get update" and "sudo apt-get install dist-upgrade".  Restart your computer.  If you wish to continue and install the KDE/Kubuntu Desktop, then, run "sudo aptitude install kubuntu-desktop". (Use Aptitude so you can remove it if necessary.) Right click the icon with the telephone pole in the taskbar, setup up your wireless.

---

### Post by bobcollard on 2009-11-08
If you have a broken package or file use Synaptic to fix and reinstall it.

---

### Post by Mayniac18264 on 2009-11-09
I'm sorry, but I saw no .iso file on the site. The download to the recovery tool gave me a link to this page
[http://www.launchpad.net/dell-recovery](http://www.launchpad.net/dell-recovery)
Only .deb files. I'm searching around dell community for a link.

If I'm being an idiot here, just tell me...

---

### Post by xeno_phile on 2009-11-09
Perhaps this might help...
posted by **mikewhatever** in another thread
> Dell uses a lot of Broadcom cards with proprietary drivers, not included in the default Ubuntu installation. There is a program to download and install the driver under **System**->**Admin** -> **Hardware** **Drivers,** but it requires internet connection to work. In short, you'll need to plug in a cable for about five minutes.
In other words you need access to the internet,via an "ETHERNET CABLE" connection, to download the updated drivers.

xeno_phile

---

### Post by bobcollard on 2009-11-09
_[http://linux.dell.com/git/?p=ubuntu-fid.git;a=summary](http://linux.dell.com/git/?p=ubuntu-fid.git;a=summary)_

Sorry, I forgot you have to be a member of the Dell Forum to get here.

---

### Post by Mayniac18264 on 2009-11-09
Thanks xeno_phile, I never thought of that. I'll give it a shot once I find out where I put my old ethernet cables :)
And no problem bobcollard- I'll download the .iso and follow the tut.

Will post back if it works :)

---

### Post by bobcollard on 2009-11-09
Hope it works for you, if not I'm on line with my Kmail all day and it will tell me when I get another message.

---

### Post by theronb on 2009-12-15
Thanks xeno_phile! Had the same problem with clean karmic install on a brand new Inspiron 1545 (first thing I did was get rid of Win7) - computer couldn't see my home network. After trying lots of suggestions, including contacting Broadcom, I plugged into the ethernet port on my router and downloaded the proprietary driver, which works fine. The only thing I can add is that there were two selections: the B43 driver didn't work for me, STA did.

---

### Post by rabil on 2009-12-22
I'm running 9.04 on my Dell 1545. It will not boot correctly from the 9.10 liveCD. It starts but the screen goes blank. I can hear it working and the tune plays but I cannot see anything nor can I get to a shell. I was able to get my HP 2133 to boot from the liveCD (although upgrading from 9.04 to 9.10 on the HP failed on re-boot).

Any ideas? I modified the bios boot sequence on the Dell and put the CD/DVD drive first in order for it to boot from the liveCD. I'm afraid to try to upgrade from 9.04 to 9.10 given my experience on the 2133 (but I have upgraded to 9.10 on 3 other computers).

Also, how can I tell whether I have a 64-bit cpu? When I ordered the 1545 I upgraded the cpu but I don't know if it is 32-bit or 64-bit.

---

### Post by mastablasta on 2009-12-23
i think newer CPU's (i think all dual core) are 64bit. Why not check the Wikipedia on this info?
 
Still 32 bit version will run on 64 bit as well as on 32 bit.

---

