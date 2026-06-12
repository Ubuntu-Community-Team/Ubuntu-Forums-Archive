---
title: "URGENT HELP! Internal Error: Failed to initialiize HAL!"
date: 2007-07-21
forum: Dell  Ubuntu Support
---

### Post by hindukush on 2007-07-21
Hi everyone!
Im very new to Ubuntu( abt 10 days). Today suddenly i got an error on startup saying "Internal Error: Failed to initialiize HAL!" Also there is now a little red cross on the Network icon in the system tray area. But the Internet connection works fine. I dont know if that has anything to do with it??

During startup i get the following error:

Starting Hardware abstraction layer: haldrun-parts: /etc/dbus-1/event.d/20hal exited with return 
code 1

Can someone pls help me? i am very very new to ubuntu so i would highlyyyyy appreciate detailed and step by step instructions. 
Thank you very much in advance!

---

### Post by hindukush on 2007-07-22
Cmon guys pleaseeeeeeeee help!!!!!!

PLEASE PLEASE PLEASE!

---

### Post by kvonb on 2007-07-22
I had much the same thing on my spare system a few days ago, I can't remember exactly how I fixed it, but it was a hardware issue, I'm sure.

I messed with the BIOS settings especially as relates to the video card.

I removed the video card and used the onboard on in vesa mode for a few days, then put my Nvidia back in, reloaded the Nvidia driver and all is now well!

I also noticed that I was getting some errors about not being able to load modules for "VirtualBox", do you have that installed?  I simply removed it.

Maybe try a disk check while you are at it.

---

### Post by hindukush on 2007-07-22
this error comes on my laptop which is a DELL XPS M1210 machine

how do i fix the damn things, ive tried everything i could from the internet

plesaseeeeeee help me someone i hate this

---

### Post by pbaumgar on 2007-07-22
> **hindukush said:**
> this error comes on my laptop which is a DELL XPS M1210 machine

how do i fix the damn things, ive tried everything i could from the internet

plesaseeeeeee help me someone i hate this

What have you tried?  Have you searched the forums for the error message?

---

### Post by kvonb on 2007-07-23
Well, we really need more info in order to help you!

The first thing I would suggest is disconnecting ALL external devices from your computer, ie printers/scanners/usb devices etc', and see what happens.

Next try booting from the liveCD, see if it works properly.

Some basic things we need to know:

1. Version of Ubuntu
2. Last thing you installed/messed with
3. Network card type - wireless/wired
4. Video drivers, which ones are you using

From my searching the net for you I found a few posts on this forum talking about disabling automatic login, or changing it to a 5 second timed login, maybe try that.


The next thing I would try is changing the video driver to "vesa", see if that makes a difference.

---

### Post by hindukush on 2007-07-23
> **kvonb said:**
> Well, we really need more info in order to help you!

The first thing I would suggest is disconnecting ALL external devices from your computer, ie printers/scanners/usb devices etc', and see what happens.

Next try booting from the liveCD, see if it works properly.

Some basic things we need to know:

1. Version of Ubuntu
2. Last thing you installed/messed with
3. Network card type - wireless/wired
4. Video drivers, which ones are you using

From my searching the net for you I found a few posts on this forum talking about disabling automatic login, or changing it to a 5 second timed login, maybe try that.


The next thing I would try is changing the video driver to "vesa", see if that makes a difference.

There are no USB devices connected to my laptop at all. The error still comes.
Version - 7.04
Last thing installed - did a few, via Automatix like unmounting the drives software under Miscelaneos tab
Network card type - wireless
Video drivers - Intel VGA onboard

I already tried the automatic login solution but did not work for me.

How do i change the video driver to vesa??

Thanks!

---

### Post by hindukush on 2007-07-23
> **pbaumgar said:**
> What have you tried?  Have you searched the forums for the error message?

yes i tried everything!!
nuthing workssss

---

### Post by aktiwers on 2007-07-23
Its a bug!
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931)

---

### Post by hindukush on 2007-07-25
Ok i could not solve the issue. sO I UNINSTALLED ubuntu and then did a clean re install . Worked fine for some time, until i started installing aps via Automatix2. I alaso install compiz and the 915resolution patch for my dell xps m1210 laptop. After a restart i got the damn HAL ERROR AGAIN, THE SAME ERROR AND THE NETWORK ICON IN THE SYSTEM TRAY HAS A CROSS OVER IT.
How to fix thisssssssssss?
please helpppp me someoneeeeeeeeee

---

### Post by jzurawski99 on 2007-07-25
Below is something I posted in another hal issue thread. It might apply here also.


Re: the infamous Failed to initialize hal error 

--------------------------------------------------------------------------------

I also suffered from this problem. After much searching, it seems that these hal issues might be the result of a recent hal update via Ubuntus automatic update system  (just speculating).

Now, with me being a newbie at Ubuntu, take everything I say with a grain of salt. But, these are the steps I followed (gathered from a few other posts) that got me up and running again.

In short, you need to roll back the hal update. Below are the steps I followed to accomplish this.

First, when this error occured I lost all USB, DVD drives and also my network connectivety (wireless and wired).

The line below allowed me to restart dbus and hal (I needed to get my connectivity back for the roll back).

sudo /etc/init.d/dbus restart

