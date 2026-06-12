---
title: "Vostro 1500 How To  and Outstanding Issues Thread"
date: 2007-08-23
forum: Dell  Ubuntu Support
---

### Post by PaganImmolator on 2007-08-23
[COLOR="Yellow"]**<<most of this how to has been culled from other posts. I put all of the info in one post for my benefit and the benefit of other 1500 owners>>**[/COLOR]

+++++++++++++++++++++
Dell Vostro 1500 How To
+++++++++++++++++++++

I am sure a lot of people bought a Dell Vostro 1500 over the last few weeks as Dell pricing was very reasonable. 

My laptop straight from the factory had:

Core 2 Duo 1.6 Ghz
1 GB of SDRAM
15.4 inch Wide Screen XGA LCD Display with TrueLife
128 MB Nvidia 8400M GS video card
Broadcom 1390 802.11g mini WiFi card
Windows XP Home Edition

+++++++++++++++++++++
[COLOR="Red"]Known Issues[/COLOR]
++++++++++++++++++++++
[COLOR="Blue"]Suspend and Hibernate do not work consistently.
Sound sometimes cuts off.
Sound comes out of headphones and speakers concurrently.
Wifi seems to have problems connecting to Windows shares at times.
If you have been 'roaming' with Wifi but then attempt to enter a manual network connect (not through the roaming pull down) the Wifi hangs requiring a hard boot to initialize the new settings.

Other than that, my Vostro is about 90% functional.[/COLOR]


Out of the box the first thing I did is test the laptop under XP. Everything seemed to be working satisfactorly. WiFi connected to my router and I was able to browse. Buttons all work. Fan's work well. 

On my computer I  had 3 partitions from the factory. One partition for XP. 2 other partitions existed on my HD. One looks like a XP install disk mirror and another looks like maybe it holds utilities. I didn't mess with those. With the one large partition holding XP I defragmented the drive 2x to make sure all the files were as close to the front of the partition. Next I partitioned the XP partition roughly in half. I used a gparted live CD to do this but there are other programs like Ghost and Partition Magic. 


+++++++++++++++++++++++++++
Installing Ubunto Feisty 7.04 32bit 
+++++++++++++++++++++++++++

The Ubuntu Live CD or the alternate install CD will NOT WORK. To install using the Live CD, I found this set of instructions invaluable:

amber_474 wrote:

Pre-Install:


Boot from the Live CD
Press F6 to edit the command line and
remove: splash quiet[COLOR="Blue"] (actually on my screen it quiet splash, but just delete it from the end of the line)[/COLOR]
add: break=top [COLOR="Blue"](to the beginning of that line)[/COLOR]
from the command line and press Enter

Ubuntu will boot and get you to the Busybox shell

     /bin/sh: can't access tty; job control turned off(sh)

Give the commands:

$ modprobe piix
$ exit

Ubuntu boots and X server fails to start, so do:

$ sudo dpkg-reconfigure xserver-xorg

Select: 'vesa' instead of 'nv' as the driver
Select /dev/psaux for mouse

and rest is default. [COLOR="Blue"](use the options the program highlights)
[/COLOR]
$ sudo /etc/init.d/gdm start
or
$ sudo /etc/init.d/gdm restart

--might have to do that last step twice, I don't know why. The live CD will run and start up the desktop. You will notice that the desktop looks wierd. Thats because it is not in the native resolution of your screen. We will fix this later.

Click your install icon and follow the prompts. I didn't do anything weird except when it gets to the partition manager make sure to choose manual to show the installer where your empty drive space is.

++++++++++++++++++++
Update and get CD to work
++++++++++++++++++++

Once you have everything installed you should reboot. At the GRUB screen you should have options for your old XP and your new Ubunto.

Log onto Ubunto and make sure you have access to the internet. You will have to use a wired connection for now. Later we will get the WiFi working. 

Earlier you'll remember us using 'piix'. This is the driver for the DVD drive. We have to tell Ubunto to load this each time so...
applications > accessories > terminal

sudo gedit /etc/modules

and at the bottom of the file add 

piix

save and exit but stay in this terminal.

Now we should take this time to update all the existing files from the install to the latest. Do so buy typing in the terminal window:

sudo update-manager &

this will start the update manager. Say yes to everything if it asks you. 

Reboot when your done

++++++++++++++++++
Installing the Nvidia Drivers
++++++++++++++++++

Nothing could be easier. Go here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

scroll down to the bottom end of the page and download the file for Debian and Ubuntu to your desktop.

Click on the file and it should extract. Once it is extracted go to

Applications>System Tools>Envy

The program will ask you if you want to install the Nvidia drivers. Go through the program. Make sure it updates your X config files. 

Reboot

+++++++++++++++++
Get Wireless working
+++++++++++++++++

Again simple. This is from a post by DarkNoob:

The installer checks for a compatible chipset. If it finds that your chipset is compatible it will tell you. If it finds that your chipset is not compatible, it will tell you. I have tested it and this detection seems to work fine. Either way, it is your choice as to which way you want to go. Just choose the method you want to use and click install. It is that easy. If your chipset is found to be incompatible, you will be given the option to install NDISwrapper and the correct Windows driver. The installer now does some automatic logging and includes some information from your kernel log and your system log.