Whatever the above line did, it allowed me to manually reconfigure my wired connection (even though it didn't look like it was working, I was able to connect to the internet).

I then followed the instrucitions below to force the hal rollback.

The info below was pasted from a thread titled "Recent HAL update caused frequently failure for "suspend when lid closes"

************************************************** *********************************

Re: Recent HAL update caused frequently failure for "suspend when lid closes" 

--------------------------------------------------------------------------------

I think i found a temp workaround for this: rollback to older versions of those hal packages.

This can be done pretty easily with Synaptic package manager in Ubuntu:

1. Open Synaptic

2. Menu: file -> history, find the history of the day you installed the hal update. For me it is under "5/11":

Code:
Commit Log for Fri May 11 15:08:47 2007

Upgraded the following packages:
hal (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
hal-device-manager (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal-storage1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1

Installed the following packages:
hal-info (20070402-1ubuntu1~feisty1)3. Now, search for each of the first 4 packages in Synaptic, then use "force version" in Package menu to force the latest version for each of them to be 0.5.8.1-4ubuntu12. When doing this for the first package, Synaptic automatically prompts to remove hal-info, which is what we want.

4. Now click on the "Apply" button. These packages will be downgraded to the good version.

5. After that, you'll immediately see the update manager pops up again to tell you there are new hal updates, this is the sign that the downgrading was successful. Of course this time you want to ignore the hal update...

************************************************** *************************************

Again, I have no idea what any of this effects. All I know is that after following the above I regained all hardware functionality. I hope this helps some of you.

JZ

---

### Post by hindukush on 2007-07-25
Hi thanks for the help!

could you please explain in a little more detail after i search for HAL in the synaptic, what do i do after tis???

---

### Post by hindukush on 2007-07-25
oh thank you thank youuuuuuuuuuu! very much!
finally got it to workkkkkkkkkkkkkkk!! yipeeeeeeeeeee

---

### Post by eeried on 2007-08-03
hello,

I'm also trying to downgrade due to possible problems with the HAL daemon -- see 
[http://ubuntuforums.org/showthread.php?t=513056](http://ubuntuforums.org/showthread.php?t=513056)

I'm running Xubuntu so the packages may be slightly different. I cleaned the /var/cache/apt/archives dir (using the command apt-get clean)so I can't find the names of the packages easily.

I always update, upgrade and install packages through the command line because it's quicker on my old machine. I've noticed some packages are kept back, (kernel and HAL) so I guess the fateful HAL packages weren't updated. In a moment of silliness I decide to upgrade the kernel through synaptic. So the HAL packages were upgraded alongside  the kernel. Now I can't even listen to a CD...

Here's the detailed howto:

After looking for the packages you've installed in Synaptic, search for them Manu Edit > Search

Search for Hal

Click the line once you've found it
Menu Packages > Force... the popup window offers to to choose a previous version. the present version is shown, so select the former one by clicking on the small triangle.

Then click the Apply button. In my case Synaptic offered to downgrade HAL and to remove hal-info.

If however I started by removing hal-info it would have removed lots of useful apps while downgrading HAL only removes hal-info which had been installed alongside the upgrading of HAL in my case.

Now I'm going to reboot and see if this HAL version is okay and if it runs fine with the upgraded kernel which was installed in the same days as the leathal HAL version.

See you soon then

---

### Post by eeried on 2007-08-03
Hello again,

I've had the same hog problem with HAL and the latest kernel (2.6.20-16-generic) on k3b. At least I was able to listen to a CD on VLC.

So I booted on the former kernel version 2.6.20-15-generic, and K3b + HAL took up all the CPU alternatively for a couple of minutes and then, vanished to the bottom of the top list. Great. At the moment I'm extracting one of my own CDs into FLAC -- (I think that's  a rather CPU consuming task for an experiment.

So now I'm going to remove 2.6.20-16 kernel and stuff through synaptic.

So many thanks for the downgrading-with-synaptic tip.

Two more tips would be very useful though:

Now how do you downgrade using the command line and apt-get?

Where do you find the  Synaptic history log in the file system (I looked into /var/log)?

============
Now I've started a second extraction and the CPU is almost throttled and doesn't get freed. So things aren't perfect yet.
The top command shows hald-addon-stor  as the hog and when it vanished K3b becomes the hog. The extraction falied, and then I killed k3b and hald-addon-stor.

---

### Post by ashishgoel on 2007-08-08
i'm also havin HAL error after update - will try ur solution soon and post it...

thanx

---

### Post by ashishgoel on 2007-08-08
it worked....  i think the updated version is havin gud daamm probs...

---

### Post by eeried on 2007-08-08
I'm glad your problem is solved ashishgoel.
To keep things nice as they are now upgrade with the command line only:
```
sudo apt-get update
```
Press Enter and wait until it's over
Then
```
sudo apt-get upgrade
```
Press Enter

You'll see a line saying some apckages have been kept back: HAL should be among them.

In synaptic there should be a way to force the program not to upgrade certains packages but I tried that once on Firefox and it didn't work for me.
cheers
PS: my awful problem with HAL isn't solved at all. I still can't rip one of my CDs :mad: so I'm going over to my original thread: [http://ubuntuforums.org/showthread.php?t=513056](http://ubuntuforums.org/showthread.php?t=513056)

---

### Post by bibobx on 2007-08-31
Finally i'm able to post in this thread.  I' newbie in ubuntu, using Gutsy  the Hal Failed... occur after logon, networkmanager fail  hardware-information   to and no DVD. I Found this solution Copy this simlink /etc/rc3.d/S12Dbus to /etc/rc2.d/. It worked for me. answer are welcome

---