Before you get started, open a terminal and type
Code:

sudo aptitude update
sudo aptitude upgrade

Then...

1. Download the GTK installer from 
[http://blakecmartin.googlepages.com/bcm43xx-gtk-installer-0.3.1.tar.gz](http://blakecmartin.googlepages.com/bcm43xx-gtk-installer-0.3.1.tar.gz)

This version is new with many changes, so if you would rather use the 0.2.1 version you can get it here. It is easiest to save this file to your home folder but it doesn't really matter where you put it.
2. Right click the .tar.gz file and click Extract Here. It should extract into its own directory.
3. Go into the bcm43xx-gtk-installer-0.2.1 folder and double click the installer.py file and click the Run button when prompted.
4. The installer should detect which installation method is appropriate for you.
5. Click the install button to install the appropriate driver.
6. Now enter your password and press the Enter key.

I am using WEP security but if your using another kind you might to research how to do that. Try this thread:

[http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom)


++++++++++++++++++++++++++++++++
Get fans to work
++++++++++++++++++++++++++++++++

Some people has complained that the fans don't work after the Ubuntu install. I have found that they do work however they seem to cut on way too late. I understand that you have to find a happy medium between battery life and cooling but sometimes the laptop seems unusually hot. So better safe than sorry. This fix will allow you to control the fans and set temperature based cut ons. This fix will sense 2 fans but apparently only one is controllable but thats enough to get your temps down 

Hophead wrote:

Fan and temp control (install gkrellm)
1. sudo apt-get install i8kutils gkrellm gkrellm-i8k
2. sudo modprobe i8k force=1
3. sudo gedit /etc/modules
4. add the following line to the end of the file: i8k force=1
5. go to System > Preferences > Sessions > Startup Programs
6. Click ADD and put the command: gkrellm
Now you will see the GKrellm utility load at startup and you can then configure your fan thresholds in settings - plugins - Dell i8k

After installing gkrellm, I opened it and under Plugins, found Dell I8K Plugin. After enabling it, I saw that only the left fan was on. I changed the Temperature Units from Celsius to Fahrenheit, then the right fan came on. I thought this was a coincidence at first, but everytime I change it to Celsius, the right fan goes back off.

++++++++++++++
Final Thoughts
++++++++++++++

piix is apparently being depreciated in the next edition of Ubuntu. I don't know what the workaround will be in Gutsy yet.

---

### Post by saru411 on 2007-08-23
> **PaganImmolator said:**
> [COLOR="Yellow"]
++++++++++++++++++++++++++++++++
Get fans to work
++++++++++++++++++++++++++++++++

Some people has complained that the fans don't work after the Ubuntu install. I have found that they do work however they seem to cut on way too late. I understand that you have to find a happy medium between battery life and cooling but sometimes the laptop seems unusually hot. So better safe than sorry. This fix will allow you to control the fans and set temperature based cut ons. This fix will sense 2 fans but apparently only one is controllable but thats enough to get your temps down 

Hophead wrote:

Fan and temp control (install gkrellm)
1. sudo apt-get install i8kutils gkrellm gkrellm-i8k
2. sudo modprobe i8k force=1
3. sudo gedit /etc/modules
4. add the following line to the end of the file: i8k force=1
5. go to System > Preferences > Sessions > Startup Programs
6. Click ADD and put the command: gkrellm
Now you will see the GKrellm utility load at startup and you can then configure your fan thresholds in settings - plugins - Dell i8k

After installing gkrellm, I opened it and under Plugins, found Dell I8K Plugin. After enabling it, I saw that only the left fan was on. I changed the Temperature Units from Celsius to Fahrenheit, then the right fan came on. I thought this was a coincidence at first, but everytime I change it to Celsius, the right fan goes back off.


How do you install i8utils? it s a a 32 bit program. when you run this code "sudo apt-get install i8kutils gkrellm gkrellm-i8k" it will not download or install it.

---

### Post by PaganImmolator on 2007-08-24
Thats easy, I am not running 64bit Ubuntu. I am running just the regular  32bit ubuntu. 64bit is not mature due to the buggyness of certain software and drivers. Adobe flash comes to mind. I doubt that you need a 64bit OS unless your doing some serious rendering or number crunching. May want to revert back to regular Ubuntu unless you just really want the geek factor of saying your running a 64bit OS.

dan@vostro:~$ uname -a
Linux vostro 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

---

### Post by saru411 on 2007-08-24
there are plenty of ways to make flash run on amd64 operating systems. thats not really the point. the point is why is there no fan control for amd64 operating systems? this is something that should not be over looked. this is not something as simple as not going to youtube. its the health of your hardware at stake. if no one uses amd64 operating systems they will never mature. i believe your thinking is flawed, but thats for another thread.  im not interested in your flame bait. i'm more interested in an answer to my cooling issue. most of the cooling threads are due to people running 64 bit ubuntu and running into the fact that they can not install i8k. the question is what are my other options for this system. no, 32 bit ubuntu is not my first or second option. its more like my last next to running the copy of vista that came with my vostro 1500.lets keep this on topic please.

---

### Post by tashmooclam on 2007-08-24
I sent my Dell Vostro 1500 back because I gave up in frustration.
But, I am impressed that Paganimmolator got his working.

---

### Post by saru411 on 2007-08-24
mine is working fine also(other than the cooling issue that im unsure is really an issue,max temp so far has been 58*C. i just want more control over my system like my desktop). the other how to for vostro + envy + howto broadcom 4xxx wireless will get you to a stable position easily. it's almost painless. i just wouldn't expect someone who is new to linux to buy a new laptop that has just come out and expect everything to work without some work. although i think anyone who took their time out to write a howto like this is a great asset to the community.

---

### Post by PaganImmolator on 2007-08-24
> **saru411 said:**
> there are plenty of ways to make flash run on amd64 operating systems. thats not really the point. the point is why is there no fan control for amd64 operating systems? this is something that should not be over looked. this is not something as simple as not going to youtube. its the health of your hardware at stake. if no one uses amd64 operating systems they will never mature. i believe your thinking is flawed, but thats for another thread.  im not interested in your flame bait. i'm more interested in an answer to my cooling issue. most of the cooling threads are due to people running 64 bit ubuntu and running into the fact that they can not install i8k. the question is what are my other options for this system. no, 32 bit ubuntu is not my first or second option. its more like my last next to running the copy of vista that came with my vostro 1500.lets keep this on topic please.

I think you misunderstand me. I encourage you to explore all the possibilities of the 64 bit OS. However, on my laptop my cooling issues are basically solved and that is enough for me. I have seen you post several times about heat issues. I suspect because you are on the bleeding edge of drivers and OS's you are probably going to have issues that are not going to be resolved for a while. In the mean time please do not tell me to keep my own thread on topic. This thread is how I installed a 32bit OS on my Intel based Vostro and the unresolved issues dealing with that install. I welcome input but lets keep it constructive.

---

### Post by PaganImmolator on 2007-08-24
Main post updated to reflect problems with the WiFi manager. Wifi does not work if you have been roaming (lets say away from the office and looking for a hot spot) and then returning to the office and attempting to connect again to office WiFi through the 

System>Administration>Network setting screen 

and then entering a manual network setting (that way you don't have to keep entering your WiFi security key)  everytime you boot.

WiFi refuses to initialize new settings without a hard boot. You can still connect using the 'roaming' menu but your windows shares will not be available. 

This is not a major issue since it's easily fixable but I suspect this issue is related to the network not being available after a suspend or hibernate.

---

### Post by saru411 on 2007-08-25
[http://ubuntuforums.org/showthread.php?t=405990&highlight=dell+wireless+1390](http://ubuntuforums.org/showthread.php?t=405990&highlight=dell+wireless+1390)

i installed this to make my dell wireless 1390 card work. i can right click on the network icon in the tool bar and pick between detected networks. as for windows networks i would not know since i dont use any. hope this helps

sorry. i forgot to check your thread. this is the same link you use.

---

### Post by elyk on 2007-09-02
I just noticed that the vostro 1500 comes with a receive-only IR port for remote control purposes. Has anyone succeeded in getting that working? Or is there a good IrDA how-to I could try?

---

### Post by Alex_Hamilton on 2007-09-03
A wonderful how-to, PaganImmolator! I got this all done on my 1500 via the same sort of painstaking trial-and-error and locating solutions like Envy and the WiFi card driver that you did... but if I'd started after your post instead of before, I could probably have gotten the whole thing done in an hour or two instead of a week. Well-written and easy to follow. Excellent work!

I've just discovered an issue with the CD/DVD burner - Ubuntu doesn't seem to be recognizing it as a burner, only as a reader. Anyone else had this problem?

---

### Post by elyk on 2007-09-03
My drive shows up as a burner in both k3b and nautilus's burner. I haven't tried gnome-baker.
However, I've run into another issue. I'm trying to install skype but the microphone doesn't seem to be working, and testing audio capture in the sound config app gives ```
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'
```. Sound recorder seem to record anything either.
Has anyone managed to get the internal microphone working, and if so, any pointers?
Thanks

---

### Post by Alex_Hamilton on 2007-09-04
> **elyk said:**
> I'm trying to install skype but the microphone doesn't seem to be working, and testing audio capture in the sound config app gives ```
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'
```. Sound recorder seem to record anything either.
Has anyone managed to get the internal microphone working, and if so, any pointers?
Thanks
Where's the sound config app?
I haven't been able to record in Gnome sound recorder or in several other audio applications, despite trying out just about every input device setting I can find. I *am* able to record audio using an external webcam's mic.

---

### Post by PaganImmolator on 2007-09-04
Sorry, guys. Haven't been monitoring the thread lately. Been working a lot of overtime. First off, thanks Alex for the kind words. As far as the microphone working. I have no idea if it works or not. I don't think I have one but if I can dig one up, I will try it. 

I tried to recompile the ALSA driver for Ubuntu with limited success. I don't think it resolved any of the outstanding issues with sound. But I will keep working on it. 

I am able to sleep to disk but I am still trying to sleep to RAM.

---

### Post by elyk on 2007-09-04
@alex: The gnome sound config app is under system>preferences>sound. 
@PaganImmolator: The Vostro 1500 comes with a built in microphone (at least mine did) above the screen - that's the one I'm trying to get to work. I could record briefly using sound recorder but then it stopped working again. 
I can suspend to ram (although the sound stops working after I resume, a bug that many people seem to be experiencing), but I can't get hibernate working yet. How did you recompile the alsa driver? I've tried using module assistant with, once again, limited success.
I probably should add if I haven't already that I'm running gutsy (it was easier than trying to get fiesty to boot), so my experiences may be slightly different. But I'm hoping that fixes you discover on fiesty will work on gutsy, and maybe they can be integrated into the final release so that it "just works".

---

### Post by .exe on 2007-09-06
Don't know what I'd do if not for these forums.

---

### Post by HiFly on 2007-09-07
> **.exe said:**
> Don't know what I'd do if not for these forums.

aye... I'd be lost as well if not for the guide compiled by PaganImmolator.

Thank you very much for you work.

---

### Post by HiFly on 2007-09-07
> **elyk said:**
> @alex: The gnome sound config app is under system>preferences>sound. 
@PaganImmolator: The Vostro 1500 comes with a built in microphone (at least mine did) above the screen - that's the one I'm trying to get to work. I could record briefly using sound recorder but then it stopped working again. 
I can suspend to ram (although the sound stops working after I resume, a bug that many people seem to be experiencing), but I can't get hibernate working yet. How did you recompile the alsa driver? I've tried using module assistant with, once again, limited success.
I probably should add if I haven't already that I'm running gutsy (it was easier than trying to get fiesty to boot), so my experiences may be slightly different. But I'm hoping that fixes you discover on fiesty will work on gutsy, and maybe they can be integrated into the final release so that it "just works".

just wondering if there are the same difficulties installing gutsy on vostro 1500 as there is with 7.04.  If so, would this same guide be applicable?

---

### Post by saru411 on 2007-09-07
why install alpha software when it can change constantly and break your system. if you want to help debug the new o/s(gutsy) feel free, but remember it's APLHA!!!

---

### Post by elyk on 2007-09-08
Well, fiesty wouldn't boot at all (I tried the instructions, but i still couldn't get the xserver to properly detect my video card for beryl). Gutsy overall is actually surprisingly stable, and supports my video card wonderfully (I think this is because I got mine with the Intel video card rather than the nVidia, and Gutsy includes updated drivers from intel).  The only problems that I've been having is with nonessential hardware (like audio), and my hope is that by using it in this early stage, and filing bug reports, I'll be able to get any outstanding issues fixed and have a "just works" system by the time gutsy final comes out.

---

### Post by aarumugham on 2007-09-10
hello all,

i have the dell 1390 card in my vostro 1500.

i am not sure what i did wrong - i used the :

/home/akilan/drivers/bcm43xx-0.3.2-internet

i actually tried to install it a few times because initially i got an error.

the last time, i got this 
screen:[IMG]/home/akilan/Desktop/Screenshot-null-3.png[/IMG]

under the system>administration>network the wireless does not even show up.

when  i type iwconfig in terminal i get no wireless extensions.

any idea what to do?

---

### Post by stubish on 2007-09-23
I've got no joy on the inbult mic as well (on the vostro 1400) anybody got a solution for this yet?

---

### Post by deadtrout on 2007-09-25
Is there any solution for the sound coming out of both the headphones and speakers concurrently?  I see the issue has been identified but I don't see anything describing a solution.

I have tried adding options=3stack to the module in  /etc/modprobe.d/options but I'm still getting this problem.   I notice if I boot the computer with the headphones plugged in I can get the headphones with no speakers.  Rebooting is a pain just to get this to work.

Thanks for all the info in one place.  This probably saved me quite a few hours.
-Terry

---

### Post by elyk on 2007-09-25
I have found one workaround, and that is to launch the volume control, go to the switches tab, and check the "line in as output" box. Go to the playback tab, mute the "front" control, and make sure that the surround control is not muted and is near or at the max. Plug your headphones into the line-in/microphone jack (which is now acting as the rear output for a surround sound setup). The downside to this is a significant reduction in volume, and possibly in sound quality, but in enables usage of headphones without reboot.
There are bugs on launchpad about both these issues.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141656](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/141656)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/129907](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/129907)

---

### Post by dandanplan on 2007-09-27
Hello,

I have also an Vostro 1500 and installed Ubuntu 7.04 on it. Basically I can only repeat what the others have written in their posts.
For the installation I choose the alternate install CD, and added the boot option all_generic_ide. Then I added the piix to the modules and removed (automatically) the all_generic_ide from grub with the kernel update. For the graphics I also had to choose the drivers from nvidia.com. (It's a pity that Nvidia don't offer a distribution specific package. At my old Laptop I used the ATI Drivers and OK they are far more worse, but at least they had the possibility to generate such packages. I feel far more saver when a package is installed the debian way.)
<maybe_interesting>
- I couldn't load the nvidia module after a reboot. So I searched the web and found out that you have to (or could) uncomment any line with nvidia in it from /etc/modprobe.d/lrm-video . Now it was possible to load the nvidia module.
- Sometimes when I reboot the Laptop hangs so I added a vga= to the grub boot options.
</maybe_interesting>
Thanks to the folks here in the forum I found the uvc stuff to get the webcam working.
External USB Drives, Wireless with WPA, the case buttons, cable networking and touchpad worked out of the box.

Still Pending Problems:
- The mic (nothing new to you I suppose). Also a external mic on the line in isn't working.
- The sound generally. I can't get the headphone jack sense to work. Even with the hint from my previous poster. Maybe I could compile a newer alsa version, but I'm to lazy and I want a clean upgrade to 7.10.
- SD Card Slot: I think this should work but I don't own any cards of these type. When a friend visited I took his micro(?) mmc card from his phone, and shortly tested it, but it didn't work. I can live with that.
- Does someone also have strange sounds from his hdd? A periodically tick when there aren't any accesses? It doesn't sound fit. I would record it but as you know the mic...
- I read in some threads (or was it here) that some people complain about the fans, but I can't comprehend the frustrated state. I think that my Laptop isn't to hot nor to loud. Now it has 48 C (room temp is about 16 C). The fan starts whispering when the temp reaches 63 C. So I think perfectly normal or isn't it?

Not tested yet: firewire, vga- & Tv-out, pcmcia

That's all for now. I'm not a native English speaker so I suppose you have to live with my version of the English language. 
Thanks for all the tips and hints
dandanplan

---

### Post by Linux_Punk on 2007-10-10
SUSPEND WORKING ON VOSTRO SERIES (ALL)
I just installed the new 100.14.19 drivers from Nvidia and the suspend and hibernate work flawlessly. if youre still using the older 100.14.11 driver the new one makes the suspend work. hooray!! now to get this damn webcam working and im done :)

---

### Post by Linux_Punk on 2007-10-12
ok people found out something interesting about the suspend issue>
If you have a desktop effects manager enabled it does not go back into the desktop properly. If you dont have any kind of manager enabled, the suspend works, but for some reason (might be a 1500 issue only) the sound does not work after coming back from suspend. just though id post my 'experiment results'

---

### Post by Merlin7777 on 2007-10-12
Thanks for the update. I still haven't loaded ubuntu onto my laptop, but I may do it today. I was just waiting for most of the issues to be worked out. It looks like most have.

Thanks for posting your results.

---

### Post by Merlin7777 on 2007-10-13
Hey guys. I am having some troubles. I am following the guide on the first page and I can't get past the:

modprobe piix
exit

bit.

I punch this in at the commandline and everything seems to go fine for about a minute. things are getting checked and initialized and all of that fun stuff.

But after it looks like things have finished intitializing, the screen goes black. Actually I am pretty sure it turns off. the DVD drive is busy for about a minute, but then nothing happens. I waited for 10 minutes and nothing happens. All I have to know that the computer is actually on is the blue power icon in the corner. 

It turns out that the DVD drive also is locked. The only wait I can shut down is if I tap the power button. Then the DVD drive spins up and spits out the disk. I have to hold the power button after this in order to get the laptop to actually shutdown. 

What is going on?

I can't even see anything after the modprobe piix step. I went ahead and tried typing the sudo dpkg-reconfigure xserver-xorg line to see if anything happened and nothing did.

I have no idea what to do know, so any help would be appreciated.

---

### Post by Merlin7777 on 2007-10-14
Partial success. 

Ubuntu 7.10 RC boots up mostly fine. Throughs one error about GNOME daemon, but otherwise runs fine.

Sound doesn't seem to be recognized.

Hopefully, everything will be fixed in final release. who knows?

---

### Post by elyk on 2007-10-14
Sound is a known issue ([LP Bug # 131133](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131133)). Word is there's a backports package to fix this, but it's not showing up for everyone yet.

---

### Post by Merlin7777 on 2007-10-14
Ok, thanks elyk. I will wait till the 7.10 final comes out, and then try and fix the audio if it still occurs.

---

### Post by Merlin7777 on 2007-10-19
This thread should probably be updated to support Ubuntu 7.10 Final. Pretty much everything is fixed and automatic except the sound, and maybe the fans.

---

### Post by JonnyBlazexx on 2007-10-21
I upgraded to Ubuntu 7.10 via the in OS prompt.  I then find my sound quit working; I see that a fix for the vostro 1500 is to update the kernel to the newest version.  I do that, I still don't have my sound working; I can only hear beeps -the beep you hear from holding down a key for too long, etc. - and can't hear anything else.  The console command to list sound card devices shows nothing is present.  

But... my main problem from upgrading to the newest kernel is that my internet connection will no longer work.  Wireless networks show up, but i cannot connect to non-secure or secure networks, i see the icon spin, with one green circle lit up, but it never actually connects.  Also, when I connect directly, with a hard-line cat-5 cable, I still only get the same spinning icon with one green circle and still can’t connect.

*head spins*  "but i updated things... shouldn't it work better?" haha.  Anyways, I know this is my first post, but I am not new to these forums as I have been quite a big reader.

Hopefully someone else had this problem and knew how to fix it?

---

### Post by elyk on 2007-10-22
The wireless card issues are probably due to the fact that the drivers must be recompiled for a new kernel. However, with recently released packages some people have been able to get sound working without a kernel upgrade (and I have found that the kernel upgrade did not consistently fix my sound, as noted on the wiki page). Try this: At the grub prompt, select your old kernel (2.6.22-14), and once it boots check if your wireless card is working. Then, use your favorite package manager to install linux-backports-modules-generic. That should automatically install the package linux-backports-modules-2.6.22-14-generic, if not install that package manually (the advantage of installing the more general generic package is that it will keep your modules up to date as your kernel updates). Reboot and check if your sound is working now (make sure you once again boot into 2.6.22-14). If all is working, then you could optionally remove the 2.6.23 kernel image, or leave it on there (it won't hurt anything) and  either edit /boot/grub/menu.lst or use startup manager to change the default kernel back to 2.6.22-14.

---

### Post by Silothepro on 2007-10-23
I just wanted to give you guys props for this thread, it has helped me out more than I can tell you!! Thank you!!!!

---

### Post by dmgthe2nd on 2007-10-26
I´ve been looking for the sound card driver everywhere online (or the method to get sound) and I can´t seem to find it.  
Does anyone have sound on their 1500?

---

### Post by professor fate on 2007-10-26
What sound card are you using?  I've got a 1400 that's refusing to cooperate.

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

---

### Post by elyk on 2007-10-26
the 1500 (and I believe all the Vostros) have soundcards that use the Intel HDA driver (found as a part of the latest alsa release - recompiling this from source has helped some people). What seems to be tricky is the codec that the card is using. The Vostro is Sigmatel STAC9205; I don't know about the 1400.

---

### Post by tylerhardy on 2007-10-26
Hi all.  I am the biggest greeny to ubuntu.  I just downloaded and installed ubuntu 7.10 on my dell vostro 1500 and I am having difficulties with many issues.

My notebook is T7500, 160GB HDD, 2GB RAM, Dell 1500 wireless N-draft, and the sigmatel (or Intel HD audio, I don't know).  

I installed it pretty much by stumbling until it worked (on the account I couldn't get any good and thorough install guides with dual booting with vista) and so I hope nothing has happend in the installation that would create these errors.  

Issue 1.) most importantly I cannot connect to the internet via wireless nor Ethernet.  Neither are listed in network settings and Dell of course doesn't have ubuntu drivers for this model.  

Issue 2.) no sound, this seems to be a major issue with all vostros but due to the lack of internet I cannot update ubuntu and I've tried to follow some guides but they are not clear on their steps and keying in the terminal.

Issue 3.) I couldn't decide how I wanted the partitions on my hard drive and I hope that I had set them right: 
vista - 100GB
Shared (fat32) - 5GB
Swap - 2GB
Ubuntu - 49GB

is this ok, I've had difficulties setting up the partitions in the g parted utility. but I don't have any problems with reinstalling the OS if it comes to it.

Sorry for the lengthy post, but I am too frusterated with this (I feel like I was dropped in china naked with no guide nor translator). Please help

---

### Post by elyk on 2007-10-26
Your partition scheme should be fine - Ubuntu only requires a few gigs to run, plus swap. You could try [downloading  linux-backports-modules-2.6.22-14-generic](http://packages.ubuntu.com/gutsy/base/linux-backports-modules-2.6.22-14-generic) from the ubuntu packages site on a different computer, then transfer the deb file to your ubuntu machine and install it on there. 
I don't know why your ethernet isn't working - I've never had that problem on my laptop, and ethernet cards in general seem to be well supported - do you see any sort of network icon in your notification area? If so, what does it look like?

---

### Post by tylerhardy on 2007-10-27
when I go into networks it just shows the modem and it can be configured but nothing else. and it is on the loop back address 127.0.0.1 and no way to change it.

---

### Post by dmgthe2nd on 2007-10-27
> **professor fate said:**
> What sound card are you using?  I've got a 1400 that's refusing to cooperate.

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

I'm not sure how to find the device I'm using since Ubuntu doesn't see my sound card but I know I took the High Definition Audio 2.0 option at time of purchase.

I guess the sound is still a major issue for now, if anyone finds a solultion please post it in this thread or make a new one.

Also, forgot to give thanks for this great resource!!  This linux noob was about to give up when I stumbled upon this thread.

Now just to hear some sweet music from my lappy... everything in due time I suppose.

Have a good one.

**Update: **Found solution to fix sound problem with Gutsy on a vostro 1500.  [http://ubuntuforums.org/showthread.php?t=569082&highlight=vostro+1500+sound]("http://ubuntuforums.org/showthread.php?t=569082&highlight=vostro+1500+sound")

---

### Post by Matei_badger on 2007-11-10
i have recently bought a vostro 1500 and i have problems partitioning my hdd. Apparently it allready has 4 partitions

hda1 - dell recovery
hda2 - NTFS - WinXP
hda3 - extended
hda4 - 2.5 GB in the extended
hda5 - 3 GB 

cause of this i am not able to create any new partitions in order to install my ubuntu.... any ideas?

thx

---

### Post by aldenhg on 2007-11-10
Has anyone with the microphone issues tried adding (or changing if it's already there) ```
options snd-hda-intel model=6stack
```
in /etc/modprobe.d/alsa-base? I currently use the 3stack layout, but with the re-routing of signals that 6stack would bring about it could help. I'd try it myself, but the girlfriend is asleep and I'm pretty sure that yelling at my computer *might* wake her up. 

EDIT:Don't bother. No sound with 6stack and if you try and run alsamixer the system goes belly up. 

BTW, I've got a 1400 and she's got a 1500 and I've noticed that the sound quality on hers (running XP) is MUCH better than mine running 7.10. I've checked and the sound cards are basically the same thing so I'm guessing it's just poor support in the alsa driver...


@Matei_badger:
You can always re-partition and make the extended partition larger and install inside of it. I'm pretty sure GRUB can handle that.

---

### Post by mjamesd on 2007-12-03
Has anyone gotten the IR port to work? My roommate has an HP Pavilion dc2000 that came with a Windows Media Center remote. I tried the instructions [here]("https://help.ubuntu.com/community/Install_Lirc_Gutsy") but when I run `irw` it gives me a new command prompt without waiting for any signal.  Rebooting doesn't work and `dmesg` doesn't show anything (i.e., doesn't reference lirc at all). My /etc/lirc/hardware.conf file says it's using modules "lirc_dev" and "lirc_mceusb2".

First off... does the V1500 have an IR port or just something that looks suspiciously like one? Second, I installed liblircclient-dev and it didn't work. And finally, should I load more modules or something? Maybe build lirc-modules-source from source rather than through apt?

Thanks.

---

### Post by elyk on 2007-12-03
The 1500 does have an IR port, or rather an IR receiver (it can't send signals). I, too, have been trying without success to get it working. It'd probably be easier if Dell told us the chipset or some identifying number for that component.

---

### Post by tamal on 2008-01-10
Hi, I found the instructions working for me till the 'set it to manual for partitioning'. Unlike you I had vista preinstalled in my laptop. So I partitioned it using the disk manager in built in vista. But when I select manual for partitioning, ubuntu does not recognize vista at all. It wants me to proceed with the complete hard disk. 

How can I make it recognize vista?

---

### Post by Steven_585 on 2008-01-28
I recently purchased a Vostro 1500 and installed Ubuntu on it.
I am having trouble connecting to my home wireless network. I enter the specified information such as name and key, but after a few moments of searching or configuring, it asks me for the encryption key again, and it does not work.

Correct me if I am wrong, but i believe that i need the driver installed for the Dell Wireless 1390 802.11g Mini Card, which i have.

Thanks for all your help,
Steven

---

### Post by Hexagrapher666 on 2008-01-31
> **mjamesd said:**
> ...does the V1500 have an IR port or just something that looks suspiciously like one?

The Vostro 1400, 1500, and 1700 have IR receivers on the front for the optional Dell Travel Remote that is designed to be transported in the ExpressCard slot on the side of the Vostro.  The Dell website says that the IR receiver on Dell laptops will not work with any other IR device other than the Dell Travel Remote (though as with all things this could be hacked with enough ingenuity).  When purchasing a Vostro, the IR remote is an additional $60, and this $60 may include the chip for the IR receiver, so it is entirely possible that if you did not purchase the Dell Travel Remote with your Vostro that the chip for the IR receiver might not even be there.  You may be able to get a functional drop-in chip for the IR receiver other than the one that Dell intended to be there.

---

### Post by twiddler on 2008-02-02
I've used LIRC and it worked for any remote I used on my HTPC. I havn't tried it on my vostro 1500 but if someone does get it to work, let me know :)

---

### Post by Mr. Splitz on 2008-02-13
> **Hexagrapher666 said:**
>  the IR remote is an additional $60, and this $60 may include the chip for the IR receiver, so it is entirely possible that if you did not purchase the Dell Travel Remote with your Vostro that the chip for the IR receiver might not even be there.

$60 is insane for that remote, i ordered mine from dell after the fact and it was only $20.  Their isn't any receiver to install it should be there out of the box.

---

### Post by DamonChyld on 2008-02-13
I posted this (these) questions earlier today on the beginner forums but thought I might have more luck reposting it here. I have been trying to get the integrated mic/webcam working on my Dell Vostro 1500.

On the mic, most of the threads instruct to go into volume controls and change around settings for my 0:HDA Intel (alsa mixer). Under Edit > Preferences I have selected Digital and Digital Input Source, Recording is turned up all the way, and Options > Input Source is Digital Mic 1 but it is still not recording.

It appears that the fix for the webcam might be the quoted post below (our lshw and lsusb info's match), but I am stuck on the load driver > modprobe uvcvideo step (I receive no output, see bottom of post for complete terminal results). How do you do this?



Quote, originally posted by chokas on thread 4204361
My lshw gets the following for the audio device:

 *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel

And lsusb shows the following for my webcam:

Bus 007 Device 003: ID 05a9:2640 OmniVision Technologies, Inc.

At first with a fresh installation of gutsy I didn't get the audio to work, so I had to update the kernel and that did the trick. I posted this in another thread so here's the link..

[http://ubuntuforums.org/showpost.php...9&postcount=37](http://ubuntuforums.org/showpost.php...9&postcount=37)

And I got the webcam to work finally today following this easy steps from the gentoo wiki

[http://gentoo-wiki.com/HARDWARE_Dell_Inspiron_1520](http://gentoo-wiki.com/HARDWARE_Dell_Inspiron_1520)

You have to do the following:

Download svn trunk

svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk

Insert the id product in uvc_driver.c

/* after line 1661 */
/* OmniVision OEM Dell Notebook */
{ .match_flags = USB_DEVICE_ID_MATCH_DEVICE
| USB_DEVICE_ID_MATCH_INT_INFO,
.idVendor = 0x05a9,
.idProduct = 0x2640,
.bInterfaceClass = USB_CLASS_VIDEO,
.bInterfaceSubClass = 1,
.bInterfaceProtocol = 0,
.driver_info = UVC_QUIRK_PROBE_MINMAX },

Compile and install
Code:
make
make install

Load driver
Code:
modprobe uvcvideo

AND NOW TEST IT WITH gstreamer-properties or with amsn, Ready for webcam calls !!

amsn gave me some bugs, and a black image, but I adjusted the settings within a chat window changing my display picture and clicking on "webcam snapshot" , hope this helps.



My Results:

damien@laptop:~/trunk$ sudo make
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
CC [M] /home/damien/trunk/uvc_driver.o
CC [M] /home/damien/trunk/uvc_queue.o
CC [M] /home/damien/trunk/uvc_v4l2.o
CC [M] /home/damien/trunk/uvc_video.o
CC [M] /home/damien/trunk/uvc_ctrl.o
CC [M] /home/damien/trunk/uvc_status.o
CC [M] /home/damien/trunk/uvc_isight.o
LD [M] /home/damien/trunk/uvcvideo.o
Building modules, stage 2.
MODPOST 1 modules
CC /home/damien/trunk/uvcvideo.mod.o
LD [M] /home/damien/trunk/uvcvideo.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'

damien@laptop:~/trunk$ sudo make install
Installing USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
INSTALL /home/damien/trunk/uvcvideo.ko
DEPMOD 2.6.22-14-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
depmod -ae

damien@laptop:~/trunk$ sudo modprobe uvcvideo
damien@laptop:~/trunk$ modprobe uvcvideo

Thanks for any help!

---

### Post by DamonChyld on 2008-02-14
Thought I would post links to the fixes I have found up to now on my Vostro 1500. I am still trying to figure out my camera and mic, but I think those are the last pieces to the puzzle. 

Broadcom 4318 (Dell Wireless 1490)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

NVIDIA 8400M GS
[http://ubuntuforums.org/showthread.php?t=521753](http://ubuntuforums.org/showthread.php?t=521753)
I also had to run sudo dpkg-reconfigure xserver-xorg, a step not mentioned here.

Sound
[http://ubuntuforums.org/showthread.php?t=695140](http://ubuntuforums.org/showthread.php?t=695140)

---

### Post by DamonChyld on 2008-02-14
Ok,  just got my mic working (I have the STAC 9205) by going into applications> sound recorder and changing input to ACDMux. It changed back to InVol after a restart but seems to be stable now... hope this will help someone ;)

---

### Post by Hexagrapher666 on 2008-02-29
> **Mr. Splitz said:**
> i ordered mine from dell after the fact and it was only $20.

Does your Dell Travel Remote work under Ubuntu?

---

### Post by mptpro on 2008-03-01
> **Mr. Splitz said:**
> $60 is insane for that remote, i ordered mine from dell after the fact and it was only $20.  Their isn't any receiver to install it should be there out of the box.

I too have the Dell Vostro and was interested in this remote.  However, when I called Dell they had no idea what I was talking about!  Do you have the model number of this remote and/or a link to Dell's site?

And, does it work under Ubuntu?

thanks.

---

### Post by noobuntu_ger on 2008-06-09
Hi
i put ubuntu 8.04 on my vostro a couple of days ago. Everything works fine. I got the mic to work (i'm so proud of myself) what took me a whole entire day to figure out. The only thing that really bugs me is that ubuntu is so slow !!! I have the feeling it is slower than vista on my vostro !!!. 
It shouldn't be a hardware issue. I have a 2 Ghz processor and 3 gig ram and 8600 gt. 

Has anybody an idea why.

---

### Post by sitric on 2008-06-17
can you please enlighten us how you got the mic to work. thanks.

---

### Post by sixstorm on 2008-07-09
I'm a little disappointed at Ubuntu's performance on my new Vostro 1500:

1.4GHz Core 2 Duo
2GB RAM
NVIDIA 8400M GS
1280x800
120GB HDD

I was going to put Mac OS X and XP on there (:D) but that didn't work out so well due to my wireless card.  Linux works great but it is very laggy, even with the latest NVIDIA drivers.  Heck, even Windows XP Pro boots up and responds faster than Ubuntu!  Never seen that one before.  Is there anything I should know?

---

