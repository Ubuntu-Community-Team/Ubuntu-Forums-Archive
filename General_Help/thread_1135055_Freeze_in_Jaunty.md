---
title: "Freeze in Jaunty"
date: 2009-04-24
forum: General Help
---

### Post by olskar on 2009-04-24
Since installing a clean copy on Jaunty I get random freezes. This is on computers with Nvidia and ATI-cards. It's not a hardwareproblem since Intrepid can run for days without freezing. 

From what I've seen, there is a couple of other people having the same problem?

Anyone know if there is a bugreport on this?

---

### Post by Stenico on 2009-04-24
My experience - 2 hard lock freezes in 20 minutes after upgrading to Jaunty.

Reading people's similar experiences, all I can say is that either Canonical's pre-release testing procedures are a joke, or they simply don't care.

I can't help but contrast this experience with my full-time use of Windows 7 *beta* during which I've experienced one serious crash in 3 months.

I would prefer to be using linux, but I won't be using Jaunty over my Win 7 install in a hurry :-(.

---

### Post by nandemonai on 2009-04-24
Been running since Beta here and I haven't had one lockup at all.

Highest uptime would be around a week before reboot for kernel upgrade or just wanting to give the machine a rest for whatever reason.

Restricted drivers, restricted extras and many additional programs and servers.

Stability will vary I guess depending on your hardware. You realise 1. Jaunty has just been released and 2. It's not a LTS (stable) release right?

Kinda irks me the constant comparisons between Linux and Windows on these forums.

---

### Post by Stenico on 2009-04-24
How many, alpha's, betas and RC's has Jaunty been through? And its still very broken on a lot of hardware.

I know its not an LTS, but that doesn't mean UI hard-freezes are acceptable surely?

How hard is it for Canonical to buy a bunch of commodity hardware and run standard tests before making releases? (I bet Dell/HP etc would donate boxes to them!)

Given my experience with Jaunty and other recent releases there is no way I can recommend Ubuntu as a "just works" distro as I used to do at one time.

---

### Post by nandemonai on 2009-04-24
> **Stenico said:**
> 
How hard is it for Canonical to buy a bunch of commodity hardware and run standard tests before making releases? (I bet Dell/HP etc would donate boxes to them!)

Not really the way it works. Ubuntu is a community driven project, Canonical merely provides support and advertising. You're talking about majority volunteer work here.

That being said things are tested pretty well. I'm curious as to what kind of hardware you're running on?

If it's 'bleeding edge' you can't really expect full support.

Did you participate in the alpha / beta? Submit bugs? Have you checked the HCL?

[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)
[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

---

### Post by Stenico on 2009-04-24
I'm running a three year old Dell dimension 9200 Intel Core 2 Duo machine with a Nvidia 7900GS with no significant hardware changes or additions.

Intrepid, Freebsd, Vista and Win7 all run on this machine without a hitch.

If you read the forums, these freezes are happening to people on different hardware including Intel, ATI and nVidia graphics cards.

Despite the large and admirable community contribution Ubuntu is very much run by Canonical, with the clear aim of becoming profitable. They need to sort their testing infrastructure out if they want to avoid losing community mindshare on the linux desktop, which is ultimately what will drive them to profibility.

---

### Post by nandemonai on 2009-04-24
> **Stenico said:**
> I'm running a three year old Dell dimension 9200 Intel Core 2 Duo machine with a Nvidia 7900GS with no signifcant hardware changes or additions.

Intrepid, Freebsd, Vista and Win7 all run on this machine without a hitch.

If you read the forums, these freezes are happening to people on different hardware including Intel, ATI and nVidia graphics cards.

Despite the large and admirable community contribution Ubuntu is very much run by Canonical, with the clear aim of becoming profitable. They need to sort their testing infrastructure out if they want to avoid losing community mindshare on the linux desktop, which is ultimately what will drive them to profibility.

Granted. Guess I've just been lucky to some extent. I'm certain though many issues will be fixed provided people keep submitting bug reports.

It ain't perfect but for me at least it's been an enjoyable release.

---

### Post by evertmantel on 2009-04-24
Issues like these here as well, but had it already with the beta versions of 9.04. 

When I try to fire up my  NEC LCD22WV as dual screen with the Nvidia-settings manager this happens->>

Using the NVIDIA driver version 180 [recommended] first freezes the system and then auto-reboots the PC.
With version 173 it works well. <<-

As stable version I use 8.04.. (dual booting) on my HP Pavillion dv6000 laptop. No issues there...(but a different nvidia driver there)

---

### Post by codeseer on 2009-04-24
Are those of you who are experiencing freezes using either an Intel video chip  or the new Ext4 file system?

---

### Post by evertmantel on 2009-04-24
Gforce 8400M GS...Ext3

---

### Post by codeseer on 2009-04-24
Reason I asked is because the release notes for Jaunty have freezes/lockups relating to the use of those.

[https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes#Display%20freezes%20with%20Intel%20graphics%20cards]("https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes#Display%20freezes%20with%20Intel%20graphics%20cards")

---

### Post by loneowais on 2009-04-24
I'm experiencing this too.
I installed a fresh jaunty alpha 6 and upgraded through the beta and rc to the Final. But the problem doesn't seem to go aways.

I'm using Dell Inspiron 1525 with an Intel x3100.

Downloading 64bit version now.

---

### Post by Ticketoride on 2009-04-24
> **Stenico said:**
> Reading people's similar experiences, all I can say is that either Canonical's pre-release testing procedures are a joke, or they simply don't care.

I can't help but contrast this experience with my full-time use of Windows 7 *beta* during which I've experienced one serious crash in 3 months.
> **Stenico said:**
> Given my experience with Jaunty and other recent releases there is no way I can recommend Ubuntu as a "just works" distro as I used to do at one time.
That just about sums it up.

> **Stenico said:**
> Intrepid, Freebsd, Vista and Win7 all run on this machine without a hitch.
Win98/2K/XP have been running flawlessly on this Machine for Years.

---

### Post by deathspal on 2009-04-24
I though I was just one of the Unlucky Intel video people (i915) well may be they get it fixed sooner rather than later as I'm ready to go back to Intrepid. (wonders why the regression and realizes that there is a complex relationship between the kernel and the drivers and the UI)

---

### Post by olskar on 2009-04-25
As Stenico says; If you read the forums, these freezes are happening to people on different hardware including Intel, ATI and nVidia graphics cards.

Canonical seems to think that these freezes are related to Intel, that is at least what it looks like by reading bugreports about freezes in Jaunty.

First of all we need a bugreport about a complete freeze happening on different hardware, not just Intel. Is there such a report or shall we create one?

---

### Post by lwpack on 2009-04-25
I'm having the same problems.  I did a clean install of 64-bit Jaunty and it froze up on me every 10 minutes or so.  I thought it might just be the 64-bit version so I installed the 32-bit version.  Same thing.  It freezes every 10 minutes or so.  I have Nvidia GeForce 7300.  I never had any of these issues with Hardy or Intrepid.  I will be reverting back, which is too bad as I'm a big fan of Ubuntu and was looking forward to this release.  Seems weird that this bug wasn't fixed before the final release.  :(

---

### Post by Seks on 2009-04-25
I had lockups all the time in hardy and occasionally in intrepid, but jaunty has been going strong for two days (since I installed it).

---

### Post by lowkey3d on 2009-04-25
Yup same problem with Ubuntu Studio on Pentium D 2.66GHz 1.2Gig of ram, nvidia Geforce 8600 GT. Its a Dell 5150.
Motherboard does have intel chip set...

Don't seem to have a issue in safe mode at the command
prompt. Seems the freeze happens when there is a bit of
network activity usually during a update or web surfing
in X. I don't have issue updating from just recovery command line
mode boot..

I want to try a non RT kernel.

---

### Post by lowkey3d on 2009-04-25
Well I got it to hang in recovery mode. I'm now convinced
this is not Xorg related. But a kernel/network driver issue..

---

### Post by dwasifar on 2009-04-25
This sounds an awful lot like what was happening in Hardy for the first few weeks after release.  I had to drop back to Gutsy for a month or two until the issue was resolved.  I think it eventually turned out to be a kernel issue but for a while people had all sorts of theories about what was causing it - video chipset, Firefox (because Hardy was shipped with Firefox still in beta), a few other guesses.

---

### Post by codeseer on 2009-04-25
Well, I think it'd be worth a try for those experiencing these issues to upgrade to the latest kernel.

---

### Post by codeseer on 2009-04-27
Here's the supposed fix for this mess: [http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582")

If you're running an Intel based video chip, follow it all the way through; if not, then follow the upgrading of the Kernel parts.

---

### Post by Luiggipro on 2009-04-27
I have two pc's :
Amd phenom x3 8450, gigabyte 790gp, 2 HIS radeon hd 4670 in crossfire mode, 4 gb ddr2 1066 memory, running ubuntu 9.04 with ext4 flawlessly.

Intel celeron 2.4ghz , 768 mb ram, nvidia geforce fx 5200 using latest drivers, running xubuntu 9.04 with ext4 amazingly fast.

This issue seems very weird.

---

### Post by jerboyd on 2009-04-27
i've been running ubuntu studio 64 bit since alpha on a spare drive with no problems but since installing the release today i've had five or six freezes. my first installation of the release was on a raid0 ext4 drive. i thought it was an ext4 problem so i reinstalled on raid0 ext3 but the problems still happen. i'm using an hp pavilion dv7 laptop with nvidia geforce 8400 graphics card. i haven't installed the restricted video drivers yet.

maybe this is a raid issue. the ubuntu studio jaunty RC has the same kernel as the official release and i never had a problem with the RC version. the only difference that i can see between the two installations on my machine is that my main OS is run with raid1 /boot raid0 / raid0 swap and raid0 /home

can anyone else confirm freezes with raid drive installs?

jeremy boyd

edit: the freezes seem to mostly happen when i'm connecting to a wireless network or when a package manager is running.

---

### Post by rudyneeser on 2009-04-27
I have a geforce 7300 and jaunty, and I'm also suffering from random freezes. While the machine does eventually die if I leave it doing nothing except running the screen saver, the freezes do seem to happen more frequently if I'm using network related software (firefox, evolution), and even more so if one of the other computer's in my apartment is using the network heavily at the same time :( Anyone else noticing a relation between network access and your machine freezing?

---

### Post by stucky on 2009-04-27
> **jerboyd said:**
> i've been running ubuntu studio 64 bit since alpha on a spare drive with no problems but since installing the release today i've had five or six freezes. my first installation of the release was on a raid0 ext4 drive. i thought it was an ext4 problem so i reinstalled on raid0 ext3 but the problems still happen. i'm using an hp pavilion dv7 laptop with nvidia geforce 8400 graphics card. i haven't installed the restricted video drivers yet.

maybe this is a raid issue. the ubuntu studio jaunty RC has the same kernel as the official release and i never had a problem with the RC version. the only difference that i can see between the two installations on my machine is that my main OS is run with raid1 /boot raid0 / raid0 swap and raid0 /home

can anyone else confirm freezes with raid drive installs?

jeremy boyd

edit: the freezes seem to mostly happen when i'm connecting to a wireless network or when a package manager is running.

werd! That Alphas and Betas all ran fine and only had one small hiccup. Release hits and it seems to go to h-e-double hockeysticks in a handbasket. Really disappointing. 

I am not using raid nor 64 bit, but my experiences seem very similar to yours, except that it's ANY network manager or package management.

---

### Post by jerboyd on 2009-04-27
thought i'd pop my jaunty RC disc back in and re-install that instead of the official release and after installing and updating the system i get freezes while the other installation on a different partition is fine. i can't think of what i've done different :(

jeremy boyd

---

### Post by codeseer on 2009-04-27
Have you guys with the freezes tried the Kernel upgrade yet?

---

### Post by ruru on 2009-04-27
I upgraded an existing install yesterday and had 5 freezes within an hour before I gave up. The same hardware has been running every release since edgy. I was working with GIMP at the time - I haven't had time to test the machine on any other tasks yet. I use nvidia graphics.
What logs should I be looking at to help shed some light on the problem?
 
I had also upgraded my laptop (3rd-gen macbook) which seems to be fine...

---

### Post by stucky on 2009-04-27
> **codeseer said:**
> Have you guys with the freezes tried the Kernel upgrade yet?

Will give it a shot this evening and report back.

---

### Post by lowkey3d on 2009-04-27
> **codeseer said:**
> Here's the supposed fix for this mess: [http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582")

If you're running an Intel based video chip, follow it all the way through; if not, then follow the upgrading of the Kernel parts.

Great I have Jaunty up and running on the provided AMD64 kernel in
the link above. But, the provided kernel is built on gcc 4.2 and 9.04 ships
with gcc 4.3 as a result the Nvidia driver fails to build. I have not tried
to by pass version checking to see if it works..

---

### Post by stucky on 2009-04-27
> **codeseer said:**
> Have you guys with the freezes tried the Kernel upgrade yet?


Shhhhhhhhh! Must be very quiet. It appears to be working. 20 minutes in and not a blip on the radar (knock on wood!) Loaded the new kernel et al. and rebooted. Was able to get in and futz around with network connections and used the different permutations of apt. So far so good. 

It should be pointed out to anyone that wants to try the .30 kernel that the end of the wget and dpkg lines listed in the link have a bit of intel specific stuff. Just be aware that you only need the bit up through the headers. 

I hope this works as the responsiveness right now seems to be even faster than what I was seeing in the beta.

Thanks, Codeseer and psyke83 for this. I owe you a cold frosty beverage of your choice.

---

### Post by jerboyd on 2009-04-27
i am using ubuntu studio. is there a way i can upgrade to a newer rt kernel? the one in the fix is the standard kernel i believe.

jeremy boyd

---

### Post by codeseer on 2009-04-27
> **jerboyd said:**
> i am using ubuntu studio. is there a way i can upgrade to a newer rt kernel? the one in the fix is the standard kernel i believe.

jeremy boyd

Yeah, that one wouldn't have the studio specific optimizations.

---

### Post by Raedwald on 2009-04-28
It doesn't just freeze........

Had a perfectly stable 8.10 installation, no issues at all.

Upgrade to 9.04 and it's been nothing but trouble.....

So far the issues have been:

[LIST]
[*]Regular system freezes (as others have reported)
[*]System powerdown on a fair few occasions
[*]On one occasion a logoff!!!!!
[/LIST]

Hardware is an AMD 6000+ dual core 64bit, 4Gb RAM on an MSI motherboard and an nVidia 9500 graphics card.

I have another system which has run 9.0 from the beginning, with no problems/issues whatsoever.

As the 8.10 install was an upgrade from 8.04, I'm currently trying an upgrade on a clean 8.10. If that fails then the final one will be a clean 9.04 install.

But I shouldn't have to! Surely the upgrade process should work ok......... :confused:

---

### Post by jerboyd on 2009-04-28
if i can't figure out how to install an upgraded ubuntu studio kernel i'm going to reinstall the 9.04 RC and just hold back any kernel upgrades until this blows over. that sounds like the easiest bet for me.

jer boyd

---

### Post by cycle_mycle on 2009-04-28
I'm using both Intel graphics (4500M) and Ext4.

I suspect it's the Ext4 thats causing the freezes because it only happens when I try to delete a large file (like a 700MB .avi) then I get no disk activity what so ever and yet the network is still running whatever it was doing before it froze.

That sound about right? Or am I way off?

I guess I'll reinstall using ext3? Any suggestions?

---

### Post by buchan on 2009-04-28
I can vouch for these problems, My config is as follows:

Amd 3000 64 (installed the x86 version)
1Gb Ram
2x40 GB ATA configured as RAID1 for the / filesystem is EXT4
1 320 GB mounted as /home filesystem is EXT4

I have installed from both the server and alternate versions and had the same problems as noted in most of the posts above.  I also have noticed one other small problem with SABNZBD throwing CRC errors during downloads which do not happen on my older machine running 8.10.  

After reading this thread I'm now leaning towards the EXT4 file system as the issue, I'll try a reinstall tonight using EXT3 and see what happens.  

Has anyone else tried this as a solution?  I have eliminated my hardware somewhat as I've now installed the same OS on two separate MB/Proc combination and seen the same problems.  I would agree with cycle_mycle on the large file activity as that's exactly what I'm doing when I start seeing the system hangs etc.

I'll post back when I've tried EXT3.

---

### Post by MarkusAurelius on 2009-04-28
I would tend to suspect ext4 as well, AND possibly tied to the Intel Video card issue...

Here's my story:

3 machines: Dell D600 ATI card; Dell D410 Intel Card; HP-nc6220 Intel Card.

The D600, with ext4, is working just fine and has never froze on Jaunty.

The HP was next on 9.04.  First install was with ext4.  Froze all the time.  After reading the reported freezes in the forums, I decided to re-install with ext3. The reason I did this is that I did not experienced the performance issues mentionned in the posts regarding the Intel drivers. This is the one I'm on now and it has performed flawlessly so far.

The last one, the Dell D410 having an Intel card as well, I decided to install / on ext3 and /home on ext4.  That one froze after a few hours.

I rebuild the /home partition to ext3 late last night and it is still up and running fine and I'm pushing it a tad more than usual to make it freeze.

Reading and trying to decypher the various notes around the forum, it appears that the freeze does seem to come on when there is a lot of disk activity both network and with external USB drives, at least for me.

Another thing that might also be related to the ext4 and Intel combo, is the suspend/resume is really flaky (???), something that I never experienced previously.

Stay tuned!

Regards.

---

### Post by jerboyd on 2009-04-28
i've tried the installation on ext3 and ext4 with the exact same results.

jeremy boyd

---

### Post by codeseer on 2009-04-28
> **jerboyd said:**
> i've tried the installation on ext3 and ext4 with the exact same results.

jeremy boyd

Thank you.

---

### Post by jerboyd on 2009-04-28
has anyone tried one of the daily cd images for ubuntu or ubuntu studio? i'm donwloading one right now and i'm going to give it a shot. i'll report back after installation.

jeremy boyd

---

### Post by ConstantC on 2009-04-28
Hi all,

here's another freezer:
AMD64 3500, ASUS A8V Deluxe, 3Gb
ATi 9600 256Mb graphic
Cherry Cymotion Linux keyb.; Logitech marble mouse
1x SATA 160Gb Maxtor

Installed Kubuntu 9.04 from CD over U7.04. ext3
Dual booting with XP.
I hardly can tune or change anything; the apparatus freezes if I try to modify something more serious.

System freezes and then the screen goes immediately black. After rebooting the old screen flashes by before Kubuntu comes with a fresh desktop.
Although locking up randomly its usually when performing an action that requires root authorization and/or when more then one program window is open.

Sample freezes:
- Trying to set inbox file in Thunderbird, trying to browse to location /media/DATA/dualboot/thunderbird/etc.  (yes a fat32) tried multiple times with same result.
- Trying to browse /media/DATA partition in Dolphin. Sometimes freezes when just clicking /media/DATA; once after typing root pswrd.
- Got only one freeze with screen on: showed gpg process as 'zombie'.
- Trying to set server in update manager (from The Netherlands to Main) Froze multiple times untill I updated through terminal apt-get.
- Setting desktop image (jpg from media/DATA/).
- Opening Konqueror.
- Selecting/installing additional package with the package manager. 

I ran Ubuntu 7.04 that was solid. 8.04 was a mess (freezes!) and I did not dare to try 8.10.

Greetings, Constant
P.S.1 How can I (try to) see what went wrong (logs?)The screen goes black, you know. I'm a linux-beginner.
P.S.2 Should I try to update the kernel? If yes, what are the lines to type? <NOOB>

*/edit may 1st: The updates I installed from the main server yesterday have -some- effect: at a freeze I keep the frozen screen with a moving pointer. The black screen seems to be gone.*

---

### Post by northwestuntu on 2009-04-28
im also getting some freezing after a new fresh install using ext4.  very random when it happens.  hopefully it will smooth out.

---

### Post by Chafnan on 2009-04-28
I am having this issue as well.  What I really want to know is how to debug this.

---

### Post by olskar on 2009-04-28
> **Chafnan said:**
> I am having this issue as well.  What I really want to know is how to debug this.

Try looking here:
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

Everyone else having freezes might want to take a look over there too.

---

### Post by buchan on 2009-04-28
> **olskar said:**
> Try looking here:
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

Everyone else having freezes might want to take a look over there too.

Thanks for the link Olskar but I'm pretty sure my problem is not related to "X" from what I can tell my hang is system wide.  

When my system stops its the whole thing... all network services seem to stop as well as the display, keyboard Caps etc do not light up, its a complete system hang.

---

### Post by Icm76 on 2009-04-28
**System:**
Asus P5N7A-VM (nvidia 730i/9300) integrated graphics motherboard.
2GB memory
80GB sata disc (EXT3 & ntfs partitions)
160GB sata disc (EXT4 & ntfs partitions)

I am also finding **9.04 (64 bit)** to be *very* unstable, and **8.10 (64 bit)** was very stable on the same machine! Have tried fresh installs of 9.04 with EXT3 & EXT4, and it seemed EXT3 might be more stable, though I now suspect that was just a coincidence with the random freezes occuring in quick succession on my first install with EXT4.

9.04, EXT3 + nvidia 180 driver: graphical corruption occurs and everything freezes. Happening at random times with Firefox, Inkscape, Partition Editor, Image Viewer, browsing files with Nautilus. **Edit:** Opening the 'Power Management' preferences GUI is a 100% guaranteed hang. Sometimes I'm seeing the mouse pointer still active, other times it vanishes.

---

### Post by northwestuntu on 2009-04-28
> **buchan said:**
> Thanks for the link Olskar but I'm pretty sure my problem is not related to "X" from what I can tell my hang is system wide.  

When my system stops its the whole thing... all network services seem to stop as well as the display, keyboard Caps etc do not light up, its a complete system hang.


same here. it's just a complete lockup :confused:

here i was all excited about jaunty.  now i wish i waited a few weeks :)

---

### Post by olskar on 2009-04-28
> **buchan said:**
> Thanks for the link Olskar but I'm pretty sure my problem is not related to "X" from what I can tell my hang is system wide.  

When my system stops its the whole thing... all network services seem to stop as well as the display, keyboard Caps etc do not light up, its a complete system hang.

Sorry to hear that :( This bug is affecting more people than I thought when starting the thread. It's good in a way, that might get attention to this serious bug and perhaps get it fixed.


Anyone know how on earth one should debug such a freeze?

---

### Post by Chafnan on 2009-04-28
> **olskar said:**
> Sorry to hear that :( This bug is affecting more people than I thought when starting the thread. It's good in a way, that might get attention to this serious bug and perhaps get it fixed.


Anyone know how on earth one should debug such a freeze?


My issue is that is is a system wide freeze.  I have carefully watched my log files and nothing is logged as to what is causing it.

---

### Post by jerboyd on 2009-04-28
it is also a system wide freeze for me.

i also experienced a freeze during boot up at the ubuntu studio screen. not sure if it's related.

i can't go 20 minutes without a freeze.

jeremy boyd
hp pavilion dv7 1174ca
ubuntu studio 64 bit

---

### Post by Chafnan on 2009-04-28
I have got my system to stay for 2 days max.  I am about there again and I am hoping that it will not freeze again.

---

### Post by chummychap on 2009-04-28
Can I buy the Toshiba laptop at [www.lavacomp.co.uk]("http://www.lavacomp.co.uk") or who knows where esle I can get them cheaper.

---

### Post by northwestuntu on 2009-04-28
anyone hearing anything yet?

i've had to reset my computer like 20 times now :(

i cant stay on more then 10 minutes now.

---

### Post by MarkusAurelius on 2009-04-28
> **buchan said:**
> Thanks for the link Olskar but I'm pretty sure my problem is not related to "X" from what I can tell my hang is system wide.  

When my system stops its the whole thing... all network services seem to stop as well as the display, keyboard Caps etc do not light up, its a complete system hang.
Ditto for me as well:  complete seizure...  no activity anywhere..

I tried to ssh (yes, I have ssh-server on all machines) into the "frozen" machine from another one, and it just hangs there...

BTW, no more freezes since I rebuild with ext3, and "suspend" flakes have gone away as well...  Touch wood!

Regards.

---

### Post by sidious1741 on 2009-04-28
I'm running with an Intel graphics card.  I remember that one person said that they tried kde and it stopped freezing for them.  I've been using gnome for so long that I decided to try kde but it has frozen too (but only once so far).  While in gnome, it ran fine most of the time but then suddenly, I restarted multiple times and it froze within like less then a minute (I'm surprised I successfully downloaded kde).  I dont know if there's any relation but it seems for me that most of it's freezing happens while I open Preferences>Appearance or while I connect to the internet.

---

### Post by cycle_mycle on 2009-04-28
For what it's worth - my system freezes only when I delete a big file as I stated earlier.

Here's my unit:

Acer Aspire 5335
Intel Celeron 575 2.0 Gig 667 fsb 1MB L2 cache
15.6" HD Acer CineCrystal LCD
Intel 4500M Graphics
4 GB RAM

I'm beginning to think it's semi-unrelated (???). I was waiting for buchan's results but I'm reinstalling with ext3.

---

### Post by northwestuntu on 2009-04-28
well i guess i might try going back to ext3 if i can't fix this.  just doesn't seem like the problem.

---

### Post by cycle_mycle on 2009-04-28
I'm back up with a fresh Jaunty, ext3, and transfering files back to my home dir, surfing the net, doing the update, chatting with Pidgin and configuring stuff.

So far so good, I even think it's faster now, actually I'm sure it is.

Acer Aspire 5335
Intel Celeron 575 2.0 Gig 667 fsb 1MB L2 cache
15.6" HD Acer CineCrystal LCD
Intel 4500M Graphics
4 GB RAM

---

### Post by dwjenkins on 2009-04-28
I have had intermittent freezes with Intrepid and Hoary, mostly if I left a GL screensaver running or if I left any Gecko browser open while the computer was idle. Now with Jaunty I get more regular freezes under the same circumstances. I have recently upgraded the whole system, but to be fair, to get Ubuntu to work at all I had to downgrade back to a Gforce 5200 card from the onboard Gforce card on my new mobo. So I still have the Nvidia issues, I guess. At any rate, it is now happening daily at least if I run any screen saver or leave a browser open, and it simply doesn't happen in my Win 2000 server installation. It also doesn't seem to happen on my laptop with Ubuntu installed. This is common enough hardware, one would think our distro could handle it.??

Don J.

---

### Post by montini on 2009-04-29
I will add my crash report here - it's in another thread, sorry:

[http://ubuntuforums.org/showthread.php?t=1141436](http://ubuntuforums.org/showthread.php?t=1141436)

Maybe someone can comment?

---

### Post by northwestuntu on 2009-04-29
ok after freezing about 30 times i decided to reinstall.  went with the same install.  64bit ext4 ubuntu.  so far so good.  

the only thing different this time.  is i didn't do all the updates right away.  so in my case it was either a bad install or those initial updates from ubuntu made the system freeze and hang.  

well see how stable my system stays now.

---

### Post by Chainz on 2009-04-29
I have same problems.
Have no Intel, no raid, system fully updated, 32bit.

And yes, I also noticed that these problems occur during extensive network load.


Please feel free to submit to my reported bug on Launchpad:
[https://bugs.launchpad.net/ubuntu/+bug/358741]("https://bugs.launchpad.net/ubuntu/+bug/358741")

---

### Post by rudyneeser on 2009-04-29
I have an nvidia graphics card and started having regular freezes when I upgraded to Jaunty. When I downgraded the drivers to the 173 series drivers (they were still available in the Hardware Drivers dialogue) the problem disappeared. My machine has been stable now since Monday morning ;)

---

### Post by rhy7s on 2009-04-29
Same here, Compaq N800c

> **Raedwald said:**
> 
So far the issues have been:

[LIST]
[*]Regular system freezes (as others have reported)
[*]System powerdown on a fair few occasions
[*]On one occasion a logoff!!!!!
[/LIST]


---

### Post by lyn james on 2009-04-29
Hardware is Dell Dimension 521 dual core 4600+ with  Nvidia Geoforce 7300 LE

Upgraded to Jaunty yesterday, and have had 3 hangs since then, (no response to mouse or keyboard) which can only be recovered by a power cycle.The system is therefore unusable. 

Assuming it may stay up long enough, how could I revert back to the Intrepid kernel without having to re-install?

---

### Post by olskar on 2009-04-29
> **lyn james said:**
> Hardware is Dell Dimension 521 dual core 4600+ with  Nvidia Geoforce 7300 LE

Upgraded to Jaunty yesterday, and have had 3 hangs since then, (no response to mouse or keyboard) which can only be recovered by a power cycle.The system is therefore unusable. 

Assuming it may stay up long enough, how could I revert back to the Intrepid kernel without having to re-install?

Look a few pages back in the thread, you can upgrade to an later kernel instead, that seems to stop the freezing

---

### Post by Nicolas19 on 2009-04-29
Same problem for me, however, with a twist. 9.04 worked like a charm since Sunday until today morning, when it froze during system update. Ever since I can't use it for more that 10-20 minutes at a time, as it freezes even during no load (such as Firefox or Evolution only). I can't do anything, no bug report as only the power button helps.
AsusX53sr, 2Gb ram, Core2Duo2GHz, ATI HD2400, ext4.
WinXP works well under heavy load, too.
This is my first ever Ubuntu, and I love it, but seems that I have to wait until this problem gets resolved.

---

### Post by cycle_mycle on 2009-04-29
My last post was six hours ago (when I reinstalled with ext3), I've had no freeze and a lot of network activity (sustained ~200kB/s for some updates while downloading a torrent and surfing the net for an hour or so - peaked at 1861 kB/s)

I finally worked up the nerve to delete a 700 MB file and it didn't freeze (that was the only thing constant as the trigger for a sure freeze)

Acer Aspire 5335
Intel Celeron 575 2.0 Gig 667 fsb 1MB L2 cache
15.6" HD Acer CineCrystal LCD
Intel 4500M Graphics
4 GB RAM (Apacer)
160 GB hdd
Jaunty 9.04 / ext3
8 gig swap

The last remaining annoyance is a screen irregularity that is usually in the exact same spot on the display and might be caused by mplayer. (???)

If I never start mplayer it doesn't seem to ever show up - I am not 100% sure yet.

One more thing - closed the lid, unit went into suspend, let it sit for a while, opened the lid, pressed a key and the unit came out of suspend as it should have - no freeze.

---

### Post by Icm76 on 2009-04-29
> **rudyneeser said:**
> ...I downgraded the drivers to the 173 series drivers...
I also tried this, and I didn't test for long but 173 appeared to be more stable. However a lot of things don't render correctly on my system (730i/9300) Web pages are subject to a lot of corruption e.g. on these forums many lines are drawn twice obscuring the correct text!

I was hoping for someone to suggest a way to install the nvidia 177 driver from 8.10 on 9.04 (64 bit)

---

### Post by buchan on 2009-04-29
Hi All, 

Sorry I didn't reply sooner, I did another (something like my 20th) reinstall last night on my test system using ext3 instead of 4.  

My main purpose for this system was to download large files using sabnzbd and with the EXT4 filesystem I was having not only the freezing issues but the sabnzb application was giving CRC errors while downloading files that when downloaded on a known working system were fine.  

Since the change to EXT3 with the new install I have not seen any system hangs and I have downloaded over 20 GB of files without seeing a single CRC error in sabnzb.

The ONLY change I made to this system from previous installs was the filesystem used.  I have been very careful the last few installs to be sure that I am not changing my installation methods so that I can be at least a little more sure of what changes are making a difference.  

Looks to me like EXT4 is the issue.  We're going to have to wait a little while more until support for EXT4 is a bit more stable I think.

As another side note, I have also upgraded several servers at work to 9.04 but of course because these servers are upgrades I left the EXT3 filesystems in place and they have not seen any of the issues I've been seeing with my own fresh installs on EXT4.

---

### Post by Chainz on 2009-04-29
Ext4 is not a problem on my side.
I always used ext3 for all installs and still get freezes.

---

### Post by northwestuntu on 2009-04-29
update.  

reinstall did not work :(  trying some new things now.  1st is to disable all nvidia drivers.  

update

well my computer froze twice while trying to finish this message.  anyway removing nvidia driver didn't seem to work.

running out of options here.

does anyone suggest a kernel upgrade?

---

### Post by olskar on 2009-04-29
> **northwestuntu said:**
> update.  

reinstall did not work :(  trying some new things now.  1st is to disable all nvidia drivers.  

update

well my computer froze twice while trying to finish this message.  anyway removing nvidia driver didn't seem to work.

running out of options here.

does anyone suggest a kernel upgrade?

Yes, a kernelupgrade could help.

So far we get freezes regardless of filesystem, videocard and networkcard.

---

### Post by cucsd1981 on 2009-04-30
I too, unfortunately, experience the occasional freeze. After reading this thread I have reason to suspect mine is somewhat different. 

My computer only seems to freeze after it has sat idle for a long time (no screen saver, or desktop effects) or after a long suspend. If the idle or suspend is short, no problem. 

Has anyone experienced this? I have tried going back to the nvidia 173 drivers (as suggested here) before trying a kernel update (I think I can wait it out). 

I seem to be able to use it for hours without problems; so for me it seems to be more of an annoyance than anything else. For those, that freeze every 10-20 mins, I empathise.

---

### Post by cycle_mycle on 2009-04-30
I am not sure if this will help any one, I was always experiencing freezing and I thought it was either my Intel graphics or ext4 file system. Even though I reinstalled in ext3 and never once froze my machine again (it was freezing when large files were deleted). I still had an annoying irregularity on my display like a thin long rectangular space trying to display a different part of the desktop. It was 1/3 the way down from the top and off to the left side of the middle. 

The only thing that seemed to make it appear was starting mplayer. It went away and hasn't been back since I disabled compiz so I just removed it all together.

I'm not saying disabling or removing compiz is the answer to freezing but just suggesting a path to look at for debugging and resolving the issue.

Right now I am extremely happy with jaunty and am getting all sorts of work done, it still looks beautimous and is rather speedy in operation. Very delightful indeed.

Acer Aspire 5335
Intel Celeron 575 2.0 Gig 667 fsb 1MB L2 cache
15.6" HD Acer CineCrystal LCD (16:9)
Intel 4500M Graphics
4 GB RAM (Apacer)
160 GB hdd
Jaunty 9.04 / ext3
8 gig swap

---

### Post by Chafnan on 2009-04-30
I reinstalled with ext3 this time, and the computer froze after 3 minutes.  I cannot afford to have my computer freeze, so I am going back to Intrepid.

Has anyone opened a bug an launchpad about this?

---

### Post by Chainz on 2009-04-30
> **Chafnan said:**
> Has anyone opened a bug an launchpad about this?
Yes, please feel free to submit to my reported bug on Launchpad:
[https://bugs.launchpad.net/ubuntu/+bug/358741](https://bugs.launchpad.net/ubuntu/+bug/358741)

---

### Post by pikpolly on 2009-04-30
Not sure if mine's the same problem but my computer keeps freezing about 2 or 3 minutes after login and it won't unfreeze after that (I got the impression that some people's computers resumed their normality after freezing but correct me if I am wrong!).

---

### Post by codeseer on 2009-04-30
> **pikpolly said:**
> Not sure if mine's the same problem but my computer keeps freezing about 2 or 3 minutes after login and it won't unfreeze after that (I got the impression that some people's computers resumed their normality after freezing but correct me if I am wrong!).

```
lspci | grep VGA
```

---

### Post by olskar on 2009-04-30
> **pikpolly said:**
> Not sure if mine's the same problem but my computer keeps freezing about 2 or 3 minutes after login and it won't unfreeze after that (I got the impression that some people's computers resumed their normality after freezing but correct me if I am wrong!).

My computer does not resume after freezing

---

### Post by drbcladd on 2009-04-30
> **cucsd1981 said:**
> 
My computer only seems to freeze after it has sat idle for a long time (no screen saver, or desktop effects) or after a long suspend. If the idle or suspend is short, no problem. 


I see the same thing here. Suspend over night and wake up to reboot machine. Has happened several times on longer suspends. I haven't had the idle lock up.

Have also seen 30-60 second lock ups when doing network I/O (I am pretty sure it is hitting the wire which causes the hiccup). Nothing moves, screen darkens, then the planets come back into alignment. 

I just report what I am seeing (with most current NVidia drivers on a 7900GT) in the hopes that commonalities become apparent. 

Good luck to all with serious locking up issues.

---

### Post by Prominence on 2009-04-30
My computer has been randomly locking up as well, is there any clue as to why it may be doing this??

---

### Post by Polygon on 2009-04-30
hi, i am having the same problem, and as there is no mention of the problem whatsoever in the logs after my computer logs up, i submitted a bug report

but since none of us have any information on what exactly is going on, they may be for different reasons

but you might want to add something useful and or subscribe to this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155)

---

### Post by codeseer on 2009-04-30
> **Prominence said:**
> My computer has been randomly locking up as well, is there any clue as to why it may be doing this??

```
lspci | grep VGA
```

---

### Post by Bulova on 2009-04-30
My computer also freezes up randomly. The mouse cursor works but nothing else. No pattern I can discern.

Jaunty seems fast and I like it------ not counting that locking up and losing all my work thing.

---

### Post by olskar on 2009-04-30
> **codeseer said:**
> ```
lspci | grep VGA
```

I can give you mine, however as we have already seen this issue is found on a lot of computers regardless of card

02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

---

### Post by codeseer on 2009-04-30
> **olskar said:**
> I can give you mine, however as we have already seen this issue is found on a lot of computers regardless of card

02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

I think it's several issues. I'd say try upgrading the Kernel only in your case.

I'm not seeing these freezing issues in my VirtualBox installs though. Not yet, at least. I think I may throw a real install on this system in the next couple of days and see if I get them.

---

### Post by Ronin_301 on 2009-05-01
> **cucsd1981 said:**
> I too, unfortunately, experience the occasional freeze. After reading this thread I have reason to suspect mine is somewhat different. 

My computer only seems to freeze after it has sat idle for a long time (no screen saver, or desktop effects) or after a long suspend. If the idle or suspend is short, no problem. 

Has anyone experienced this? I have tried going back to the nvidia 173 drivers (as suggested here) before trying a kernel update (I think I can wait it out). 

I seem to be able to use it for hours without problems; so for me it seems to be more of an annoyance than anything else. For those, that freeze every 10-20 mins, I empathise.

I've been having a similar problem with Jaunty on my desktop. It works fine on my laptop (Inspiron 1525), but on my desktop it'll freeze if it sits idle for awhile (don't know how long exactly, usually if it's left overnight or while I'm at work all day). Never seems to happen while I'm actually working on it, though. And that's with the Ext3 filesystem, and a Radeon 9200 Pro.

---

### Post by night-wing on 2009-05-01
I have the same freezes on an intel core duo, ati x1250.

Intrepid worked flawlessly. But I do not believe, it's the kernel, because: In intrepid I installed the same kernel (2.6.28-11) from jaunty repos the last weeks and had no freeze at all.

---

### Post by northwestuntu on 2009-05-01
> **night-wing said:**
> I have the same freezes on an intel core duo, ati x1250.

Intrepid worked flawlessly. But I do not believe, it's the kernel, because: In intrepid I installed the same kernel (2.6.28-11) from jaunty repos the last weeks and had no freeze at all.

that's weird because i reinstalled ipex and after i updated the latest kernel is when i started getting freezing again.

i think it somehow relates to the video driver?

when disable the ubuntu nvidia driver no freezing?

---

### Post by zugol on 2009-05-01
Nvidia GeForce 8500Gt / Ext4

tried driver 180.22 => Freeze
tried driver 180.53 (packages found here [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates"))=> Freeze
tried no Compiz => Freeze
tried to do nothing => Freeze
tried to turn off my computer => Freeze during the turne off process !!!

for the moment I try 173.14, but no VDPAU...

---

### Post by DeMus on 2009-05-01
> **olskar said:**
> Since installing a clean copy on Jaunty I get random freezes. This is on computers with Nvidia and ATI-cards. It's not a hardwareproblem since Intrepid can run for days without freezing. 

From what I've seen, there is a couple of other people having the same problem?

Anyone know if there is a bugreport on this?

I use Jaunty 24/7 since installation and no problems at all. Not one time did I get a frozen computer. I did do a clean install, maybe that works better than an upgrade, maybe it's just the same. It's just I don't like upgrades because I think much of the old system is staying on the disk while with a fresh install all is clean.

---

### Post by Nicolas19 on 2009-05-01
Well, I did a clean install of Jaunty onto ext3 filesystem, just to give it a try. I did not update it with anything (only java), neither the system, nor firefox, nor ATI drivers. It's on for 16h 28min (according to gkrellm), so far so good. Did heavy network traffic, moving, deleting large files, left it idle for hours. It's working for me now, and won't update till this thread gets flooded with "freezing is gone" replies;)

---

### Post by steve. on 2009-05-01
One of my boxes freezes if left idle causing downloads and cd burns to fail.
It only happens if I boot into Jaunty, Intrepid is fine.
The screen is still on and it wakes up after moving the mouse then shows the download or CD burn has failed but otherwise seems OK.
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

---

### Post by DeMus on 2009-05-01
> **steve. said:**
> One of my boxes freezes if left idle causing downloads and cd burns to fail.
It only happens if I boot into Jaunty, Intrepid is fine.
The screen is still on and it wakes up after moving the mouse then shows the download or CD burn has failed but otherwise seems OK.
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

This looks like something powermanager is doing. Try to change actions which are taken after so many minutes of being idle. Maybe this helps.

---

### Post by steve. on 2009-05-01
> **DeMus said:**
> This looks like something powermanager is doing. Try to change actions which are taken after so many minutes of being idle. Maybe this helps.

I had them set to "never" but it didn't make any difference.

It seems to be something new in Jaunty that doesn't like this hardware :(

---

### Post by guayusa on 2009-05-01
Same problem here.

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

EXT4 / i386

[RIGHT]
:([/RIGHT]

---

### Post by dlopez on 2009-05-01
The same here!!!
Random freezes for Ubuntu 9.04 64 bits.  Sometimes after 23 hours on, sometimes in the boot.  Sometimes selecting text on the web, sometimes watching a video...  I can not find any regular behaivor.

I have been using Ubuntu since 6.10 and this is the first time something like this happens to me.

Mi logs don't show anything strange (syslog, messages, xorg.log, ...).
For example:

1rst freeze today (8:28 am):
May  1 07:40:01 borriquito /USR/SBIN/CRON[7110]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May  1 08:28:05 borriquito syslogd 1.5.0#5ubuntu3: restart.

2nd freeze today (9:15 am):
May  1 09:15:59 borriquito pulseaudio[4648]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
May  1 09:24:59 borriquito syslogd 1.5.0#5ubuntu3: restart.

As you see, diferent messages without any relation.  The same messages appear in logs sometimes without causing freezing.

I think it is a SERIOUS BUG!!

My hardware: Asus P5Q3 / 4 GB DDR3 RAM / Intel E8400 / GeForce 7300 GS

Any any suggestions / solutions????

---

### Post by bearozo on 2009-05-01
Same here random freezes, ext 3  Geforce 7300,  Amd 4400+ X2, mostly in FF but once in thunderbird, at first I thought it was a flash issue as it happed while watching Youtube
but when it happend just surfing FB and watching pics in albums,  it does seem to be only when there is a network activity and mostly while watching youtube so maybe a sound problem with pulse ? a friend suggested reinstalling ALSA but since I am such a noob and reading this thread I will wait as there is so many sugestions (getting RC2 kernel, using the intelfix etc.) I do not have as many freezez as some report I can use most things like replying to this thread etc. but netactivity + sound or video often freezes.
Hope someone figures it out zoon though.

Now it frooze just scrolling this page to see if someone posted since I did (no video or sound)

---

### Post by pikpolly on 2009-05-01
> **codeseer said:**
> ```
lspci | grep VGA
```

```
02:00.0 VGA compatible controller: Nvidia corporation G72 [GeForce 7300 SE] (reva1)
```

---

### Post by sealview on 2009-05-01
Hi guys,

I have an HP Compaq 6820s. I have been running every release since Gutsy Gibbon till Intrepid Ibex. I've tried to install Jaunty on ext4 as it comes after some work in GIMP the system freeze out for 5-10 seconds. this didn't happened in the older release, no sir! I thought is because of the ATI driver and I've installed the ATI driver X.Org from the Add/Remove... and after my restart I couldn't get into the desktop any more.
What it seams to be my problem, or how can I remove that ATI driver.
I'm in the process of saving my data from Jaunty and probably waiting till the bugs disappear in this release.

I'm really sorry to say this, but this is the worst release since 5.04 Desktop, actually Intrepid amazed me much, not a thing for Jaunty.
I don't like what I'm saying!

---

### Post by olskar on 2009-05-01
> **sealview said:**
> 
I'm in the process of saving my data from Jaunty and probably waiting till the bugs disappear in this release.

I'm really sorry to say this, but this is the worst release since 5.04 

I agree, I moved to Intrepid a while ago. Really hope the bugs get some attention soon.

This important and serious bug has not yet been given an importancelevel after nearly a month. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155)

---

### Post by buchan on 2009-05-01
Well, I was watching this thread very closely but over the past couple of days I've pretty much tried everything to stablize my 9.04 install.  I have installed from scratch at least 10 times and while I think EXT4 has something to do with the error its not the only problem.  

Once I removed EXT4 from the equation, my system stopped hanging but I am still seeing random CRC errors when downloading large files with SABNZBD.  I have tried downloading the same large files on my 8.10 install with no errors which verifies that this is a problem with 9.04.  

I will be reluctantly downgrading my system to 8.10, I wish I could stay with 9.04 but if its not stable I may as well be using M$.  I have been using 8.10 as my desktop for some time now and I have had almost no issues at all... I guess I should just stick with what I know works.

My system config is as follows in case anyone is seeing similar problems:

Ubuntu 9.04 Alternate x86
AMD 3000 64Bit
1GB DDR
2x 40 GB seagate IDE configed in raid1 mounted as /
1x320 GB Seagate mountest as /home
Gigabyte GA-K8VM800M MB
Integrated UniChromeTM2 Graphics (no idea what driver, it's mostly going to run headless anyways)

---

### Post by northwestuntu on 2009-05-01
i think i have done 20 fresh installs now of 9.04. i finally gave up :(

back to 8.10 now.


i've never seen so many complete freezes of the system before in my life.

---

### Post by J3anyus on 2009-05-02
I'm not sure if the issues I'm having are the same as what everyone else is seeing, but I figure it's worth mentioning.  I had a 32-bit Intrepid installation that was rock solid, and upgraded to Jaunty on release day.  I had a ton of different problems, including occasional freezes, and figured I'd go ahead and try a clean install.  When I did this I moved to 64-bit Jaunty, since I no longer have any reason to run a 32-bit OS.

While the clean install fixed the majority of my problems, the freezing has remained.  I'm using ext3 and have ATI graphics (integrated Radeon HD 3200 on my AMD 780G-based motherboard).  My freezes are weird though - the machine only partially locks up.  I can still move the mouse cursor, and sometimes I can even interact with window decorations, but I can't do anything in any other processes I have running (Firefox, Audacious, anything else).  I've noticed that when I'm listening to music in Audacious and one of these freezes comes on, Audacious stops outputting sound about 5-10 seconds before the rest of the system becomes unresponsive.  I've also noticed that if I wait long enough (sometimes 3 minutes, sometimes 30 minutes), the system will come back and be totally normal until the next freeze.  During this time when it's frozen though, I can't drop to a terminal with Ctrl-Alt-F(1-6) or do anything else.  I can ping my frozen machine from another computer and even SSH into it, but once I'm SSH'd in, I can't run any commands.  For example, trying to run top just does nothing - I type top, hit enter, and then top doesn't come up until after the machine is done being frozen.

I've checked dmesg and /var/log/syslog and neither of them are showing anything out of the ordinary.  These freezes are happening once every hour or two, and it's getting very frustrating trying to use my machine.  Any ideas where I should go from here?

---

### Post by Nicolas19 on 2009-05-02
Maybe this will help.

As I've said, I've done a clean install to ext3, and didn't have a freeze for a day. Didn't update anything. Finally, today I installed the "closed" FGLRX ATI driver for my HD2400, and restarted the machine. After 1 hours of gaming, etc, the freeze reappeared.
I had gkrellm on, so, when it froze, I noticed the following:
1. I had only Firefox and gkrelln running, Firefox loading a page (from WineHQ)
2. My first core went on 100% (don't know why, I couldn't open system viewer), but the second core was on 0% (Intel Core 2 Duo). CPU temp was between 65-70C, normally it's 45-50.
3. The screen didn't stop responding, gkrell updated, however, all inputs were broken, so the windows. Mouse moved, but didn't seem to notice where (the buttons didn't highlight)
4. altgr+printscr+reisub restarted the machine. No ctrl+alt+backspace, nor ctrl+alt+del worked.

---

### Post by g-raf on 2009-05-02
I upgraded my Ubuntu Studio to the 9.04 Jaunty Jackalope and now everything runs slower and freezes occasionally (when i try to open programs such as open office or audacity). 

I'm using ATI/AMD propriety FGLRX graphics driver. 

I'm not very educated in computer technologies. If anyone has an idea about what can solve this problem, please let me know. I'm having a difficult time using the computer. My e-mail is [email]giraffe@riseup.net[/email]
Thanks

---

### Post by Daoro on 2009-05-02
I've 2 friends having the freeze issue. Configuration varies from ATI to nVidia graphic cards (both about 1 y.o.) and using Core2 proc. One have Compiz running, the other doesn't. Both are updated systems from 8.10, using ext3.

Both are experiencing "deep" freeses : display, input, sound... only way to get out is to do a hard reboot.

They happen soon after the system has booted (like 5min), or way later (like 4-5 hours), under many different conditions (working, surfing the web, listening to music, etc..).

I can't see a common action that triggered the freeze, so I'm guessing it'll be kinda hard to find out what the problem is :sad:

---

### Post by olskar on 2009-05-02
> **Daoro said:**
> 

I can't see a common action that triggered the freeze, so I'm guessing it'll be kinda hard to find out what the problem is :sad:

I'm afraid so :( So far we have seen crashes appear regardless of filesystem, processor, videocard and compiz

Perhaps it's time to make some kind of warning in the releasenotes? So far the warning is only for Intel but as we have seen a lot of other people is getting crashes

Edit: Filed a bug about the releasenotes, please confirm
[https://bugs.launchpad.net/ubuntu/+bug/370794](https://bugs.launchpad.net/ubuntu/+bug/370794)

---

### Post by squee on 2009-05-02
I get irregular log offs. The writing on the screen isnt there long enough for me to see it. Where are the logs for that? Might help the issue some what.

Machine is in sig.

---

### Post by bearozo on 2009-05-02
My freezes still happen occasionly and I cannot pinpoint why, it happens when FF is running
but not otherwise (well once in thunderbird) mostly happens when watching youtube but also in regular browsing while scrolling but trying to force a freeze doing the same thing as when freeze happened I cannot get it to freeze, it freezes randomly but it seems to be only when browsing though it is frustrting to not be able to pinpoint exactly what triggers the freezes. I can leave puter on for hours with just transmission running and no freezes or even over night but when browsing it can happen all of the sudden, so FF or network activity seems to be involved in the problem at first I thougt it was audio related and disabled pulse session and reinstalled ALSA which seemed to solve the problem but it didn't
well it does not happen as often as before though I also tried IRQ poll at start but it does not seem to do any difference.

I sure hope this will be solved soon because Jaunty is good otherwise.

---

### Post by Quinn The Eskimo on 2009-05-02
i froze up 3 times reading this thread praying a solution is posted in it
i only made it to page 3
if there is a solution to this bug and someone can PM it to me i would very much appreciate it

i've been using ubuntu exclusively since feisty and have had many minor issues along the way that i quickly found solutions for and it was rarely more than a line or two of code i had to copy/paste into the terminal, but this issue is pretty serious and in my search i have found several complaints and no solution
i'm actually shocked i was able to type this all without another freeze
my pc is my sole source of home entertainment and i can't continue to hard boot every 10-20 minutes

---

### Post by linuxkrn on 2009-05-02
I had the same problem with lockups.

I did everything that other have done, ext4->3, tried all the kernel options noapic/etc.

What SEEMS to have worked is installing the backport-modules for jaunty.  From my testing, it always happened during wireless network traffic.  Mostly in firefox on youtube or in on-line games or system updates.  I have the Intel 4965 wireless and someone in chat suggested that a 8.10 bug (which I didn't seem to have) could be a problem.  Sure enough, after installing modules I've been able to run for hour + without lockups.  

Note, I'm afraid to try the other bug which caused instant locks. 'strace gedit' :o

I'm just happy that I can surf for more then 5 mins now.

---

### Post by stepanstas on 2009-05-02
Same issue here.  Had no problems with previous version.  CPU is showing 100% (both CPUs).  If i leave the computer for a few hours it will get stuck.  Will take maybe 5-10 min to do CTRL ALT F1 (no hope to get back to graphic) and then log in, reboot.  Gets annoying.

Also using Skype which I didn't have problems with before.  Now the person gets a lag with a few sec on the other end.  Something is slowing down machines.

Ubuntu 9.04
Memory: 1001.5 MiB
Processor 0: Intel(R) Pentium(R) D CPU 3.00GHz
Processor 1: same as above ^
Available disk space: 50.9 GiB
CPU1: 97-100%     CPU2: 100%
Memory: 52.9%

---

### Post by /\\/_\\/\\/ on 2009-05-03
Getting on the "me too" train on this one - went from 8.10 to 9.04 today and started experiencing those strange "everything but the mouse" hangs every 10 minutes or so with no rhyme or reason and nothing seems to go into the logs.

I haven't the slightest clue what's happened, I didn't have a single problem with 8.10 release-to-date.

System (old one):
9.04, with 2.6.28-11 kernel, using ext3 & everything up to date
AMD Athlon XP 2600+
1.2GB RAM 
ATI Radeon 9200, using compiz (worked since it was Beryl)
Dual-booting XP which still works fine, fsck-ed, memtest-ed and xfix-ed without problems - fairly sure it isn't the hardware.

---

### Post by Filian on 2009-05-03
My housemate has the same problem. He's an Ubuntu newbie so he's getting a very bad impression of the linux world.

The system usually takes from 10 to 30 minutes to freeze, it depends on wich apps are running. But it hangs in no more than **3 minutes** if he runs **xmame**.

He has an AMD processor + nVidia chipset.

But Jaunty runs smoothly on my HP Pavillion dv5, it has never frozen :confused:

---

### Post by pikpolly on 2009-05-03
> **Filian said:**
> My housemate has the same problem. He's an Ubuntu newbie so he's getting a very bad impression of the linux world.

The system usually takes from 10 to 30 minutes to freeze, it depends on wich apps are running. But it hangs in no more than **3 minutes** if he runs **xmame**.

He has an AMD processor + nVidia chipset.

But Jaunty runs smoothly on my HP Pavillion dv5, it has never frozen :confused:

What's **xmame**?

---

### Post by olskar on 2009-05-03
> **pikpolly said:**
> What's **xmame**?

Multiple Arcade Machine Emulator :)

---

### Post by moodog on 2009-05-03
Same problems here. Running Ubuntu 9.04 AMD_64 on an Asus G1 - Geforce Go 7700, ext4 on root, ext3 on /home. I thought it was happening only when I started up Virtualbox (running 32bit Vista), as the last log message before crash was often something to do with Virtualbox using 32 bit code, but then it happened randomly. Also seems to happen when I was doing something with a window (resizing, moving etc.), so thought it might be compiz, but disabled and it still locked up. Sometimes I can use Ctrl-Alt-Shift-SysRq, R-E-I-S-U-B to reboot, but sometimes it doesn't respond to this and I have to power off and back on. Is very annoying, cos when I restart I have to boot back in, start Virtualbox, boot into Vista... it's made a bit better by Jaunty booting so fast, but would be better if it didn't happen. As others have said, I haven't been able to find anything in the logs about what's going on.

---

### Post by Nicolas19 on 2009-05-03
Freeze again, this time a bit different. Had gkrellm on, so hope this helps.
- Both cores 0% (what suprised me, as usually one of both go at 100% during a freeze)
- CPU tmep 47C
- Running programs: gkrellm, Firefox (loading a page), Transmission (not downloading, and upload stopped with the freezeing... strange)
- Mouse moves, but can't click, keyboard doesn't work, but screen updates.
- After RESUB, Ubuntu couldn't boot, had a black sreen with two grey lines (top and bottom), mouse moves, but nothing helps for minutes, RESUB again.
Now here I am. Will inclue sys specs in sig if Ubuntu lasts... Are there any kernel updates that fix this problem?

---

### Post by olskar on 2009-05-03
Have all of you filed bugreports? For some reason they say they want a different bugreport for each freeze so I guess there will be about >100 bugreports :confused:

---

### Post by bearozo on 2009-05-03
Pardon a noob but what is RESUB or R-E-I-S-U-B  ?

---

### Post by olskar on 2009-05-03
> **bearozo said:**
> Pardon a noob but what is RESUB or R-E-I-S-U-B  ?

It's a combination you use to umount your drive and reboot kind of.

Press Alt+SysRq and the letters one at a time

---

### Post by norcim on 2009-05-03
There seems to be a GUI related bug because working in the terminal does not produce a freeze.

---

### Post by petrakito on 2009-05-03
My Ubuntu 9.04 desktop (32-bit, i686) is also freezing randomly during the last 5 days. Here's my spec:

Asus P4C800 deluxe mobo
Intel Pentium 4 w/HT 2.8GHz
GeForce 6600GT 128MB AGP 8X, using the NVIDIA driver ver. 180 [recommended] 
1GB ram
80GB IDE hdd

the machine is old and weak, but I am not stressing it at all, actually most of the freezes happen without any activity on my behalf.
After freeze, the screen image is preserved, but no mouse/keyboard is working.
The LAN LED flashes (!) when I ping the machine from another computer, but it does not reply to the ping (the ping reports "destination host unreachable"). Also, ssh does not connect.

Only hard reset works. :confused:

It's not a temperature overheating, I checked. 
It's not the RAM either, ran memtest for long time, no problem with it. 
Checked the syslog - nothing interesting, only update-motd immediately before the crashes, but it's running every 10 minutes anyway, so it's not a suspect.

Any advice appreciated! :(
(Is Ubuntu 9.04 server crash-free?)

---

### Post by Daoro on 2009-05-03
Still probing but it may be a problem with some WLAN driver.
Are all of you using Wifi ?

---

### Post by bearozo on 2009-05-03
> **olskar said:**
> It's a combination you use to umount your drive and reboot kind of.

Press Alt+SysRq and the letters one at a time


Thanx one learn something new every day :)

---

### Post by bearozo on 2009-05-03
> **Daoro said:**
> Still probing but it may be a problem with some WLAN driver.
Are all of you using Wifi ?

Not me, just a wired.

---

### Post by moodog on 2009-05-03
> **bearozo said:**
> Pardon a noob but what is RESUB or R-E-I-S-U-B  ?

You can read about it here:

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

It's a safer way to reset your computer when it's not responding (to a certain degree), than holding down the power button for 5 seconds. 

it kills all processes, syncs disks, unmounts file systems then reboots (plus a couple of other letters obviously).

As mentioned in my original post though, I'm finding two levels of crash - one where this key sequence works, and one where it doesn't. In all cases though, my mouse keeps working, but the whole screen freezes otherwise.

---

### Post by bearozo on 2009-05-03
Bookmarked, Thanx

btw. my mouse stops working at freezes and I think my keyboard stops working as well
but I will try reisub next time and see if it responds.

> **moodog said:**
> You can read about it here:

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

It's a safer way to reset your computer when it's not responding (to a certain degree), than holding down the power button for 5 seconds. 

it kills all processes, syncs disks, unmounts file systems then reboots (plus a couple of other letters obviously).

As mentioned in my original post though, I'm finding two levels of crash - one where this key sequence works, and one where it doesn't. In all cases though, my mouse keeps working, but the whole screen freezes otherwise.

---

### Post by moodog on 2009-05-04
> **bearozo said:**
>  I think my keyboard stops working as well
but I will try reisub next time and see if it responds.

My keyboard stops working from the point of view of the applications on screen, and Alt-F[1-6] doesn't work to switch to console, but the magic keys still work (most of the time).

I think wikipedia mentions this, but some of the steps can take a little while (i.e. seconds), so it's worth leaving a second or two between each key stroke. You should also notice some disk activity when you press some of them.

---

### Post by Allegretto on 2009-05-04
Glad it's not just me who's having this problem then. I'm also getting random freezes, although the system does carry on working 'normally', just really, really slowly. My second core goes up to 100% usage despite the system monitor reporting nothing using the CPU in the processes section.

My specs:

Ubuntu 9.04 x64
AMD Phenom II X3 @ 3.1ghz
4GB Corsair DDR3 RAM
ATI Radeon HD 4870 using proprietary driver
Gigabyte GA-MA790XT-UD4P motherboard

I dual-boot Windows 7 on the same system and haven't had any problems there, so I can't imagine it's a hardware fault.

---

### Post by bearozo on 2009-05-04
Mine freezes as soon as I click a tab or scroll a page in FF if I haven't used it for 7-8 hours (over night) (except for letting deluge run over night) but then it can be fine most of the day and if it freezes it is while scrolling fast (last time scrolling fast in about:config) or watching youtube first the sound stutters and when it freezes.
Can it be a memory management problem ?

---

### Post by madomac on 2009-05-04
I was able to isolate the wireless connection as the root cause for my freezes.

I am using Jaunty 64bit on a Dell Inspiron 1545. System works nice for a while (up to two days in the beginning), then suddenly freezes when there is traffic via wlan0. R-E-I-S-U-B will not help. System is totally frozen (i.e. clock not ticking anymore, cannot move mouse pointer etc.). After resterting via power-off/power-on the system will work a couple of miutes and freeze again. Only solution found at the moment: Reboot to Windows Vista, reboot to Ubuntu again. Works...until the next freeze occurs.

I will try to gather additional information before I open a bug.

I have two questions: What tool will give me a complete overview of the hardware installed? I remember there was a tool to do this, but do not know if it was on Fedora or Intrepid or...?! And how can I try to use a different driver for the wireless device (should be an Intel 5100)?

Thanks,
Marc

---

### Post by delSys on 2009-05-04
Hey guys,

yes, i also have problems with random freezes of KDE. ;)

I dont read that anyone here can reproduce this kind of crash, is this correct? (I skipped some sites, please don't beat me. :))
Because i can. I just need to start Kopete, try to talk to an G-Talk Buddy and it's over.
The message window/tab opens, but its empty - realy empty, there is nothing inside, i only can see the window decoration.
ICQ and MSN works fine, just G-Talk causes the crash.

With Pidgin there are no problems.

I read some people here are thinking that wifi could be the reason?
I realy don't know, i just can say: For me, wifi works without any problems.

It's unbelievable, a ton of symptoms why KDE4 could crash..

Im running the following system, no idea if this is important:
Amilo Pi 1536
- CPU: Core Duo T2300
- Graphic: ATI Mobility Radeon X1400 (M54)
- Mainboard: Intel i945PM
- Wifi: Intel Pro/Wireless 3945ABG

---

### Post by bearozo on 2009-05-04
hardinfo (in synaptics)  > **madomac said:**
> I was able to isolate the wireless connection as the root cause for my freezes.

I am using Jaunty 64bit on a Dell Inspiron 1545. System works nice for a while (up to two days in the beginning), then suddenly freezes when there is traffic via wlan0. R-E-I-S-U-B will not help. System is totally frozen (i.e. clock not ticking anymore, cannot move mouse pointer etc.). After resterting via power-off/power-on the system will work a couple of miutes and freeze again. Only solution found at the moment: Reboot to Windows Vista, reboot to Ubuntu again. Works...until the next freeze occurs.

I will try to gather additional information before I open a bug.

I have two questions: What tool will give me a complete overview of the hardware installed? I remember there was a tool to do this, but do not know if it was on Fedora or Intrepid or...?! And how can I try to use a different driver for the wireless device (should be an Intel 5100)?

Thanks,
Marc

---

### Post by madomac on 2009-05-04
> **bearozo said:**
> hardinfo (in synaptics)

Thanks! That's what I was looking for.

---

### Post by dndzz on 2009-05-04
Had jaunty freezes on mouse action every so often (20 mins). Changed Nvidia driver back to 173 from 180 and seems to have fixed the problem. (2 days clear)
BTW, if you want to restart without a hard shutdown, use the following method. Hold down ALT+PrintScr and type reisub

---

### Post by bearozo on 2009-05-04
> **dndzz said:**
> Had jaunty freezes on mouse action every so often (20 mins). Changed Nvidia driver back to 173 from 180 and seems to have fixed the problem. (2 days clear)
BTW, if you want to restart without a hard shutdown, use the following method. Hold down ALT+PrintScr and type reisub

Have tried reisub but no cigar :(  with 173 I only get 600 x 480, no fun :(

---

### Post by Icm76 on 2009-05-04
Is anyone finding that opening high res jpegs in **Image Viewer** causes a freeze? Specifically I'm finding that a low res images open just fine, but if the image is larger than the desktop res and needs some scaling to fit the window then it hangs every time. Same image will be fine in GIMP

I think mentioned earlier in the thread that opening the **Power Management GUI** is a 100% guaranteed hang. Also seems that removing apps from **Add/Remove** is very likely to result in a hang when it's finished.


Using Asus P5N7A-VM (730i/9300) with 2GB RAM & EXT3 filesystem

---

### Post by NoVista on 2009-05-04
I thought when the final release came out I was running fine.
Alas, system freezes at various times. 

To be clear: I have image files I can restore from going all the way back to Edgy. My Intrepid system runs flawlessly. I have tried the upgrade three times from Intrepid. There is something wrong though in 9.04. I usually go into a hard freeze, and sometimes I get booted down to the login screen. Then there are the times I get booted completely off, and I see on the screen that either there is an I/O error, or I can see Power management is trying to do something.
The all of a sudden out of nowhere instability issue of 9.04 can occur as often as every 5 to 20 minutes. 

Nevertheless, as stated, my Intrepid release runs perfect.
Too bad it looks like I'll have to go back to it, as Jaunty is simply not stable.

---

### Post by Ormente on 2009-05-04
I have the same problem with my laptop (HP tx1240ef). I ran Jaunty since Alpha 6 on my desktop and my netbook (msi wind U100), so i thought it was time to say good-by for real to Windows... i installed Jaunty on my tx1240, wich ran fine with Vista and Wubi-Hardy. And it turned totaly unusable : random freeze every time, while surfing or watching movies, or anything else.

I made a lot of tests, and to check things i ran a torrent download while watching a movie : that surely freeze "my" Jaunty in less than 3 minutes.

Now i've installed Hardy on this laptop, and everything works flawlessly ! So i think it's not a hardware issue, but probably a kernel one.

During my tests, i tried with/without compiz, with/without nVidia driver, with/without wifi, and so on ! Jaunty was installed with an ext2 /boot partition and ext4 for / and /home... tried to install with everything on a single ext4, and got the very same issues... even on ethernet with no proprietary driver installed, just after install. 

As i spent 3 days trying all things possible, i skipped the last test : reinstalling without ext4 at all, and went back to Intrepid (no, not to vista). I needed to go back to work with this laptop.

That's very... unpleasant and disturbing... so weird ! so strange ! In the same time my two others PC works very well with Jaunty.

BTW, even with this bad trip, I want to thanks all that GNUnixbuntu people for building such a good OS. I hope they'll solve the issue, and thanks each and all of them for that too.

(and sorry for my english, it's far from being my native language !)

---

### Post by krendar on 2009-05-04
I have a fresh install of Jaunty with same problems. I only installed:

-Ubuntu-restricted-extras
-ATI Restricted drivers from their homepage (not from the hardware applet)

I first had a suspicion on the ATI drivers, but reading this thread it seems nVidia and even Intel is affected as well.

I have just been listening to a podcast. My computer froze completely every 5-10 minutes so it was pretty frustrating.

I have started wondering if this could have something to do with the screensaver? Since I was listening to audio and didn't do anything it might be plausible that the screensaver was supposed to kick in when it crashed.

---

### Post by xl_cheese on 2009-05-04
My fresh install freezes evertime I maximize a window.  I'm running my LCD TV with an NVIDA card and the 180 driver from the repos.

I can't start some programs because they start as a maxed window so they freeze immediately.

---

### Post by newman on 2009-05-04
after the upgrade to 9.04 my system randomly locks up too. system was stable for past few years.

---

### Post by laplace/d on 2009-05-04
running ubuntu on an HP pavilion dv5. i did a fresh install of jaunty and i experienced a several number of freezings...

my hardware:
```
simon@simon-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

---

### Post by utkjamie on 2009-05-04
I started using the Jaunty Release Candidate and had no problems with freezing until today -- after I upgraded from Ext3 to Ext4. I have had 2 freezes today, both of which required me to physically kill the power to my computer. I can't even remember the last time I had a freeze like this. Two freezes in a month would be rare in my experience, so what's going on??

UPDATE: Since posting the above, I have had 2 more system freezes. Both of these happened while trying to have Firefox open a torrent file in Ktorrent. Ktorrent works fine and can open torrent files from within the app but sending a torrent file from Firefox to Ktorrent seems to be a recipe for disaster. One of the previous freezes took place while watching a video in VLC. I had zero freezes before upgrading my filesystem from Ext3 to Ext4.

---

### Post by bearozo on 2009-05-05
This time it took 21 hours before deep freeze, it froze going into screensaver while listening to a song on youtube.

---

### Post by utkjamie on 2009-05-05
I had 2 more freezes since my last post, which puts me at 6 in the last 24 hours -- all since I upgraded to Ext4.

I started a file transfer to a thumbdrive a few minutes before the last freeze. The file is now completely gone and the thumbdrive is short 80 MB. This freeze caused me to lose 180 MB of data even before I had a chance to back it up.

---

### Post by montini on 2009-05-05
More details on my new freeze:

When opening skype window, and then maximize/restore/maximize it, the maximized window starts to blink or smth and then the famous freeze.

I tried to set desktop effects to "None" - that way I have experienced no freezes on maximize/restore cycles.

So this seems to be somehow related to video driver/compiz effects. Any thoughts?

P.S. I recall last time the freeze occured on opening .pdf file from firefox browser, and my browser opens PDF viewer _maximized_ (!!) by default.

---

### Post by however on 2009-05-05
I am experiencing the freeze problem on my laptop. No reaction to keystrokes, only mouse pointer moves. Didn't try the SysRq thing yet. It seems to happen more frequently now - last night I had to restart everything about five times before I gave up...

It seems like all the freezes happened while using the computer interactively (browsing with Firefox). When it hangs, sound stops, too.

I use ext3, Desktop effects are set to "none", no proprietary drivers. I do have Intel graphics, though (855GM).

Hardware:

ASUS M2400N laptop
Pentium M 1.3GHz
768 MB (yes, it's an old machine)
Intel 855GM graphics (worked fine with i810 driver in previous releases)

I just found this thread. Is it worth trying the kernel update, or is that issue related only to newer Intel graphics? That wasn't clear to me from what I found so far.

---

### Post by crowin on 2009-05-05
> **Stenico said:**
> 
How hard is it for Canonical to buy a bunch of commodity hardware and run standard tests before making releases? (I bet Dell/HP etc would donate boxes to them!).
 
I am very happy with the _FREE_ operating system. Why dont you donate all of your old out of date equipment to open source? Get real, the people who write and test this are doing the world (including you) a service. How many versions of open source Windows are being developed? None! Linux is for people, not for customers.
Have a nice day.

---

### Post by roberthr on 2009-05-05
Same here on using Jaunty on 4 different machines. It's working without a glitch on these machines:

Laptop Dell Inspiron 1525 ext4 and Intel driver
Desktop MB Gigabyte M57SLI-S4, nVidia 8400 GS with nVidia driver and ext4

Now the problematic machines (where Interpid worked without a problem):

Desktop MB Gigabyte nVidia-nForce2, nVidia 6200 and ext4 - on this one, programs keep crashing (aMSN, Thunderbird, Firefox, SMplayer...). 

Syslog message when programs crashed:
```

May  5 17:59:49 bdesktop pulseaudio[3150]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
May  5 17:59:49 bdesktop pulseaudio[3150]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
May  5 17:59:49 bdesktop pulseaudio[3150]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
May  5 17:59:49 bdesktop pulseaudio[3150]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
May  5 18:00:45 bdesktop kernel: [   79.225355] ondemand governor failed, too long transition latency of HW, fallback to performance governor

```Desktop MB Gigabyte M55S-S3, nvidia 7600 GS and ext4 - this one completly locks up. It's not even possible to connect through ssh, so only reset helps. 

Syslog message around freeze:
```

May  5 14:13:14 asgard pulseaudio[3593]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 32000 Hz.
May  5 14:13:14 asgard pulseaudio[3593]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
May  5 14:14:05 asgard kernel: [   81.012031] Clocksource tsc unstable (delta = -282068898 ns)

```Since nobody has yet narrowed what seems to be the problem, is there any way to debug those two machines to get more useful data what happened? I know it will be difficult on hard lock-ups, because there's nothing logged and I can't connect through ssh to see what's going on.

I agree, this is really serious problem and I had to put friends that want to upgrade to Jaunty, on hold.

---

### Post by utkjamie on 2009-05-05
> **crowin said:**
> I am very happy with the _FREE_ operating system. Why dont you donate all of your old out of date equipment to open source? Get real, the people who write and test this are doing the world (including you) a service. How many versions of open source Windows are being developed? None! Linux is for people, not for customers.
Have a nice day.

I don't think anyone is questioning the loyalty or dedication of the Ubuntu team. Yes, the OS is free but that doesn't mean that users are expected to endure potentially destructive bugs. Losing data or being unable to work is bad. I doubt anyone is thinking* "Gee, I just lost 200 MB of family photos, but hey since I don't pay for the OS I'm totally cool with data loss every now and then."*

---

### Post by delSys on 2009-05-05
Ok, now there are not only my G-Talk-Buddies in Kopete, which will let freeze my system. Pidgin must thougt "Oh, what Kopete can do, i also can do - and that a lot better". Nearly every single contact i open causes in a freeze. And that is realy hard because i need it to work.

As i said, i need my laptop to work, not to reboot 10 times a day...
I switch back to 8.10 (Or should i test mandriva? Dont know right now. ;)), because i think there's coming no solution within the next half year...

---

### Post by olskar on 2009-05-05
> **utkjamie said:**
>  This is completely unacceptable and I really want to know how this kind of disasterous bug ever made it out of beta.

Short answer, the freezebug was not in the beta. It was introduced later (by what i think was a kernelupdate of some kind)

---

### Post by roberthr on 2009-05-05
> **olskar said:**
> Short answer, the freezebug was not in the beta. It was introduced later (by what i think was a kernelupdate of some kind)

I think that too. One of my machines was working without freezes until I reinstalled with final release.

---

### Post by utkjamie on 2009-05-05
> **olskar said:**
> Short answer, the freezebug was not in the beta. It was introduced later (by what i think was a kernelupdate of some kind)

Ah, okay. For me the problem didn't start until I upgraded to Ext4 yesterday so I've been working under the assumption that Ext4 was at least part of the cause. Thanks for correcting me.

---

### Post by olskar on 2009-05-05
> **utkjamie said:**
> Ah, okay. For me the problem didn't start until I upgraded to Ext4 yesterday so I've been working under the assumption that Ext4 was at least part of the cause. Thanks for correcting me.

Ext4 is probably responsible for the dataloss you had, however freezes appear regardless of filesystem

---

### Post by nyk on 2009-05-05
Now I haven't read through all of the posts here, but I would like to throw my two cents out into the pile. I had the package alarm-clock installed, which for some reason or another caused the GUI to freeze, with only a moving mouse. Research led me to [this bug]("https://bugs.launchpad.net/ubuntu/+source/alarm-clock/+bug/321176"), after which I just uninstalled the package and and everything worked fine. This probably won't help everyone as it seems to be a diverse problem, but I hope it helps someone.

---

### Post by roberthr on 2009-05-05
> **utkjamie said:**
> Ah, okay. For me the problem didn't start until I upgraded to Ext4 yesterday so I've been working under the assumption that Ext4 was at least part of the cause. Thanks for correcting me.

According to my calculations EXT4 is not reponsible for lockups. 

I also have a server machine which runs Gentoo Linux - no ext4, no X, just plain shell with few services. Few weeks ago, I've upgraded kernel to 2.6.28 when whole machine started to lock up randomly, then I upgrade to 2.6.29 and lock ups were still present so I've decided to put back 2.6.27 and server seems to be happy since then. Didn't try 2.6.30, since it's not yet stable enough on Gentoo.

I would love to help more, but I'm just lost in all those bug reports and duplicates and I don't even know in which project should I start and what to report when lockups doesn't give any ouput.

---

### Post by CA_Warren on 2009-05-05
This clearly hasn't worked for everyone, but I'll throw my 2c in in case it helps anyone else: freezes perfectly matching the above symptoms and introduced by upgrading to 9.04 (averaging 3+/day) seem to have stopped for me since disabling desktop effects.

Lenovo Thinkpad R61i
Kubuntu 9.04
Intel Mobile GM965/GL960 Integrated Graphics

---

### Post by trevelyon on 2009-05-05
Well I thought I would chime in with some hopefully helpful info.  My laptop is locking up about twice a day.  Sometimes this seems in response to actions and sometimes not.  Below is the hardware / software info as well as some actions that were in process while the freeze occurred.  Hope this helps make Ubuntu better.

Hardware:
Laptop: MSI GX720 barebones laptop
Graphics: Nvidia 9600M GT
Memory: 4GB DDR2 800
Wifi: Intel 5300 AGN
webcam (not sure if it works): Chicony (ID 04f2:b073)
sound: Intel HDA 82801I rev 3
ethernet: RTL8111/8168B rev 2

OS: jaunty x86_64
Filesystem: reiserfs (not reiser4)
often open apps (most if not all are running during the freeze):
evolution
psi
skype
jpilot
firefox

Notes:
Twice Skype lost sound and when I went to close the process I couldn't kill it (even with kill -9).  Soon after I got a hard freeze.
A few times I left the laptop and came back to a frozen screen (which means it happened before power management kicked in).
I should mention suspend and hibernate both seem to be working flawlessly on this (in case that is a suspect).

Hope this helps, let me know if any other info is particularly helpful and I will try and provide it.

---

### Post by shelby_vn on 2009-05-05
I upgraded an existing install yesterday and had 5 freezes within an hour before I gave up. The same hardware has been running every release since edgy. I was working with GIMP at the time - I haven't had time to test the machine on any other tasks yet. I use nvidia graphics.
What logs should I be looking at to help shed some light on the problem?

I had also upgraded my laptop (3rd-gen macbook) which seems to be fine...

---

### Post by primski on 2009-05-06
similar problem here, not quite though:

haven't experienced these hard types of freezes, had one or two but not for a while now so it looks like thats resolved.

However i do have issues with network connection, wireless that is, havent treid wired, perhaps it would help. Connection keeps freezing, at an hourly rate, it would freeze for 10 seconds, letting no traffic through. all my IM apps lose connection, i often use RDP, which also loses connection, torrents, everything, whole connection just freezes for 10 seconds or so and then continues normally, very annoying. 

the other situation is when i get disconnected from my wireless network, and have wireless adapter unavailable for 10, 15 seconds. like module would get unloaded from kernel and reloaded automatically again, no networks available during the period, right click on the network applet shows no wireless adapters available. 10 seconds later its back, get reconnected and works normally on.

wierd, any idea of debugging is appreciated

edit: forgot to mention my specs:
Ubuntu Jaunty 9.04 32bit
Dell Inspiron 1525
Broadcom STA wireless driver wl
Core2Duo. 3GB of RAM

---

### Post by madomac on 2009-05-06
> **delSys said:**
> 
As i said, i need my laptop to work, not to reboot 10 times a day...
I switch back to 8.10 (Or should i test mandriva? Dont know right now. ;)), because i think there's coming no solution within the next half year...

Just _my_ experience: My freezes seem to be related to activity on wlan0. In the course of troubleshooting I installed Intrepid amd64 (jeeeez - Jaunty is so much nicer!). And to my surprise the same effects showed up on Intrepid!!!

My solution to work around the freezes: When the freezes start to show up again, I boot into Vista. And then back to Jaunty again. Is it possible that the wireless drivers of Vista reset some fancy hardware registers?!

Simply switching off the computer doesn't help. I switched it off, removed the battery, let it sit there for 30 minutes - still freezing. Vista seems to be the workaround... :confused:

Just for the records: Dell Inspiron 1545 with ATi graphics and Intel Wifi Link 5100AGN / iwlagn driver.

Cheers,
Marc

P.S.: I'd love to assist the developers with meaningful information - the issue is just hard to reproduce. Any thoughts how I could be of help?

---

### Post by brntoki on 2009-05-06
Same thing here. Fresh install from DVD. Thought it may be graphics related, tried different nvidia drivers (none but 180.44 would even work no matter what I tried), uninstalled all nvidia stuff, still freezes up. Fresh installed again, deleting the old root dir and reformatting, froze within a minute, before, I might add, I even tried to install the nvidia drivers.

One thing that does seem to be related in all but perhaps one or two instances was that there was network activity going on. I.E., starting web-browser, doing an update, or trying to look for answers via google. It just seems there is possibly some connection to the network activity.

[COLOR="RoyalBlue"]The video on this page seems to reproduce the crash without exception:[/COLOR] [http://linuxcrypt.net/?p=255](http://linuxcrypt.net/?p=255)

I don't know what logs or anything to look for. FYI, no ext4, though I did use my old /home dir in order to keep settings. I wonder if there is some conflict within those settings. I was coming from a totally trashed upgrade attempt of 8.10 (didn't last long), so essentially I was coming from 8.04.

gigabyte ga-p35-ds3l, intel dual core, ge-force 7300 gt, 4gb mem.

---

### Post by olskar on 2009-05-06
> **brntoki said:**
> 
[COLOR="RoyalBlue"]The video on this page seems to reproduce the crash without exception:[/COLOR] [http://linuxcrypt.net/?p=255](http://linuxcrypt.net/?p=255)


Works fine here :/

---

### Post by bearozo on 2009-05-06
It actually did freeze my puter but I had to watch for quite a while before it happened and I could get out of it using REISUB I have done the reisub wrongly before so I think I could've gotten out of freezes before using reisub.

oh. sorry running the movie about installing nVidia driver in thread above.

---

### Post by however on 2009-05-06
I have applied the fix mentioned on one of the first pages of this thread:

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

As yet no more freezes... I hope it stays like that! Should they reappear, I'll post again.

So, my freeze problem probably was related to the Intel graphics issue.

---

### Post by cucsd1981 on 2009-05-07
I'll give a brief update.

I was having problems of freezing after long idle periods. A few days now, and no more freezes. I didn't do anything specific, installed updates. I did do one thing: I went from my nvidia drive 180 to 173, and then back again (because going to 173 didn't solve it). 

I am going to assume that somewhere in the updates something got fixed that was associated with my problem of long idle freezing. I noticed a few others reported the same problem - did yours subside, too? If not, for whatever reason, if you are using an nvidia, you can try what I did... who knows...

I hope for the rest of you the freezes stop soon!

---

### Post by brntoki on 2009-05-07
Can someone give me a quick rundown on how to install the rc kernel for amd_64.  I don't have intell graphics, so don't need all parts of the linked tutorial.  I don't quite get what I do and don't need to do, however.  I tried to figure it out but couldn't quite get it.  I did use the correct instructions for amd_64, too.  ???

Also, **I think** this _definitely_ has to do with the network activity.  I downloaded the 8.04 image on another box, and upon transferring that file to this box (other box can't burn the dvd), it crashes every time.  If I'm doing lighter activity I could stay up 'n runnin' for maybe a couple hours, but if the network got too busy it was freeze city.

P.S. Question:  Why does XP on this same machine download soooo slowly from the exact same mirrors?  It can only achieve about a 1/4 of what Ubuntu can.  Crazy!

---

### Post by roberthr on 2009-05-07
My update: upgrading nVidia driver on work desktop machine to 180.53 seems to solve the problem. I can have compiz, listen music and browse internet now without a hiccup. Will try to do the same with second desktop where programs are crashing randomly.

---

### Post by ladydeth666 on 2009-05-07
I reinstalled to the 180 nvidia driver last night after I got some big updates....it seems to run well....but Ive been watching the thermometer on the nvidia-settings, and it takes my card up to over 74C!  Thats only when bringing up WoW in Wine, but Im not even loading the game, just the login screen.  I did turn off the compiz settings and set my desktop to an easier to draw interface, and it dropped to 64ish.  I reinstalled the 173 driver and it only gets to 69C while actually playing Wine/WoW.

---

### Post by black_shadow on 2009-05-07
No problems here with Jaunty I have one PC that has been running Jaunty since the day of release.

Is your install a clean install or an upgrade as this can cause problems.

Mike

---

### Post by ladydeth666 on 2009-05-07
mine was a clean install of 9.04 beta, most updates up to last night (6May09)

---

### Post by brntoki on 2009-05-07
Mine was a clean install.  I did keep my old /home directory, however.  Running the rt kernel for Ubuntu Studio x64.

---

### Post by madomac on 2009-05-07
> **black_shadow said:**
> No problems here with Jaunty I have one PC that has been running Jaunty since the day of release.

Is your install a clean install or an upgrade as this can cause problems.

Mike

Clean as it could be - bought the new notebook, erased Vista and installed Jaunty. :P

---

### Post by Chemical Imbalance on 2009-05-07
> **Polygon said:**
> hi, i am having the same problem, and as there is no mention of the problem whatsoever in the logs after my computer logs up, i submitted a bug report

but since none of us have any information on what exactly is going on, they may be for different reasons

but you might want to add something useful and or subscribe to this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155)

I subscribed and commented on your bug report as I am also having the same issues.

This is a very annoying bug.

I have an onboard nvidia 8300 (rev 2)
64 bit Jaunty with EXT4 and latest default kernel along with latest nvidia drivers in jockey-gtk.

I am trying running without nvidia drivers atm.  Seems to be working so far...but it sucks without drivers

I am also installing the kernel recommended in this post: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by krendar on 2009-05-07
I wrote a few pages back that I used the ATI drivers from their homepage. Well, I now tried a reinstall. Even with the shipped opensource drivers I get hard locks of my system. I have then installed the drivers from the "hardware" applet since it seemingly made no difference :(

-Ubuntu 9.04 x64
-Radeon HD 4870
-Core2Duo 7500

---

### Post by Chemical Imbalance on 2009-05-07
Okay, I have gone a record 47 minutes without freezing after uninstalling the nvidia drivers.  I don't have 3D acceleration now, but at least there seems to be no more freezing.

---

### Post by suresnjain on 2009-05-07
till  this bug is sorted out, may be one can disable this screensaver set up by commandline or some application.Any suggestions?

---

### Post by brntoki on 2009-05-08
Running without nvidia drivers doesn't help.  Disabling the screensaver wasn't helpful either.  I'm pretty sure this is down to the network activity somehow or another.  I'm gonna visit the bug report page, then go back to my Jaunty install and disable my network connection and try to actually get some work done.  If I'm able to stay up for more than, say, 4 or 5 hours, then I'll be convinced that it's something with the network activity.

---

### Post by mr.tapac on 2009-05-08
hi. Ubuntu 9.04 on my laptop works fine.
but clean install on desktop have problem.
system freezes in 5-30 seconds after Gnome loaded.
some times system reboot, sometimes it freeze.

some times I can see "artefacts" on desktop.
I try to add 'driver "vesa"' in my xorg.conf - same problem.

what is it?

uname -a
Linux gil-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

AMD 64 X2 3800+

---

### Post by hype on 2009-05-08
Did people having issues upgraded their previous install? or was it a fresh install?

For the desperate ones, just try backing up your home folder, format it and make a fresh install.

Edit: you can also try latest kernel from here [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
Try the 2.6.29.2 or latest 2.6.30 Rc's

---

### Post by mr.tapac on 2009-05-08
my installation is absolutely clean..

I have backed up my "/home" (mv /home/gil /home/gil.bak)..
I have formated my "/"..
New user was named "gil", and directory /home/gil new..
no more mount-points..

---

### Post by rajeeja on 2009-05-08
Tip : Never Uninstall Python 2.6.

---

### Post by trash on 2009-05-08
no problems on my desktop
1-3 times daily on my laptop...Intel Corporation Mobile 4 Series Chipset

---

### Post by madomac on 2009-05-08
I just signed up to this bug mentioned above:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155/)

And I would like to encourage everybody with a complete system freeze (that is "ALT+SysReq+R-E-I-S-U-B" does not reboot the system) to submit their xorg.0.log, dmesg and "lspci -vvnn" output to the bug.

Cheers,
Marc

---

### Post by brntoki on 2009-05-08
I disbled my network connection and went several hours without a freeze.  As soon as it was turned back on and I went back to the bug report page it immediately froze.  This has to do with networking.  If someone else has the opportunity to work on their box for a while without need of networking, maybe you could see if disabling the network connection does stop the freezing.

---

### Post by bearozo on 2009-05-08
I still have the freezebug after the updates, this movie does it all the time [http://linuxcrypt.net/?p=255](http://linuxcrypt.net/?p=255)
but this last time I was listening to music (Foobar through wine) andtried to browse at the same time, I am also pretty convinced that it is a network problem using browser  only surfing works most of the time except with above mentioned movie but with other stuff running and browsing the freeze happen. Not all network stuff will make a freeze though, leaving Deluge running overnight is no problem.

---

### Post by brntoki on 2009-05-08
> **bearozo said:**
> I still have the freezebug after the updates, this movie does it all the time [http://linuxcrypt.net/?p=255](http://linuxcrypt.net/?p=255)
but this last time I was listening to music (Foobar through wine) andtried to browse at the same time, I am also pretty convinced that it is a network problem using browser  only surfing works most of the time except with above mentioned movie but with other stuff running and browsing the freeze happen. Not all network stuff will make a freeze though, leaving Deluge running overnight is no problem.

My guess is that if you started any big download, like an Ubuntu image, that you'd freeze up.

---

### Post by Chemical Imbalance on 2009-05-08
I can trigger the freeze every time I use glxgears.

I've tried the .30 rc4 kernel and the latest beta nvidia drivers, but I'm still getting the mouse freezing.

---

### Post by crowin on 2009-05-08
> **utkjamie said:**
>  I doubt anyone is thinking* "Gee, I just lost 200 MB of family photos, but hey since I don't pay for the OS I'm totally cool with data loss every now and then."*

I am not sayin thats a good thing either. I will say in response perhaps a USB HD or other device for a backup? Even James Brown suggests that you backup.
:guitar:


Aloha

---

### Post by kemorc on 2009-05-08
> **krendar said:**
> I wrote a few pages back that I used the ATI drivers from their homepage. Well, I now tried a reinstall. Even with the shipped opensource drivers I get hard locks of my system. I have then installed the drivers from the "hardware" applet since it seemingly made no difference :(

-Ubuntu 9.04 x64
-Radeon HD 4870
-Core2Duo 7500

I'm in the same exact boat... I don't dare making adjustments or attempting to.  They simply lock up my machine.

-Ubuntu 9.04 x64
-ATI Radeon HD 3870
-Phenom 9500

Does Jaunty = Vista?

---

### Post by bearozo on 2009-05-08
the button says edit/delete but how do I delete mypost ?

---

### Post by bearozo on 2009-05-08
> **brntoki said:**
> My guess is that if you started any big download, like an Ubuntu image, that you'd freeze up.

No I just clicked a tab in FF when it froze, I forgot to mention  that in all freezes now I can reboot with 
REISUB, since I learned how to do it right i.e. Ctrl + Alt + SysRq and  when still holdnig down Ctrl + Alt while pressing REISUB one at the time giving it some time for each.

---

### Post by brntoki on 2009-05-08
> **bearozo said:**
> No I just clicked a tab in FF when it froze, I forgot to mention  that in all freezes now I can reboot with 
REISUB, since I learned how to do it right i.e. Ctrl + Alt + SysRq and  when still holdnig down Ctrl + Alt while pressing REISUB one at the time giving it some time for each.

Well, it can happen on any simple page loading as well, I know.  It's just that sometimes it'll go for a while with no problems with normal browsing.  Anything heavier, however, seems 100% fatal.  It has also frozen when there were updates being downloaded or getting software via Synaptic.  It happened at least once when there was no *apparent* network activity, but I suspect there was something in the background using the network.  Again, when I disabled networking I was up for the whole day, but when re-enabled I froze withing a few minutes.

Can you disable your networking for a while to see if you are stable without it?

Whoever said that glx gears triggered the freeze, can you also disable networking and then try glx gears again?  Glx gears didn't freeze my system even with networking enabled.

---

### Post by francesco44 on 2009-05-09
Fortunately I had no freeze in Jaunty since an upgrade on three different Laptop.


I could therefore consider myself lucky....But I had MANY freezes in 7,04, 7,10 if my souvenirs are correct....I struggled for a few month as many people from that thread.


Il I can come to a conclusion it is that "freeze detection" fellows (many thanks to them) doesn't apply a convenient procedure to understand the problem. The absence ob communication between the forum and lauchnpad is disastrous....Many people are really desperate. They cannot work....If i had not kept for few month a laptop with XP...I would have been FIRED from my job.


If a thread goes up to more than 20 pages...it SHOULD be treated by the Canonical folks...it means the community is lost and something MUST be done.

Mark Shuttleworth should take himself this question seriously. Many thing are possible....The first one would be to try a statistical automatic approach on the forums. In some cases...this can give results...It is not always a solution.

Another issue would be to select 10 or 30 cases.....and try to solve the problem systematically by mail...or even better by taking a remote control of the computers.

It is now too complicated in some issues to rely on forums...it works 1 in 10 times.

From my experience....the freezing seems to have a close relation to the structure of the device section in xorg.conf

A statistical analysis of this section might be helpful

---

### Post by madomac on 2009-05-09
I am not familiar with the bug tracking process in launchpad. The bug is now in the state "confirmed", as we submitted system information. What is the process to change the importance from "undecided" to some other state, what is the escalation process? 

Obviously this bug is not only cosmetic, so we should give it an appropriate severity class.

Thanks,
Marc

P.S.: Always good to have a backup system - typing this on a Dell Mini 9 which is rock solid w/ Jaunty i386 ;)

---

### Post by madomac on 2009-05-09
<Deleted>

---

### Post by steelyeyes on 2009-05-09
I have been using ubunto 9.04 for just over a week. I am new to Linux but I am really impressed with the whole open source ethos.

I have had constant freezes and unexplained reboots for the past 5 days and it is really frustrating.  I am using an Intel Pentium 4 2.4 Ghz with an ATI 9250 graphic card.  I run update manager & disk janitor every day to try and solve the problem -  but no joy!

Help?

---

### Post by cmdrtebok on 2009-05-09
I am having the same issue that Jaunty constantly locks up on me. It only happens after I use the nVidia 180 drivers. When I looked through the forums and looked at nVidia based problem posts they weren't quite having the same problem I am. Its a total random freeze of everything and the only way around it is to turn the power off and back on. I could probably recreate it if I was to reinstall the drivers but I don't know where to look on the logs (or where the logs are) to submit bug reports.

---

### Post by olskar on 2009-05-09
Could people experiencing crashes try disabling all network connections (pull the cable and reboot might work too) for a while and see if the system still crashes? So far this seems to be the 
common denominator.

---

### Post by cmdrtebok on 2009-05-09
For me it doesnt freeze as long as I use the default video drivers and not the restricted ones. I'm pretty sure.

---

### Post by brntoki on 2009-05-09
> **olskar said:**
> Could people experiencing crashes try disabling all network connections (pull the cable and reboot might work too) for a while and see if the system still crashes? So far this seems to be the 
common denominator.

For me, all that was needed was to go to Administration, Network, and after unlocking with password, to uncheck the box next to my network connection which inactivated it, and close the network settings.  I then opened Firefox and did some other poking around to be sure that the connection really was disabled.  That stopped the crashes for me.

---

### Post by krendar on 2009-05-09
My Jaunty has been completely stable since yesterday. Not a single crash! Before that it was crashing at least once per 1-2 hours.

There was a compiz-config update yesterday, not sure if that's what did it, but I am happy :)

---

### Post by trash on 2009-05-09
> **olskar said:**
> Could people experiencing crashes try disabling all network connections (pull the cable and reboot might work too) for a while and see if the system still crashes? So far this seems to be the 
common denominator.

Well i tried the other fix of disabling visual effects and didn't freez for an entire day... weathers bad hear so while i was having some network problems i switched from my wireless router to my neighbors... first off i noticed that those little green lights showing connecting don't appear anymore, further i was able to connect as far as connection status says but could not access the net at all. Started to shutdown programs to restart the machine and on restart the machine froze... so ya i'm convinced it network issues!
System monitor applet also fails to monitor anything after network switching occured, from there is was all down hill.

EDIT: sadly i can't reproduce it:(
OH btw what key is the sysrq??

---

### Post by olskar on 2009-05-09
> **trash said:**
> Well i tried the other fix of disabling visual effects and didn't freez for an entire day... weathers bad hear so while i was having some network problems i switched from my wireless router to my neighbors... first off i noticed that those little green lights showing connecting don't appear anymore, further i was able to connect as far as connection status says but could not access the net at all. Started to shutdown programs to restart the machine and on restart the machine froze... so ya i'm convinced it network issues!
System monitor applet also fails to monitor anything after network switching occured, from there is was all down hill.

EDIT: sadly i can't reproduce it:(
OH btw what key is the sysrq??

Usually sits on the PrintScreen button

---

### Post by trash on 2009-05-09
yes thought so, mine reads syst... didn't do anything when i did ctl+alt+sys

---

### Post by trash on 2009-05-09
Another! why won't ctl+alt+syst do anything for me?:(

---

### Post by bearozo on 2009-05-09
I have now had it disabled for over 2 hrs. Started a lot of stuff, like virus scanning, playing music in foobar through wine, playing with compiz, watching pictures, doing stuff in O-O etc. all on different desktops yeah really trying to provoke a freeze but no cigar, so I am even more convinced now that it really is a network problem.

> **brntoki said:**
> Well, it can happen on any simple page loading as well, I know.  It's just that sometimes it'll go for a while with no problems with normal browsing.  Anything heavier, however, seems 100% fatal.  It has also frozen when there were updates being downloaded or getting software via Synaptic.  It happened at least once when there was no *apparent* network activity, but I suspect there was something in the background using the network.  Again, when I disabled networking I was up for the whole day, but when re-enabled I froze withing a few minutes.

Can you disable your networking for a while to see if you are stable without it?

Whoever said that glx gears triggered the freeze, can you also disable networking and then try glx gears again?  Glx gears didn't freeze my system even with networking enabled.

---

### Post by bearozo on 2009-05-09
> **trash said:**
> Another! why won't ctl+alt+syst do anything for me?:(

I can reboot with 
REISUB, since I learned how to do it right i.e. Ctrl + Alt + SysRq and when still holdnig down Ctrl + Alt while pressing R+E+I+S+U+B one at the time giving it some time for each.

---

### Post by trash on 2009-05-09
> **bearozo said:**
> I can reboot with 
REISUB, since I learned how to do it right i.e. Ctrl + Alt + SysRq and when still holdnig down Ctrl + Alt while pressing R+E+I+S+U+B one at the time giving it some time for each.

Ya it doesn't seem to work for me.
For me most freezes occure during or just after video chats in amsn or skype.. most often skype.

---

### Post by brntoki on 2009-05-10
> **bearozo said:**
> I can reboot with 
REISUB, since I learned how to do it right i.e. Ctrl + Alt + SysRq and when still holdnig down Ctrl + Alt while pressing R+E+I+S+U+B one at the time giving it some time for each.

I'm going to go into Jaunty and try an update.  I can't believe that it's a Compiz thing since I never even enabled it, but I'll give it a shot anyway.

That'll give me a chance to try the REISUB technique.  I do wonder what the advantage is of doing this over a hard reset; extra finder exercise?  I'm guessing it's a fancy way of doing exactly what a hard reset does, but who knows???  I'm curious if anyone has an explanation.

EDIT:  Nevermind.  I know Google is my friend. [http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart)

---

### Post by Nicolas19 on 2009-05-10
All of you problems with ctrl+alt+sysrq. It doesn't work for me either. Try ctrl+ALTGR+sysrq instead, that should do the trick. Wish we wouldn't have to use it though...

---

### Post by karamu on 2009-05-10
Just going to add my "me too" to this rather long thread! Things were working fine with 8.04- Windows crashed the machine and caused a full re-install of everything so I took the opportunity to do a fresh install of 9.04.

First couple of times I booted into it, it froze- everything, including the mouse pointer- had to hit the case reset button.

It behaved for a few days without any hitch then started doing it again intermittently, like every couple of hours or so.

Looks like it's a pretty big gremlin in the system- I'll give it another re-install and if it persists might be time for me to try another distro (been toying with the idea for a while but Ubuntu has always worked for me before.....).

---

### Post by dimach_ on 2009-05-10
I had the system freezing after 2-3 min. Got it running fine after removing NVIDIA proprietary drivers...

Any ideas how to configure 1920x1080 resolution with standard driver?

---

### Post by bearozo on 2009-05-10
> **roberthr said:**
> My update: upgrading nVidia driver on work desktop machine to 180.53 seems to solve the problem. I can have compiz, listen music and browse internet now without a hiccup. Will try to do the same with second desktop where programs are crashing randomly.
Where did you find 180.53 ? I can only find 180.51, 185.18.04 beta and 185.18.08 beta.

The 180.51 does not solve the problem for me.

BTW. I forgot to mention when my puter freezes in a movie or with music playing it starts with stuttering sound (using ALSA, the pulse audo does not work well for me)

---

### Post by zugol on 2009-05-10
The 180.53 nvidia driver does'nt fix my problem. 

Found here :

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

You can also try this kernel...

[http://doc.ubuntu-fr.org/kernel_2.6.29]("http://doc.ubuntu-fr.org/kernel_2.6.29")

Actually I does'nt know if it fix the problem until the system freeze again !... But the pre-release 180.53 don't !

---

### Post by moodog on 2009-05-10
Similar to others, I've had a few updates installed over the last week or so, and it appears that all of my freezes have gone. I've had my laptop on almost contantly running azureus, virtualbox with vista, suspend and wakeup etc., and not one freeze for a good few days. 

i think one of the updates must have fixed my problem...

---

### Post by Mirge on 2009-05-10
I have not had a single freeze in 9.04 since it first came out... until I ran that Mac4Lin installer. Then I decided I didn't like it, so I went back to my old theme I had customized... figured all was good, moved on. Then out of no where, my first freeze. Then another. Now I'm just waiting for another to happen... and another. The *only* change I made was using that Mac4Lin installer... I'd like to just re-install & be done with it, but if I re-install and re-import my account from this install, those same files & config will be back and I'll just keep experiencing the freezing I'm sure. So now I'm at a loss as what to do.

---

### Post by atngplusultra on 2009-05-11
> **Mirge said:**
> I have not had a single freeze in 9.04 since it first came out... until I ran that Mac4Lin installer. Then I decided I didn't like it, so I went back to my old theme I had customized... figured all was good, moved on. Then out of no where, my first freeze. Then another. Now I'm just waiting for another to happen... and another. The *only* change I made was using that Mac4Lin installer... I'd like to just re-install & be done with it, but if I re-install and re-import my account from this install, those same files & config will be back and I'll just keep experiencing the freezing I'm sure. So now I'm at a loss as what to do.

the Mac4Lin may be messing my machine up as well, so, you're not alone. I have the theme majorly but not completely implemented into what i've been using ever since 7.10, and surprisingly, even though i did a complete re-install to upgrade to 9.04 from a live CD (i don't just use the updater) the X environment was the same, which i was pleased by, but there have been many performance problems.

---

### Post by karamu on 2009-05-11
For what it's worth, I just tried a fresh install and the problem is even worse! It boots up fine and I get into the desktop environment but as soon as I try to do anything, it freezes- open Firefox, home folder or preferences whatever.

This is really starting to annoy me- unlike some other posters I don't use my home PC for work but it is my entertainment centre and I want to use it! Looks like I'm going back to Ubuntu 8 unless anyone has any suggestions.......

---

### Post by bearozo on 2009-05-11
I said before that I think it is a network problem but in my home network; ipcop router/firewall my wifes vista laptop, my sons xp machine and this ubuntu machine all works fine I can transfer files (using samba) without freezes, using ff though gives freezes and especially if I watch movies so for me it is network through internet that is the problem.

---

### Post by Mirge on 2009-05-11
> **karamu said:**
> For what it's worth, I just tried a fresh install and the problem is even worse! It boots up fine and I get into the desktop environment but as soon as I try to do anything, it freezes- open Firefox, home folder or preferences whatever.

This is really starting to annoy me- unlike some other posters I don't use my home PC for work but it is my entertainment centre and I want to use it! Looks like I'm going back to Ubuntu 8 unless anyone has any suggestions.......

Man that stinks :( Wish I could offer up some helpful advice to solve it, but unfortunately I can't... for me, it was my xorg.conf. I restored to a known working backup I had created after re-installing last time (my own fault lol).... and NO freezing.

---

### Post by jespdj on 2009-05-11
The last few days I've also noticed occasional random freezes on my laptop: Dell XPS M1530, ext3 filesystem, nVidia 8600M GT (using nVidia driver 180.44 which is included with Jaunty).

It doesn't happen often, but maybe once a day or so it just locks up, I can't even move the mouse pointer anymore. Very annoying... :(

I'm running 64-bit Jaunty.

---

### Post by dannyboy1121 on 2009-05-11
> **norcim said:**
> There seems to be a GUI related bug because working in the terminal does not produce a freeze.

Sorry but wrong.

I've been running PXE booted system for the last three years using Ubuntu.  I recently upgraded my server to Intrepid which worked for a couple of weeks then began exhibiting the same problems listed in this Jaunty thread .. upgraded to Jaunty and still get the syslogd 1.5.0#5ubuntu3: restart. error in /var/log/messages.

Being PXE booted I've swapped out the client (completely different hardware) .. my kernel is the latest from kernel.org (made specifically for the PXE booting process) and I run from terminal only. My system falls on its **** between 1 and 10 times a day - and seems to be influenced by load.

---

### Post by Stenico on 2009-05-11
> **crowin said:**
> I am very happy with the _FREE_ operating system. Why dont you donate all of your old out of date equipment to open source? Get real, the people who write and test this are doing the world (including you) a service. How many versions of open source Windows are being developed? None! Linux is for people, not for customers.
Have a nice day.

No. Canonical, the company behind Ubuntu linux want to become profitable and make money. They are trying to monetise the efforts of people who write open-source software. That we get Ubuntu desktop linux free from them (for which I am very grateful and happy) is a side-effect of their strategy to make money from selling linux products and services.

Canonical make the Ubuntu *distribution* of linux, and by giving it away for free hope to demonstrate to private enterprises that it is good enough for them to use and buy service contracts from Canonical. They spend a lot of money towards this aim. I'm suggesting they should spend more of this money on testing their software before release if they want to persuade people its good enough for commercial use.

If you want to use a truly free distribution of linux, investigate the Debian distribution, which Ubuntu is based on.

---

### Post by dannyboy1121 on 2009-05-11
> **roberthr said:**
> According to my calculations EXT4 is not reponsible for lockups. 

I also have a server machine which runs Gentoo Linux - no ext4, no X, just plain shell with few services. Few weeks ago, I've upgraded kernel to 2.6.28 when whole machine started to lock up randomly, then I upgrade to 2.6.29 and lock ups were still present so I've decided to put back 2.6.27 and server seems to be happy since then. Didn't try 2.6.30, since it's not yet stable enough on Gentoo.

I would love to help more, but I'm just lost in all those bug reports and duplicates and I don't even know in which project should I start and what to report when lockups doesn't give any ouput.

Now that sounds like a suggestion worth trying. 2. 6. 27. My issues have been with 2. 6. 29 (skipped .28). Time to compile a new (err old) K.

---

### Post by YS1 on 2009-05-11
I am experiencing the same problem.

My wlan card is "Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)" (pci id : 17fe:2220). I tried the (Windows) driver that was shipped with my computer, and the one described in the ndiswrapper compatibility list.

The problem is not X related as it occurs even in a console session (gdm not started).

The "time-before-freeze" seems to depend on the network I connect with : I can use my home network (WEP) for some minutes (depending on what I actually do), but if I try to connect to the University network (unencrypted), it freezes immediately. But sometimes it freezes even if I am not connected to any network. However, I never experienced a freeze when the wlan card was disconnected or no driver for it was installed.

When the freeze occurs, I am not able to reboot using the SysReq REISUB combination.

---

### Post by Yathi on 2009-05-11
guys stop blaming the company and instead think of some solution. I am also experiencing the same freeze ups. Wat is the solution to it or do i have to restart the pc as i m doin now??

---

### Post by Wild-Storm on 2009-05-11
Well i have the same problem here. My system freezes pretty often (about 2-3 times a day, although it didn't freeze today). Symptoms are the same as in the opening post.
I could not find any hints in the logfiles (by the time the system froze, there were no logfiles)
I thought it may be truecrypt, but i don't think so since I'm copying about 20 gigs right now. My sys just laggs a bit.
For the network part: I was looking TV last night (with kaffeine) but I didn't download anything - suddenly the sys just froze. Just right now I tried downloading about 500 megs, but there was no freeze either. I have no idea what to do. The problem came after upgrading to 9.04

---

### Post by suresnjain on 2009-05-11
My system freezes totally after 10 minutes of idle time(time I have set for the screensaver).As soon as, this saver appears,the system goes into total freeze-and I mean total.This is particularly noticeable after 10 minutes of Rhythmbox play. Till, this bug gets fixed, I have found a temporary way out.Have launched an application on desktop-monitor off with command xset dpms force off.After I start Rhythmbox, I shut off monitor and the system does not go into freeze because screensaver does not appear.Today,i tried this one,and it was quite successful.Can someone suggest complete solution.Remember I am a newbie.:confused:

---

### Post by squee on 2009-05-11
With a problem this big I'm surprised that first of all, no-one knows exactly what the problem is and secondly that it hasnt been fixed yet.

Is it even being worked on? If its not going to be fixed soon, I'm going back to 8.10 where my gfx card didnt just randomly log me off every few minutes.

---

### Post by Mirge on 2009-05-11
> **dannyboy1121 said:**
> Sorry but wrong.

I've been running PXE booted system for the last three years using Ubuntu.  I recently upgraded my server to Intrepid which worked for a couple of weeks then began exhibiting the same problems listed in this Jaunty thread .. upgraded to Jaunty and still get the syslogd 1.5.0#5ubuntu3: restart. error in /var/log/messages.

Being PXE booted I've swapped out the client (completely different hardware) .. my kernel is the latest from kernel.org (made specifically for the PXE booting process) and I run from terminal only. My system falls on its **** between 1 and 10 times a day - and seems to be influenced by load.

Well I'm sure there is a variety of ways that could be causing a freeze issue, and could vary for different users. Mine turned out to be a xorg issue.

---

### Post by bearozo on 2009-05-11
Well today I gave up :(  I installed from CD instead and it got even worse + other stuff happening like envyng crasched gnome commander refused to install etc. to much for a noob in linux otherwise I have been with puters since DOS and Basic 3 Mhz ABC 800 and learned to do much in DOS so I am not new to puter life but jaunty was to much so now I've just finnished installing UbuntuStudio 8.04.1 and it feels rock solid :D Compiz work fine watching movies works fine etc.etc.. I will wait untill things settle and start running smooth in Jaunty before I upgrade.

---

### Post by however on 2009-05-11
I had reported (a couple pages back) that the kernel update / xorg driver fix seemed to work for me. Unfortunately, that's not true. Now I had a few freezes again. Already two today, within an hour. The magic SysReq key combinations still work when it freezes.

---

### Post by Mega__ on 2009-05-11
Same problem here. So far only experienced it once since I updated 24 hours ago...

---

### Post by brntoki on 2009-05-11
Yes, the total and complete freezes (I.E., REISUB doesn't work) are network related.  Otherwise, if REISUB *is* working, you *may* have other issues.  

But, I'm now getting a little irked that the bug report is sitting there and there seems to be no urgency to get it worked out.  I know that may not *actually* be the case, but a little blurb from someone that they are looking into the issue would really be nice.  I mean, at least they should know from user reports that there is a problem with networking that's causing the total lock-ups.  It would seem that from there it could be tracked down pretty easily???

Does anyone have perspective on how bugs on launchpad get dealt with?  It seems that total system freezes, on what seems like not an insignificant number of machines, would demand some fairly urgent attention.

---

### Post by rplantz on 2009-05-11
My freeze hocus pocus.

Two machines:
Desktop - amd64 3200; nvidia 5200 128MB graphicx; used several hours each day, shut down at night.
Laptop - Intel core 2 duo T5550; Intel x3100 graphics; used less than an hour a day.

No problems with beta 64-bit, all ext3 on either machine.

1. Installed released 9.04 on both machines; ext3 for /home and ext4 for /.

2. No problems for 2 weeks.

3. Installed Opera on desktop, freezes started.

4. Purged Opera, freezes continue.

5. Opened box and saw that the cooling fan on video card is broken. The actual blade wheel is broken in half.

6. Started using laptop several hours a day; one freeze.

All the rest refers to my desktop machine.

7. Bought and installed new nvidia 6200; freezes continued.

8. Reinstalled 9.04, still ext4 for /; freezes continued.

9. Reinstalled 9.04, but ext3 for /; freezes continued.

10. Opened box and reseated all connections (memory, disks, etc.), and it has been running all day now without any problems.

Okay, my experience with this sort of stuff goes way back to designing parts of the guidance system for the Gemini capsule and the LEM. I have a PhD in EE. So with great authority (;-)) I can conclude from all of this that the fan on my 5200 video board is broken! I taught CS at a university for 20 years and had trouble convincing most students that compilation errors are the easy-to-fix problems.

As an aside, a previous version of Ubuntu had lots of freeze problems. Mine went away when I opened my box and saw that the CPU heat sink was clogged with dust. I did a thorough cleaning and reseated all the connections.

---

### Post by madomac on 2009-05-12
> **brntoki said:**
> (...)
Does anyone have perspective on how bugs on launchpad get dealt with?  It seems that total system freezes, on what seems like not an insignificant number of machines, would demand some fairly urgent attention.

I'd like to second that post. First thing is that there seems to be no connection between this forum and/or this thread and the developers. So I think everyone with a freeze problem should open a bug report in launchpad or aubscribe to the existing one and add the information asked for (log files etc.)

Second things is: How do you escalate a bug report in launchpad? OK, the bug is confirmed now, but it has no level of importance. What can we do about this?

And last but not least: How can we support the developers to fix it? I'm happy to supply any information / log file and run tests as needed. At least as long as I stick to Jaunty. My system is completely unusable right now, so I might have to go back to Hardy in the next days.

---

### Post by anto1ne on 2009-05-12
After updating everything up to kernel 2.6.29-020629-generic and Nvidia driver 185.18.08, the freeze/crash stop.. but, the network would die after some time (integrated forcedeth). only reboot fixed the network.
Now changed the network card and disabled the integrated one, everything seems ok.
(amd x2, geforce 7300LE, jaunty x64)

---

### Post by starhalo on 2009-05-12
hi chaps,

im starhalo and im new to the forum. i already tried everything install from the cd, upgrade, disable wireless, switch to epiphany... it always crashes. its really annoying

its odd theres is no notice in the homepage

---

### Post by jerboyd on 2009-05-12
i reverted to ubuntustudio 8.1 because of the crashes and the other day had some spare time so i installed ubuntustudio 9.04 on a spare drive. i'm using the 64 bit and i installed on ext4. i previously had freezes with just about every configuration; ext3, ext4, raid0, single drive, with nvidia driver, without, etc. you get the point. these freezes were on a system that was using the 2.6.28-2-rt kernel. the kernel that came with my current installation is 2.6.28-3-rt. previously the freezes would happen within a half hour of boot but i've been able to run for a day or more with heavy network and disk activity with no problems. i might just try a real install.

the disk i used was from a recently downloaded iso file so it must have some updated packages on it, definitely the kernel is new.

i'll report back after i install.

jeremy boyd

---

### Post by rplantz on 2009-05-12
> **rplantz said:**
> My freeze hocus pocus.

Two machines:
Desktop - amd64 3200; nvidia 5200 128MB graphicx; used several hours each day, shut down at night.
Laptop - Intel core 2 duo T5550; Intel x3100 graphics; used less than an hour a day.

...............

9. Reinstalled 9.04, but ext3 for /; freezes continued.

10. Opened box and reseated all connections (memory, disks, etc.), and it has been running all day now without any problems.



11. Reinstalled 9.04 with ext4 for /. Kept ext3 for /home. No freezes for several hours.

---

### Post by waterfox on 2009-05-12
Since I did fresh install of 9.04 at release I have had regular freezes. Not experienced before on previous releases. I use the new ext4 and suspect this is the cause. The freezes have happened when I transfer files to an external HD and also several times when I try to delete the trashcan. If I rightclick the trashcan and delete then it's OK but when I open the trashcan and click "empty" it freezes. Except for this I have no cons with 9.04. But this is annoying. Maybe I should go back to ext3?

---

### Post by briggsb on 2009-05-12
I too am experiencing freezes in Jaunty.  Not using Ext4.  Didn't happen for over a day after I installed pre-release versions, but just got another freeze. Very frustrated. Booting into Windows instead seemed to fix the problem.

---

### Post by Mirge on 2009-05-12
> **briggsb said:**
> I too am experiencing freezes in Jaunty.  Not using Ext4.  Didn't happen for over a day after I installed pre-release versions, but just got another freeze. Very frustrated. **Booting into Windows instead seemed to fix the problem.**

I have to admit, that made me laugh lol...

---

### Post by brntoki on 2009-05-12
Would everyone who hasn't already, please go here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155) and, not to be too ranty, just put in a "Me too; would really like an answer/fix for this", comment.  For the life of me I don't understand how there cannot be a high priority assigned to this bug that is ***system debilitating***.

---

### Post by brntoki on 2009-05-13
OK!  User Madomac has made a fresh bug report to launchpad.  I'll link to it below.  The reason for the new report is that the old one seems it may be somewhat diluted due to people with slightly dissimilar problems reporting as well.

THIS NEW BUG REPORT is for those who have narrowed their issue down to networking ONLY!  We are hopeful to get the developers headed in the right direction on this and make their job a little easier.

Therefore, if you wish--and you really should wish--to subscribe to the bug and help towards a fix, please verify the following:

[INDENT]1. Can you work on the machine without freezing if you have disabled networking?  If you are stable without networking, and then upon re-enabling it the freeze returns, you are a good candidate for this bug report.
2. When your computer freezes, are you able to get out of the freeze with Ctrl+Alt+SysRQ, and after releasing only SysRq key, slowly typing R-E-I-S-U-B?  If not, you are probably a good candidate for this bug report.[/INDENT]

If this is you, please help with a fix by visiting this launchpad bug report and submitting your logs (submitting logs is easy... even I learned how).  Here is the new bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/375986](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/375986)

Thanks everyone.  And thanks to Madomac for taking the initiative on this.

---

### Post by LinuxStudio on 2009-05-13
Tried to upgrade from intrepid, didnt work. So download the jaunty image and did a fresh install. Setup Nvidia and compizfusion with twin view on my amd. It now randomly restarts especially when i try to get it to do anything. Intrepid was fine wtf?
Is there a fix?
I took a look at the syslog and it shows a restart. How does it have time to write a restart on a crash?
[http://ubuntuforums.org/images/smilies/icon_mad.gif](http://ubuntuforums.org/images/smilies/icon_mad.gif)

---

### Post by Allegretto on 2009-05-13
The freezes were making it impossible for me to get anything done, so I decided to nuke my 9.04 installation and go back to 8.04. Unsurprisingly, the freezes are totally gone now back on Hardy. It's a shame that Jaunty seems to be such a disaster on so many different hardware configurations.

---

### Post by LinuxStudio on 2009-05-13
they should not have released Jaunty untill the problem gets fixed.
if i roll back to intrepid will it still be updated?

---

### Post by GARoss on 2009-05-13
Lots of reading here!
My story is we have 3 computers, one is all Ubuntu 9.04 32 bit, one dual XP/Ubuntu 9.04 64 bit & one dual XP/Ubuntu 9.04 32 bit. Only the dual XP/Ubuntu 9.04 32 bit freezes. It is also the only one that I had to convert ext3 to ext4, which makes me think it has something to do with the conversion. 
The freeze occurs when printing or upgrades but we don't work with large files as others do, so can't comment on that. The mouse locks & cannot be unlocked; only reset. If lock occurs while printing, the printer will continue until its buffer runs out.

---

### Post by LinuxStudio on 2009-05-13
GAROSS

i am running a dual boot on separate hds 32bit that randomly restarts on me. Is it the dual boot 32bit thats the prob?

---

### Post by tweeek on 2009-05-13
Hello!

My computer is now unusable after installing Ubuntu 9.04. I have been using Ubuntu 7.10 to 8.04 on it, all have worked perfectly.

After boot it freezes in GDM after about 10 seconds. If I'm quick I can log in to the desktop, but after a few seconds logged in it freezes again. Completly unusable. Everything freezes, including my mouse and keyboard. The keyboard caps-lock and scroll-lock lights starts flashing.

My computer is an old Dell Dimension 8200, nvidia graphics. All components are really old and works flawlessly with Ubuntu 8.04.

I haven't read the entire thread. Are other people experience freezes like mine, freezes after a few seconds in GDM, for example?

---

### Post by GARoss on 2009-05-13
> **LinuxStudio said:**
> GAROSS

i am running a dual boot on separate hds 32bit that randomly restarts on me. Is it the dual boot 32bit thats the prob?
Yes. The DB XP/9.04-64bit & the 32bit 9.04 only (no DB) are fine. Both were installed with ext4 from the start. For what ever reason, ext4 wasn't an option when I installed on the DB XP/9.04-32bit so I converted it from ext3 to ext4 thinking it was no big deal. May it was.

---

### Post by DerGermel on 2009-05-13
Hello,

I suffered from this freeze too. Technical data:
GA-K8VT800 (Pro) motherboard with VIA K8T800 Chipset
CPU: AMD Athlon(tm) 64 Processor 2800+
Graphic: ATI Technologies Inc RV280 [Radeon 9200 PRO]
Network: Realtek Semiconductor Co., Ltd. RTL-8029
Ubuntu Jaunty + Kubuntu Jaunty + Ubuntu Studio with Realtime kernel (fresh install)

The freeze was clearly dependent on networking activities. Sometimes after minutes, sometimes after hours. I was able to reboot with REISUB.

I tried a few proposals from this thread without success as there are: Changing ATI drivers, installing kernel 2.6.30rc, ...

Finally I solved the problem for me by installing the 2.6.27 kernel (see this thread for how to do it 
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158))
Change all occurence of string 2.6.29 against 2.6.27 in the examples.

I'm rock-stable since 3 days now.

---

### Post by kaar3l on 2009-05-13
Same problem here

System
JHL90; NV 9600M GT; Intel 5100

I changed to 2.6.29 kernel for a test.

---

### Post by ladydeth666 on 2009-05-13
> **suresnjain said:**
> My system freezes totally after 10 minutes of idle time(time I have set for the screensaver).As soon as, this saver appears,the system goes into total freeze-and I mean total.This is particularly noticeable after 10 minutes of Rhythmbox play. Till, this bug gets fixed, I have found a temporary way out.Have launched an application on desktop-monitor off with command xset dpms force off.After I start Rhythmbox, I shut off monitor and the system does not go into freeze because screensaver does not appear.Today,i tried this one,and it was quite successful.Can someone suggest complete solution.Remember I am a newbie.:confused:

Are you using an nvidia card, suresnjain?  I used Synaptic to roll back my driver to 173 and my screensaver no longer locks my system up.  Send me a message or google if you are unsure of the procedure.

---

### Post by olskar on 2009-05-13
> **brntoki said:**
> Would everyone who hasn't already, please go here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155) and, not to be too ranty, just put in a "Me too; would really like an answer/fix for this", comment.  For the life of me I don't understand how there cannot be a high priority assigned to this bug that is ***system debilitating***.

Do NOT just add lots of "me too"-posts, that will only clutter the bugreport. 

Keep that kind of posts in this thread. Instead wait for a developer to ask you for information.

Edit: See the little link above the bugdescription, "This bug doesn't affect me (change)", please click that.

---

### Post by brntoki on 2009-05-13
> **olskar said:**
> Do NOT just add lots of "me too"-posts, that will only clutter the bugreport. 

Keep that kind of posts in this thread. Instead wait for a developer to ask you for information.

Well, I honestly do not want to make things any harder for the developers.  I did post a comment asking if anyone knew the workings over at launchpad.

It seems that they aren't too concerned about this, however, with it just sitting there with no priority assigned.  Again, just a little blurb that it's being looked into would help.  It's hard to help the devs with a system that is completely useless.  I mean, eventually I'd like to be able to actually work on my machine instead of leaving 9.04 there and making it a fancy paperweight.  I.E., it would be more beneficial for me to install 8.04 or 8.10 and just let others worry about it, but I figured that if everyone did that the developers would have a harder time.

At any rate, I don't want to make things go slower than they already are.  Though, honestly, wouldn't having more people post help them by allowing them to see the problem is on a larger scale than they perhaps realize?  Makes sense to me.  Maybe then they'd give some priority to this.

---

### Post by olskar on 2009-05-13
> **brntoki said:**
> Well, I honestly do not want to make things any harder for the developers.  I did post a comment asking if anyone knew the workings over at launchpad.

It seems that they aren't too concerned about this, however, with it just sitting there with no priority assigned.  Again, just a little blurb that it's being looked into would help.  It's hard to help the devs with a system that is completely useless.  I mean, eventually I'd like to be able to actually work on my machine instead of leaving 9.04 there and making it a fancy paperweight.  I.E., it would be more beneficial for me to install 8.04 or 8.10 and just let others worry about it, but I figured that if everyone did that the developers would have a harder time.

At any rate, I don't want to make things go slower than they already are.  Though, honestly, wouldn't having more people post help them by allowing them to see the problem is on a larger scale than they perhaps realize?  Makes sense to me.  Maybe then they'd give some priority to this.

I can surely understand your frustration, but clicking the "Affects me too"-link would have the same effect, they see what bug affects many people.


Earlier today I posted this to the bugsquad-mailinglist:

> I would argue that bug 355155 get a high priority following the
guidelines at [https://wiki.ubuntu.com/Bugs/Importance](https://wiki.ubuntu.com/Bugs/Importance).

This is a bug that makes a default Ubuntu installation generally
unusable for some users. One of the reporters say that he "experience
freezes within two or three minutes after booting".

That is what I would call generally unusable, and a lot of other people
are suffering from this.

Can any member of UbuntuBugControl please mark this as high priority?

---

### Post by brntoki on 2009-05-13
Olskar,

Super!  That's great that you know what to do.  I really didn't know and that's why I had posted to see who had any idea of what could be done to sort of escalate this. When I got no response I decided to do what I thought may work.  It sounds like you are more bug-report savvy.

Thanks for helping out by pointing out the "affects me, too", link, and the email you sent.

---

### Post by karamu on 2009-05-14
I seem to have some progress- after about five or six attempts to get into X when it completely froze I was able to run update manager successfully. Since then (two days and a few computing hours ago) it hasn't frozen at all. It did crash to (from X) to a non-usable command line screen (ie black with white text) which I have never experienced before with Linux but otherwise it is behaving so far.

So, things are obviously not 100% perfect but at least I can use my computer now. Fingers crossed it stays that way- I hope the others in this thread get somewhere too.

---

### Post by petrus4 on 2009-05-14
> **Stenico said:**
> 
Intrepid, Freebsd, Vista and Win7 all run on this machine without a hitch.

Despite the large and admirable community contribution Ubuntu is very much run by Canonical, with the clear aim of becoming profitable.

I should have known.  I've already said, however, that Ubuntu is by far the most poorly designed Linux distribution that I've ever seen, bar none.  It's absolutely appalling.

It is therefore entirely consistent and logical, based on both history and human nature, that Ubuntu will remain the most popular Linux distro, and Canonical will end up becoming insanely profitable.

We're watching the birth of the next Microsoft here, kids.  It almost brings a tear to my eye.

---

### Post by bearozo on 2009-05-14
Hello fellows! ):P

Back in Jaunty 9.04 alternate am64 with the 2.6.28-11 generic kernel and so far no freezes :D just watched the movie that allways gave me the freeze all the way through ([http://linuxcrypt.net/?p=255](http://linuxcrypt.net/?p=255)).  I tried Ubuntu studio 8.04.1 but it had issues with nVidia like messing with xorg, all of the sudden wastebasket applet crashed and would not start I could not add applets etc. when going into to terminal to edit conf files it did not respond to kbrd I could not edit at all ! so I tried some more distros but allways some issue :(
It all comes down to me being such a NOOB, I used an old non-plug and play monitor so I put HorizSync and VertRefesh into xorg.conf to get a better resolution which worked but there should have been more stuff
I think :tongue:. So I got another monitor with plug and play and things got so much easier, everything seems 
to work well so far (since yesterday evening) no freezes yet, compiz working fine etc. I am using the 180:53
nVidia driver (which did not solve the freeze problem earlier).

So for now I am a happy Jaunty user  :popcorn:

---

### Post by JEDIDIAH on 2009-05-14
> **Stenico said:**
> How many, alpha's, betas and RC's has Jaunty been through? And its still very broken on a lot of hardware.

I know its not an LTS, but that doesn't mean UI hard-freezes are acceptable surely?

How hard is it for Canonical to buy a bunch of commodity hardware and run standard tests before making releases? (I bet Dell/HP etc would donate boxes to them!)

Given my experience with Jaunty and other recent releases there is no way I can recommend Ubuntu as a "just works" distro as I used to do at one time.

I dunno. Maybe perhaps you should run the numbers yourself and get back to us rather than just running your mouth off about it. I don't think  you have the slightest clue what the scope of the problem is.

Then once you've come up with these numbers tell us what you are personally willing to pony up to help with the effort.

---

### Post by NoVista on 2009-05-14
I'm going to chime back in here, and hopefully not pre-maturely.
You can go back to my previous post to see my hardware and other notes.

I am not running proprietary drivers, and I use ext3.
The day before yesterday, there were updates available for mesa.
Since then I have not had one freeze. I have been stable ever since.

---

### Post by Allegretto on 2009-05-14
Hmm... I got rid of 9.04 a few days ago because of the freezing issues, but I managed to wreck the 8.04 installation I replaced it with via some ill-advised display driver tinkering, so I decided to give 9.04 another try. 

I installed it this morning, and the freezing issues I had with my last install are gone. I've not experienced one lock-up so far, even when performing tasks which were guaranteed to make it happen before (like opening Catalyst Control Center).

Perhaps the theory that a (very) recent update has fixed it (at least for some people) is correct.

---

### Post by Iusedtowearatie on 2009-05-14
No guarantees, but you could try my hint in this post:
[http://ubuntuforums.org/showpost.php?p=7276084&postcount=4](http://ubuntuforums.org/showpost.php?p=7276084&postcount=4)

---

### Post by dannyboy1121 on 2009-05-15
So here's an odd thing.....

After searching the net on this issue I found various possible causes and resolutions.

My resets were completely non uniform and appeared to be load related .. sometimes withing minutes of each other .. sometimes hours and other times over 24hrs.

I added a boot time option of 'clocksource=jiffies' ... now my machine still resets but only once a day ... it seems to be uniform but I'm still gathering data.

Crazy stuff. I think I'll try Iusedtowearatie's suggestion of acpi=off and see if it improves the situation any further.

---

### Post by brntoki on 2009-05-15
I "fixed" my problem by installing Linux Mint-6 x64 Edition with 2.6.27-14-generic kernel (Ubuntu 8.10 with different makeup).  The only thing that's worse than a broken Linux box is having to use Windows again.

So, life goes on...  Thanks for the memories ):P

---

### Post by NoVista on 2009-05-15
Well those updates fixed me.
Still stable, three days now.
Thank goodness.

---

### Post by dannyboy1121 on 2009-05-15
> **Iusedtowearatie said:**
> No guarantees, but you could try my hint in this post:
[http://ubuntuforums.org/showpost.php?p=7276084&postcount=4](http://ubuntuforums.org/showpost.php?p=7276084&postcount=4)


RE: acpi=off

Tried and died :(

---

### Post by dannyboy1121 on 2009-05-15
Three times in one afternoon ... ](*,)

---

### Post by bearozo on 2009-05-15
> **dannyboy1121 said:**
> Three times in one afternoon ... ](*,)

Do you have  a nVidia graphics card, do you have the latest updates ?

---

### Post by madomac on 2009-05-15
The last words of my kernel before the system froze point to the "iwlagn" module:

> May 15 16:52:33 ubuntutop kernel: [13354.757395] iwlagn: Microcode SW error detected.  Restarting 0x82000000.
May 15 16:52:33 ubuntutop kernel: [13354.808717] Registered led device: iwl-phy0:radio
May 15 16:52:33 ubuntutop kernel: [13354.808734] Registered led device: iwl-phy0:assoc
May 15 16:52:33 ubuntutop kernel: [13354.808749] Registered led device: iwl-phy0:RX
May 15 16:52:33 ubuntutop kernel: [13354.808764] Registered led device: iwl-phy0:TX
May 15 16:53:09 ubuntutop kernel: [13391.372757] wlan0: deauthenticated
May 15 16:53:09 ubuntutop kernel: [13391.372765] HW problem - can not stop rx aggregation for tid 0
May 15 16:53:09 ubuntutop kernel: [13391.384145] mac80211-phy0: failed to remove key (0, 00:21:e9:b7:d1:bf) from hardware (-22)
May 15 16:53:10 ubuntutop kernel: [13392.376060] wlan0: direct probe to AP 00:21:e9:b7:d1:bf try 1
May 15 16:53:10 ubuntutop kernel: [13392.382305] wlan0 direct probe responded
May 15 16:53:10 ubuntutop kernel: [13392.382312] wlan0: authenticate with AP 00:21:e9:b7:d1:bf
May 15 16:53:10 ubuntutop kernel: [13392.384603] wlan0: authenticated
May 15 16:53:10 ubuntutop kernel: [13392.384608] wlan0: associate with AP 00:21:e9:b7:d1:bf
May 15 16:53:10 ubuntutop kernel: [13392.394673] wlan0: RX ReassocResp from 00:21:e9:b7:d1:bf (capab=0x431 status=0 aid=2)
May 15 16:53:10 ubuntutop kernel: [13392.394677] wlan0: associated
May 15 16:53:10 ubuntutop kernel: [13392.397060] phy0: failed to restore operational channel after scan
May 15 16:53:20 ubuntutop kernel: [13402.397856] wlan0: disassociating by local choice (reason=3)
May 15 16:53:22 ubuntutop kernel: [13404.467327] phy0: failed to restore operational channel after scan
May 15 16:53:22 ubuntutop kernel: [13404.480088] wlan0: authenticate with AP 00:21:e9:b7:d1:bf
May 15 16:53:22 ubuntutop kernel: [13404.482030] wlan0: authenticated
May 15 16:53:22 ubuntutop kernel: [13404.482035] wlan0: associate with AP 00:21:e9:b7:d1:bf
May 15 16:53:22 ubuntutop kernel: [13404.488823] wlan0: RX ReassocResp from 00:21:e9:b7:d1:bf (capab=0x431 status=0 aid=2)
May 15 16:53:22 ubuntutop kernel: [13404.488827] wlan0: associated
May 15 16:53:22 ubuntutop kernel: [13404.511254] wlan0: authenticate with AP 00:21:e9:b7:d1:bf
May 15 16:53:22 ubuntutop kernel: [13404.514577] wlan0: authenticated
May 15 16:53:22 ubuntutop kernel: [13404.514582] wlan0: associate with AP 00:21:e9:b7:d1:bf
May 15 16:53:22 ubuntutop kernel: [13404.519634] wlan0: RX ReassocResp from 00:21:e9:b7:d1:bf (capab=0x431 status=0 aid=2)
May 15 16:53:22 ubuntutop kernel: [13404.519638] wlan0: associated
May 15 16:53:25 ubuntutop kernel: [13406.824296] phy0: failed to restore operational channel after scan
May 15 16:53:25 ubuntutop kernel: [13406.824356] phy0: failed to restore operational channel after scan
May 15 16:53:25 ubuntutop kernel: [13406.836770] wlan0: disassociating by local choice (reason=3)
May 15 16:53:25 ubuntutop kernel: [13406.912239] phy0: failed to restore operational channel after scan
May 15 16:53:25 ubuntutop kernel: [13406.913453] wlan0: authenticate with AP 00:21:e9:b7:d1:bf
May 15 16:53:25 ubuntutop kernel: [13406.917339] wlan0: authenticated
May 15 16:53:25 ubuntutop kernel: [13406.917347] wlan0: associate with AP 00:21:e9:b7:d1:bf
May 15 16:53:25 ubuntutop kernel: [13406.925218] wlan0: RX AssocResp from 00:21:e9:b7:d1:bf (capab=0x431 status=0 aid=2)
May 15 16:53:25 ubuntutop kernel: [13406.925221] wlan0: associated

---

### Post by zugol on 2009-05-15
Recent updates doesn'f fixe freeze problem.
Even with kernel 2.6.29.

---

### Post by utkjamie on 2009-05-15
I thought recent updates fixed this for me since I was able to go several days without a freeze. I got my hopes up too soon. Went out for a bit and returned to find my computer frozen. Rebooting now gives me *kernel panic* errors with:

```
Not syncing VFS: unable to mount root fs on unknown block (0,0)
```I can't even log into recovery mode now.

**UPDATE:** The problem for me is trying to boot with the 2.6.28-12 kernel. Not sure if it is the kernel itself or a bad kernel upgrade, but booting with 2.6.28-11 gets me back into the system.

---

### Post by Mirge on 2009-05-15
Just had another freeze... went over 24 hours without a freeze, went away from the comp for a bit to play some sweet SNES, came back & it locked up on me. No clue what is causing it either. Leaving top running so I can see MAYBE what the last process(es) were the next time it freezes that are taking up CPU if any are...

---

### Post by utkjamie on 2009-05-15
Does anyone know if this is Ubuntu-specific or if it is affecting other distros, too?

---

### Post by MacAlert on 2009-05-15
> **bearozo said:**
> Do you have  a nVidia graphics card, do you have the latest updates ?

I have an nvidia card in my desktop and have freezes whenever I try to load a page with Java. Now, on my laptop with an ATI card, there was an update (mesa as someone else had mentioned) and the same pages load fine when they froze previously.

---

### Post by NoVista on 2009-05-15
Well the mesa updates cured me. I would have froze by now.
Hope the rest of you work it out.
I'm on the 26.28-11 generic kernel by the way, ext 3.

---

### Post by MacAlert on 2009-05-15
> **NoVista said:**
> Well the mesa updates cured me. I would have froze by now.
Hope the rest of you work it out.
I'm on the 26.28-11 generic kernel by the way, ext 3.

Never mind. Figured it out.

---

### Post by Chemical Imbalance on 2009-05-16
> **utkjamie said:**
> Does anyone know if this is Ubuntu-specific or if it is affecting other distros, too?

Out of desperation, I just switched to Fedora 11 preview release and it works like a dream.

I'm using the .29 kernel with the 180.51 Nvidia drivers.

I still love ubuntu, but I need a working computer too ;)

---

### Post by karamu on 2009-05-16
I spoke too soon- after a few days of freezeless computing it happened again twice in a row- once after launching Firefox, the other just after login before X loaded.

This and the fact that Jaunty is only intermittently mounting my MP3 player (never had any problems before I "upgraded") is making me seriously think about going back to Ubuntu 8.

I thought it was only Windows that had these kind of problems- never had a crash in Linux until I changed to Jaunty......

---

### Post by jsday187 on 2009-05-16
Freezing in KDE very often for me. 
Haven't tried Gnome really but...

I also noticed that file transfers from my hard drive to a usbstick keep stalling too. Like a half hour to transfer a 1GB file.

PLUS after a freeze my wireless stops working, and wlan0 disappears so I have to run
```
# modprobe ath5k
```after rebooting to get that working again. This DOES NOT happen if I purposefully hard reset my computer when it ISN'T frozen though. I only checked once I swear!

Ok three times. 
But what's the difference if things all seize up every 10 minutes on their own anyway. ;-)

Anyone else having these problems on top of the freezes??
Sorry if you've already mentioned them, I couldn't read all 29 pages of this thread. dB^)

These freezes are accompanied by keyboard lock, plus pressing my power button once doesn't power things down nicely like it usually does either, so I have to hard reset to recover.

Funny thing is I've started using LXDE and now? No more freezes AT ALL!!! 
Plus it only takes a few minutes to transfer 1GB. 

WEIRD!!

It a Acer Aspire 4720Z laptop running Kubuntu 9.04.
Hard drive is formatted in _**ext4**_
grub**2** bootloader.
KDE is **4.2.3**

```

Linux jsday187-laptop 2.6.30-020630rc5-generic #020630rc5 SMP Mon May 11 15:03:39 UTC 2009 x86_64 GNU/Linux

vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Pentium(R) Dual  CPU  T2370  @ 1.73GHz

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

---

### Post by Mirge on 2009-05-16
I'm debating on switching to LinuxMint 6 (based on Ubuntu 8.10) or not until the Jaunty bugs get worked out. My freezing issue is pretty rare compared to some others, but still it's enough to be irritating as hell when I lose work.

---

### Post by brntoki on 2009-05-16
> **Mirge said:**
> I'm debating on switching to LinuxMint 6 (based on Ubuntu 8.10) or not until the Jaunty bugs get worked out. My freezing issue is pretty rare compared to some others, but still it's enough to be irritating as hell when I lose work.

Yeah; my freezes were very frequent; say no more than 30 minutes up time if I was lucky.  Often only 5 minutes or so before I had to hard reset.

Anyway, I'm just checking in for nostalgia.  I already went to Mint-6 and am very happy with it.  I decided not to stray too far from Ubuntu because it's what I know, though I'd like to some time give another distro, or three, a whirl.

---

### Post by connorh123 on 2009-05-16
Let's start from the beginning.
The reason why it froze for him, is because 3 weeks ago, Jaunty came out. So I'm assuming he downloaded it when everyone else did, and of course, it's going to lag/freeze up.

---

### Post by Mirge on 2009-05-16
> **brntoki said:**
> Yeah; my freezes were very frequent; say no more than 30 minutes up time if I was lucky.  Often only 5 minutes or so before I had to hard reset.

Anyway, I'm just checking in for nostalgia.  I already went to Mint-6 and am very happy with it.  I decided not to stray too far from Ubuntu because it's what I know, though I'd like to some time give another distro, or three, a whirl.

Bah, I downloaded the 32-bit version. Now I'm downloading the 64 bit version... the 32 bit live CD looked pretty decent. We'll see how it turns out.

---

### Post by Mirge on 2009-05-16
Well Linux Mint 6 looks better out of the box, but it's also giving me some issues... now I'm leaning towards wiping out Linux Mint 6 in favor of Ubuntu 8.10.

---

### Post by dannyboy1121 on 2009-05-17
> **bearozo said:**
> Do you have  a nVidia graphics card, do you have the latest updates ?


No .. I'm running this as a server from console without X.

---

### Post by dannyboy1121 on 2009-05-17
Although we have 30 pages of complaint here .. I'm still no clearer whether this is perceived as a major or minor issue in Ubuntu land.

Has a bug report already been raised on this subject? What's the process here?

Although this is causing me massive issues - I refuse to jump ship without having a good go at working this out.

I want to pump up the volume with the debugging but as my system is PXE booted (i.e. the disk is sitting on the network) - when things die - the chances are that I don't get anything written in to the logs. To try and get round this, I've amended my logging to write out to the console ....

So far I've captured nothing unexpected. Sysrq will allow me to reboot and that's it!

How can I crank up the verbosity of the logging to try and catch this?

Help me Obi Wan ....

---

### Post by olskar on 2009-05-17
> **dannyboy1121 said:**
> Although we have 30 pages of complaint here .. I'm still no clearer whether this is perceived as a major or minor issue in Ubuntu land.

Has a bug report already been raised on this subject? What's the process here?

Although this is causing me massive issues - I refuse to jump ship without having a good go at working this out.

I want to pump up the volume with the debugging but as my system is PXE booted (i.e. the disk is sitting on the network) - when things die - the chances are that I don't get anything written in to the logs. To try and get round this, I've amended my logging to write out to the console ....

So far I've captured nothing unexpected. Sysrq will allow me to reboot and that's it!

How can I crank up the verbosity of the logging to try and catch this?

Help me Obi Wan ....

Here is a bugreport.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155)

I have tried mailing the bugsquad on their mailinglist without any sucess. I started this thread three weeks ago and we haven't got a lot further. It seems releated to networkactivity (for most people), deactivate network and freezing stops.

If you want, or anyone else, you can enter #ubuntu-bugs to try to get some attention to the bug. My attempts to do that have failed. Good luck!

And may the force be with you ;)

---

### Post by bstanley on 2009-05-17
> **dannyboy1121 said:**
> Although we have 30 pages of complaint here .. I'm still no clearer whether this is perceived as a major or minor issue in Ubuntu land.

Has a bug report already been raised on this subject? What's the process here?

Although this is causing me massive issues - I refuse to jump ship without having a good go at working this out.

I want to pump up the volume with the debugging but as my system is PXE booted (i.e. the disk is sitting on the network) - when things die - the chances are that I don't get anything written in to the logs. To try and get round this, I've amended my logging to write out to the console ....

So far I've captured nothing unexpected. Sysrq will allow me to reboot and that's it!

How can I crank up the verbosity of the logging to try and catch this?

Help me Obi Wan ....



========================================================================

Hi!
I have been having freeze problems with Jaunty also but now it seems I
have resolved the problem on my system.

I am using an ABIT KT7A Mother board with an ATI Radeon 7000/VE Rv100qy
Video card. The driver being used is the open source radeonfb driver.

I solve the problem by changing the xorg options in the /etc/X11/xorg.conf
file.
I replaced the following entry for by video card:

            Section "Device"
                  Identifier      "Configured Video Device"
            EndSection

 with:
            Section "Device"
                 Identifier      "Radeon 7000"
                 Driver          "ati"
                 Option          "BusType" "PCI"
                 Option          "AGPMode" "1"
            EndSection

Notice that I no longer allow Xorg to auto configure the driver and
the two option values were suggested as a freeze fix on the Xorg website
for systems having opengl freeze (an other freeze proglems).

I thing that the "AGPMode" "1"  line may be turning bus mastering mode
off on the video card.  I know that my motherboard does have a problem 
with freezes with any card running in that mode regardless of the OS being
used.  This may not help anyone here, but it's worth a try.

The driver for may system being loaded with the 'Driver "ati"' line is
the open source  "radeonfb" driver.

Hope this helps!

:D

---

### Post by Mirge on 2009-05-17
Haven't had another freeze yet... day or so... maybe 2 days now. I'm starting to heavily lean towards Flash being a potential culprit for my particular case. Each time it's frozen I've had Pandora loaded for a long period of time... and I haven't had pandora loaded at all since the last freeze, and no freeze yet. It's a long-shot, but I'm gonna fire up Pandora again tomorrow & see what happens.

---

### Post by rop962 on 2009-05-18
After upgrading from 8.10 to 9.04, my Dell-Notebook (Intel Graphic Chip: GM965/GL960) freezes regularly, when I'm using firefox for browsing. All other applications don't freeze the desktop. After changing to Opera for browsing the internet, the notebook is working without any problems. Maybe there is an issue with firefox too.

---

### Post by jsday187 on 2009-05-18
> **bstanley said:**
> ========================================================================

Hi!
I have been having freeze problems with Jaunty also but now it seems I
have resolved the problem on my system.

I am using an ABIT KT7A Mother board with an ATI Radeon 7000/VE Rv100qy
Video card. The driver being used is the open source radeonfb driver.

I solve the problem by changing the xorg options in the /etc/X11/xorg.conf
file.
I replaced the following entry for by video card:

            Section "Device"
                  Identifier      "Configured Video Device"
            EndSection

 with:
            Section "Device"
                 Identifier      "Radeon 7000"
                 Driver          "ati"
                 Option          "BusType" "PCI"
                 Option          "AGPMode" "1"
            EndSection

Notice that I no longer allow Xorg to auto configure the driver and
the two option values were suggested as a freeze fix on the Xorg website
for systems having opengl freeze (an other freeze proglems).

I thing that the "AGPMode" "1"  line may be turning bus mastering mode
off on the video card.  I know that my motherboard does have a problem 
with freezes with any card running in that mode regardless of the OS being
used.  This may not help anyone here, but it's worth a try.

The driver for may system being loaded with the 'Driver "ati"' line is
the open source  "radeonfb" driver.

Hope this helps!

:D

Ah yes, this could be my problem. I forgot to mention I was getting xorg errors on every boot requiring me to run ubuntu in "low-graphics mode." Although, the graphics did not appear any different to me at all.

I just did a format and re-install this time with gnome/ubuntu) instead of kubuntu and have already experienced one freeze.

---

### Post by Mirge on 2009-05-18
> **Mirge said:**
> Well Linux Mint 6 looks better out of the box, but it's also giving me some issues... now I'm leaning towards wiping out Linux Mint 6 in favor of Ubuntu 8.10.

Ditched Linux Mint 6 to install Kubuntu 9.04...I definitely think it looks better right out of the box than Ubuntu 9.04 (granted, essentially gnome vs kde)... even my wife complimented it.. which is way rare haha. She wants to try Kubuntu now and she's only ever used Windows. So far no freezing or anything bad really.. except sound issue, and it DOES seem to be a tad slower than gnome.

EDIT: sound issue was "PCM" was all the way down. I am thoroughly enjoying Kubuntu 9.04 so far.

---

### Post by gtc803per on 2009-05-18
I was having this exact same problem, but I've solved the issue by reading the posts here. I'm glad I found this site!

---

### Post by Mirge on 2009-05-18
> **gtc803per said:**
> I was having this exact same problem, but I've solved the issue by reading the posts here. I'm glad I found this site!

If you're talking about the freezing issue, please specify exactly what worked for you to help others in the future.

---

### Post by dannyboy1121 on 2009-05-18
It seems likely that we're experiencing more than one bug ...

Mine appears to happen most under network load. I had 26 hours uptime ... then sent a mail with a large attachment via the server (it runs postfix) ... and it keeled over.

Just thinking out loud here ... I have an Atheros nic - and at some point after kernel 2.6.27 support was added for Atheros. I wonder if it's buggy. Hmmmmmm that's science.

Just curious if anyone else with freezing issues is running with an Atheros nic.

---

### Post by oblio9 on 2009-05-18
I am experiencing the freezing as well. Also seems to only be when downloading. To get thru the first batch of updates after install it froze on me four or five times. My hardware:

evga 590 sli motherboard
AMD X2 4600
3 GB of RAM 2 sticks Corsair one stick no name
Dual monitors on an EVGA 7900 gs
Single 320 GB Hard drive WD I think
M Audio 2496 soundcard

Edit: In case it is relevant: I have Windows 7 RC1 on this same drive. Originally it used the whole drive but I used Windows built repartitioner to shrink the volume it is on.

---

### Post by Chemical Imbalance on 2009-05-18
> **dannyboy1121 said:**
> It seems likely that we're experiencing more than one bug ...

Mine appears to happen most under network load. I had 26 hours uptime ... then sent a mail with a large attachment via the server (it runs postfix) ... and it keeled over.

Just thinking out loud here ... I have an Atheros nic - and at some point after kernel 2.6.27 support was added for Atheros. I wonder if it's buggy. Hmmmmmm that's science.

Just curious if anyone else with freezing issues is running with an Atheros nic.

I agree that there seems to be multiple bugs present in this thread. 
Not all of us (at least me) seems to have this network thing going on.
Uninstalling the nvidia drivers solved the problem for me.
Network didn't seem to affect it.  Often my pc was idle when it hit.

Fedora solved the problem for me, so I guess I'll check back with the next release of Ubuntu in october.

I filed a bug report and replied to another.  
That's all I can really do right now.

---

### Post by night-wing on 2009-05-19
For me, using the madwifi - driver for my atheros AR5006 seems to help in jaunty.

What I do not understand, is, that when I use the same (2.6.28-12) - Kernel in intrepid, I do not have any freeze!

For me personally, it's better to use intrepid and I will go back to it. The open source ati driver is still not fast enough for me and in intrepid I can use the proprietary ati driver.
(I have an X1250 internal and this card is now "legacy supported" in jaunty by ati - what means-> no proprietary driver anymore.)

Maybe karmic will be better. Except the 2.6.28er - Kernel (which I also can use in intrepid) there are no benefits for me in using jaunty. So let's stay on intrepid.

---

### Post by bearozo on 2009-05-19
Still no freeze since my post here: [http://ubuntuforums.org/showthread.php?t=1135055&highlight=jaunty+freeze&page=27](http://ubuntuforums.org/showthread.php?t=1135055&highlight=jaunty+freeze&page=27) I am using the 2.6.28-11 generic kernel and will not upgrade for a while.

---

### Post by Mirge on 2009-05-19
I booted back into Ubuntu 9.04 yesterday, about an hour of Pandora going, comp locked up. Ran for a few hours before that without pandora with no freezing. Booted back into Kubuntu 9.04 (which I love, btw)... pandora loaded all the time, no freezing at all. I installed Kubuntu 9.04 on one of my laptops as well. About to do the other laptop here in a minute.

It did strike me as odd though that the Migration Assistant only seems to work for me in Ubuntu, not in Kubuntu during install. Sucks, but oh well. Beats freezing.

---

### Post by kimda on 2009-05-19
I have had four complete lockups after converting my ext3 filesystem to ext4. These lockups would occur when I started up more than one program at once (ex. firefox and evolution and/or nautilus). Also I noticed this behavior when deleting big files or movind big files in nautilus. After searching the internet on this bug i found some posts suggested upgrading to a newer kernel. So i have installed the latest karamic kernel. Hopefuly this fixes this annoying prolem because i havbe never experienced this behavior with ext3.

---

### Post by Mirge on 2009-05-19
> **kimda said:**
> I have had four complete lockups after converting my ext3 filesystem to ext4. These lockups would occur when I started up more than one program at once (ex. firefox and evolution and/or nautilus). Also I noticed this behavior when deleting big files or movind big files in nautilus. After searching the internet on this bug i found some posts suggested upgrading to a newer kernel. So i have installed the latest karamic kernel. Hopefuly this fixes this annoying prolem because i havbe never experienced this behavior with ext3.

Yeah I've heard of this exact behavior pretty commonly, which stinks because I am using Ext3 filesystem and I really want to use Ext4. The laptops which I put Kubuntu 9.04 are using Ext4 and with less powerful hardware and less RAM, they are faster on most aspects! Maybe when I get some downtime from work I'll just back everything up & wipe it clean & install on Ext4 on my work PC. Due to all of the complaints I'm hearing like yours, I refuse to try to convert to Ext4.

---

### Post by dannyboy1121 on 2009-05-19
> **bearozo said:**
> Still no freeze since my post here: [http://ubuntuforums.org/showthread.php?t=1135055&highlight=jaunty+freeze&page=27](http://ubuntuforums.org/showthread.php?t=1135055&highlight=jaunty+freeze&page=27) I am using the 2.6.28-11 generic kernel and will not upgrade for a while.

What made you select 2.6.28-11 ?? I'll compile myself a new K if there's a chance it would clear up this mess.

---

### Post by bearozo on 2009-05-20
> **dannyboy1121 said:**
> What made you select 2.6.28-11 ?? I'll compile myself a new K if there's a chance it would clear up this mess.

That is the kernel which came with the  9.04 alternate am64 distro.

---

### Post by magicke on 2009-05-20
got an acer 4530 (amd64, geforce9100MG) set up with Jaunty 9.04 installed from an alt dist (2.6.27-7-generic (buildd@yellow)), with all the current updates. video driver is nvidia 180.44.

Soon after i enabled normal video effects and upgraded firefox from 3.0 to 3.05, the acer would freeze at random times, and application/applet windows would randomy close. Firefox would freeze also whenever i would start manually typing a url in the address bar.

After a few restarts and reviewing the logs (couldn't find anything out of the ordinary), i disabled all visual effects and disabled the ubuntu extensions for Firefox.

3 hours after, my acer's still running without freezing up.

Just sharing my firsthand experience with all this freezing up. Sorry, I ain't a linux techie so I cant suggest any fixes and stuff :D

peace ^^

---

### Post by utkjamie on 2009-05-20
Two more freezes for me today, both within 20 minutes of each other. I'm using Ext4 and this time the freeze destroyed my Firefox profile, so instead of working today I get to rebuild the profile.

Does anyone know if this is affecting other distros? I've been dealing with this problem for weeks now and losing data is too much of an unacceptable risk. If this is an Ubuntu/Kubuntu-specific problem, it may be reason enough for me to drop this distro after more than 2 years and use one that doesn't make me cringe every time I sit down to use my computer.

---

### Post by kimda on 2009-05-20
I've been running Ubuntu with the karmic kernel for two days now and its been stable like before with ext3, so utkjamie try installing the karmic kernel instead of the latest jaunty kernel. if you run proprietary drivers like me with my nvidia videocard you might want to install the nvidia drivers aswell from karmic. I do not know why they do not release the 2.6.30 kernel for jaunty. It would probably fix all these problems.

---

### Post by Chemical Imbalance on 2009-05-20
> **utkjamie said:**
> Two more freezes for me today, both within 20 minutes of each other. I'm using Ext4 and this time the freeze destroyed my Firefox profile, so instead of working today I get to rebuild the profile.

Does anyone know if this is affecting other distros? I've been dealing with this problem for weeks now and losing data is too much of an unacceptable risk. If this is an Ubuntu/Kubuntu-specific problem, it may be reason enough for me to drop this distro after more than 2 years and use one that doesn't make me cringe every time I sit down to use my computer.

Fedora 11 fixed it for me.  Give it a go if you have the time.

---

### Post by dannyboy1121 on 2009-05-21
> **Chemical Imbalance said:**
> Fedora 11 fixed it for me.  Give it a go if you have the time.

This has been so painful for me that I'm currently migrating my systems to a different distro - not out of spite or anger - purely because I can't deal with rebooting my server several times a day. I thought about pure Debian but ended up going for a complete change and have started moving to CentOS. I will be using the same custom Kernel though to see if the problem follows the Kernel or stays with Ubuntu.

In the event this gets fixed - I'm sure I'll come back. Ubuntu has been great for several years. Shame this issue is so nebulous.

---

### Post by bearozo on 2009-05-21
Anyway I went ahead and installed/upgraded to 2.6.28-12 and it seems fine so far no freezes yet and I tried the instruction movie mentiond a few times and it is all fine, will report in if I have a freeze.

---

### Post by zugol on 2009-05-21
One freeze in one week since I change to 2.6.29, but no specific module suported like my VFD display... Can this kind of specific module cause my freezes ?...

Anyone has a VFD ? (iMon for exemple)

---

### Post by madomac on 2009-05-23
Finally solved the problem - by switching to ArchLinux. :( Sorry guys, maybe I'll come back for Ubuntu 10.04 LTS.

---

### Post by daponz on 2009-05-23
Same problem here, I get random freezes several times a day... This is very annoying. I think I'm gonna switch back to intrepid or a pure Debian.
Using Ati proprietary driver, flash and ext4 file system (only for / not for /home) if it can help.

---

### Post by madone1 on 2009-05-24
I am really pissed off because officially every thing is working grate in Ubuntu but the truth is that the latest edition is freezing on at least 30% of PC. And Canonical haven't  honesty to admit that and say what is doing and when will fix problem.

When something is bad in Ubuntu guilty is community and for every thing good responsible is Canonical.

Ubuntu is stable, yeah right

---

### Post by mannequin on 2009-05-24
I'm getting lockups, but only with gnome-screensaver.  I've never liked that package since they introduced it anyway...  I might go back to x-screensaver and just rename gnome-screensaver the way I did oh-so-many years ago.

Anyway, I haven't reported it because I cannot find a predictable way to get it to lock the machine up other than running it.

---

### Post by utkjamie on 2009-05-24
> **daponz said:**
> Same problem here, I get random freezes several times a day... This is very annoying. I think I'm gonna switch back to intrepid or a pure Debian.
Using Ati proprietary driver, flash and ext4 file system (only for / not for /home) if it can help.

I hear you. I've been a Kubuntu user since Edgy (2.5 years?) and I am so fed up with this bug rendering my system unstable that for the first time I'm giving serious consideration to dropping Ubuntu for good and moving to a distro that doesn't leave me cringing every time I open an app for fear of a freeze. I've had my fill of data loss as the result of these freezes and I've seen nothing to indicate that this problem is being addressed or even acknowledged as a serious problem. I feel like Jaunty is an unstable beta and we're all waiting for the stable release. I've lost a lot of respect for Ubuntu over this mess.

Debian is top of my list as a possible replacement. I'm in the middle of a big project so I haven't had a chance to play with it but if these freezes continuing screwing up my work schedule, I may not have a choice. If you switch to Debian, drop me a line and let me know how it goes. I'm using an ATI video card, too, so I'm curious to know how that works out. Thanks in advance!

**NOTE:** Just to see how big this problem is, take a look at some of the comments about this problem being made on Twitter at [http://bit.ly/111eNn](http://bit.ly/111eNn). The first page alone has several people talking about dropping Ubuntu for another distro.

---

### Post by AlterEgo on 2009-05-24
I solved my freeze-problems....by migrating to Debian Testing.

---

### Post by gillmt on 2009-05-24
I have two boxes - both AMD 64, both running Jaunty. One is perfect, the other keeps locking up - keyboard and mouse - can't get anything helpful from logs other than npviewer segfault and clock tsc unstable (unfortunately I can't even find a common theme - sometimes I'm using FF and once I was deleting documents in Nautilus).

I tried to get some help on Launchpad - don't know if people are too busy.

When Jaunty works, it's great!

---

### Post by utkjamie on 2009-05-24
> **AlterEgo said:**
> I solved my freeze-problems....by migrating to Debian Testing.

Switching to another distro seems to be the only common solution I've found.

---

### Post by Chemical Imbalance on 2009-05-24
I found out something today.

Ubuntu isn't the only distro freezing.

I recently switched to Fedora-- and the freezing began a few days ago on it too!  It was the 11 preview release fully updated.

So, since I missed Ubuntu, I switched back to Jaunty to test out again, and I learned something else.  
Before, I assumed that the problem was with the nvidia drivers, but right after I reinstalled Jaunty (before having any chance to install the nvidia drivers) it froze on me!  The same freeze I've been getting.
But the important thing is that it happened right after I plugged in a wireless usb adapter.  

Maybe this *is* a network problem after all.  And it appears to be cross-distro too.

---

### Post by Mr.Banana on 2009-05-25
I have started experiencing freeze-ups too. I have been playing Nexuiz, Ubuntu freezes, restarted. Couple hours later, I'm browsing the net in firefox, freeze. I cant even move the mouse. 

Most often it happens in firefox for some reason, without any warning, just a sudden freeze, and everything stops working, and I cant even drop to CLI, nor I can restart X. Nada. 

While at the same time this same PC can run windoze for days.

---

### Post by Beigeman on 2009-05-25
I'm getting some rather frustrating freezes too. I have 9.04 on my laptop. (64-bit, ext4, dual boot with XP pro) and that works without a hitch.

My desktop on the other hand is an older machine. (Single core 1.8Ghz AMD, 1GB RAM, Nvidia 6200 graphics). I tried installing 8.04 and 8.10 on it and the always froze when trying to load the live disk (usually right before the end it would just lock up). I figured 9.04 might work, and it did.... sort of.

I was able to install it, (with ext3 initially) however after a few minutes on the desktop it just freezes. I can't run updates because I've not actually had it running for more than 5 minutes without freezing.

I tried reinstalling with ext4 instead, and it does exactly the same. With people here saying it might be networking related I'm wondering if removing the PCI wireless card I have in it, and trying to use a little Belkin USB stick might make some difference.

Can't hurt to have a bit of a play.

Edit: Nope... that failed miserably. It lasted a bit longer this time though... I get much slower speeds with the stick. Could it have something to do with how much data is received over the network?

---

### Post by extreme_blue on 2009-05-25
I am experiencing a freeze after opening certain applications:
firefox - lets me browse for a few minutes and then freezes
funamboladmin - sometimes freezes right away, sometimes freezes after logging in
I haven't really tried opening other applications.

Here's the video info, but I think it's happening across the board on different video cards:
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800   Pro]

I have this "system freeze" in KDE as well as Gnome. My mouse cursor still moves, but other inputs are dead.

I can ssh into my box from another system and I see that Xorg is at 95% or higher CPU usage. I can't stop the kdm service, I can't reboot (it just hangs and then I can't get back into the system).

This was a fresh install on a new system. I did not have the freezing issues until I did a safe-upgrade with aptitude about a week ago (I'm guessing).

Hope this helps in some way.

---

### Post by Fator dee on 2009-05-26
> **extreme_blue said:**
> I can ssh into my box from another system and I see that Xorg is at 95% or higher CPU usage. I can't stop the kdm service, I can't reboot (it just hangs and then I can't get back into the system).


I'm having the same problem as you, freeze happens few seconds after login, though I have an Nvidia GF6600GT, I am able to use the system with vesa-drivers, nv and nvidia freeze the system.
And killing the X by doing "sudo /etc/init.d/kdm stop" you can get it into working order to get logs.

---

### Post by utkjamie on 2009-05-26
> **Chemical Imbalance said:**
> Ubuntu isn't the only distro freezing.

Even if that is the case, it doesn't explain (and someone correct me if I'm wrong) why Canonical has failed to even acknowledge that this problem exists, much less that it is a very serious problem for a large number of users. I think Canonical's reputation may take a hit when the dust settles on this one. I've come across a lot of Ubuntu users saying that they have already switched to new distros. 

Here's a quote I found on [bug #355155]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155/comments/130"):
> 
Jaunty is a pile of sh*t for me so far. And there seems to be very few
new updates coming????? Has Canonical gone bankrupt? Are they still
working? Where are they? Who are they? What is Ubuntu? And does it have
a future?

---

### Post by agniruc on 2009-05-27
> **extreme_blue said:**
>  I have this "system freeze" in KDE as well as Gnome. My mouse cursor still moves, but other inputs are dead.


I have exactly the same problem.

After some upgrades, I got the feeling the freezes became more spaced, but I have not been able to relate them to any specific software (for some time, I thought that something in kdeapps or firefox was causing the freezes, though).

Since I had to work with that computer, I decided it was a good moment to test other distros. I installed OpenSuse with kde and everything worked fine. After some period testing it, though, I decided that it was an easier solution for me simply installing Kubuntu Intrepid Ibex, and that's what I did.

So, I'm back to Intrepid and it is working fine.

---

### Post by bryncoles on 2009-05-27
canonical mention this issue here:

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

scroll down and you'll see an entry for performance regressions and freezes under intel chipsets. they recommend shutting off compiz, which ive tried (reverted to metacity) and so far, so stable (touch wood). 

not sure why the bug report isnt critical though...

its good (i suppose) to hear the bug affects other distros though, means more people will work on it, and who knows, it may even get fixed!

given that i can work without compiz, and other than freezing jaunty is a nice distro for me, ill wait this one out... unless i get a freeze with metacity now!

---

### Post by Beigeman on 2009-05-27
I managed to get 9.04 running by removing a lot of my aftermarket hardware and just stripping it down to the simple basics. 

My freezing seems to be a bit different to that most people were getting. (As mine usually froze within 30 seconds of startup every single time I booted up).

I'm beginning to suspect it *might* have been the fact I had two 512MB sticks of RAM. One was a crucial running at 400mhz, one was Kingston running at 333Mhz.

Anyone more in the know able to tell me if that would make a difference or am I just crazy? :P

Edit: Stuck my Edimax Wireless card back in, just made it through an entire update. (Been running about 15 minutes without a freeze.) Next step is to put my Nvidia graphics card back in, and my second burner.

Edit2: Graphics and CD drive are back in. Seems like it was the RAM. No freezes since removing it.

---

### Post by vincent orange on 2009-05-27
after a week of head scratching I'm happy that I've found this thread. I've got Juanty running on my mother's computer. She alerted me that the machine would freeze and restart seemingly all on its own. I tried stripping the machine down to it's basic componets and have turned off the compiz effects. It seemed to do the trick but isn't really a long term solution to have to reopen a machine and fiddle with the hardware and software.

I'll stick with the LTS releases in future.

---

### Post by Fudgey05 on 2009-05-27
I would suggest kernel update to fix this problem, new versions available here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

I'm running v2.6.30rc7, and it seemed to work untill i reinstalled NVidia drivers, which leads me to think that they have some part to play in this after all

---

### Post by jack24 on 2009-05-27
It seems to be a problem with the latest kernel upgrade.  Something is making the clock unstable which eventually leads to a freeze.

The solution that seems to work best is to use a different kernel.  Some people have reported good luck going backwards.  I'm going to try using a newer generic kernel.

I posted about this a few days ago here: [http://ubuntuforums.org/showthread.php?t=1170811&highlight=jaunty+locks](http://ubuntuforums.org/showthread.php?t=1170811&highlight=jaunty+locks)

The post includes the bug reports that seem to be related to this.  I've been monitoring them hoping for a fix, but nothing yet.

jack

---

### Post by duanerobertson on 2009-05-27
My desktop system, based on a cheap Intel motherboard/CPU and an old nVidia 77xx card, would lock up repeatedly after installing 9.04 and reformatting all but the home partition as ext4. There was no indication in the logs that anything had happened, and no warning that the clocksource was unstable at any time. The system stopped responding in any way. Sysreq commands did not work, nor did restarting X.

I tried a number of different suggestions, but in the end, the problem seems to have been the ath5k driver for my PCI wifi card (I tried the proprietary version as well--no help). When I disabled the card and started using a spare Dlink usb-based wifi adapter, the lockups stopped immediately, and I've been running the system for 24 hours with no problems, even after deliberately trying to provoke a freeze. I've stressed the network, the CPU, and the video system without issues. I also repeatedly disabled/enabled networking, which seemed to be the surest way to cause a lockup before.

I should also mention that I'm not using the proprietary nvidia driver in this case.

---

### Post by bstanley on 2009-05-28
> **extreme_blue said:**
> I am experiencing a freeze after opening certain applications:
firefox - lets me browse for a few minutes and then freezes
funamboladmin - sometimes freezes right away, sometimes freezes after logging in
I haven't really tried opening other applications.

Here's the video info, but I think it's happening across the board on different video cards:
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800   Pro]

I have this "system freeze" in KDE as well as Gnome. My mouse cursor still moves, but other inputs are dead.

I can ssh into my box from another system and I see that Xorg is at 95% or higher CPU usage. I can't stop the kdm service, I can't reboot (it just hangs and then I can't get back into the system).

This was a fresh install on a new system. I did not have the freezing issues until I did a safe-upgrade with aptitude about a week ago (I'm guessing).

Hope this helps in some way.


=========================================================================

Hi!   I made a post to this thread a few days ago concerning freeze problems and compiz.

If you are running compiz (I believe it is on by default when you first
install the system), and having freeze problems,  the xorg website suggest
trying a couple of option modes to your xorg.conf file.

Have you tried them?  (see my prior post).

I do believe you have to change the device statement form auto config
mode to specifying your actual video card and the driver name you are
currently using.  

This suggestion from xorg was not video card specific.  It could help
ATI or nvidia cards.

---

### Post by zugol on 2009-05-29
I'm using "kernel-team" package version 2.6.29u4 and I have encounterd the freeze only ONE time in a week. I think changing kernel or video driver does'nt actually fix the freeze but it fixe a several problems that lead to this freeze/crash.

Remerber that it's Karmic UDS... So no ubdate for the moment...

---

### Post by pilbender on 2009-05-30
I'm an old school Slackware user.  I've used Slackware at work at a previous job.  I defected from Windows when Windows Me came out so I never used Windows XP outside of a corporate issued laptop.  Last November, 2008, I switched to Kubuntu 8.10 when my Windows XP installation started crashing and corrupting data.  I figured since they hadn't gotten Windows XP stable by now, it would probably never would be.

I was very happy with Kubuntu 8.10 and I was very impressed with all the things that work right out of the box with no configuration effort.  Kubuntu is slow compared to Slackware but it was still much faster than Windows XP was on the same computer.

Then I upgraded to 9.04 a few weeks ago.  I was pleasantly surprised when I shut the laptop lid and suspend worked flawlessly.  That's never been the case with *any* Linux install I've ever used.  I still use Slackware on all my other systems except for my work computer, which is uses Kubuntu.

The random freezes started shortly after the upgrade.  I figured I had a hardware issue at that point because I've never seen anything like this in *any* Linux install in 14 years.  After some research and finding this thread, I don't believe that's the case.

I get freezes at least once a day but usually several times a day.  It's not so bad that I can't work on the system so I haven't switched distributions yet.  I can always shutdown the system with <Ctrl> <Alt> <SysRq> <R> <E> <I> <S> <U> <B> but nothing else responds.  The mouse still works but the display clock is frozen.  I have the clock configured to show seconds, so when the seconds stop ticking by I know the dreaded hard freeze has occurred.  Once in a while I have to fsck the file system on install media to get it to boot again.  This is the ext 3 filesystem.  This is the same file system I use on 3 Slackware systems with obsene uptimes, so I see no reason to believe there's a problem with it.

The freezes are completely random.  I have found no pattern at all.  Sometimes the laptop is hot, sometimes cold.  Sometimes it happens with wireless turned off, sometimes on.  Sometimes it happens during boot up and sometimes I've been loading the system hard all day during development.  I see no pattern *at all*.  

Laptop specs:
Dual core 2.0GHz Intel Centrino processor
4GB of RAM
Dell Latitude D630

I think all the other specs are red herrings.  I don't think they have any affect because I've disabled other things and nothing has helped.  Be it wireless, graphics or whatever.

I then installed Kubuntu 9.04 on an old HP laptop with a Turon 64 bit *single core* processor.  This laptop has been flawlessly stable.  I've used KDEnLive to render several movies, surfed he net endlessly, put it into supsend and shut the lid, done heavy devlopment on it and it is stable as a rock.  With video rendering, it gets hammered for hours at a time in my 100 degree F office and it has no issues.  This is the exact same 64 bit distribution that the dual core system uses.

I am inclined to believe this has something to do with the dual core processor.  It is the only thing different that makes sense based on reading everything on this thread.

I'm very upset with the freezes.  I've stopped recommending this distribution to anyone.  I don't want people to have a bad experience with Linux.  I am going to give this as much time as possible to get resolved.  That is going to be based on my needs of getting my work done at my job.  I'm very close to installing Slackware on this laptop.  If I do, I will probably never look back.  That would be a very sad development because other than the random freezes, I've been very pleased with Kubuntu 9.04, but I need a stable, reliable system.

I am willing to provide whatever help to anyone that would help in diagnosing this issue.  I am extremely busy at my job, so I don't have endless time to spend on this, but I will try to help whereever I can.

Richard Scott Smith, pilbender at gmail.com

---

### Post by mvalviar on 2009-06-01
I'm not the only one after all. I've been intrepid and xp runs fine on my box but jaunty hangs sporadically . I hope this gets fixed real soon.

---

### Post by newman on 2009-06-01
I did the upgrade to 9.04 on my desktop pc and experienced random freezes few times a day. it's too bad because 9.04 has some nice new features, and faster boot times. I'm back to 8.10. I don't remember having any system hard freezes in the past several years of using various linux distros. I'm very disappointed in this new buggy release.

oh, and not to mention the ati video driver issues - although I think that's more of a xserver issue...

---

### Post by starhalo on 2009-06-02
this is so unstable its impossible to get work done. i bet the developers are using debian:p

---

### Post by newman on 2009-06-02
> **starhalo said:**
> this is so unstable its impossible to get work done. i bet the developers are using debian:p

actually I believe the developers use Mac OS X

---

### Post by starhalo on 2009-06-03
well yesterday i installed packages check and checkpolicy and havent had a freeze ever since, still unstable though

edit: nevermind, doenst work

---

### Post by utkjamie on 2009-06-04
There are a lot of Twitter users experiencing this problem ([http://bit.ly/111eNn](http://bit.ly/111eNn)). For some of them, this is their first experience with Ubuntu and Linux. It's unfortunate that this bug is chipping away at the reputation of Ubuntu, even among those of us who have been using it for years. It's even worse that Ubuntu's shortcomings are reflecting on Linux as a whole.

With that said, I upgraded to the 2.6.29-02062903-generic kernel and haven't had any freezes since. It's too bad whatever fixes in that kernel haven't been pushed to Jaunty.

---

### Post by Ormente on 2009-06-05
> **pilbender said:**
> I am inclined to believe this has something to do with the dual core processor.  It is the only thing different that makes sense based on reading everything on this thread.
It's definitely something to investigate. Due the freezes i switched from 9.04 to 8.10 (very stable, on the same PC) and now i'm back to Jaunty... freezes are back too !

I noticed something : a "slow freeze" occurred while running the system monitor : _one of the 2 CPU curves dropped down and sticked to the floor_, and within 20 seconds everything was locked.

I tried to reproduce this situation, but without any success, as freezes are mostly instant ones. But i got it this morning for the second time.

As i said in my first post, nothing special seems to be corelated to the bug. It freeze with or without Wifi, nvidia driver etc.

The only thing that match nearly each freeze is a "clocksource tsc unstalble" :

```
kern.log :
Jun  5 13:34:12 lapbuntu kernel: [   86.000075] Clocksource tsc unstable (delta = -64193242 ns)

messages :
Jun  5 13:34:12 lapbuntu kernel: [   86.000075] Clocksource tsc unstable (delta = -64193242 ns)

syslog :
Jun  5 13:34:12 lapbuntu kernel: [   86.000075] Clocksource tsc unstable (delta = -64193242 ns)

daemon.log :
Jun  5 13:33:20 lapbuntu ntpdate[3685]: adjust time server 91.189.94.4 offset 0.470649 sec
```

Some weeks ago I tried alternate clock sources and NOTSC otions, but still got freezes.

Maybe we should call an exorcist ? Or a ghost buster ?

---

### Post by Entropy_Sam on 2009-06-05
Actually I thought the common problem is with Firefox/web use, possibly WiFi or Flash. And the symptoms generally seem in line with a graphics crash.
 
So tying everything together, **it must be somewhere in the code that handles how dual-core processors transfer information between a WiFi input and the graphics drivers**. Certain drivers seem to fare better than others too - in my experience, the open source ATi drivers are much more stable than the proprietary nVidia ones (no crashes at all under the former).
 
Either way, it's certainly reassuring to find this thread and realise it's happening to a lot of people... :-p

---

### Post by ozhoo on 2009-06-05
Big bump...

I've tried isolating this to alsa, pulseaudio, xserver-xorg-video-intel, X, firefox-3.xx, adobe flashplugin, compiz, pidgin, and NOTHING appears to solve this for me

Running a latitude D830 w intel graphics

---

### Post by Bearly Able on 2009-06-05
I can't believe it's taken me two weeks of going demented over crashes and freezes to find this thread.  I had no problems under 8.04, but since I upgraded to 9.04, I've had nothing but trouble.  I have an Nvidia GeForce 7900 GS, and I originally thought the Nvidia drivers were causing the problem, because removing them completely seemed to fix it, but I've just had yet another crash, and am now unable to boot Ubuntu, even in recovery mode.  I also have a Pentium Duo processor (3.4GHz).

---

### Post by tsali on 2009-06-05
Celeron 540M, Xubuntu 9.04

Hard Freeze today using Firefox while viewing flash heavy site. System completely unresponsive.

Only cure was ON/OFF

---

### Post by ozhoo on 2009-06-05
Follow up

My random freezing has stopped after updating to the latest kernel, currently @_ _[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc8/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30-rc8/")

I don't have more than a few hours testing on my system, but one operation that would guarantee a freeze on my system with 2.6.28-11 does not freeze the system now.  This is when I would try to decrypt a file with seahorse via nautilus.  

I'll update again if I see the freezes continue, but users may want to try this fix.  I would not uninstall your old kernels so you may go back to them if problems occur running with the new one.

---

### Post by pilbender on 2009-06-05
> **Ormente said:**
> It's definitely something to investigate. Due the freezes i switched from 9.04 to 8.10 (very stable, on the same PC) and now i'm back to Jaunty... freezes are back too !

I noticed something : a "slow freeze" occurred while running the system monitor : _one of the 2 CPU curves dropped down and sticked to the floor_, and within 20 seconds everything was locked.

I tried to reproduce this situation, but without any success, as freezes are mostly instant ones. But i got it this morning for the second time.

As i said in my first post, nothing special seems to be corelated to the bug. It freeze with or without Wifi, nvidia driver etc.

The only thing that match nearly each freeze is a "clocksource tsc unstalble" :

```
kern.log :
Jun  5 13:34:12 lapbuntu kernel: [   86.000075] Clocksource tsc unstable (delta = -64193242 ns)

messages :
Jun  5 13:34:12 lapbuntu kernel: [   86.000075] Clocksource tsc unstable (delta = -64193242 ns)

syslog :
Jun  5 13:34:12 lapbuntu kernel: [   86.000075] Clocksource tsc unstable (delta = -64193242 ns)

daemon.log :
Jun  5 13:33:20 lapbuntu ntpdate[3685]: adjust time server 91.189.94.4 offset 0.470649 sec
```

Some weeks ago I tried alternate clock sources and NOTSC otions, but still got freezes.

Maybe we should call an exorcist ? Or a ghost buster ?

I went through my logs as well.  I didn't see this correlation that you pointed out with the "Clocksrouce tsc unstable" but now I'm watching for it.  What I'm seeing is "hpet increasing min_delta_ns" entries is /var/log/kern.log and /var/log/messages:
CE: hpet increasing min_delta_ns to 15000 nsec
CE: hpet increasing min_delta_ns to 22500 nsec
CE: hpet increasing min_delta_ns to 33750 nsec
CE: hpet increasing min_delta_ns to 50624 nsec

After the last one it froze.  So I'm grepping for both of these strings in kern.log and messages (also syslog, but nothing is there) to see if I can isolate that as a factor during a freeze.

This is either something with X or a kernel issue.  I don't see anything in my X logs to indicate a problem though.  My goal is to at least isolate that.  Then take it from there.  If it's a kernel issue, I'll try and roll back to an earlier version.  If it's an X issue I might try going to an earlier version too.

---

### Post by pilbender on 2009-06-05
I'd be very interested if the new kernel helped fix the problem.  Ozhoo, please let us know if you have anymore freezes!

scott

---

### Post by trash on 2009-06-05
Well, i can now successfully reproduce this freeze up by trying to print to my HP 1350 usb printer.. 3 times in a row, then i got to frustrated to continue.. can anybody else confirm this weirdness?

---

### Post by fillintheblanks on 2009-06-05
I am using EXT4 with 9.04

it seems to lock up when I run *./configure* or *make* every now and then, and sometimes when I do *svn update* it will lock up also. this never happened in version 7.10

I will try the latest kernel see if it fixes its kind of annoying

---

### Post by ozhoo on 2009-06-06
I've been doing a lot of multimedia oriented multitasking.  Still no freezes!

Had to patch/build the Broadcom STA driver for my wireless because the stock B43 had really horrible performance.

Sorry I really didn't care to spend the time isolating this to something specific with the stock kernel.  So far I don't know of a bug for this logged in bugzilla, but if anyone does let me know.

---

### Post by carlotheman on 2009-06-06
Apparently, this problem can be resolved by installing a kernel equal or higher than 2.6.29.

One way to do this is to install a 'mainline kernel'.

Since I am running the 'realtime' kernel for my professional audio work, I upgraded to the latest [64studio kernel]("http://ubuntuforums.org/showpost.php?p=7380975&postcount=26"), as described at UbuntuStudio forums.

---

### Post by ozhoo on 2009-06-06
System froze as I was doing work.  Looking for answers

---

### Post by jery_wang2002 on 2009-06-06
I just install fresh Jaunty on AMD X4 810 using Nvidia 8200 motherboard.

2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC 2009 x86_64 GNU/Linux

And I install ubuntu-desktop
Default settings, and install thunderbird.

Launch thunderbird, the screen freezes (hard lock, no mouse, nothing, not even ctrl-alt-bkspace or ctrl-alt-del). The only way I can see what is going on is by ssh-ing from another computer and found out that X-org is 99%-100% CPU consumption using top command.

I have to turn off compiz, to be able to launch thunderbird. It's a shame that I can't have compiz. It's no use to buy good motherboard if we can't use it.

---

### Post by Entropy_Sam on 2009-06-06
> **carlotheman said:**
> Apparently, this problem can be resolved by installing a kernel equal or higher than 2.6.29.

Sorry, not true. I compiled 2.6.29.4 (latest stable) earlier today and it froze on me a couple of hours ago while I had some high WiFi network traffic.

Gettign sick of this - starting to look at alternative distro's...

---

### Post by newman on 2009-06-06
9.04 really sucks, I gave up and went back to 8.10 on my desktop pc, and vista on my laptop. Jaunty(I hate the stupid names BTW, why not just call it 8.04, 9.04, etc?) is making ubuntu look lame.

---

### Post by pilbender on 2009-06-07
I have to tell you all that this HP laptop with a Turion 64 bit *single* core processor has been flawless.  No matter what I do, it has been stable as a rock.  Here's the latest uptime output:
01:10:21 up 34 days, 10:47,  1 user,  load average: 1.18, 0.46, 0.20

Again, this is video editing, file transfers, surfing the web, email, wireless on and off, suspend, software updates, development, flash web sites, ssh, ftp, printing via cups over a network, I don't know... I'm trying to think of all the things that people have mentioned here and elsewhere...  None of these activities has caused any problems.

Contrast this with my *dual* core Dell Latitude D630 which has these random freezes all the time.  I had a pretty stable day on Friday (one or two freezes) but that's the exception.

I want to know if anyone is having this mystery freeze problem with *single* core processors on 9.04.  I think this could be a dual core processor issue only.

As some have mentioned, I too am looking at trying to install another distro, probably Slackware.  I feel like I should never have invested my time in Kubuntu 9.04.  It has been a real disappointment.  I loathe the idea of having to reconfigure my work computer and get email set up and all my development tools working again.

It's going to be a question of whether I hate the freezes more than facing a reinstall and (re)configuration of my work environment.  I think I'm going to try to wait for the next kernel update.  If that doesn't fix it, I may be forced to give up on this.

scott

---

### Post by Ormente on 2009-06-07
Pilbender, i confirm that my freezing HP **is** a dual core (AMD 64, but with a 32 bits Ubuntu). And your idea is the best i've heard so far.

When freezes happens slowly, i notice on the system monitor and the system monitor applet that :
- **one core** activity suddenly drop to zero.
- 100% CPU usage as **I/O latency**.

---

### Post by wea3el on 2009-06-07
I'm experiencing freezing in Kubuntu 9.04 on Dell 500 laptop with Intel Celeron 550 CPU @2.00 GHz.

This is single core processor.

Tried the new kernels: .29  and .30rc  but it didn't work.

At this moment I'm using Ubuntu next to Kubuntu on my laptop in order to try and isolate the problem.

I really hope this problem will be solved soon, Kubuntu is unusable for me at this moment :(

---

### Post by brntoki on 2009-06-07
I isolated this a long time ago.  It's JAUNTY!

No, really; I think if you disable networking the freezes will cease.  It seem that everyone that has tried this has reported that no freezes occur if networking is disabled.

[COLOR="SeaGreen"]***Please try disabling your network connection from the network manager settings.  Just uncheck the box.  See if you have any freezes.  I bet you won't.***[/COLOR]

---

### Post by wea3el on 2009-06-07
> **brntoki said:**
> I isolated this a long time ago.  It's JAUNTY!

No, really; I think if you disable networking the freezes will cease.  It seem that everyone that has tried this has reported that no freezes occur if networking is disabled.

[COLOR="SeaGreen"]***Please try disabling your network connection from the network manager settings.  Just uncheck the box.  See if you have any freezes.  I bet you won't.***[/COLOR]


It seems this doesn't fix the problem.
I disabled network and it worked for some time, so I enable it again and still no freezes.
Then I disabled network by a switch on my laptop and when I reboot the system I got freeze, literally seconds after starting the system (without network)!

No freezes when using Ubuntu on the same machine

---

### Post by brntoki on 2009-06-08
> **wea3el said:**
> It seems this doesn't fix the problem.
I disabled network and it worked for some time, so I enable it again and still no freezes.
Then I disabled network by a switch on my laptop and when I reboot the system I got freeze, literally seconds after starting the system (without network)!

No freezes when using Ubuntu on the same machine

Well I would imagine that *how* it is disabled would also be important.  I'm not clear what you mean by, "Then I disabled network by a switch on my laptop...".  I suppose that this means the OS was still running the networking daemons and whatnot.  If that's the case then I would imagine that it would still freeze.  A network connection may not have been detectable to Jaunty, but it was still *attempting* to make/find a connection.

But, I don't know for sure, of course...

---

### Post by Entropy_Sam on 2009-06-08
Absolutely.
 
In almost all cases, Jaunty froze while I was using Firefox, Transmission or Pidgin. Alt-SysRq-R-E-I-S-U-B worked for a relatively tidy shutdown every time.
 
In about 50% of cases, I can see the system starting to slow down in "waves", becoming slightly unresponsive before recovering again and eventually just seizing up completely.
 
I did have one freeze yesterday when I wasn't using an internet app (I'd just receved a "commandnot found error after trying to use the DOS 'md' in place of 'mkdir' - I keep forgetting about that), but I did have Firefox open.
 
The strange thing is that although I'd generally attribute this crash to Network usage, it didn't happen once while I used my old ATi card with the open source drivers - it only started once I upgraded to a newer nVidia card and binstalled the proprietary drivers.

---

### Post by ozhoo on 2009-06-08
Can anyone confirm this happening while running metacity?  I've only been using compiz.

---

### Post by gillmt on 2009-06-08
I was beginning to wonder the same about dual core - I have two AMD64 boxes running Jaunty - one is great, one keeps freezing.

I've replaced Network Manager,disabled visual effects,re-seated the RAM, changed to Swiftfox for browsing, dusted the keyboard...but the one that keeps freezing is dual core

---

### Post by mpittman on 2009-06-08
Networking is certainly enabled for me when the freezes occur - let me set out first what is happening when my desktop computer freezes :

EITHER - I am copying several megabytes of files to a folder on a laptop over the network (the folder is mounted via sshfs).  In this case everything including mouse pointer freezes, and Alt-SysReq-REISUB does not work - can't kill X, can't get a virtual terminal with Ctrl-Alt-F2/3/etc.  Only a power button recycle works.

OR - I have left the computer on but unattended for an hour or more.  Symptoms as above, but also screen is black.

What is NOT a cause for me : 
Intel or nVidia drivers (I use ATI card with radeon driver)
WiFi - I'm using a cable for networking
Xorg in general - I've ignored the normal login screen, gone to a virtual terminal, mounted a remote folder with sshfs, started copying files - and a freeze occurs!

The machine is a HP with Jaunty on one hard drive and (thank goodness) Hardy on another.  Intrepid ran fine for months - I only upgraded because I hoped the real-time kernel was working with dual processors in Jaunty (it seems to be).

I'm sure there are several bugs affecting different users in this forum.  I use Jaunty at work; no freezes at all.  Why is there little if any feedback from developers - is it all too much for them?

---

### Post by ozhoo on 2009-06-08
> **mpittman said:**
> Networking is certainly enabled for me when the freezes occur - let me set out first what is happening when my desktop computer freezes :

mpittman: are you running compiz by chance?

---

### Post by pilbender on 2009-06-08
One confirmation of a single core freeze.  Anyone else with a single core processor and 9.04 freezes?  My single core is an AMD Turon 64 bit.  That was a Celeron, which is 32 bit?

scott

---

### Post by Entropy_Sam on 2009-06-08
In my case at least, I'm now about 95% certain this is Firefox and/or Flash related, but it also seems to be linked to the graphics drivers (and now I have reason to believe that beyond the fact that this didn't happen before I switch from an older ATi vard to a nwere nVidia card). Here's why...

I was watching a flash news clip and I could see the system starting to seize up. I un-maximised my browser so I could watch the CPU monitor on my SysMon screenlet. Both CPU's maxxed out at 99% and then everything stopped. I patiently moved the cursor over the top-right 'x' and clicked repeatedly. Eventually, Firefox closed and the system gradually recovered. I was even able to continue a conversation on Pidgin with a friend.

I reopened FF and left the computer alone for a while, then returned to find that it had crashed and the sceen was blank. I hit alt+sysrq-R-E to request all apps to terminate, and was able to switch to tty terminals 1-6. running **sudo /etc/init.d/gdm restart**, however, just caused an unrecoverable crash. It seized completely on an *_fullscreen nVidia splash_*, with flickering artifacts.

EDIT: Spoke too soon! Can't find the strikethrough font style, but discount the workaround suggested below - second time around, it crashed Ubuntu again... :-p
> 
Interestingly, I just installed Firefox and Flash on Wine and tried to recreate the crash. I got about a minute of a random YouTube video and then the CPUs went crazy again and the graphics started to glitch - _**BUT UNDER WINE, FIREFOX CLOSED AUTOMATICALLY BEFORE IT STARTED TO AFFECT THE WHOLE SYSTEM**_[B]_._

So although it's not ideal, it's definitely a viable workaround. Anyone who suspects their crashes might be related somehow to Firefox/Flash should find that it's much safer running Firefox on Wine [/B](there's also the added bonus that it's noticeably faster...)[B].
[/B]
Can anyone confirm that they've experienced freezes like this while using Wine/Firefox, as opposed to native Firefox?

---

### Post by GrahamP on 2009-06-08
[SIZE=3]Like others posting here I've been experiencing seemingly random problems since upgrading from Hardy to Jaunty. Hardy was rock solid. With Jaunty I've seen: 

Complete freezes, frequently in screensaver
Logouts
Random shifting between full screen and windowed with DosBox
Virtualbox 2.2.4 shutting down ([/SIZE][SIZE=3]Windows 2K guest)[/SIZE]
[SIZE=3]
No obvious repeatability. Duplicating as faithfully as I can the original situation in which a problem occurred does not seem to replicate the problem. As a Ubuntu/Linux newbie I don't know which logs I should look in for debug info, and wouldn't be able to extract much if any useful information from the logs even if I did know. 

AMD Sempron 3400
2Gb Ram 
AMD 690V Integerated Graphics
Default video driver

About six hours ago I switched off all visual effects (System -> Preferences -> Appearance) and haven't had a problem since doing so. That's not a long enough period to be definitive but is suggestively hopeful. I'll continue running in this state for a couple of days to see if there is a genuine improvement in stability, and if so will switch back to normal visual effects and see if the problems reappear. But in the meantime, this might be something worth trying if you're having similar issues.


[/SIZE]


[SIZE=3]



[/SIZE]

---

### Post by Entropy_Sam on 2009-06-09
[SIZE=3]> **GrahamP said:**
> Random shifting between full screen and windowed with DosBox[/SIZE]> **GrahamP said:**
> 
[SIZE=3]Virtualbox 2.2.4 shutting down ([/SIZE][SIZE=3]Windows 2K guest)[/SIZE]
...[SIZE=3]I switched off all visual effects (System -> Preferences -> Appearance) and haven't had a problem since doing so.[/SIZE]
 
Thanks for the suggestion. I've experienced the last two myself while I had compiz enabled, but after I moved my XP virtual machine from an NTFS partition to a FAT32 partition, I stopped getting random shutdowns.
 
Edit: Sorry for messy quote. I've removed the [(/)quote] tags from the middle of the quoted section but they seem to have been helpfully autoformatted back in place :-p

---

### Post by mpittman on 2009-06-09
ozhoo - I'm not running Compiz, I use Enlightenment (e16) and Rox-filer.  I re-created a freeze in a virtual terminal by leaving gdm on tty7 and using Ctrl-Alt-F2 to go to a terminal tty2; this was in order to rule out any X involvement in the freezes.

In this terminal, I mounted a directory on my laptop (using sshfs) and started to copy large files to it; the system (keyboard and all) froze shortly into the process, and as usual even REISUB wouldn't work.

---

### Post by wea3el on 2009-06-09
> **brntoki said:**
> Well I would imagine that *how* it is disabled would also be important.  I'm not clear what you mean by, "Then I disabled network by a switch on my laptop...".  I suppose that this means the OS was still running the networking daemons and whatnot.  If that's the case then I would imagine that it would still freeze.  A network connection may not have been detectable to Jaunty, but it was still *attempting* to make/find a connection.

But, I don't know for sure, of course...


Maybe you're right, it probably has something to do with how it is disabled. I thought this was not the problem so I moved along, but if I get more freezes I'll try network again.

I tried one more thing. Rolled back driver for my graphics card to older version and haven't had a freeze since yesterday.

Graphic card is: Intel Mobile GM965/GL960

---

### Post by Entropy_Sam on 2009-06-09
Downloading Fedora 11 now :-(

I didn't like Fedora 10 nearly as much as Jaunty, but it was more stable than this. :-/

I'll wait for Karmic's release and hope it's been fixed by then...

---

### Post by dspisak on 2009-06-09
With 9.04 my computer hangs 1) when I move a window by grabbing the title bar with the mouse, 2)when moving the vertical scroll bar, 3) moving the mouse pointer slowly close to the scroll bar.  There appear to no other problems.  I am not running compriz.  The freeze happens with other programs in addition to firefox.

I had absolutly no problems when running ubuntu 8.10, kernel 2.6.27-11.  I will reinstall kernel 2.6.27-11 and see if the freeze thaws.


Here is my system:
MB - Asus M3A78-T, 0802 bios
CPU - AMD Phenom II x4 810, 3.18 GHz
RAM - 2 GB Crucial PC8500
On-board Video - ATI Radeon HD 3300
On-board Audio - ATI RS780 Azalia and/or ATI Technologies Inc SBx00 Azalia (Intel HDA)
OS - was ubuntu 8.10, kernel 2.6.27-11, is now 9.04, kernel 2.6.28-11

---

### Post by pilbender on 2009-06-09
I normally don't run Firefox unless Opera has a rendering problem with a particular site.  Flash is still problematic in general (I hate flash) but I've had freezes under all sorts of conditions, from typing an email to using vi in a command console window to surfing the Internet and so on.

I still think this is some sort of race condition with the kernel.  Graphics driver... probably not given the wide variety of graphics cards and configurations with the same problem.

By the way... I use Virtualbox fairly often, and it seems to make no difference with the frequency of the freezes.

Again, any more single cores with freezing issues?

Scott

---

### Post by Entropy_Sam on 2009-06-09
> **pilbender said:**
>  Graphics driver... probably not given the wide variety of graphics cards and configurations with the same problem.

I'd agree, but this never happened before I changed cards. I even changed back for a little while and the crashes stopped.

I can now faithfully recreate the crash by opening a Flash-using site in Firefox. Opera handles Flash just fine, so I've disabled Firefox Flash and set checkgmail to open my inbox in Opera.

So far, so good... (11th hour and all that, given the Fedora 11 DVD image is 55% downloaded).

Going to leave this on overnight with Opera doing stuff that might normally crash FF and see if everything's working fine in the morning...

---

### Post by pilbender on 2009-06-10
Interesting Entropy_Sam.

I'm working on another theory.  I run my computers a lot.  My work computer (which has the freeze problem) is usually always on for the weekends and on about 16 hours a day during the week.

I just had another freeze after hammering it for a few hours.  I tried to restart it... freeze again shortly after.  Gave up and went home.  Let it sit for a few hours.

I started hammering it again.  By hammering, I mean running it hard on the processor level.  Shortly after that... another freeze.  This is under much warmer ambient conditions.

Took it apart and blew the dust out of it with compressed air.  Hammered it some more.  Freeze.

Propped it up for better airflow, my office is quite warm.  I've been hammering it again for several hours and things are good.  My shiny, new, swell theory is that it is overheating in a way that I've never seen before.  Instead of turning off, it simply freezes.

This may explain why flash appears to make other people's machines freeze as flash is sometimes a high processor load activity because flash sucks... in my opinion anyway.  It often causes a lot of processor load on Linux.

That's it.  So... anyone else with some correlation to my new (possibly nonsense) theory?  Or how about some evidence to the contrary?

Scott

---

### Post by wea3el on 2009-06-10
My computer is entering his third day since downgrading graphics card driver. The comp is on all the time, during the night also. Still no freezes!!!
I've been using it normally as I would before: surfing the net, listening music, watching movies, doing OO.org stuff, GIMP etc, using K9copy (which use a lot of processor power).

I know that computers with ATI 'n' NVidia graphics also freeze, not only Intel. Maybe you should also roll back your drivers to see if it helps.
Maybe the problem is how other parts of the system are working with new drivers, but this is only my guess...

Anyone to try and maybe confirm?

---

### Post by Entropy_Sam on 2009-06-10
Well for my part, I can confirm that using Opera + Flash seems to be considerably more stable, as I left the computer streaming the BBC News Channel all night, and the computer hadn't frozen (the channel was playing jerkily when i came back, but I doin't care if an hour or 2 of flash streaming ends up like that -- point is, the system is still running).
 
The first thing I noticed about Opera, btw, is that it's a considerably lighter browser.

---

### Post by petricb on 2009-06-10
After installing drivers for nvidia from their site I had no more problems with system hang. For me NVIDIA-Linux-x86_64-185.18.14-pkg2.run works great.

---

### Post by wea3el on 2009-06-10
It seems that we're maybe onto something!

Anyone else's experiences?

---

### Post by throwingks on 2009-06-10
> **petricb said:**
> After installing drivers for nvidia from their site I had no more problems with system hang. For me NVIDIA-Linux-x86_64-185.18.14-pkg2.run works great.

> **wea3el said:**
> It seems that we're maybe onto something!

Anyone else's experiences?
I have 185.18.14 and "acpi=force irqpoll" in my grub.lst. I still get freezes.

My vid card in an onboard nVidia 780a.

---

### Post by Entropy_Sam on 2009-06-10
> **throwingks said:**
> I have 185.18.14 and "acpi=force irqpoll" in my grub.lst. I still get freezes.

My vid card in an onboard nVidia 780a.

What are you usually doing when the computer freezes?

The best options so far seem to be:

a)Browsing in Opera rather than Firefox (I seem to have isolated my crashes to being entirely caused by running flash in firefox - even if it's in Wine)
b)Updating your proprietary graphics drivers to the latest version from the manufacturer's site

Anyone else had definite success with their crashes by taking these or other steps?

---

### Post by throwingks on 2009-06-10
> **Entropy_Sam said:**
> What are you usually doing when the computer freezes?

The best options so far seem to be:

a)Browsing in Opera rather than Firefox (I seem to have isolated my crashes to being entirely caused by running flash in firefox - even if it's in Wine)
b)Updating your proprietary graphics drivers to the latest version from the manufacturer's site

Anyone else had definite success with their crashes by taking these or other steps?
My driver is the latest. I am now going to try Opera instead of Firefox. Will post back later with results.

---

### Post by Laysan_A on 2009-06-10
Like everyone else here (well, almost) I'm really disappointed with Jaunty. I'm thinking of going back to Intrepid.

Most of my crashes have been while firefox was running, but it has happened at other times as well. For instance, I was rebooting after a crash and clicked with my mouse on a notification from [the services daemon?] that a certain sound card driver set was no longer required and would I like to remove it, at the same moment the sound initialization music started - the screen went immediately black (sometimes it goes beige - my app window color), and nothing but holding the power button down until it died would do anything. 

Someone mentioned the scroll bar in firefox - My last crash occurred just after opening firefox and while I was using my mouse's scroll wheel. I now have a mouse wheel phobia. I'm afraid to touch it (so far so good).

I just don't know what's going on...(not that I know anything anyway).

I installed the latest fglrx driver from ATI last night and I was experiencing the most awful tearing of objects on my screen (before and after the update). But I don't think I had any crashes until I uninstalled it. But to be honest the hours I spent wrestling with the graphics driver is all one long blur. I did spend some time online with firefox - maybe as much as a couple of hours - before I did the fglrx upgrade, and downgrade/removal, and there was no crashing. After that there was lots, because I was having problems with X. Whose wonderful idea was it, anyway, to make sure there is no simple utility to set-up graphics drivers and monitors any more?

I'm bummed....

I just wanted it to work....

I had a crash while watching a dvd. About halfway through the screen just went black and nothing would work. Firefox was downloading something in the background. I did a ctl alt esc and nothing seemed to have happened, but I noticed the hd light was still flickering, and since I didn't want to lose my download, I just sat and waited. After awhile the little skull appeared, I clicked and vlc's video window disappeared, and everything seemed back to normal. I was careful not to touch anything until the download finished.

This has been going on for more than a month now, judging from the posts. We, here, must be the unlucky few since the rest of the Ubuntu world is relatively silent...I just hope someone finds something soon.

By the way I was using Kubuntu 8.10 and now I'm also using Kubuntu.

Note: I've been flagrantly wheeling my mouse - since my post is done - to no effect.

---

### Post by pilbender on 2009-06-10
I had a display freeze and I was able to ssh into the frozen computer and still use it.  So I still think the freezes correlate to heat, but that particular freeze was obviously not the kernel.

So I'm going to take the advice of others and roll back the graphics driver for my Intel 965GM Chipset.  We'll see what happens.  *Anything* is worth a try.  I will let you all know the results.

Here's the exact version I installed for others to reference.
xserver-xorg-video-ati_6.9.0.91-1ubuntu1_amd64.deb

Scott

---

### Post by Chemical Imbalance on 2009-06-11
The freeze for me has nothing to do with Compiz as I always uninstall it after a fresh system install.

My freezes also are seemingly random, whether or not firefox is open. 
It has happened when idle many times now.

It hasn't happened much with flash--maybe a few times out of 50.

Just to restate, Fedora 11 ended up having the same issue for me.

I'll try the latest rc kernel, though I've been this route a few weeks ago without success.

This is the most annoying bug I've ever encountered. 
What one might call a showstopper  :-({|=

---

### Post by throwingks on 2009-06-11
> **throwingks said:**
> My driver is the latest. I am now going to try Opera instead of Firefox. Will post back later with results.

Opera instead of Firefox does nothing at all. Crashed after 15 minutes. If I change terminals, computer freezes. Otherwise I can use the PC with keyboard only and I am fine.

---

### Post by petricb on 2009-06-11
> **throwingks said:**
> I have 185.18.14 and "acpi=force irqpoll" in my grub.lst. I still get freezes.

My vid card in an onboard nVidia 780a.

I don't know what could be problem with your machine, but before installing this drivers I have frustrating random freezes. Now everything works OK.

---

### Post by Entropy_Sam on 2009-06-11
> **Chemical Imbalance said:**
> Just to restate, Fedora 11 ended up having the same issue for me.
Heh, I would have been really miffed to install Fedora 11 and find it was still happening then... :-p
 
Well, I'm going to stick around with Ubuntu for a while, but I'm keeping half an eye on Linux Mint - I think it's more my thing than Fedora anyway.
 
If Ubuntu starts pulling funny stuff on me again, and Linux Mint's next stable release goes without serious issues, I'm there...

---

### Post by gorgon on 2009-06-11
Hi all,

With a critical problem like this I guess that Im not alone in wanting to test new and possibly unstable "updates" just to stop the freezes. 

Ive been looking around a bit, on launchpad and the forums, and now Ive enabled the "proposed" updates for Jaunty in software update and can wait for the lauchpad bug 359392 webpage to tell me that the fix has been released.

I can see that the fix is released for Karmic, so Im wondering: is there a way to be even more on edge of testing the new updates without upgrading to Karmic?

Thanks!
g

---

### Post by Chemical Imbalance on 2009-06-11
I just switched to this kernel in Jaunty and so far everything is stable.  _So far._

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/)

Won't hold my breath though ;)

I know the .30 kernel was just released, but there are no working nvidia drivers so far as I know, and have tried.

Hope this fixes this problem [-o<





Edit:

Okay, it seems the freezes are gone with this kernel, but now my ethernet connection randomly disconnects and wont reconnect.

The .30 kernel doesn't do this.  The .30 kernel wont load any nvidia modules however...

These last 2 kernels 28/29 have been nothing but trouble for me, though .30 is looking pretty good, especially when it will be able to load nvidia drivers.

---

### Post by Laysan_A on 2009-06-11
Two more freezes today - the first right after initial boot (unrelated to temp.).

Had a temp. incident though...

Please see my post here for a description of my continued suffering...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/352373](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/352373)

Oh, yesterday I uninstalled pulse. Doesn't seem to have helped.

---

### Post by pilbender on 2009-06-11
Hi all.  Tentatively good news.  I've been running since last night without rebooting and no freezes.  I've been pretty hard on my system today.  Here's my uptime:
 18:13:20 up 22:28,  1 user,  load average: 1.44, 1.52, 1.54

That's 22 and a half hours!  Man I'll take it

I have an Intel 965GM Chipset.  I rolled back to this version:
xserver-xorg-video-ati_6.9.0.91-1ubuntu1_amd64.deb
found here:
[https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/1:6.9.0.91-1ubuntu1](https://launchpad.net/ubuntu/+source/xserver-xorg-video-ati/1:6.9.0.91-1ubuntu1)

I had the latest version before that which I'm guessing can be found here:
[https://launchpad.net/ubuntu/jaunty/amd64/xserver-xorg-video-ati/1:6.12.1-0ubuntu2](https://launchpad.net/ubuntu/jaunty/amd64/xserver-xorg-video-ati/1:6.12.1-0ubuntu2)

All the drivers are listed here:
[https://launchpad.net/ubuntu/jaunty/amd64/xserver-xorg-video-ati](https://launchpad.net/ubuntu/jaunty/amd64/xserver-xorg-video-ati)

In case anyone wants to roll back to something else.  I'm going to leave my computer on.  We'll see how this goes.  I will report back tomorrow with either good or bad news.

scott

---

### Post by Entropy_Sam on 2009-06-12
> **Chemical Imbalance said:**
> I just switched to this kernel in Jaunty and so far everything is stable.  _So far._

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29/)


Ah, sorry - my bad, but I should have mentioned I'm on kernel version 2.6.29.4. I get crashes in Firefox & Flash, but not witt Opera & Flash,

Edit: AND I Upgraded my nVidia drivers to the latest...

---

### Post by Chemical Imbalance on 2009-06-12
Okay.  I've been using the .30 final kernel and it has been working great.

No freezes yet.  

Just no nvidia drivers for this kernel at the moment.

---

### Post by colau on 2009-06-12
No freeze in jaunty.
uname -r 
```

2.6.29-020629-generic

```

---

### Post by dspisak on 2009-06-12
I had thought the problem was the mouse driver since the computer would freeze when I either moved a window by the title bar or used the right vertical scroll with the mouse.  However, I followed pilbender's tip (see above) and reloaded the xserver driver.  It was 1:6.12.1.  I replaced it with 1:6.9.0.91 and I have had a two hour session and a 1 hour session without any problems.  Here are my specific steps.

1. Remove in Synaptic: compriz, paman, paprefs, pavumeter, pavucontrol (these steps may not be necessary, but I had already removed them).

2. Remove existing xserver installations from the system by running:
sudo apt-get -y purge xserver-xorg-video-ati   xserver-xorg-video-radeon

3. Down load and install xserver-xorg-video-ati_6.9.0.91-1ubuntu1_amd64.deb using GDebi Package Installer.

4. Go to System/Administration/Hardware Drivers and deactivate the FGLRX graphic driver.

5. Reboot.

Thanks for all the tips.

Dan

My System:
MB - Asus M3A78-T, 0802 bios
CPU - AMD Phenom II x4 810, 3.13 GHz
RAM - 2 GB Crucial PC8500
On-board Video - ATI Radeon HD 3300
On-board Audio - ATI RS780 Azalia / ATI Technologies Inc SBx00 Azalia (Intel HDA) / ALC1200 
OS - ubuntu 9.04, kernel 2.6.27-14-generic
Video Driver - xserver-xorg-video-ati_6.9.0.91-1ubuntu1_amd64

---

### Post by Chemical Imbalance on 2009-06-12
I've gotten the 180.60 nvidia driver to load on the 2.6.30 kernel now. For some reason I had to install it twice.
It's still working great, no freezes.

I suggest everybody give the .30 kernel a shot: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by Laysan_A on 2009-06-12
> **Chemical Imbalance said:**
> I've gotten the 180.60 nvidia driver to load on the 2.6.30 kernel now. For some reason I had to install it twice.
It's still working great, no freezes.

I suggest everybody give the .30 kernel a shot: [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")


Hi,

I've noticed a number of people (no doubt you have too) who went to the .30 kernel (or the .29) and thought they had it licked only to report later that they had a recurrence. Please continue to report, will you? I've got ati, myself. I'm waiting...I haven't changed anything on my system yet - I don't want to break anything...

One guy reported that he only had success after he changed both his kernel  to the latest .30 and his Xorg to the edge release. I  don't know what kind of graphics he had, nor whether his fix held.

Here's an update: 
Last night I went for about twelve hours without a crash, before shutting down. There was one incident with an errant program (firefox), but I caught it in time. Today I've been up for about five hours without an incident - though this is all I've been doing ;)

My freezes seem to occur without regard to the program being used at the time. I've had them in firefox, vlc, abiword, while network manager was connecting the wireless, while alsa was initializing. I may be having more than a single kind of hang-up. One kind occurs completely unexpectedly. I touch something, a mouse wheel, click a box, or even touch nothing at all during boot, and the screen goes black (or the dominant window color), usually there isn't even a cursor left. The other kind involves a single program getting hung-up, with heavy constant processor use and rapid rise in internal temperature. If I can terminate the program everything returns to normal. This has happened twice that I know of, once when I opened a document in abiword, and, strangely, just after I closed out a flash video, in firefox.


 Though my freezes are not limited to video applications, I have noticed something strange related to videos in this new installation. I can play videos, both avi and dvd in full screen from the desktop, even while firefox is running in the taskbar, but videos streamed through firefox run slow and out of synch in full screen, both flash and avi. It doesn't seem related to bandwidth.


Those of you following this thread might also want to check out (I'm sure there are likely more, as well):


[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/352373](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/352373)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155?comments=all)

---

### Post by Chemical Imbalance on 2009-06-12
The .29 kernel had some odd ethernet driver bug for me.

It would kick my connection after a few minutes and refuse to reconnect.

.30 has been great on the other hand.

I've had it installed for about a day now on my desktop and all has been good so far.  I will definitely keep you updated if it ever freezes.

---

### Post by luuke on 2009-06-12
I've been using jaunty for a month or two now, and I've been getting a lot of freezes.
Very annoying, but I have faith that it will be fixed in updates, and I wouldn't ditch ubuntu for this alone.

---

### Post by pilbender on 2009-06-12
> **dspisak said:**
> I had thought the problem was the mouse driver since the computer would freeze when I either moved a window by the title bar or used the right vertical scroll with the mouse.  However, I followed pilbender's tip (see above) and reloaded the xserver driver.  It was 1:6.12.1.  I replaced it with 1:6.9.0.91 and I have had a two hour session and a 1 hour session without any problems.  Here are my specific steps.

1. Remove in Synaptic: compriz, paman, paprefs, pavumeter, pavucontrol (these steps may not be necessary, but I had already removed them).

2. Remove existing xserver installations from the system by running:
sudo apt-get -y purge xserver-xorg-video-ati   xserver-xorg-video-radeon

3. Down load and install xserver-xorg-video-ati_6.9.0.91-1ubuntu1_amd64.deb using GDebi Package Installer.

4. Go to System/Administration/Hardware Drivers and deactivate the FGLRX graphic driver.

5. Reboot.

Thanks for all the tips.

Dan

My System:
MB - Asus M3A78-T, 0802 bios
CPU - AMD Phenom II x4 810, 3.13 GHz
RAM - 2 GB Crucial PC8500
On-board Video - ATI Radeon HD 3300
On-board Audio - ATI RS780 Azalia / ATI Technologies Inc SBx00 Azalia (Intel HDA) / ALC1200 
OS - ubuntu 9.04, kernel 2.6.27-14-generic
Video Driver - xserver-xorg-video-ati_6.9.0.91-1ubuntu1_amd64

I said I would report back as I was getting tentatively excited that my machine may be fixed.  I still believe this is the case.  I'm glad this seemed to work for someone else.  Good instructions Dan.  Thanks for adding your input.  I'm sure many will be helped.  Here's my latest uptime:
 17:57:07 up 1 day, 22:11,  1 user,  load average: 0.54, 1.50, 1.61

That's almost 2 days.  I take this laptop to work and use it all day for heavy development use.  All I've been doing is unplugging it, shutting the lid and putting it in my bag.  Then I plug it in when I get home.   It comes out of suspend with everything still up and running!

I totally abuse my machine.  I ran skype for 4 hours continuously today with Teamviewer running through Wine.  I ran Netbeans, Oracle SQL Developer, Soap UI, many console prompts, several instances of OO Writer, Opera, Firefox (at the same time), Evolution, Thunderbird, Kopete, and I stream radio over the Internet all day long!  I normally have 50 to 60 tabs open in Opera.  I had several other applications open at different times but this represents my standard work environment.  I use it this way daily.

I've been faithfully applying all updates except the ati driver Dan and I mention.  I do nothing else special on this Kubuntu release.  I also run dual display.  I turn it on when I get into work and I turn it off before I leave.  I use single display when I'm at home.  This thing hasn't missed a beat.

I plan on working through the weekend to make some deliverables by June 30th.  I will leave my system up.  I will also be looking for posts on when it is safe to upgrade to the latest driver.  I'm not too experimental because this is my work computer.  I can't afford to be down.  I'm also in a Windows dominated shop, so I don't get any help when there are problems.

Hope this helps some users and I hope the ATI developers are listening.  I think somewhere along the line a bug was introduced between the versions mentioned above.  This is strange behavior because my graphics chipset is the Intel 965GM Chipset.  I was only taking a shot in the dark on this rollback because someone else mentioned it as a possible cause.  It must have some dependency it is carrying along that's causing my problems.  My system should have *nothing* to do with the ATI drivers!

I'll keep the updates coming.

Scott

---

### Post by trash on 2009-06-12
> **luuke said:**
> I've been using jaunty for a month or two now, and I've been getting a lot of freezes.
Very annoying, but I have faith that it will be fixed in updates, and I wouldn't ditch ubuntu for this alone.

Yes well, i forget which release it was the last time but constant reboots did in fact fry my g3 ibook. I don't feel comfortable rebooting what can be 2-4 times a day on my new machine lol. Having spent the last 5 hours in Vista though i'm not sure how long i will last!! HAHA.

---

### Post by pritcharded on 2009-06-12
On my PC (Core 2 Duo, FireGL V7200, three Hds) I have Vista (on sda), and 8.04 and 9.04 installed on sdb. Vista and 8.04 both run perfectly.

9.04 has been a major problem child.

With it running off the installation CD, it seems to work perfectly. Once installed when 9.04 is selected from the start-up options, the OS loads OK (type in user name and password and the appropriate sounds result), but the screen goes into power-saving mode and the only option is to force a restart with the on-off switch. Starting in safe mode gets one no further.

On the other hand if 8.04 is started first and used for awhile, a restart this time in 9.04 usually results in 9.04 working perfectly!

This suggested to me that enough residual code might be being retained in the graphics card to get 9.04 up and running. 

Unwisely I failed to comprehensively interrogate these forums first, but assumed that as the standard application manager shows ATI binary V.Org driver to be an appropriate driver for my card, perhaps I should try it.

Big mistake as now if I select 9.04 and press enter, my system freezes every time and I have no way to uninstall this driver.

Being a novice before I do more damage I would appreciate some advice on how to proceed. I have in mind to:

1. Back up my Windows and 8.04 files externally.
2. Using 8.04 running off the installation CD, load Gparted and delete the partition on sdb containing 9.04.
3. Reinstall 9.04 in its own partition.
4. Continue using 8.04 until the Ubuntu developers sort this out.

When it works 9.04 seems like a very nice system so I'm reluctant to give up on it entirely and simply go back to 8.04 permanently. 

Ted

---

### Post by pilbender on 2009-06-12
Ted,
   If you can't start up, I'd suggest trying to run fsck off one of the installation CD's.  I had to do this a few times because my file system was corrupted during some of these freezes.

   The procedure is as follows:
1. Boot from one of your installation CDs.
2. Open a Konsole or command prompt of your choice.
3. sudo -s and put in your password
4. fsck /dev/sda1 or whatever your boot partition is that you can't boot from
5. Reboot.

If that doesn't work then you can see if Grub is corrupted.  Post back if running fsck doesn't help you.  More often then not, I think this will get you going again.

Scott

---

### Post by zugol on 2009-06-13
Everything seems ok for my since I installed kernell 2.6.30, but I would like to know if anyone has installed kernell 2.6.29-13 provided by "ubuntu-proposed" ? 

For your information, if you encountered problems while installing kernell 2.6.30 with nvidia driver, give a try to this : 
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
It's not the latest stable version but work for me.

---

### Post by Laysan_A on 2009-06-13
> **Chemical Imbalance said:**
> The .29 kernel had some odd ethernet driver bug for me.

It would kick my connection after a few minutes and refuse to reconnect.

.30 has been great on the other hand.

I've had it installed for about a day now on my desktop and all has been good so far.  I will definitely keep you updated if it ever freezes.

I just don't know about upgrading my kernel...

I discovered and installed KernelChecker and it seems pretty straightforward. It even offers to change the x server. But I wonder about all the other stuff like the restricted extras and graphics drivers that are tied to specific kernel releases. I know you're using nvidia while I have ati, but how did you handle all the other stuff - did you just leave it?

I could just try downgrading my graphics driver as pilbender suggests (but he also recommends removing a bunch of other stuff I don't recognize).

I guess I'm still trying to gather more information before I come to a decision. What do you think?

---

### Post by trash on 2009-06-13
Just to add that in vista I am having no issues with my wireless router, as opposed to Jaunty which would constantly disconnect, try to find other available networks and then completely give up trying to connect to any at which point a restart was required.

---

### Post by pilbender on 2009-06-13
> **Laysan_A said:**
> 
I could just try downgrading my graphics driver as pilbender suggests (but he also recommends removing a bunch of other stuff I don't recognize).


Slight correction here... check my earlier posts.  Dan, whom I quoted, removed the other stuff.  My only change was the .deb package for the ATI drivers.  You might try that shot in the dark the way I did and if it works or doesn't, please let us all know!

I'm still up:
11:24:49 up 2 days, 15:39,  1 user,  load average: 0.42, 1.63, 1.68

Given my usage patterns, you can read about those too, I'd say this is working well.  I should also, again, mention that I have been faithfully applying all updates except for the ATI driver I rolled back.  I didn't see anything in the updates that would have fixed this freezing issue, but then I'm also using the Intel 965GM graphics card and the ATI driver should have nothing to do with my system!  So who knows if those updates were dragging something along that happened to fix this issue like the ATI driver seems to be doing.  

I'm very happy with these results so far.  No freezes at all.  It's worth a shot if it fixes your problem.

Scott

---

### Post by Laysan_A on 2009-06-13
> **pilbender said:**
> 

I'm very happy with these results so far.  No freezes at all.  It's worth a shot if it fixes your problem.

Scott

Hi Scott,

I guess I'll give it a shot. I was hoping you had an ati chip in there. 

I did fairly well yesterday. Only one black screen freeze and a couple of program freezes. Today I've had two black screens within five to ten minutes of booting (I hope that's not a sign of things to come). Last night there was an update of hal and restricted extras.

Update: Well, I rolled back my open source ati driver. So far no sudden black screens, although I did just get a program freeze with heavy processor use and rising int. temps. in firefox. I had a few tabs open and I started to load the "about plugins" page. I was able to terminate the program. So, it's way too soon to tell if anything has really changed. I can definitely say, however, that media streaming still sucks. In intrepid I was using the propriatary fglrx driver, so I don't really know if this is worse (though I think it must be) than it would have been in Intrepid using the open source driver.

---

### Post by pilbender on 2009-06-15
Well...  I had a crash, but it wasn't the dreaded display freeze.  I'm not used to this kind of unreliability on Linux.  I feel like I'm on Windows here.  This release is truly buggy.

I had a file system corruption.  I use ext3.  I also use ext3 on Slackware.  It is much better there.  I actually carry a boot disk now.  I can't believe, I have to do these.

The freeze still appears to be fixed but now I'm running into other issues.  I still may switch to Slackware because I find this unexceptable and shameful for Linux.

Scott

---

### Post by Chemical Imbalance on 2009-06-15
You know, just when you think you find a solution...
BAM! 

Another freeze.

I've had it.  I'm moving to BSD or Solaris.

I'm gonna install the latest version of PC-BSD right now.

I need something other than the linux kernel.

I tried 2.6.30, but still no go.  It worked fine, then I got a freeze, then another.

BSD here I come.  Oh well to Flash 10 and the latest apps, but hopefully a stable system.  I liked BSD last time I tried it.  Here goes.


Edit:

Ahhh! :-x

BSD can't even mount ext3 as ext3, only as ext2.

Forget it.  I guess I'll deal with freezes.


Edit #2 :)

Okay, I'm going to try Debian.  Don't know if that will change anything with this freeze, but oh well, worth a shot.

---

### Post by Laysan_A on 2009-06-15
> **Chemical Imbalance said:**
> You know, just when you think you find a solution...
BAM! 

  Okay, I'm going to try Debian.  Don't know if that will change anything with this freeze, but oh well, worth a shot.

I'm just wondering...why don't you just go back to Intrepid - it was very stable for me?

Well, I rolled back my ati driver as pilbender suggested, but I wasn't at all pleased with the graphics performance. Streamed media would not play properly in full screen. Still, for the time I had it on, there were no more frozen black screens. I went ahead and installed the 2.6.30 kernel, well two of them, actually, the ultimate and the candela (I had a problem with kernelcheck, so I ended up with two .30s). At that time I also upgraded my xorg-ati drivers to the most recent.

I'm now getting as many freezes as I ever was.

This is an interesting series of posts, at least for ati users. This one,
[http://www.kdedevelopers.org/node/3942](http://www.kdedevelopers.org/node/3942)  is referenced in this one,
[https://bugs.launchpad.net/fedora/+source/xserver-xorg-video-ati/+bug/348332](https://bugs.launchpad.net/fedora/+source/xserver-xorg-video-ati/+bug/348332)

Those of you subscribed to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155?comments=all) (Chemical Imbalance, at least), already know this bug has just been marked critical and triaged. Hopefully we'll see some progress soon.

I don't know what my next step will be. With pilbender's success with his xorg-ati rollback, and our experiences with various kernels, I'm thinking of trying the xorg rollback in the kdedevelopers post above (though it doesn't look like it'll be of any help for nvidia or intell users). I've been through so very many posts by so very many users, many of whom had their own little fix or one kind or another, that I'm of the opinion that whatever this is it won't be solved by anything other than a downgrade to something stable, or an upgrade, by which I mean an actual fix, of x, mesa, or whatever it is that's screwing things up (once someone figures out just what it is).

I like (k)ubuntu. I like it a lot. I admit I'm a bit disappointed by this upgrade and wish I had simply been lazy enough to ignore the constant reminder "Would you like to upgrade to Kubuntu 9.04?" in adept for another few weeks. When it's working it's pretty nice. When it's not working...well, it reminds me a lot of Windows ME after service pack 2. 

I know this is just a hiccup, and that soon (hopefully very) I'll be able to forget about my operating system and just do what I do. Until then, I'll be here with the rest of you staring at your monitors, obsessing over the black screens and graspings at solutions of the rest of us, finger poised above the reset button.

---

### Post by pilbender on 2009-06-15
Laysan_A, I have to agree with you.  There is a performance hit.  I wasn't too worried about it since I don't really need great graphics performance.  But I think you are right about it.

I had another crazy day of computer use and no freezes, so at least I've got that going for me.  I'm still angry about losing a few files after the file system corruption I just posted about yesterday.  

I'm disturbed about not being able to trust my computer anymore.  I always do backups and so on.  I'm not talking about that.  But I have come to expect a level of functionality in Linux, any distribution, and for the first time, I'm not seeing it.

I used to be a RieserFS fan, but multiple file system corruptions a while back (this was while Hans Reiser was still leading Namesys) I switched to ext3.  Ext3 has been great, but on 9.04, it's been less than reliable.  It could be faulty hardware.  I'd like to allow for that possibility.

I like 9.04's features and functionality, but I'm thinking more and more of going back to Slackware.  That's what I run on all my other systems anyway.

Laysan_A, thanks for posting the links.

scott

---

### Post by flowingfire on 2009-06-15
I just wanted to add my two cents and say that I experienced these complete lock-ups on my 9.04 upgrade, but they didn't happen until I had been using it flawlessly for weeks.

I run a Nvidia Geforce 6150 on the motherboard.  

Then, I started getting these random freezes and lockups requiring a hard reboot.  Then, upon reboot, I now get a fuzz screen just seconds after seeing a desktop with all the icons and having enough time to enter a keyring password.

It's not a hardware problem, that's for sure.  I tested my other OS's.

What... The... Hell?

---

### Post by pritcharded on 2009-06-16
> **pilbender said:**
> Ted,
   If you can't start up, I'd suggest trying to run fsck off one of the installation CD's.  I had to do this a few times because my file system was corrupted during some of these freezes.

   The procedure is as follows:
1. Boot from one of your installation CDs.
2. Open a Konsole or command prompt of your choice.
3. sudo -s and put in your password
4. fsck /dev/sda1 or whatever your boot partition is that you can't boot from
5. Reboot.

If that doesn't work then you can see if Grub is corrupted.  Post back if running fsck doesn't help you.  More often then not, I think this will get you going again.

Scott
Scott

I didn't get very far with this. 

I booted from the 9.04 installation disc and using Gparted found the only partition with a boot flag to be sda1. 

Using a terminal I then got this output:

ubuntu@ubuntu: ~$ sudo /dev/sda1
fsck 1.41.4 (27-Jan-2009)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda1
ubuntu@ubuntu: ~$

I then booted from my installed copy of 9.04 in safe mode and ran fsck from the repair options menu. It ran thru sdb9 (the partition containing 9.04) but didn't find any errors. 

As fsck presumably compares installed code with a known correct source, and as "Install & Remove Applications" loaded "ATI binary X.Org driver" from the 9.04 repository in the first place, I guess there is no reason why fsck should find its presence to be a problem (ie: the problem is ATI binary X.Org driver simply shouldn't be a selectable option in 9.04 - at least without some warnings).

If Grub is responsible for the graphical interface then presumeably it is selecting the wrong driver to use as opposed to the driver being corrupted. (ie: it's selecting X.org as opposed to fglrx - which works at least some of the time).

If this is the case can I somehow correct it.

Ted

---

### Post by Laysan_A on 2009-06-16
> **flowingfire said:**
> 

What... The... Hell?

Woah!

The only thing I can think is that maybe your driver got changed by x (or grub?), or maybe it got corrupted. 

When I first installed I also installed the proprietary ati driver fglrx. At boot-up and whenever the screen refreshed it looked fine, but as soon as the screen stopped refreshing everything on the screen would tear horizontally clear across the screen. It was hard to see, but still useable (barely). Nothing like yours!

@pilbender

Why don't you just install intrepid for a while? That's what I would do if I were more familiar with the process. As it is, every time I install from the cd I end up having to reformat everything, losing everything in the process. Unlike you I don't have everything backed-up (and I just don't want to hassel with reinstalling all the programs I've collected over the months).

---

### Post by pilbender on 2009-06-16
> **pritcharded said:**
> Scott

I didn't get very far with this. 

I booted from the 9.04 installation disc and using Gparted found the only partition with a boot flag to be sda1. 

Using a terminal I then got this output:

ubuntu@ubuntu: ~$ sudo /dev/sda1
fsck 1.41.4 (27-Jan-2009)
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda1
ubuntu@ubuntu: ~$

I then booted from my installed copy of 9.04 in safe mode and ran fsck from the repair options menu. It ran thru sdb9 (the partition containing 9.04) but didn't find any errors. 

As fsck presumably compares installed code with a known correct source, and as "Install & Remove Applications" loaded "ATI binary X.Org driver" from the 9.04 repository in the first place, I guess there is no reason why fsck should find its presence to be a problem (ie: the problem is ATI binary X.Org driver simply shouldn't be a selectable option in 9.04 - at least without some warnings).

If Grub is responsible for the graphical interface then presumeably it is selecting the wrong driver to use as opposed to the driver being corrupted. (ie: it's selecting X.org as opposed to fglrx - which works at least some of the time).

If this is the case can I somehow correct it.

Ted

There's a lot I don't understand about this post.  I'm sorry for not really being able to follow along.  I'll give it a shot though.

I used /dev/sda1 as an example.  If your installation partition for 9.04 is /dev/sda9, then run fsck on /dev/sda9.  Don't mount the partition before you do it.  You can't normally run fsck on a mounted partition.

fsck stands for "file system check."  It has nothing to do with comparing code.  It only looks at physical disk structures and makes sure they are correct.  Sometimes it will cause a loss in data when it has to fix broken structures.  Usually there is nothing you can do about this.

Grub is responsible for loading the kernel image.  Xorg is loaded sometime during init with system initialization scripts.

If you were successful in running fsck on /dev/sda9 (or whereever your 9.04 installation lives) then that's not a problem for you.  It was just a suggestion.  It's something I've had to do several times myself on 9.04 and I figured others were likely having similar issues.

I hope I helped here.  I apologize if I misinterpreted your post in any way.

scott

---

### Post by pilbender on 2009-06-16
> **Laysan_A said:**
> 
@pilbender

Why don't you just install intrepid for a while? That's what I would do if I were more familiar with the process. As it is, every time I install from the cd I end up having to reformat everything, losing everything in the process. Unlike you I don't have everything backed-up (and I just don't want to hassel with reinstalling all the programs I've collected over the months).

If I go to the trouble of reinstalling my system and getting everything set up, I'm going to invest in something I know works well, Slackware.

Seriously, I'm giving it a shot, trying to fix my own system and trying to help others too.  I may not be doing a good job here, but I'm really trying.

If I make the switch though, I'm done with Ubuntu/Kubuntu.  It means I've given up.  I like getting work done and using my computers.  I'm really quite angry at having to spend so much time on this.  I allow that it's free and community driven.  So I try to contribute and help.  It's the right thing to do.

I have a limit though.  I haven't hit that limit, but I see others have.  If I go through this (I mean set up and configuration) again, I'm going to do it on a reliable platform.  And absolutely nothing has been more reliable in my 15 years of Linux experience than Slackware.

Scott

---

### Post by pritcharded on 2009-06-16
Scott

No apologies needed as I've much appreciated your help and learnt a bit more in the process.
You refer to initiation scripts. Do you know their file location? If I can find them I may be able to simply edit them.

Ted

---

### Post by Chemical Imbalance on 2009-06-16
@Laysan_A

Intrepid had sound issues with my chipset

-- -- --


Okay, I just migrated to Debian Lenny and upgraded from there to "Testing".

The default kernel was 2.6.26 (old), so I compiled my own kernel from the 2.6.30 source.



Everything is going very smoothly.


Debian is so nice!

---

### Post by Entropy_Sam on 2009-06-17
> **Chemical Imbalance said:**
> Okay, I'm going to try Debian. Don't know if that will change anything with this freeze, but oh well, worth a shot.
 
Why not look at Linux Mint - keep Ubuntu's user-friendliness, but with less restriction on restricted formats?
 
Also I can report that with a self-compiled 2.6.29.4 and the latest nVidia drivers, I still get crashes if I use Flash in Firefox, but not in any other browser. I disabled the Flash Plugin in FF and switched my default browser to Opera. I don't really like Opera, but I can probably get used to it, and at least it's more lightweight then FF (I liked epiphany better, but it doesn't seem to play Flash correctly).
 
I also noticed that my AppArmor kernel module isn't loading at startup (I get a FAILED message). Done a bit of reading, and it look like it restricts the system resources that can be accessed by set processes. If it's not loaded, I guess it would make the system much more susceptible to a serious crash if Flash/Firefox gets buggy and starts consuming 100% cpu...
 
I haven't fully investigated this yet, but I don't recall seeing the FAILED message when I used the open source ATI drivers for my old card - I think it only appeared after installing the nVidia drivers. Which explains why the crashes only happened when I changed my graphics card.
 
In my case I'm think the crash is a combination of 2 bugs:
 
1) a FF/Flash "resource-hog" bug, which would normally just result in the automatic closure of FF.
2) Somehow AppArmor is conflicting with the nVidia drivers and not being loaded
 
... so FF isn't closed by AppArmor (or the impending crash isn't detected and prevented) and Flash ends up being granted %100 of the CPU power.
 
If I think I'm this close to solving my own crashes, it's probably about time I registered a Launchpad account and posted these bug reports.
 
***CAN ANYONE ELSE WITH FIREFOX FLASH-CRASHES CONFIRM THAT APPARMOR IS NOT BEING LOADED AT STARTUP?***

---

### Post by VastOne on 2009-06-17
I want to add my experiences to this fray....

I have 2 near identical machines. My original AMD 940 Phenom was my original Jaunty setup and rock solid.

I bought the exact same configuration except used a AMD 955 Phenom.

I then imaged the 940 and used that as on my 955. Again, same hardware same drive same NIC same nVidia 9500 GT same PS etc etc etc

I never saw any of these freeze ups until one week ago after a load of updates.

I only see it on the 940 and never on the 955 even tho it is the exact image.  It can happen to me at any random moment. In 45 minutes, in 3 hours or in 23 hours. There is no pattern to it. 

I am getting the generic gdm_slave_xioerror_handler error message on every reboot

As I have seen others report, this is the most complex and baffling issue I have seen to date with Ubuntu.

---

### Post by madone1 on 2009-06-17
I did fresh install 9.04, and update after installing nvidia drivers. And  don`t have freezes anymore(4 day). How, i don`t now. Before i tried upgrade from 8.10 to 9.04, clean install, new kernel, upgrade from 9.04 to Karmic and nothing help`d until now when i did clean install for the second time (i even used my old /home partition)

---

### Post by pilbender on 2009-06-17
> **pritcharded said:**
> Scott

No apologies needed as I've much appreciated your help and learnt a bit more in the process.
You refer to initiation scripts. Do you know their file location? If I can find them I may be able to simply edit them.

Ted

Ted,
   I'm far from an expert on Ubuntu/Kubuntu.  But it seems to follow what's known as System V init.  Which is a way of arranging system initialization scripts.  These are located in /etc/init.d.  There is also a README file there with a little, very little, explanation on what's there and some conventions on this distribution.

   Most distributions are following this.  Slackware is one of the hold outs for the BSD style initialization which is located in /etc/rc.d.  I personally perfer BSD style because it seems simpler to me and I've used both on many different distros in the past.

   **Freeze update:**  I was having great luck, for several days in a row, with the roll back of that ATI driver I posted about a few days ago.  Then I had the file system corruption and lost some data.  It was stable for another day or two and then I got another couple of freezes in quick succession.  I was doing a lot of compilations at the time, so the processor was getting hot again.

   I went ahead and just updated to the latest drivers again.  I have not seen freezes associated with Firefox using Flash.  I ran that for about an hour on a youtube.com video.  No freezes because of it.  Sorry Entropy_Sam, but I tried to reproduce your Firefox freeze and couldn't do it.

   The next thing I'm considering is madone1's suggestion of reinstalling 9.04.  I won't have to set up my development environment if I go with that because it's configured on my local account.  I will still have to install and configure email and a couple of other things.

   I have another release due at the end of June.  If I don't get a solution by that time, I may take that opportunity to reinstall with Slackware.  I need an ending to this.  This whole thing is insane.

scott

---

### Post by ozhoo on 2009-06-17
> **pilbender said:**
> 
I need an ending to this.  This whole thing is insane.
scott

Agree... I've tried upgrading/downgrading everything (kernel, sound, video, ff, pidgin), and Jaunty still freezes my D830.  I'm seriously thinking about reinstalling with another distro.

---

### Post by pilbender on 2009-06-17
I'm on my 9.04 system still.  I've started to track down the pieces I need for Slackware.  I haven't had a freeze yet, but I'm about done with all this.  The only things I haven't put on Slackware are Teamviewer running through Wine and Evolution.

I can even live without Evolution for Exchange access, as I can use the web interface.  Everything else is good on Slackware and I don't have freezes on that Distro.

I use Teamviewer all the time through Wine.  If I get all this done, that will be it.  Unless a solution is found damn quick.

scott

---

### Post by Laysan_A on 2009-06-17
If anyone is interested in helping diagnose and fix these freezes to black, go here
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355155?comments=all)
and see what you can do to help the developer Manoj Iyer do his work. It looks as though he could use some more folks to help with testing and reporting. 

If you want to help, he's asked if installing the mainline kernel removes the freezes on your machine. That kernel is located here: (there's a link to the kernels here)
[https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds) and if that doesn't work for you to try this kernel: [http://people.ubuntu.com/~manjo/lp355155-jaunty/]("http://people.ubuntu.com/%7Emanjo/lp355155-jaunty/") and report back to him.

Go take a look at the bug thread in launchpad, sign-up if you aren't already registered there, and lend a hand. So far it seems only maybe one or two folks are actively involved.

---

### Post by VastOne on 2009-06-17
I am beginning to believe this an overclock or a over heating issue.

My system(s) are identical images. I have a Phenom 940 Black that has
run stable for 4 months. When a customer defaulted on a 955 Phenom
chassis with the same specs (except the 955) I kept it and imaged the
940 to the same exact drive on the 955

Both ran great for 1 month.

Then I got into overclocking.  The 955 has handled everything I have
thrown at it and has never frozen.  It also maintains a very good core
temp of 44

Since an Update Manager update one week ago, the 940 has done nothing
but freeze and/or reboot with no discernible pattern. It could happen in
45 minutes, 4 hours or 10 hours. It could happen with only term running
20 apps running or nothing at all sitting completely idle.

Until today.  I turned off the overclock on this 940 and have seen
stable system again. My core temp with the over clock on was a wierd
one.  Using gKrellM I would see core 1 and 3 at 41-42 but core 2 at
51-53.  Overclock off now I see all core temps at 39-40

The only other thing I can add to this is that I am getting the
gdm_slave_xioerror_handler in Xorg after a freeze/reboot.

And that since that same update a week ago, on both machines, neither
monitors go into a dark mode with inactivity like they used to.

I am running kernel:

2.6.29.4-candela #1 SMP Tue May 26 22:26:20 CDT 2009 x86_64 GNU/Linux

I stay completely updated.

In both machines I have the same make and model nVidia 9500 GT running
driver 185.18.14

Both with the same ram

Hoping some of this helps....

---

### Post by Chemical Imbalance on 2009-06-18
> **Entropy_Sam said:**
> Why not look at Linux Mint - keep Ubuntu's user-friendliness, but with less restriction on restricted formats?


Mint is Ubuntu...same kernel, same packages.  It just adds minor UI tweaks and some restricted packages.  Therefore, it will probably have the same bugs as Ubuntu.

I've been using linux for a few years now so user-friendliness isn't a must.

Good luck to everyone.  Debian works great so far.

---

### Post by pilbender on 2009-06-18
I had to fsck my file system again today.  I can't even leave the house without a boot CD so I can recover from this stuff.  Even if the freeze issue is ever resolved, I'm not sure I'd even want to stay on this distribution.  It's not reliable in any case.  I had no freeze on this either.  I did a normal shutdown.

I checked the bug reports Laysan_A pointed out.  The posts on that bug don't seem to be any more meaningful than what we're talking about on this thread.  I hate to add more noise.  As a developer I don't see how to make any more sense out of what's happening for this bug.

All of this seems related even though there are a wide variety of symptoms.  I'm so frustrated with this.  I make a living on my computer.  It's a hobby too, but this is critically important to me.  It's bad business to put your eggs in this kind of basket.

The only thing I need now, is to get Evolution working on Slackware, or some Exchange compatible email client.  I hate to lose, but my practical side is more than ready to give up on this.

scott

---

### Post by Mirge on 2009-06-18
> **pilbender said:**
> I had to fsck my file system again today.  I can't even leave the house without a boot CD so I can recover from this stuff.  Even if the freeze issue is ever resolved, I'm not sure I'd even want to stay on this distribution.  It's not reliable in any case.  I had no freeze on this either.  I did a normal shutdown.

I checked the bug reports Laysan_A pointed out.  The posts on that bug don't seem to be any more meaningful than what we're talking about on this thread.  I hate to add more noise.  As a developer I don't see how to make any more sense out of what's happening for this bug.

All of this seems related even though there are a wide variety of symptoms.  I'm so frustrated with this.  I make a living on my computer.  It's a hobby too, but this is critically important to me.  It's bad business to put your eggs in this kind of basket.

The only thing I need now, is to get Evolution working on Slackware, or some Exchange compatible email client.  I hate to lose, but my practical side is more than ready to give up on this.

scott

No offense scott, but of your 19 "beans" it seems like dang near half are you ranting about Ubuntu. I can definitely understand your frustration, as I experienced those damned freezes too when I ran Ubuntu 9.04..... I switched to Kubuntu 9.04 on 4 comps, not a single one has had ANY freezing issues with the same programs installed. They use varying hardware, some ATi, some nVidia, Intel, etc. I don't honestly know why Kubuntu worked out for me, but it does extremely well... and I prefer KDE to GNOME anyway, so it's an extra bonus for me :).

Good luck on whichever distro you pick.

---

### Post by pilbender on 2009-06-18
> **Mirge said:**
> No offense scott, but of your 19 "beans" it seems like dang near half are you ranting about Ubuntu. I can definitely understand your frustration, as I experienced those damned freezes too when I ran Ubuntu 9.04..... I switched to Kubuntu 9.04 on 4 comps, not a single one has had ANY freezing issues with the same programs installed. They use varying hardware, some ATi, some nVidia, Intel, etc. I don't honestly know why Kubuntu worked out for me, but it does extremely well... and I prefer KDE to GNOME anyway, so it's an extra bonus for me :).

Good luck on whichever distro you pick.

I actually do take offense to this.  I've spent a lot of time on this and done my best to supply as much information as I can for others to correlate.  In addition, I've read through everyone else's posts as well.  I have followed most of the suggestions here and many have followed mine.  So far we are 100% failures.  No one has come up with a slam dunk reason to end this.  No one has definitively identified the problem we are facing.

I am not new to Linux.  But I guess you knew this because you read through my measly 19 posts.  I guess you out rank me then with more posts?  I'm okay with that.

There are a lot of people here who have had filesystem corruption issues as well as freezes.  Sometimes they go hand in hand.  I believe it is critically important that people know about filesystem corruption, freezes and any other behaviors as we try to sort this out.

Consider yourself extremely fortunate you haven't had to face 6 weeks or more of this.  It is very disruptive to productivity.

Mirge, you may have a point though.  Perhaps I shouldn't post anymore.  Perhaps I should stop sharing my experiences.  Perhaps I have lost all objectivity.  I am okay with that too.

No freezes after the fsck.  I also applied the latest updates this morning.  Over 5 hours, crossing my fingers and hoping for a miracle.

R. Scott Smith

---

### Post by Mirge on 2009-06-18
> **pilbender said:**
> I actually do take offense to this.  I've spent a lot of time on this and done my best to supply as much information as I can for others to correlate.  In addition, I've read through everyone else's posts as well.  I have followed most of the suggestions here and many have followed mine.  So far we are 100% failures.  No one has come up with a slam dunk reason to end this.  No one has definitively identified the problem we are facing.

I am not new to Linux.  But I guess you knew this because you read through my measly 19 posts.  I guess you out rank me then with more posts?  I'm okay with that.

There are a lot of people here who have had filesystem corruption issues as well as freezes.  Sometimes they go hand in hand.  I believe it is critically important that people know about filesystem corruption, freezes and any other behaviors as we try to sort this out.

Consider yourself extremely fortunate you haven't had to face 6 weeks or more of this.  It is very disruptive to productivity.

Mirge, you may have a point though.  Perhaps I shouldn't post anymore.  Perhaps I should stop sharing my experiences.  Perhaps I have lost all objectivity.  I am okay with that too.

No freezes after the fsck.  I also applied the latest updates this morning.  Over 5 hours, crossing my fingers and hoping for a miracle.

R. Scott Smith

What exactly did you take offense to? Me saying you had 19 posts? Where did I imply that I "out-rank" you or anybody?

[quote=Mirge]
No offense scott, but of your 19 "beans" it seems like dang near half are you ranting about Ubuntu. I can definitely understand your frustration, as I experienced those damned freezes too when I ran Ubuntu 9.04..... I switched to Kubuntu 9.04 on 4 comps, not a single one has had ANY freezing issues with the same programs installed. They use varying hardware, some ATi, some nVidia, Intel, etc. I don't honestly know why Kubuntu worked out for me, but it does extremely well... and I prefer KDE to GNOME anyway, so it's an extra bonus for me :smile:.

Good luck on whichever distro you pick.
[/quote]

If you go through the pages, you'll see my posts earlier in the thread too where I experienced the dreaded freezing, and I offered the solution that I went with that's worked for me for quite a while now. I make my living using these computers as well, so downtime is not an option either.

Don't know WHY you are so upset, and saying you're leaving the boards now. Your choice though, I'm not gonna beg you to stay or tell you to leave. You're a grown man (I assume), you can make your own decisions.

BTW, I don't consider the following "helpful" or "informative"...

[quote=pilbender]
I had to fsck my file system again today. I can't even leave the house without a boot CD so I can recover from this stuff. Even if the freeze issue is ever resolved, I'm not sure I'd even want to stay on this distribution. It's not reliable in any case. I had no freeze on this either. I did a normal shutdown.

I checked the bug reports Laysan_A pointed out. The posts on that bug don't seem to be any more meaningful than what we're talking about on this thread. I hate to add more noise. As a developer I don't see how to make any more sense out of what's happening for this bug.

All of this seems related even though there are a wide variety of symptoms. I'm so frustrated with this. I make a living on my computer. It's a hobby too, but this is critically important to me. It's bad business to put your eggs in this kind of basket.

The only thing I need now, is to get Evolution working on Slackware, or some Exchange compatible email client. I hate to lose, but my practical side is more than ready to give up on this.

scott
[/quote]

[quote=pilbender]
I need an ending to this. This whole thing is insane.
scott
[/quote]

[quote=pilbender]
I'm on my 9.04 system still. I've started to track down the pieces I need for Slackware. I haven't had a freeze yet, but I'm about done with all this. The only things I haven't put on Slackware are Teamviewer running through Wine and Evolution.

I can even live without Evolution for Exchange access, as I can use the web interface. Everything else is good on Slackware and I don't have freezes on that Distro.

I use Teamviewer all the time through Wine. If I get all this done, that will be it. Unless a solution is found damn quick.

scott
[/quote]

Regardless, I apologize if I upset you. Again, good luck w/ whatever distro you end up choosing.

---

### Post by Laysan_A on 2009-06-18
@pilbender

Try not to take Mirge's comments too personally. He obviously doesn't like your attitude, and called you on it, in what may have been an ungracious manner, but it's really no biggie.

All of us who continue to experience this issue are frustrated. Mirge is simply basking in the peace of a stable system now. 

I'm no fan of complaining, but I really do understand your feelings. It's hard not to feel frustrated, and equally difficult not to express it. It's not as if there aren't real problems with this release, after all. You're not just being a troll.

There are a lot of good people working on (K)Ubuntu though, and I feel certain this issue will get solved soon. 

Oh, and Mirge, I don't know how your system got fixed either. I've been using K from the initial upgrade. You're just extremely lucky, I guess (send some of that my way).

---

### Post by Mirge on 2009-06-18
Any issues that I experience now are all with Firefox 3.0.11 and the Firefox 3.5 beta..... but more specifically, I only experience those issues when I am viewing a page that uses Flash. I'm using the Adobe Flash plugin from the repo's...

I didn't think I was being harsh in what I said. I just really enjoy Ubuntu and sincerely appreciate the efforts of the developers who participate. Being a developer, I can relate to the massive amount of work that must go into this. Like many others here, I hold Ubuntu pretty close to heart, and hearing people essentially call it a piece of junk & threaten to "not use it" because it doesn't work for them... well, my advice to that is DON'T use it if it's causing you that much grief and downtime! Seriously... if Ubuntu (Kubuntu in my case) caused me downtime, I wouldn't be able to *afford* to use it.

4 clean installs, all using Ext4 filesystem on 4 diff computers with different hardware.. Kubuntu 9.04. Maybe I am just extremely lucky, but I don't have a single complaint, other than the wireless network manager widget doesn't work nearly as well as wicd ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)) for me!

---

### Post by VastOne on 2009-06-19
> **Mirge said:**
> Any issues that I experience now are all with Firefox 3.0.11 and the Firefox 3.5 beta..... but more specifically, I only experience those issues when I am viewing a page that uses Flash. I'm using the Adobe Flash plugin from the repo's...

I didn't think I was being harsh in what I said. I just really enjoy Ubuntu and sincerely appreciate the efforts of the developers who participate. Being a developer, I can relate to the massive amount of work that must go into this. Like many others here, I hold Ubuntu pretty close to heart, and hearing people essentially call it a piece of junk & threaten to "not use it" because it doesn't work for them... well, my advice to that is DON'T use it if it's causing you that much grief and downtime! Seriously... if Ubuntu (Kubuntu in my case) caused me downtime, I wouldn't be able to *afford* to use it.

4 clean installs, all using Ext4 filesystem on 4 diff computers with different hardware.. Kubuntu 9.04. Maybe I am just extremely lucky, but I don't have a single complaint, other than the wireless network manager widget doesn't work nearly as well as wicd ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)) for me!

I agree with you.  I have 2 machines with one acting up and I solved it. It is chronicled in this thread. I know it is not the same as everyone else but I do think it is a link to the ultimate solution. And that is what we can all hope for, give a bit of our experiences and solutions and ultimately the answer will be found.  I hope I hope I hope. And I will not give in or up. Been using Ubuntu for 2 years now and though I have never been this frustrated, I am also even more profoundly sure that I will never turn my back on such a great OS and community.

VastOne

---

### Post by Entropy_Sam on 2009-06-19
> **Mirge said:**
> Any issues that I experience now are all with Firefox 3.0.11 and the Firefox 3.5 beta..... but more specifically, I only experience those issues when I am viewing a page that uses Flash. I'm using the Adobe Flash plugin from the repo's...
 
Just wondering if you've checked whether the AppArmor module is loading at startup, as
a) AppArmor isn't loading for me, and
b) FF+Flash causes a system-wide crash.
 
I **strongly** suspect that my nVidia drivers are conflicting with AppArmor at startup, preventing AppArmor from starting (it loaded when I used the open source ati drivers on the same install).
 
If it loaded properly, I suspect it would safeguard my system from these crashes by closing FF quickly if it starts to hog resources aggressively.

---

### Post by Mirge on 2009-06-19
I actually meant to put Firefox 3.0.10.... I just upgraded to FF 3.0.11 last night..... and so far, I've actually not had any problems! Hopefully that trend continues... I'd be extremely happy.

---

### Post by throwingks on 2009-06-19
Ubuntu 9.04 x86_64

2.6.28-13-generic

FF3.0.11

Opera 9.64 Build 2480

nVidia 185.18.14

AMD II X4 940
4GB RAM

Still freezes. :(

---

### Post by bearozo on 2009-06-20
Hi you all :D

I posted here way back, havn't had freeze since I changed to a monitor with proper plug and play (about a month and half ago) this is what happened to my xorg.conf when I plugged the new monitor in.

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder58)  Fri Apr 17 00:40:57 PDT 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Tue Apr 21 23:48:22 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nokia 447Xa.."
    HorizSync       30.0 - 91.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 LE"
EndSection

Section "Screen"

# Removed Option "metamodes" "1024x768 +0+0"
# Removed Option "metamodes" "1024x768_85 +0+0"
# Removed Option "metamodes" "1024x768 +0+0; 1024x768_85 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1024x768_85 +0+0; 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```So maybe people that still have problems with nVidia and freezes should have a look at their monitor settings, hope this will help some of those with the problems.

I forgot to say I used the instructions in this video, which btw. triggered freezes every time
I played it so I used my lappy to follow the vid.

This might help as well if you know the specs of yer monitor: [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

and a ```
sudo ddcprobe
``` will also give info about yer monitor.

---

### Post by test-virus on 2009-06-20
ok guys this is what i gots going ive read and used that box up in the right hand side that no one uses they just post frist so i thought i would add whats i got my system and alot of things i ran acorss here is my system in lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8T890 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.2 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:0a.0 Ethernet controller: Atheros Communications Inc. AR5413 802.11abg NIC (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GTX (rev a1)

i have duel boot vista and ubuntu 9.04 nivida drivers 180 i have tryed 173 locks up too my computer also likes to kick my wifi and lan connection to the curb so far its been up for 30 mins with out lock up let me know what you guys think it is please =D

---

### Post by Entropy_Sam on 2009-06-20
> **Mirge said:**
> I actually meant to put Firefox 3.0.10.... I just upgraded to FF 3.0.11 last night..... and so far, I've actually not had any problems! Hopefully that trend continues... I'd be extremely happy.

Hmm, I have Firefox 3.0.11 installed, Kernel 2.6.29.4, 64-bit Flash alpha from Adobe Labs and the latest nVidia drivers. I run the Gnome Display manager,  AppArmor module fails to load at startup and the only freezes I get are running Flash (both the 64-bit wrappers from the repositories and latest alphas from Adobe) in Firefox...

After experimenting with multiple browsers, I've eventually settled with Flock. Opera was quite nice, but just a little too far out of my comfort zone.

---

### Post by Mirge on 2009-06-20
> **Entropy_Sam said:**
> Hmm, I have Firefox 3.0.11 installed, Kernel 2.6.29.4, 64-bit Flash alpha from Adobe Labs and the latest nVidia drivers. I run the Gnome Display manager,  AppArmor module fails to load at startup and the only freezes I get are running Flash (both the 64-bit wrappers from the repositories and latest alphas from Adobe) in Firefox...

After experimenting with multiple browsers, I've eventually settled with Flock. Opera was quite nice, but just a little too far out of my comfort zone.

Firefox is still a bit slow, I'm gonna check out Flock, thanks!

The "Looking up <insert domain here>" taking 30+ seconds gets old sometimes..

---

### Post by Bealer on 2009-06-21
> **Chemical Imbalance said:**
> Mint is Ubuntu...same kernel, same packages.  It just adds minor UI tweaks and some restricted packages.  Therefore, it will probably have the same bugs as Ubuntu.

I've been using linux for a few years now so user-friendliness isn't a must.

Good luck to everyone.  Debian works great so far.

It does actually use a different kernel, or at least doesn't upgrade it anywhere near as much as Ubuntu does in the lifetime of a release.

The packages, are obviously, also different. It also adds in additional applications such as a different upgrade manager etc...

From my experience, when Ubuntu is freezing, I try Mint, and it didn't freeze. Which is why I skipped out 8.10. I've got Jaunty running now, but again, it's freezing. Of the 3 pc's and 2 laptops, the laptops are all ok. And one pc is ok. The Core2Duo pc's both freeze using a fresh install.

---

### Post by Johnny B on 2009-06-21
i had many freezes my first month with jaunty mainly from deleting files. I have since downgraded to ext3 with no problems

---

### Post by Entropy_Sam on 2009-06-21
DAMN!

After changing browsers from Firefox, I didn't have a crash in 4 weeks and just now I had one at startup - full seizure but for the mouse, and a screen the flickers occasionally. My desktop screenlets hadn't even finished loading...

seems entirely random, as one Alt+SqsRq,R,E,I,S,U,B and one full reboot later, everything seems to be running "cool as der cucumber"...

---

### Post by Chemical Imbalance on 2009-06-21
> **Bealer said:**
> It does actually use a different kernel, or at least doesn't upgrade it anywhere near as much as Ubuntu does in the lifetime of a release.

The packages, are obviously, also different. It also adds in additional applications such as a different upgrade manager etc...

From my experience, when Ubuntu is freezing, I try Mint, and it didn't freeze. Which is why I skipped out 8.10. I've got Jaunty running now, but again, it's freezing. Of the 3 pc's and 2 laptops, the laptops are all ok. And one pc is ok. The Core2Duo pc's both freeze using a fresh install.

The base system is the same, as are most of the packages.

He can only handle so much on his own, so Ubuntu is a good base.

Mint does have a few custom apps though.

If Mint "fixes" your freezing it is probably by virtue of using an older kernel.  Likewise, Intrepid doesn't freeze for me.

---

### Post by sdbrogan on 2009-06-23
I had this freezing problem on a single-core machine : an AMD Sempron 3000+ with nVidia GeForce FX5500 graphics card.  Changing neither the nVidia drivers nor the kernel helped (though I didn't try any mainline kernel).

---

### Post by oookkkooo on 2009-06-23
Might not be relevant to this thread but for those with nVidia Corporation G72 [GeForce 7300 SE] (rev a1) this helped with my random freezes.

[http://forums.nvidia.com/index.php?showtopic=92268](http://forums.nvidia.com/index.php?showtopic=92268)

---

### Post by u-slayer on 2009-06-23
I thought I'd let you guys know that I've solved my freezing problem in Jaunty the same way I did in Hardy. I update my nvidia drivers:

I now use 185:
[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

---

### Post by Chemical Imbalance on 2009-06-23
> **u-slayer said:**
> I thought I'd let you guys know that I've solved my freezing problem in Jaunty the same way I did in Hardy. I update my nvidia drivers:

I now use 185:
[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

My 8300 still freezes with the latest 185's.

---

### Post by cbhargava on 2009-06-23
After June 22 compiz update on Jaunty, I see the application turn dark. for example when I hit reply in evolution, it would freeze and remain dark for a minute and then the reply window pops up. Also in Firefox, in print dialog box, when I change printer from physical printer to file printer (ps / pdf) I see the same behavior. :rolleyes:

-cbhargava

---

### Post by Laysan_A on 2009-06-24
Well, I tried a .29-5 generic kernel and it didn't work out too well, so I've been back with my .30 ultimate kernel for the past four days (no sudden freezes to black). 

Chemical Imbalance went for a week, I think it was, on the .30 without a freeze to black, so though part of me is secretly hoping some update or other (or maybe just the grace of god) has accidentally fixed it, I'm just going about my business, taking it easy, trying not to think about it, taking a break from all the frustration. 

Until the next time...:)

Oh, it might help matters (or it might not...) if when you have a crash you try to describe whether it was a sudden freeze with a black screen and no warning, or if it was accompanied by heavy processor use and system slowdown just prior to the freeze (there might be a couple different things going on).

---

### Post by cbhargava on 2009-06-24
Hi,
No warnings, no CPU load, no network usage and no disk access. Looks like it happens when an application tries to bring up a save/save as dialog.

Thanks.

> **Laysan_A said:**
> 
Oh, it might help matters (or it might not...) if when you have a crash you try to describe whether it was a sudden freeze with a black screen and no warning, or if it was accompanied by heavy processor use and system slowdown just prior to the freeze (there might be a couple different things going on).

---

### Post by Chemical Imbalance on 2009-06-24
My freezes aren't to a black screen, rather my mouse no longer moves and my keyboard stops functioning about a minute later. 

Then my screen just freezes and all background apps stop.

I can still see everything, no black screen.

---

### Post by JohnnyVW on 2009-06-25
Here's my experience.

I upgraded from 8.04 to 8.10 to 9.04 through Synaptic.  Ever since I went to Jaunty, my PC randomly starts.  It gets the spash screen, the progress bar makes it to the end, the screen changes resolution for Gnome, then nothing.  Sometimes I get the mouse pointer, then nothing.  Sometimes I get the "busy" wheel, then nothing...  Once it boots, I can run it for days, and it runs great.  No freezes after it finally boots.  The only way to get it to boot after the failure is to hit the reset button.  

I've checked the logs and nothing stands out and grabs me.  My wife is getting really tweaked about this too...  (yikes!)

This is a dual-boot system (XP/Jaunty).  I do have am nVidia GeForce 7300...  I never had a problem with Hardy on this machine, and am regretting upgrading!  :(

All these resets can't be good for my hard drives and PC!  

Cripes, it took 5 tries to get it to boot this time.  It has booted the first time for the past three days.  It's intermittent, but it borks more often than not.

XP boots _*every*_ time.

Any files, logs, info or whatever I can share to help solve this, let me know!

---

### Post by bearozo on 2009-06-25
Have you tried REISUB instead of reset ?

CTRL+ALT+SySRq (PrintScrn)  keep holding CTRL+ALT and hit R+E+I+S+U+B.

[http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart).


> **JohnnyVW said:**
> Here's my experience.

I upgraded from 8.04 to 8.10 to 9.04 through Synaptic.  Ever since I went to Jaunty, my PC randomly starts.  It gets the spash screen, the progress bar makes it to the end, the screen changes resolution for Gnome, then nothing.  Sometimes I get the mouse pointer, then nothing.  Sometimes I get the "busy" wheel, then nothing...  Once it boots, I can run it for days, and it runs great.  No freezes after it finally boots.  The only way to get it to boot after the failure is to hit the reset button.  

I've checked the logs and nothing stands out and grabs me.  My wife is getting really tweaked about this too...  (yikes!)

This is a dual-boot system (XP/Jaunty).  I do have am nVidia GeForce 7300...  I never had a problem with Hardy on this machine, and am regretting upgrading!  :(

All these resets can't be good for my hard drives and PC!  

Cripes, it took 5 tries to get it to boot this time.  It has booted the first time for the past three days.  It's intermittent, but it borks more often than not.

XP boots _*every*_ time.

Any files, logs, info or whatever I can share to help solve this, let me know!

---

### Post by gtaluvit on 2009-06-25
I'm also seeing lockups on a Dell Mini 12 running Jaunty however, I'm able to recover. I lose audio, keyboard, mouse, etc. but if I press the power button or plug/unplug something from USB, everything comes back to life. I have to escape out the shutdown screen but at least I can work again. Nothing in dmesg points to a particular reason.

---

### Post by Laysan_A on 2009-06-25
> I can still see everything, no black screen. 

Weird...

How's your processor load, any sluggishness just before it freezes?

I just had two freezes to black in a row. Both happened soon after a reboot (most of mine have happened within about thirty minutes of a boot). The first happened as I removed a hd monitor from my panel. It disappeared, and then so did the screen. The second happened soon after I'd rebooted from the first. I just had time to start the package manager for three security updates. I started the installation and I lost it (now the packages won't update). 

Well, I'm hoping for another five days (at least).

---

### Post by Chemical Imbalance on 2009-06-25
> **Laysan_A said:**
> Weird...

How's your processor load, any sluggishness just before it freezes?

I just had two freezes to black in a row. Both happened soon after a reboot (most of mine have happened within about thirty minutes of a boot). The first happened as I removed a hd monitor from my panel. It disappeared, and then so did the screen. The second happened soon after I'd rebooted from the first. I just had time to start the package manager for three security updates. I started the installation and I lost it (now the packages won't update). 

Well, I'm hoping for another five days (at least).

I've went back to the .28 kernel as it isn't too bad.

I'm getting at least a few hours before it freezes.  I always shut my desktop off at night when I'm done, to save energy--many times it doesn't freeze at all.

I can get around 15 hours or more some days and no freezes.  Some days I don't even go 30 minutes.


It does not get sluggish at all before the freeze and my processor load is normal if not very light.

The only time my processor load is excessive is if flash is running, but that's normal for everyone as flash just plain sucks.

I've heard people with nvidia drivers getting similar issues.  I'm fairly sure you and I aren't experiencing the same bug.

---

### Post by dufm04 on 2009-06-25
Hi everyone. 

My first freeze was when I tried to play a movie with vlc. After to this, my laptop never loaded jaunty again. I tried to use recovery mode boot with dpkg and xfix options without sucess. Then I reinstalled jaunty and all runs very well (included movies but with totem!).

But system collapsed just after first upgrade (to kernel 2.6.28-13 from 2.6.28-11) and trying to activate privative ati drivers. The freeze seen like small ubuntu logos on black screen and system never can get in and load graphics.

Following are the specifications of my laptop and Jaunty installation....

Acer Aspire 4535
AMD Turion X2 RM-72, 2.1 GHz, 1MB L2 Cache
ATI Radeon HD 3200 Graphics
14.0' HD Acer CineCrystal LED LCD 
320 GB Memory in HDD
4 GB RAM

Dual Boot: 
XP (50GB)
Jaunty 9.04 AMD 64 bits, ext3 (270GB)

In this moment I'm thinking seriously come back to hardy LTS.

Cheers from Colombia. Bye.

---

### Post by gradinaruvasile on 2009-06-25
Here s another one:

Dell D630 2 GB RAM/160 GB HDD/Nvidia Quadro NVS 135M (Dual boot)
Hardy, Intrepid ran well.

But with jaunty i had some problems:
First a black screen no cursor at boot. Had to press the shutdown button for a few secs to turn off. Then I couldnt mount the Jaunty's partition (NFS stale file lock or something and i tried everything i could google up but couldnt get rid of that - btw it was JFS - formatted it back to ext3).
I had installed Intrepid on another partition and i started it and ran fine. Then i upgraded it too to jaunty.
Then in a few days i started getting freezes (before them the screen became garbled, and froze up).

I upgraded today to the proprietary 185.18.14 drivers and no freeze since about 6 hours. The video card fan started up in full speed for about 1-2 mins at startup but then dropped the speed to a "quiet" level. Might have been a temp issue after all.

In contrast i have my work desktop - Dell Optiplex 755 / Core2Duo E6550 / 2 GB RAM / 200 GB HDD / Nvidia Quadro NVS 285 /128 MB Vid card Dual Monitors
I played games on it (wined and native), ran virtualboxed windozes, played videos with vlc/mplayer/totem, used skype with webcam, tried quite a few programs, installed proprietary nvidia drivers (2-3 versions), disabled/enabled one of the monitors a few times,  accessed it through VPN/ssh/vnc, running compiz all the time. And no pulseaudio...

It has an uptime of 45 days and counting.....

Not using the 13 kernel - if it aint broke dont fix it...

---

### Post by Chemical Imbalance on 2009-06-25
> **gradinaruvasile said:**
> Here s another one:

Dell D630 2 GB RAM/160 GB HDD/Nvidia Quadro NVS 135M (Dual boot)
Hardy, Intrepid ran well.

But with jaunty i had some problems:
First a black screen no cursor at boot. Had to press the shutdown button for a few secs to turn off. Then I couldnt mount the Jaunty's partition (NFS stale file lock or something and i tried everything i could google up but couldnt get rid of that - btw it was JFS - formatted it back to ext3).
I had installed Intrepid on another partition and i started it and ran fine. Then i upgraded it too to jaunty.
Then in a few days i started getting freezes (before them the screen became garbled, and froze up).

I upgraded today to the proprietary 185.18.14 drivers and no freeze since about 6 hours. The video card fan started up in full speed for about 1-2 mins at startup but then dropped the speed to a "quiet" level. Might have been a temp issue after all.

In contrast i have my work desktop - Dell Optiplex 755 / Core2Duo E6550 / 2 GB RAM / 200 GB HDD / Nvidia Quadro NVS 285 /128 MB Vid card Dual Monitors
I played games on it (wined and native), ran virtualboxed windozes, played videos with vlc/mplayer/totem, used skype with webcam, tried quite a few programs, installed proprietary nvidia drivers (2-3 versions), disabled/enabled one of the monitors a few times,  accessed it through VPN/ssh/vnc, running compiz all the time. And no pulseaudio...

It has an uptime of 45 days and counting.....

Not using the 13 kernel - if it aint broke dont fix it...

I also have a D630, but with an Intel chipset.  It doesn't freeze.  I wonder if that has any significance?

---

### Post by karamu on 2009-06-26
I think Jaunty just killed my machine.

I too have been suffering from these horrible freezes- I posted earlier on this thread. There were intermittent but generally happened within a minute or so after login- sometimes launching Firefox, sometimes not doing anything at all but generally if it was OK for a few minutes I knew it would continue to run OK.

When it did freeze the only thing I could was hit the hard reset button on the case and boot again. I tried the REISUB technique but it didn't work.

Well, last night I booted the machine, it froze, rebooted it and it let me launch Firefox OK, started to read the news then it froze- hit the reset button and....... nothing!

The machine now does not start up when powered up- the power comes on and I can hear the initial spin of the drive but there is no video output to the monitor (it stays in power save) and I don't even get the motherboard splash screen- nothing.

I don't think it is even just the video output- I don't hear the spin of the drive I would if the machine was booting (I have a kind of old and noisy drive- it is pretty obvious when it is booting)- just the initial power up.

I will try stripping and cleaning out all the connectors etc on the motherboard and will see if I can get it to life again but I doubt it will work- pretty ****ing annoying considering I just built the machine 6 months ago...!!!

A friend of mine has an old machine I can have- if it comes to that I will be installing linux again but NOT Ubuntu- it has totally lost my trust after this fiasco with Jaunty.

Any suggestions about good alternative distros to try? I do prefer a Gnome based system (tried Kubuntu but didn't like KDE).

---

### Post by Mirge on 2009-06-26
> **karamu said:**
> I think Jaunty just killed my machine.

I too have been suffering from these horrible freezes- I posted earlier on this thread. There were intermittent but generally happened within a minute or so after login- sometimes launching Firefox, sometimes not doing anything at all but generally if it was OK for a few minutes I knew it would continue to run OK.

When it did freeze the only thing I could was hit the hard reset button on the case and boot again. I tried the REISUB technique but it didn't work.

Well, last night I booted the machine, it froze, rebooted it and it let me launch Firefox OK, started to read the news then it froze- hit the reset button and....... nothing!

The machine now does not start up when powered up- the power comes on and I can hear the initial spin of the drive but there is no video output to the monitor (it stays in power save) and I don't even get the motherboard splash screen- nothing.

I don't think it is even just the video output- I don't hear the spin of the drive I would if the machine was booting (I have a kind of old and noisy drive- it is pretty obvious when it is booting)- just the initial power up.

I will try stripping and cleaning out all the connectors etc on the motherboard and will see if I can get it to life again but I doubt it will work- pretty ****ing annoying considering I just built the machine 6 months ago...!!!

A friend of mine has an old machine I can have- if it comes to that I will be installing linux again but NOT Ubuntu- it has totally lost my trust after this fiasco with Jaunty.

Any suggestions about good alternative distros to try? I do prefer a Gnome based system (tried Kubuntu but didn't like KDE).

Yikes!! Hope everything is ok bud. I've heard good things about Fedora... and some like OpenSuSE. Could always try Ubuntu 8.10...

---

### Post by sub_acoustic on 2009-06-26
I've also got these freezes, (and hopefully I can post this before it freezes again).  Intel Pentium M 1.8GHz, 1G RAM, ATI Radeon 9700.  I've had to disable compiz, when I tried reinstalling fglrx X would fail completely so I removed it.  Currently the computer locks up (can see every and move the cursor) about 10-20 minutes into use.

I have reason to believe that this is not a kernel issue though as my computer recently started freezing on a 8.10 install just in the last few weeks after some recent updates.  It would freeze on DVD play in VLC and on audio play in Amarok.  Part of my motivation to upgrade was to solve this although now the situation is worse.  

It seems like the processor is much busier and everything is much slower than it was on Intrepid.  On the upside I can still use my computer for a bit and the weather outside is too good to be stuck in front of a computer, although I am prohibited from doing any serious work.  

Not quite sure what I need to file a bug report.  Happy to wait for the updates that fix this in the meantime.  Everything else about Jaunty looks great, though it took a while how to figure out how to play mp3s again.

---

### Post by karamu on 2009-06-26
> **Mirge said:**
> Yikes!! Hope everything is ok bud. I've heard good things about Fedora... and some link OpenSuSE. Could always try Ubuntu 8.10...

Yeah, thinking about Fedora, and could go back to 8.10- I never had any problems before Jaunty- but feel kind of negative towards Ubuntu now......

---

### Post by Laysan_A on 2009-06-26
@Chemical Imbalance
> I've went back to the .28 kernel as it isn't too bad.

I'm getting at least a few hours before it freezes. I always shut my desktop off at night when I'm done, to save energy--many times it doesn't freeze at all.

I can get around 15 hours or more some days and no freezes.  Some days I don't even go 30 minutes.


It does not get sluggish at all before the freeze and my processor load is normal if not very light.

The only time my processor load is excessive is if flash is running, but that's normal for everyone as flash just plain sucks.

I've heard people with nvidia drivers getting similar issues.  I'm fairly sure you and I aren't experiencing the same bug.The pattern of your freezes sounds very similar to mine. The only differences seem to be that your mouse stops before the freeze and you retain your screen. I don't know what to think of the mouse, but perhaps whether or not the screen remains is a video flavor thing, unrelated to the cause.

What .28 kernel did you switch to. Is it the one the developer linked to on launchpad?

I like my .30 kernel. Though I can't exactly tell you why, I do know it's not freezing any more than my .28-13 was.

@sub-acoustic
> It seems like the processor is much busier and everything is much slower than it was on Intrepid. On the upside I can still use my computer for a bit and the weather outside is too good to be stuck in front of a computer, although I am prohibited from doing any serious work.This seems to me to be the "other" kind of freeze people are experiencing, characterized by heavy processor use and general sluggishness. My install seems faster than intrepid (as it's supposed to be). However, I did have your symptoms when I installed the .29-5 generic kernel. It was awful. I didn't experience any complete freezes with it, but then I didn't keep it around for very long. You might at least think about another kernel.

@dufm04
> But system collapsed just after first upgrade (to kernel 2.6.28-13 from 2.6.28-11) and trying to activate privative ati drivers. The freeze seen like small ubuntu logos on black screen and system never can get in and load graphics.You have the same chip on your mb that I do. I didn't have any success with the propriatary ati drivers either (even tried the 9.5 driver from ati), though mine at least loaded well enough. If you want to try, there's a guy who compiled the ati drivers for intrepid to work on jaunty. I'm pretty ignorant when it comes to manipulating my system, so I couldn't figure out how to install them, but if you'd like to give it a shot here's the link to his site:
[http://www.kdedevelopers.org/node/3942](http://www.kdedevelopers.org/node/3942)


Oh, by the way, I had another sudden freeze to black today within about five to ten minutes of booting.

---

### Post by Chemical Imbalance on 2009-06-26
> **Laysan_A said:**
> @Chemical Imbalance
The pattern of your freezes sounds very similar to mine. The only differences seem to be that your mouse stops before the freeze and you retain your screen. I don't know what to think of the mouse, but perhaps whether or not the screen remains is a video flavor thing, unrelated to the cause.

What .28 kernel did you switch to. Is it the one the developer linked to on launchpad?

I like my .30 kernel. Though I can't exactly tell you why, I do know it's not freezing any more than my .28-13 was.

.

Just using the updated Jaunty default kernel as it isn't any better or worse than .30 for me.  I have .30 installed, but I just boot into .28.

---

### Post by Chemical Imbalance on 2009-06-26
> **karamu said:**
> Yeah, thinking about Fedora, and could go back to 8.10- I never had any problems before Jaunty- but feel kind of negative towards Ubuntu now......

Mandriva is another good distro to try.  It's probably my second favorite.  It was the first one I ever used a few years ago on Linux, so it always has a special place for me.

---

### Post by alistair_mc on 2009-07-01
> **sub_acoustic said:**
> I've also got these freezes, (and hopefully I can post this before it freezes again).  Intel Pentium M 1.8GHz, 1G RAM, ATI Radeon 9700.  I've had to disable compiz, when I tried reinstalling fglrx X would fail completely so I removed it.  Currently the computer locks up (can see every and move the cursor) about 10-20 minutes into use.

I also got freezes like yours at my Pentium-M labtop. Grep in dmesg - if you find line(s) with "tsc clocksource unstable", try to change the kernel clocksource manually. Adding "hpet=force clocksource=hpet" to kernel boot options solved the problem for me.

Alistair

---

### Post by utkjamie on 2009-07-01
> **alistair_mc said:**
> I also got freezes like yours at my Pentium-M labtop. Grep in dmesg - if you find line(s) with "tsc clocksource unstable", try to change the kernel clocksource manually. Adding "hpet=force clocksource=hpet" to kernel boot options solved the problem for me.

I was able to fix the problem by upgrading to the 2.6.30 mainline kernel ([https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds)). That version of the kernel probably won't be part of the supported Ubuntu repositories until Karmic, though. Anyone who thinks October is a little too long to wait, might want to check out the mainline builds.

---

### Post by Laysan_A on 2009-07-01
Hi Y'All,

This is a copy of a post I just made over in launchpad.

Well, something odd happened today in my sys.log. I started the computer at about 10:56. It suddenly froze to biege (the color of my Firefox window) at 11:33. REISUB didn't work; I hit the reset button.


 Looking at my sys.log, there is a restart shown at 11:19, 11:24, and (the real one) at 11:33. What's up with that?


 There are no entries in my kernel.log from 11:08 to 11:33. What's up with that??


 I have the 2.6.30 ultimate kernel.


 Here's an excerpt from my sys.log:


 Jul  1 11:19:41 DESKTOP syslogd 1.5.0#5ubuntu3: [COLOR=Red]restart.[/COLOR]
Jul  1 11:19:41 DESKTOP anacron[3945]: Job `cron.daily' terminated
Jul  1 11:19:41 DESKTOP anacron[3945]: Job `cron.weekly' started
Jul  1 11:19:41 DESKTOP anacron[4863]: Updated timestamp for job `cron.weekly' to 2009-07-01
Jul  1 11:20:01 DESKTOP /USR/SBIN/CRON[4930]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jul  1 11:24:18 DESKTOP syslogd 1.5.0#5ubuntu3: [COLOR=Red]restart.[/COLOR]
Jul  1 11:24:18 DESKTOP anacron[3945]: Job `cron.weekly' terminated
Jul  1 11:24:18 DESKTOP anacron[3945]: Normal exit (2 jobs run)
Jul  1 11:30:01 DESKTOP /USR/SBIN/CRON[11432]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Jul  1 11:33:31 DESKTOP syslogd 1.5.0#5ubuntu3: [COLOR=Red]restart.[/COLOR]
Jul  1 11:33:31 DESKTOP kernel: Inspecting /boot/System.map-2.6.30-ultimate
Jul  1 11:33:31 DESKTOP kernel: Inspecting /usr/src/linux/System.map
Jul  1 11:33:32 DESKTOP kernel: Cannot find map file.
Jul  1 11:33:32 DESKTOP kernel: Loaded 56577 symbols from 47 modules.
Jul  1 11:33:32 DESKTOP kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul  1 11:33:32 DESKTOP kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 1 11:33:32 DESKTOP kernel: [ 0.000000] Linux version 2.6.30-ultimate (root@DESKTOP) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #1 SMP Sun Jun 14 02:22:59 PDT 2009
Jul  1 11:33:32 DESKTOP kernel: [    0.000000] Command line: root=UUID=64dd790a-876b-4a81-a0c4-d02b1a9442a8 ro quiet splash
Jul  1 11:33:32 DESKTOP kernel: [    0.000000] KERNEL supported cpus:
Jul  1 11:33:32 DESKTOP kernel: [    0.000000]   Intel GenuineIntel
Jul  1 11:33:32 DESKTOP kernel: [    0.000000]   AMD AuthenticAMD
Jul  1 11:33:32 DESKTOP kernel: [    0.000000]   Centaur CentaurHauls
Jul  1 11:33:32 DESKTOP kernel: [    0.000000] BIOS-provided physical RAM map:
Jul  1 11:33:32 DESKTOP kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
Jul  1 11:33:32 DESKTOP kernel: [    0.000000]  BIOS-e820:

---

### Post by Chemical Imbalance on 2009-07-01
Does anyone know what the kernel updates for Jaunty today are?
Had several today with headers, image, etc.

Does anyone know where the release notes are for updates?

---

### Post by colau on 2009-07-01
> **Chemical Imbalance said:**
> Does anyone know what the kernel updates for Jaunty today are?
Had several today with headers, image, etc.

Does anyone know where the release notes are for updates?
[http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/)

---

### Post by Chemical Imbalance on 2009-07-01
> **colau said:**
> [http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/](http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/)

Not exactly what I'm looking for, but thanks.

I'm looking for the list of changes in the updates for Jaunty, especially for the kernel updates that rolled out today for 2.6.28-13.

---

### Post by Laysan_A on 2009-07-02
I spent a couple hours looking, but I couldn't find that sucker anywhere. The closest I could find is package updates here [http://packages.ubuntu.com/jaunty-updates/base/linux-image-2.6.28-13-generic](http://packages.ubuntu.com/jaunty-updates/base/linux-image-2.6.28-13-generic)

Synaptic lists the 2.6.28-13.44 update, but packages.ubuntu.com lists .28-13.45 updates. There wasn't even a change log for the kernel update. Nowhere could I find a synopsis of recent updates.

---

### Post by Chemical Imbalance on 2009-07-04
Well, I guess it doesn't matter now.  The freezing still occurs.

---

### Post by JohnnyVW on 2009-07-05
> **bearozo said:**
> Have you tried REISUB instead of reset ?

CTRL+ALT+SySRq (PrintScrn)  keep holding CTRL+ALT and hit R+E+I+S+U+B.

[http://kember.net/articles/231/reisub-the-gentle-linux-restart](http://kember.net/articles/231/reisub-the-gentle-linux-restart).

Thanks for the tip!  Yeah, <ALT><SysRQ> R E I S U B does reboot the system.  I feel a lot better doing that than hitting RESET 3 or 4 times.  

It did it this morning.  It took 4 reboots to get it started.  Once started, it'll run for days without issue.

Once again, it sometimes will boot on the first try.

XP boots *every* time without issue.

I turned off autologin to see where it stops.  It stops between the splash screen's progress bar being at 100% and the login screen (the login screen never shows up).

I tried to ssh to it from another PC, but couldn't connect.  

Hardy ran so smooth...  Why did I upgrade?  

Any logs I can post to help?  I'm really wanting to avoid a fresh install...

Here's what's "in the box:"

Intel Core2Duo E4500 2.2GHz processor
ASUS P5GC-MX/1333 motherboard
1 GB DDR2 667 (PC-5300) SDRAM
nVidia 7300 GS 256MB video card
2X Western Digital WD1600AAJS 160GB SATA-2 hard drive

---

### Post by Laysan_A on 2009-07-05
[quote=JohnnyVW;7565996] I'm really wanting to avoid a fresh install...

Hi,

I can understand why you might not want to start from scratch, but it really sounds like you just have something missing, or maybe improperly configured, from your upgrade/install. Have you tried just installing a new kernel? You never know, it might work for you, and it's not too involved if you use one of the precompiled ones from the ubuntu kernel source. If it doesn't work, no harm, no foul.

---

### Post by bearozo on 2009-07-06
What type of monitor do you have ? I had problem configuring my old KFC (smile) monitor when I changed to a newer Nokia with proper plug and pray all problems disappeared.


> **JohnnyVW said:**
> Thanks for the tip!  Yeah, <ALT><SysRQ> R E I S U B does reboot the system.  I feel a lot better doing that than hitting RESET 3 or 4 times.  

It did it this morning.  It took 4 reboots to get it started.  Once started, it'll run for days without issue.

Once again, it sometimes will boot on the first try.

XP boots *every* time without issue.

I turned off autologin to see where it stops.  It stops between the splash screen's progress bar being at 100% and the login screen (the login screen never shows up).

I tried to ssh to it from another PC, but couldn't connect.  

Hardy ran so smooth...  Why did I upgrade?  

Any logs I can post to help?  I'm really wanting to avoid a fresh install...

Here's what's "in the box:"

Intel Core2Duo E4500 2.2GHz processor
ASUS P5GC-MX/1333 motherboard
1 GB DDR2 667 (PC-5300) SDRAM
nVidia 7300 GS 256MB video card
2X Western Digital WD1600AAJS 160GB SATA-2 hard drive

---

### Post by Trapper on 2009-07-06
> Originally Posted by bearozo
Have you tried REISUB instead of reset ?

CTRL+ALT+SySRq (PrintScrn) keep holding CTRL+ALT and hit R+E+I+S+U+B.

[http://kember.net/articles/231/reisub-the-gentle-linux-restart]("http://kember.net/articles/231/reisub-the-gentle-linux-restart")


Are you sure it's:

CTRL+ALT+SySRq (PrintScrn) keep holding CTRL+ALT and hit R+E+I+S+U+B

I ask because the link seems to indicate it's:

Hold ALT+SySRq (PrintScrn) and type R+E+I+S+U+B

> Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB will get you safely restarted. REISUO will do a shutdown rather than a restart.

Of course, doing ALT+SySRq (PrintScrn) and type R+E+I+S+U+B without 3 hands might be a bit tricky so I consider the link might be giving the incorrect info. Plus you get the print screen popup box :-)
Trapper

---

### Post by ProphetOfDoom on 2009-07-06
How did I not find this thread earlier I wonder - I've just started a new one of my own on this subject.

The last few weeks I've been getting freezes with jaunty that leave me no option but to reboot by hitting the power button.

I get random freezes that can occur a minute or an hour after booting. It happens sooner rather than later when I do something graphically intensive like use gimp with my wacom tablet.

System is up to date with patches, I upgraded rather than a clean install.

I tried fedora 11 on the same PC and its better but I got the same thing last night suggesting it might be a common driver. kernel is much higher version in fedora. 

I've got AMD athlon, radeon 9200, ext3 filesystems. no error in any logs

---

### Post by Jebtrix on 2009-07-06
Just throwing it out there, maybe try disabling ACPI support in the BIOS....

---

### Post by jsravn on 2009-07-06
I too am experiencing this and it's a minor relief to see I'm not the only one.

The freezes started about 1 to 2 weeks ago on jaunty. I thought it might be the machine so I swapped machines at work. Same deal. Then I got fed up with ubuntu and installed arch. Guess what, same freezing. 

It only happens when doing lots of disk activity, such as building some large projects. I've gotten to the point where I can easily duplicate it.

There are no error messages in any of my logs, but after killing x and running a build in a virtual console I was finally able to see a kernel panic error message: "not syncing: Aiee killing interrupt handler". 

My machines are both dells, both xeons with nvidia cards and intel chipsets.

Edit: Upgrading kernel to 29 or 30 did not help. I'm using 64-bit ext4.

Edit: I can duplicate it 100% doing an svn up. So it may be a network problem instead of an IO problem - lack of error messages make it impossible to tell.

Edit: [Solved?] Disabling AHCI in my bios seems to make the system more stable... at least I can't easily reproduce the freeze anymore.

Edit: Nevermind, still freezing...

Edit: [Solved!] Finally got it fixed by installing Arch, and downgrading to the 2.6.28 kernel with nvidia 180.29 driver. Not sure why this fixes it considering Jaunty uses 2.6.28, but it does.

---

### Post by JohnnyVW on 2009-07-06
> **Laysan_A said:**
> [quote=JohnnyVW;7565996] I'm really wanting to avoid a fresh install...

Hi,

I can understand why you might not want to start from scratch, but it really sounds like you just have something missing, or maybe improperly configured, from your upgrade/install. Have you tried just installing a new kernel? You never know, it might work for you, and it's not too involved if you use one of the precompiled ones from the ubuntu kernel source. If it doesn't work, no harm, no foul.[/QUOTE]

Thanks!  Now, forgive the noob question (I've [i]only been using Linux for 9 years!  :lol:)  How do I do that?

---

### Post by JohnnyVW on 2009-07-06
> **bearozo said:**
> What type of monitor do you have ? I had problem configuring my old KFC (smile) monitor when I changed to a newer Nokia with proper plug and pray all problems disappeared.

It's a Viewsonic A75f.

---

### Post by JohnnyVW on 2009-07-06
> **Trapper said:**
> Are you sure it's:

CTRL+ALT+SySRq (PrintScrn) keep holding CTRL+ALT and hit R+E+I+S+U+B

I ask because the link seems to indicate it's:

Hold ALT+SySRq (PrintScrn) and type R+E+I+S+U+B



Of course, doing ALT+SySRq (PrintScrn) and type R+E+I+S+U+B without 3 hands might be a bit tricky so I consider the link might be giving the incorrect info. Plus you get the print screen popup box :-)
Trapper

LOL!!!  I just got a mental image of pressing all of that at the same time!

I think the idea is:

(right hand) hold <ALT> & <SysSq>, then (left hand) press & release R, then press & release E, etc., etc.

It works when mine freezes.  It still can take three or four resets...  sometimes one...  before it starts.

The intermittentness (is that even a word?!) is driving me nutty.

---

### Post by Chemical Imbalance on 2009-07-06
ProphetOfDoom, I also had the same freezes in both Fedora 11 and Jaunty.

Perhaps it could be an ext4 issue?

My ideas are nVidia, a kernel setting conflict of some sort, or Ext4.

---

### Post by bearozo on 2009-07-07
> **JohnnyVW said:**
> It's a Viewsonic A75f.

It seems to be about 10 years old maybe the Plug and Pray is not detected properly.

But if you can set refresh rates and resolution as u wish it should be allright.

If not you could find figures in the windows inf. file to write your own modelines in xorg.conf.

You could borrow a newer monitor and plug that in to see what happens though.

Also this, but get the right drivers i386 or am64 depending on what you use: [http://linuxcrypt.net/?p=255](http://linuxcrypt.net/?p=255)

---

### Post by bearozo on 2009-07-07
> **Trapper said:**
> Are you sure it's:

CTRL+ALT+SySRq (PrintScrn) keep holding CTRL+ALT and hit R+E+I+S+U+B

I ask because the link seems to indicate it's:

Hold ALT+SySRq (PrintScrn) and type R+E+I+S+U+B



Of course, doing ALT+SySRq (PrintScrn) and type R+E+I+S+U+B without 3 hands might be a bit tricky so I consider the link might be giving the incorrect info. Plus you get the print screen popup box :-)
Trapper


You hold down ALT +SySRq  and pres REISUB one at the time, give a little time betwix each press.

---

### Post by Lety on 2009-07-07
I'm experiencing freezes with Jaunty 9.04 i386 (ext3) too, when it happens my laptop keyboard's capslock LED is blinking all the time.
This often happens when browsing with Firefox, rarely when watching a movie (SMPlayer).
Sometimes I'm facing automatic logoffs to the logon screen with unsaved data loss.
Freezes and logoffs happen once in 6-8 hours.

There was no such kind of issue when running 8.10 AMD64.
My cpu is Athlon 1,6 GHz, video is ATI x1250. 

Maybe I'll update the kernel.

---

### Post by sub_acoustic on 2009-07-08
Since this started, I've also had freezes on live cds and  on 8.04.  Diagnostic tests on my memory and hard drive show no errors so I'll try to reinstall 9.04 from scratch...

Never again will I upgrade unless it's really essential, such a hassle...

---

### Post by throwingks on 2009-07-08
> **Chemical Imbalance said:**
> ProphetOfDoom, I also had the same freezes in both Fedora 11 and Jaunty.

Perhaps it could be an ext4 issue?

My ideas are nVidia, a kernel setting conflict of some sort, or Ext4.
Im on ext3, and still get crashes.

---

### Post by sub_acoustic on 2009-07-09
I reinstalled 9.04 - still with the freezes, but now I've installed the 2.6.29 kernel following the easy instructions here
[http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/]("http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/")
and all is almost well, the system seems to behaving better, but still there are freezes when i try to do too much...

---

### Post by FabriceV on 2009-07-09
Not so much to add... I have tested with Nvidia card or Intel and Ext3. Resume function is still erratic. Freeze is frequent (less frequent if you don't hibernate). I have stopped to use hibernate (do not change from years ago). I also search another distro, stable but that includes last version of common softwares like OpenOffice.

---

### Post by Chemical Imbalance on 2009-07-10
Found this interesting post that at least applies to my problem:

[http://www.nvnews.net/vbulletin/showthread.php?t=123583](http://www.nvnews.net/vbulletin/showthread.php?t=123583)

---

### Post by agurk on 2009-07-11
Although downgrading kills kittens, I just had to give up and revert to 8.10 to get things done. I'll leave you with some of my observations and a weakly supported theory.

Observations:
* ext3 or ext4 doesn't matter, I've tried both.
* X and video driver doesn't matter, the freezing occurs in safemode as well (no X running).
* It isn't completely frozen; a watchdog kicks in every 60 seconds and writes about something going on with cpu0 (can't remember exactly what it says, sorry).

Theory:
The freezing is related to CPU scaling. Why? Because when having the CPU set to either 'powersave' or 'performance' (using the cpufreq-applet), I can't reproduce the freezes.

---

### Post by merlyn on 2009-07-11
Hi folks, I've browsed this thread from start to finish, and while I've found a some useful tips that have helped minimise the lockups on my system they still occur.

I've added a comment to the bug in launchpad, that hopefully will assist.

Other than that I'll keep a weather eye on this thread, (subscribed).

For the record, I experience random lock ups. To date I have not been able to pin it down to a single trigger though.

At times the system will simply lock up after launching Kpackagekit. I play with it once in a while, but use synaptic / command line for package management most of the time.

I'll often have a couple of apps open at once, ie I'll be listen to music (Amarok), surfing (Firefox) and chatting (Kopete) and maybe even pulling down a torrent.

I can be doing this all day, without a hitch, yet at other times it'll lock up 3 - 4 times in the space of half an hour. ](*,)

I've had limited success with kernel / video card upgrades, xorg.conf modifications to date.

I'm running Kubuntu, on an Athlon XP system with an nvidia 7800gs, rock solid under 8:10 and any release of Ubuntu that I've run previously.

Currently set up as a dual boot with Ubuntu 8:10, though currently spend all of my time in Kubuntu 9:04.

I'll throw my 2 cents in and state that I do not believe that this problem has anything to do with ext4 as I'm currently running Fedora 11 on my test system (ext4) with no dramas whatsoever.

It's (test system) up every day and most nights and has been for about two weeks now.

Furthermore, despite the random lock ups with Jaunty, I've experienced no data loss whatsoever.

When you take into account that in the last week alone I've had to run fsck manually twice, that's pretty good.

 I'm not sure what's more disappointing, having an install with problems that defy all efforts to resolve them or Canonicals lack of response and seeming lack of  action.

All I can say is that for now I'll be checking out other distros as mentioned earlier on my testing system with a view to moving away from *buntu after many years of use.

I personally know of others who are doing the same.

---

### Post by VastOne on 2009-07-11
> **merlyn said:**
>  All I can say is that for now I'll be checking out other distros as mentioned earler on my testing system with a view to moving away from *buntu after many years of use.

I personally know of others who are doing the same.

This, with great pain and sorrow, is exactly the route that I am heading. After years of promoting *buntu to scores of business and schools, churches and friends, I am on path to something that will run that does not have the word Microsoft in it.

What frustrates me is the lack of a coordinated effort of problem solving.

ABC's of problem solving:

A - Aware (identify, is it a kernel to cpu stepping/scaling issue?)

B - Brainstorming - Come up with as many solutions as possible

C - Choose a solution

D - Do it!

E - Evaluate ( if failure go back to C)

Is there any coordinated resolution?  I have been a part of [https://bugs.launchpad.net/bugs/355155](https://bugs.launchpad.net/bugs/355155) but it too seems to be a repo people reporting the issue.

I have 3 machines all running the EXACT same build of kernel 2.6.30.

AMD Phenom 955 overclocked - No issues
AMD Phenom 940 overclocked freeze all day until overclock turned off, now no issues.
AMD Phenom 955 with a MSI AMD 3 and DDR3 setup overclocked, 2 freezes in two weeks but identical to the other freezes I have seen

Random random and more random

---

### Post by JohnnyVW on 2009-07-11
I gave up.

I re-installed 9.04 fresh.  What do I get when the system rebooted agter install?  Yup, you guessed it.  It froze just before the login screen.

After a barrage of blue words (and my wonderful and understanding wife calmed me down), I decided to downgrade to 8.10 to see how it goes.  8.04 ran perfect on this PC...  This sucks large.  Once 9.04 would finally boot, it ran flawlessly!  I didn't get the freezes after Gnome started.  My printers, scanner and file-sharing worked great.  

Oh well...  :(

---

### Post by Caraibes on 2009-07-11
You guys... I triple boot, Ubuntu 9.04 (amd64), CentOS 5.3 x86_64 & XP...

I have an AM2 L110, a MSI K9Neo v3 mobo, and a brand new Kingston DDR2 ram of 2 gigs... Also an Nvidia GeForce 7300...

I experiment random freezes in Ubuntu & CentOS, but it seems that Ubuntu freezes more...

I thought it was a ram issue, so I bought a new ram, and installed it on its own... No luck... Power supply is good... CPU fan is running (I see it, the case is open...)

I guess it must be a Nvidia issue, somehow... I am running both Ubuntu & CentOS using the proprietary drivers...

Maybe I should try the "nouveau" drivers, or stick to "nv"...

Just wanted to let you guys know...

---

### Post by JohnnyVW on 2009-07-11
Caraibas might be right.  Might be an Nvidia thing.  It happens to me with either the "nvidia" proprietary driver or the "nv" driver.  A fresh install uses the "nv" driver and it froze.

I need a working and *reliable* PC.  Looks like Jaunty is NOT the one for me.  Hopefully, Intrepid will work better for me.  Maybe things will get fixed in 9.10.  Maybe I'll switch distros.  Too bad.  I've had a ***great*** experience with Ubuntu since Dapper.  *sigh*

---

### Post by freonchill on 2009-07-11
though im not a guru
i debated switching from ubuntu 9.04 to fedora 11.0/11.1 till this got solved.
sadly, it seems that this "bug" exists for them also.

it seems that there are problems with people who have any of the following
ext3, ext4, amd, intel, nvidia (either gpu or northbus), ati

i have seen debates on both the ubuntu forums and the fedora forums about it being the filesystems problem, the graphics accelerator, the kernel, acpi, cpu speed scaling, disabling compiz...

i guess ill just keep my eyes pealed for now as my problems: hard lockup, failed resume from suspend/hibernate are minimal compared to the problems that some of you are having (e.g. i typically only have a lock-up when having massive data through-put (extracting a rar file, deleting a cd image), so i just refrain from that and make sure i save/close everything in case suspend/hibernate does not resume correctly - and fsck seems to stop any data loss since i started doing it on boot after a resume failure...

---

### Post by VastOne on 2009-07-11
> **JohnnyVW said:**
> Caraibas might be right.  Might be an Nvidia thing.  It happens to me with either the "nvidia" proprietary driver or the "nv" driver.  A fresh install uses the "nv" driver and it froze.

No. At [https://bugs.launchpad.net/bugs/355155](https://bugs.launchpad.net/bugs/355155) there are several with ATI drivers with the exact same issues

---

### Post by merlyn on 2009-07-12
I've been observing my lock ups to see if there are any consistencies / patterns that may provide some insight to the cause.

At least on my system, that is.

One 'action' that consistently locks up my system is this.

A) updates are indicated as available by the presence of an icon in the system tray.

B) Click on said icon to launch the package manager, (in my case this is Kpackagekit).

C) Lockup without fail, and only a hard reboot, or power recycle will resolve this.

The workaround: quit the notification tool in the system tray and launch Kpackagekit via "systemsettings", or of course use apt-get / aptitude etc.

What is the current process for checking and notifying of updates, ie services, etc that are involved?

I've grown somewhat "lazy" using since using Ubuntu (warty), in the sense that my knowledge of Linux systems has diminished, since I began using Linux back when Redhat 5 hit the shelves.

Why is this? Simply because *buntu for me has been essentially troublefree.

Any problems that have eventuated have been easily resolved through information provided in this and other forums. 

Or my now somewhat dull and out of date knowledge base / skill set. :oops:

Either that or the Devs have got the thing by the 'short and curlies' and released a fix within days.

Hence I really haven't had the need to put my thinking cap on.

_**Edit:**_ I've browsing through the PPA's for packages that might be useful, as some of the upgrade options mentioned in this thread have (for me) resulted in little improvement.

Here are the ones that stand out.

[Kernel Backports]("https://launchpad.net/%7Ea7x/+archive/kbp") - which has a backports of the Karmic kernel and requisite nvidia drivers for Jaunty. (sorry no ATI or other video drivers).

And for those who may be experiencing problems with ext4.

[ext4 fixes]("https://launchpad.net/%7Ea7x/+archive/ext4fixes") - dated 24 June, so I'm not sure if these fixes have or will make it into 'official' updates. I'm not concerned about this as ext4 has given me no grief, but for others .....

_**Note:**_ - I haven't tried either of these yet, (but) I will, so I cannot vouch for their stability or possible damage they may do to your installs.

Furthermore, I'll be blowing away Fedora 11 on my test system within the next 24 hours, and installing Sidux. I'll keep you folks posted on how that goes.

Cheers once again.

---

### Post by jig on 2009-07-12
recent install of 9.04 64bit into a machine with on-board nvidia 9400, 4GB of ram, ext4, AHCI SATA. All cpu stepping is enabled in bios, intel e8500. nvidia 180 drivers installed.

I'm seeing some of the same hangs. BUT, I've found that I can stop most of the hangs by switching off all the special display effects under display properties. That has helped the most, but I've still experienced a hang this evening after changing some share settings (using nautilus interface, not the command line) and then right-clicking and choosing new folder, while looking at the same folder (network share) on a windows machine. The folder was created, but I had to hard reset to get the dektop back.

There <may> be some issue with samba and nautilus (it has led to hangs for me before), but for sure there is an issue with the desktop display effects and 64bit 9.04. Turn those off and see how you do.

Hm. I should note that I don't think I've experienced a hang without system monitor running, but I keep that running almost all the time. 

Anyway. Does anyone have any comments about using the 29 kernel? It seems to have some benefit for other hang issues, but I don't really want to jump unless there are a lot of users that have already jumped. Also, how detrimental to the filesystem are these hard resets? Should I be running something to check the data integrity after each one?

Thanks, and I'll keep checking back.

---

### Post by Caraibes on 2009-07-12
Ok, but in my case, what does Ubuntu 9.04 64-bit and CentOS 5.3 64-bit have in common ???

2.6.28 vs 2.6.18...

Not much, except that both are 64-bit...

Bot are using Nvidia proprietary drivers... (on my box...)

Both  are freezing every now and then...

I have not experimented those freezes with any other *Buntus...
-Any 32-bit users out there experimenting freezing as well ?

-Any of you have a multiboot with other(s) distro(s), and only experiment freezes with Ubuntu ???

---

### Post by jig on 2009-07-12
i think the connection is nautilus. (and 64bit, and maybe nvidia drivers if you are using 180, and maybe samba).

do you have visual effects turned on for your desktop?

---

### Post by Caraibes on 2009-07-12
> **jig said:**
> i think the connection is nautilus.
Possibly, as I am mainly using Gnome, but I sometimes use Fluxbox only... And I had many freezes while using CentOS and Fluxbox...

> **jig said:**
> (and 64bit,
That makes sense... I plan to re-install CentOS, but the 32-bit version... We'll see, then...

> **jig said:**
>  and maybe nvidia drivers if you are using 180, and maybe samba).
I don't think it is Samba related... Right now I am on CentOS, and this is my Nvidia driver: nvidia-x11-drv-96xx-1.0.9631-1.nodist.rf.src.rpm (from the RPMforge repos)

> **jig said:**
> do you have visual effects turned on for your desktop?
No, I never use any visual effect, neither on Ubuntu nor in CentOS...

---

### Post by ProphetOfDoom on 2009-07-12
I posted issues with freezing about a week ago (see page 50 I think). Anyway I did a completely fresh install on monday - ie 6 days ago,  and it's been better with regard to general web browsing - hasn't froze once.

But today was the first time I've really had an opportunity to do any painting with gimp/ wacom and it's frozen once so far. So a completely fresh install has not fixed this problem.

---

### Post by arichard03 on 2009-07-13
Hi all, I'm new on this forum and on Ubuntu as well. I am having the same freezing problem as well. I noticed everyone talking about either rolling back their graphics driver or updating it. I went to the Nvidia website and came across their newest driver for linux based distros----> Latest Version: [185.18.14]("http://www.nvidia.com/object/linux_display_ia32_185.18.14.html"). I dont know if this would help yet, but I am going to try it once i get home to my desktop computer. Please let me know if this helped anyone.

Edit: Well, being that I'm a noob, i couldn't get to installing the new drivers because it is a .run pkg .... the only solution i had was to uninstall the proprietary drivers. That managed to stop my computer from freezing for now. If anyone tries installing it and it works... again, please let me know.

---

### Post by Chemical Imbalance on 2009-07-13
> **arichard03 said:**
> Hi all, I'm new on this forum and on Ubuntu as well. I am having the same freezing problem as well. I noticed everyone talking about either rolling back their graphics driver or updating it. I went to the Nvidia website and came across their newest driver for linux based distros----> Latest Version: [185.18.14]("http://www.nvidia.com/object/linux_display_ia32_185.18.14.html"). I dont know if this would help yet, but I am going to try it once i get home to my desktop computer. Please let me know if this helped anyone.

Edit: Well, being that I'm a noob, i couldn't get to installing the new drivers because it is a .run pkg .... the only solution i had was to uninstall the proprietary drivers. That managed to stop my computer from freezing for now. If anyone tries installing it and it works... again, please let me know.

The latest nvidia drivers from their site don't fix it for me.  My desktop doesn't freeze when the nvidia driver is uninstalled.

Right now I'm about to give the Nouveau drivers a whirl.

---

### Post by JohnnyVW on 2009-07-13
> **Chemical Imbalance said:**
> The latest nvidia drivers from their site don't fix it for me.  My desktop doesn't freeze when the nvidia driver is uninstalled.

Right now I'm about to give the Nouveau drivers a whirl.

I never did update or roll back my 180.x driver, but I did switch to the nv driver and suffered the same freezes.  

Just an update, I backed up my home directory and did a fresh install of 8.10.  No problems at all!  I'm sticking with 8.10 until there's a fix for 9.04, or wait until I think 9.10 will work.

---

### Post by merlyn on 2009-07-13
Hi folks, here is an update from my last post found [here]("http://ubuntuforums.org/showpost.php?p=7601799&postcount=522").

I can now state, that update notifications via the system tray are a cause of system lockups for me, (without fail).

I cannot say that they are the only cause however, as system lockups have occurred without updates being available.

Nevertheless. each and every time an update is available the system locks up every time. There are two variations on this situation.

A) the system will lock up, restarting x or accessing a terminal is unavailable, so a hard reboot is the only option. Upon rebooting the update notification icon appears in the system tray.

B) updates are notified via the system tray. Any attempt to access the updates by left clicking the icon results in a system lockup. Remedy as per above.

The only way around this at present is to quit the system tray update notification and install update by another means, i.e. Kpackagekit, Adept, Synaptic, Command Line.

I also mentioned the following PPA archives which peaked my interest, that may be of help.

[Kernel Backports]("https://launchpad.net/%7Ea7x/+archive/kbp") - which has a backports of the Karmic kernel and requisite nvidia drivers for Jaunty. (sorry no ATI or other video drivers).

Since the last round of crashes, three this morning, (local time), within 20 minutes, I installed the kernel updates and nvidia driver updates from this repository.

The upgrades went smoothly.

It's too early to say whether the freeze problem has been resolved, (need to wait for an update to come down).

My system though is running noticeably faster.

For example prior to the upgrade there would be a pause in loading the desktop after login, and the background would display a checker board effect during the pause.

This no longer occurs, the desktop loads without pause, and no checkerboard.

In fact the whole desktop experience is much more responsive, loading applications (Firefox in particular), switching desktops.

I'll post an update should the 'update notification' lockup occur again.

As for installing Sidux on my test system. I'll be doing that soon.

Cheers.

_**Edit:**_ a quick update. The burning capabilities of my optical drives were not recognised under the 2.6.31-2 kernel provided in the above mentioned ppa. I've notified the packager.

---

### Post by psychoelf on 2009-07-13
Getting random freezes here.  Running Jaunty 9.04 with 2.6.28-13 kernel.  I have an ATI video card and run the proprietary drivers.  I'm leaning towards a cpu scaling issue as the only time I get freezes are when I open programs (i.e. Firefox or VLC).  I have a dual core Centrino T5550.  I can see my cpu meters on Conky right before it freezes.  CPU 1 goes all the way to 100% while CPU 2 is at maybe 5%.  right after that the program barely opens and my laptop is hosed.  This has happened while using ext3 and ext4.  I never had this issue with 8.10.  Hope this helps!

---

### Post by Caraibes on 2009-07-14
Well, as mentioned earlier, I have a triple-boot... Ubuntu & CentOS are both freezing every once in a while... This morning I have been booting Windows XP, and so far it doesn´t seem to be freezing (!!!)
This is quite an offense to a Linux user such as myself ;)
I noticed both Ubuntu & CentOS to be freezing on a cold boot in the morning, sometimes twice in a row...
Yesterday, at the end of the day, CentOS froze while "screensaving"...

---

### Post by sub_acoustic on 2009-07-14
Well back to 8.04 and the problem continues, (I've previously been on 8.04 and 8.10 with no problems in the past).

So my thoughts are that maybe its

- some update included in 9.04 and 8.10 that was also applied to 8.04 LTS
- a hardware issue (though ram and hard disk tested okay)
- a power issue (though it seems to happen either on battery or adaptor)
- a wireless thing (though it's also happened when on a wired connection)
- some BIOS thing (though I've altered nothing)
- some kind of conspiracy?

Freezes generally seem to happen with high CPU loads, though that has never happened before, and sometimes it freezes when not much is happening.

Not even sure how to file a bug report that could in any way be useful.....

---

### Post by Caraibes on 2009-07-14
> **sub_acoustic said:**
> - a hardware issue (though ram and hard disk tested okay)
- a power issue (though it seems to happen either on battery or adaptor
I believe it is a hardware issue... This morning, while I went away for about an hour, I let Windows XP run (screensaver etc...) When I came back, it was frozen...

I shall buy a new power-supply unit...

My ram is brand new, from last week... Memtest says it's fine...

Has to be the PSU...

I am sticking to CentOS right now, as it is supposed to be the most "rock solid" distro out there...

---

### Post by arichard03 on 2009-07-14
Hey, everyone...for me, it was the nvidia 180 driver that was buggy. I still never got to installing the 185 driver from nvidia website...can't figure out how to kill x to install it...lol. But I rolled back to the 173 driver and my system works great now.

---

### Post by Chemical Imbalance on 2009-07-14
> **JohnnyVW said:**
> I never did update or roll back my 180.x driver, but I did switch to the nv driver and suffered the same freezes.  

Just an update, I backed up my home directory and did a fresh install of 8.10.  No problems at all!  I'm sticking with 8.10 until there's a fix for 9.04, or wait until I think 9.10 will work.

Intrepid didn't freeze on me ever.  Jaunty and Fedora 11 do though, which I'm assuming is a kernel conflict with the nVidia drivers.  I think it has to do with IRQ sharing/assignment (see my earlier post with the link to a forum discussing this).

---

### Post by rhchia on 2009-07-14
I faced this problem recently too.

_My Machine_
Compaq Presario V3788TU Notebook PC
Microprocessor: 2.40 GHz Intel Core2 Duo processor T8300 featuring Intel Centrino Duo processor technology
Video Graphics: Intel Graphics Media Accelerator X3100

---

### Post by Hated On Mostly on 2009-07-15
Finally got around to installing and testing 9.04 (Jaunty Jackalope) a day ago and had the freezing issue. The issue only popped up after I updated the system. I realized that the updates after install set "Visual Effects" to "Normal". I always turn off all effects (no compositing window manager effects or Compiz). Did a reinstall and turned the effects off immediately after updating and have had no freezes since then.

Never had freezes in 8.04 (Hardy Heron) or 8.10 (Intrepid Ibex), so hopefully I won't have any problems over the next week or so and can keep 9.04 (Jaunty Jackalope) on my system. Jaunty is so much nicer, smoother, and faster than Intrepid (which was good for me) that I would hate to not be able to use it due to freezes. So far so good...

---

### Post by Anybloodyid on 2009-07-15
Just thought I'd add my little bit, I too get random freezes using firefox or maybe playing some game.
I figure I'll wait for the next release and if that does the same then look to one of the other distros.

---

### Post by Caraibes on 2009-07-15
I booted in Jaunty today, for some updates, and it froze after 5 mn...

I am using CentOS 5.3 everyday with (almost) no freeze...

---

### Post by merlyn on 2009-07-15
Hi folks,

I've given up on a resolution to this.

Yet another lockup today, low and behold it corresponded once again with the availability and notification of updates.

No bloody updates to help fix the #%#$%#@ problem though.

Sidux installed nicely on my test system, being sid it's a different animal, it's fun though and I'm learning a good deal.

Once I've got a hang of things and been able to track down suitable debs for my favourite apps its ):P *buntu.

Cheers all.

---

### Post by Chemical Imbalance on 2009-07-15
I think I found the solution to my freezing at the least.

I believe it is an issue with IRQ assignment and sharing.

Here are my /proc/interrupts and my lsusb:

```
cat /proc/interrupts
           CPU0       CPU1       CPU2       CPU3       
  0:        102          0          0          3   IO-APIC-edge      timer
  1:          0          0          0          2   IO-APIC-edge      i8042
  4:          0          0          0          1   IO-APIC-edge    
  7:          1          0          0          0   IO-APIC-edge    
  8:          0          0          0          1   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 12:          0          0          0          4   IO-APIC-edge      i8042
 14:          0          0          2       3582   IO-APIC-edge      pata_amd
 15:          0          0          0          0   IO-APIC-edge      pata_amd
 19:          0          0          0          3   IO-APIC-fasteoi   ohci1394
 20:          0          0          0        477   IO-APIC-fasteoi   ohci_hcd:usb3, nvidia
 21:          0          0          1       1660   IO-APIC-fasteoi   ehci_hcd:usb2, HDA Intel
 22:          0          0          0          1   IO-APIC-fasteoi   ehci_hcd:usb1
 23:          0          0         11       7448   IO-APIC-fasteoi   ohci_hcd:usb4
2298:          0          0         58      50716   PCI-MSI-edge      eth0
2299:          0          0         16       7431   PCI-MSI-edge      ahci
NMI:          0          0          0          0   Non-maskable interrupts
LOC:      22949      13508      10719      30490   Local timer interrupts
RES:      14107       7407       9277       7849   Rescheduling interrupts
CAL:        156        180        173         49   Function call interrupts
TLB:       1146        877        877        881   TLB shootdowns
SPU:          0          0          0          0   Spurious interrupts
ERR:          1
MIS:          0

```

```
lsusb
Bus 002 Device 004: ID 05ac:021d Apple, Inc. 
Bus 002 Device 002: ID 05ac:1005 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


Notice that nvidia is sharing an irq with my usb hub # 3.

I had my mouse plugged into usb hub 3 and I had freezing.  
I simply moved my mouse to hub 4 and no more freezing.

It seems it is an irq problem for me.

Good luck all.

---

### Post by jig on 2009-07-16
interesting. well, i think we've nailed the broad freezing problem. nvidia drivers coupled with the system trying to draw visual effects, with the drivers causing a hardware conflict that isn't dealt with well by the OS. turning off visual effects seems to be a band-aid, though i'm not sure what the system is calling that firefox, vlc, and etc are not - i guess it could be application window acceleration.

let us know about the usb thing. if that is a solid fix for you, even after enabling the desktop visual effects, then we have a winner (though the OS should be fixing that for us - even if the propritary drivers have an issue). it would be interesting to know if more recent drivers than the 180 somehow fix the problem. alternatively, whether a newer kernel does so. for my sake, try one or the other and test, not both at the same time.

to the person that is having issues with windows, ubuntu, and something else... it really sounds like a memory issue. it MAY be a hard drive buffer memory problem. if you have a seagate 1TB drive, there were/are some issues with those and their buffers. aside from that, it's clearly a hardware problem. to that end, you may want to run a very recent version of memtest86 and let it go a long time. or, boot from a recent Hirens CD and run some of those system checkers. you may be having a temperature issue, which you'll only be able to track down by being able to view the various temps (vid card, cpu, mboard, HDs) - not sure if there is a bootable cd that will be able to tell you all that.

---

### Post by Chemical Imbalance on 2009-07-17
I've been running for 3 days without freezes.

That is as solid a guarantee that I can hope for.  

Before it was a freeze every couple hours.

It is solved for me.

Note that this could be hardware-specific.  This may not apply at all to anyone else in this thread, or perhaps it could apply to everyone.

I am using an up to date Jaunty install with the default kernel.

I have an Asus M3n78-pro motherboard with and onboard nvidia 8300.

Using the latest drivers from nvidia's site. (185.xx)
These drivers do not fix the problem by itself, at least for me.  Check your interrupts and what they are sharing.


btw, I do not run Compiz.  

_

---

### Post by psychoelf on 2009-07-17
I have an ATI 2600 mobility with effects disabled.  Mine froze again today when I went to watch a video with VLC.  This was right after closing firefox.  My screen froze and the fan kicked in high gear.  I don't think it is Nvidia only.  This has happened since I started using Jaunty.  I hoped it was just an early bug, but it still happens.  I'm just glad a reboot only takes 30 seconds now.

---

### Post by Chemical Imbalance on 2009-07-17
> **psychoelf said:**
> I have an ATI 2600 mobility with effects disabled.  Mine froze again today when I went to watch a video with VLC.  This was right after closing firefox.  My screen froze and the fan kicked in high gear.  I don't think it is Nvidia only.  This has happened since I started using Jaunty.  I hoped it was just an early bug, but it still happens.  I'm just glad a reboot only takes 30 seconds now.

I guarantee there are at least several different bugs in this thread with different people being affected.

---

### Post by tominto on 2009-07-17
I'm experiencing freezes today too.  I've had Jaunty running fine for several day, and just this morning downloaded the latest updates...I then shut down my computer for several hours.  When I turned it back on again , I got as far as the Ubuntu splash screen before it froze.  My second attempt, I got as far as the desktop but it froze when I tried to open an application.  On the third attempt it froze shortly after loading the desktop.  I have a dual boot system on a single drive, and I can boot into Windows (what I'm using right now)  Not sure if this is a Ubuntu specific problem or a hardware problem.  I would appreciate help with this one

---

### Post by Hated On Mostly on 2009-07-17
> **Chemical Imbalance said:**
> I guarantee there are at least several different bugs in this thread with different people being affected.

> **tominto said:**
> I'm experiencing freezes today too.  I've had Jaunty running fine for several day, and just this morning downloaded the latest updates...I then shut down my computer for several hours.  When I turned it back on again , I got as far as the Ubuntu splash screen before it froze.  My second attempt, I got as far as the desktop but it froze when I tried to open an application.  On the third attempt it froze shortly after loading the desktop.  I have a dual boot system on a single drive, and I can boot into Windows (what I'm using right now)  Not sure if this is a Ubuntu specific problem or a hardware problem.  I would appreciate help with this one


tominto it sounds like you are experiencing the Jaunty data corruption bug (others probably are as well, thankfully that was not my problem). According to the very long bug report it doesn't just affect 64-bit or ext3 and ext4. It also does not affect everyone (I got lucky).


[http://ubuntuforums.org/showpost.php?p=7382178&postcount=29](http://ubuntuforums.org/showpost.php?p=7382178&postcount=29)


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all)


There is a solution (update kernel) but your current install might be destroyed.

Good Luck


Solution:

> **quixote said:**
> Symptoms: [Bug #346691]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all") affects 64-bit installs and causes the system to freeze up randomly, not associated with any specific program.  A hard reset is the only way to regain control, and then the system usually won't boot because of filesystem corruption: missing or bad inodes reported, and so on.  Fsck has to be run manually from recovery mode to fix it, until the next time it blows up again.

This bug is not related to **ext4** filesystem corruption on i386, ie 32-bit installs, so the fix below is probably irrelevant in that case.

The cause appears to be the 2.6.28.11 kernel that comes with Jaunty.  The fix is to install a 2.6.29 kernel:
```

$ wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb
$ sudo dpkg -i linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb
(or **_i386.deb if on 32bit**)
``` (Thanks to Daniel J. Blueman for the fix!)

---

### Post by gjtoth on 2009-07-17
Just to sort of confirm -- I disabled visual effects and have had no freezes.  Although, my freezes were no system lock-ups.  They were/are application freezes.  I'm running an Nvidia with 256mb on a 32-bit machine with 1GB of RAM.

---

### Post by tominto on 2009-07-17
> **Hated On Mostly said:**
> tominto it sounds like you are experiencing the Jaunty data corruption bug (others probably are as well, thankfully that was not my problem). According to the very long bug report it doesn't just affect 64-bit or ext3 and ext4. It also does not affect everyone (I got lucky).


[http://ubuntuforums.org/showpost.php?p=7382178&postcount=29](http://ubuntuforums.org/showpost.php?p=7382178&postcount=29)


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691?comments=all)


There is a solution (update kernel) but your current install might be destroyed.

Good Luck


Solution:
Thanks for your help.
I tried again but this time I booted into Ubuntu using recovery mode.  Then I repaired broken packages, and checked the filesystem and I got a warning about Fsck or something to that effect??.  I'm able to use Ubuntu again now, but maybe I should upgrade to the latest kernel as you suggested or is this something else?
btw I'm using a 32 bit system.

---

### Post by Hated On Mostly on 2009-07-19
> **tominto said:**
> Thanks for your help.
I tried again but this time I booted into Ubuntu using recovery mode.  Then I repaired broken packages, and checked the filesystem and I got a warning about Fsck or something to that effect??.  I'm able to use Ubuntu again now, but maybe I should upgrade to the latest kernel as you suggested or is this something else?
btw I'm using a 32 bit system.


If there was corruption, and fsck was run, there will be files located in the "lost+found" folder which can be found in the root folder of the drive (i.e. /lost+found). You will need to have admin privileges to access the folder.

```

gksudo nautilus
```

You can also review the fsck log to find out exactly what happened. The logs can be found in the /var/log/fsck/ folder.

```

nautilus /var/log/fsck
```

As far as what you should do, that is tough to say. People are saying the kernel I posted about and the ones above it and various other custom modified kernels solves the problem, but I saw at least one report out there for data corruption on a supposedly good kernel. Could be a hardware problem in that case from what was posted however. Most people say the newer kernels don't exhibit the problem. Problem with the newer kernels is that they have their own bugs, but I would take just about any other bug over possible data corruption so it is worth a shot as long as you back up everything before switching kernels.

Me personally, I went back to 8.04 LTS and installed the latest point release (8.04.3). I will miss tabbed Nautilus and a couple of other subtle usability features from Intrepid and Jaunty, but I want the stability back that attracted me to Linux in the first place. From now on I think I will stick with LTS releases only and might even wait for the first point release before upgrading to the next LTS version which is supposed to be 10.04. I don't want to have to keep playing with my machine and worrying about critical bugs and other things. I want to use my computer to get work done. The current releases are nice, but too buggy for me.

Whatever you choose to do, good luck, hopefully you don't have any data loss. It sounds like you might be lucky because you were able to boot back into the system. Most experiencing data corruption can't do that.

---

### Post by Hated On Mostly on 2009-07-23
Some more info related to the data corruption/system freezing problem:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691/comments/165](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691/comments/165)

> Fact: I've been using the 2.6.29-04 kernel with up to date 64-bit Jaunty on ext3 for a couple of months now with no problems at all.


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691/comments/122](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346691/comments/122)

> I thought a short howto would be good for some people, about how to get Jaunty running on the effected systems. This is for paranoid people like me, who don't trust a system installed with an installer running the buggy kernel or booted up with it once (and have no intention to create/wait for a new installer). Note: headers might not be needed on some system, but it can not hurt (and for nvidia driver it will be needed)

- save all your data if possible
- install 64 bit intrepid
- boot up system
- upgrade to latest packages
- upgrade to jaunty, but do not restart system after upgrade finished
- wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb)
- wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-headers-2.6.29-02062904_2.6.29-02062904_all.deb)
- wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.29.4/linux-image-2.6.29-02062904-generic_2.6.29-02062904_amd64.deb)
- dpkg -i linux*2.6.29-02062904*deb
- reboot
- make sure to select above kernel (most probably it will be the default, but it worth to check)
- install nvidia driver if needed (it's ok if you installed it on intrepid, it will be "recompilled" when you install the new kernel automatically

This way your system should not get corrupted as you'll never run the buggy kernel. Of course this way you'll download most of the packages 3 times (intrepid version, intrepid update version, jaunty version). In case there's an updated install medium, please let us know, because that way all this stuff in unnecessary.

Have a nice day! Loci

---

### Post by dspisak on 2009-07-24
pilbender, are you still here?

In your 6/11/09 comment you said you loaded the "xserver-xorg-video-**ati**_6.9.0.91-1ubuntu1_amd64.deb".  Why did you not also load the "xserver-xorg-video-**radeon**_6.9.0.91-1ubuntu1_amd64.deb" file?

7/27:
I tried the radeon_6.9.0.91 file and it messed up the video.  I was stuck at 1280x960 resolution and the monitor could not be identified.  Reverting back to the latest version, radeon_1.6.12.1, brought back my previous resolution of 2048x1152 and correctly identified the monitor.

---

### Post by merlyn on 2009-07-26
I've finally found some success with my freezes by adding this [Kernel Backports]("https://launchpad.net/%7Ea7x/+archive/kbp") repo from the PPAs which provides you guessed it "backports" from the Karmic release.

It may not be the solution for all of you folks, as such I recommend that you keep your old kernel installed as a back up.

Regardless, this whole experience has soured my regard for *buntu, particularly due to the lackluster "official" response to this freezing debacle.

My Sidux experiment has gone extremely well, it's light fast, very current, (with one or two exceptions), and fully compatible with Debian Sid.

What more could you ask for?

I'll be migrating my main machine over to Sidux in the next day or two once all my data is secured.

Following that it's likely that this will be my last post on these forums.

):P Bye *buntu, it's been great for the most part, but this sort of nonsense is totally uncalled for.

---

### Post by Caraibes on 2009-07-26
Just a quick word to report no more freezes in Jaunty (neither in CentOS).

As of me, my freezes were from ram problems, caused by bad voltage & humidity...

---

### Post by Anybloodyid on 2009-07-26
I've started to use Linux Mint and so far no freezes.  :D

Maybe that's the answer change your distro.

---

### Post by martial on 2009-07-26
Just a status update from my jaunty install. I was having similar issues regarding freezes (few times a day) and took the suggestion of installing the latest nvidia drivers off their website. No freezes (3+ days up) as long as I don't have the special effects enabled. Still doesn't _solve_ the problem, but it is at least less frustrating.

---

### Post by merlyn on 2009-07-27
> **martial said:**
> Just a status update from my jaunty install. I was having similar issues regarding freezes (few times a day) and took the suggestion of installing the latest nvidia drivers off their website. No freezes (3+ days up) as long as I don't have the special effects enabled. Still doesn't _solve_ the problem, but it is at least less frustrating.

The Kernel Backports PPA repo mentioned in my previous post, (just a couple of posts earlier), also has nvidia drivers.

With both the kernel and nvidia drivers I no longer have a freezing problem, and I'm able to take advantage of desktop effects.

Perhaps it would be an option for you also.

Cheers.

---

### Post by martial on 2009-07-27
> **merlyn said:**
> The Kernel Backports PPA repo mentioned in my previous post, (just a couple of posts earlier), also has nvidia drivers.

With both the kernel and nvidia drivers I no longer have a freezing problem, and I'm able to take advantage of desktop effects.

Perhaps it would be an option for you also.

Cheers.

Seems to be working thus far (8+ hours up). Thanks for the suggestion!

---

### Post by dspisak on 2009-07-27
Well, I think I may have solved my freeze problem.  During the freezes I was using an old keyboard, from the '80s,  with a DIN/mini-DIN adapter.  It was connected to the combination keyboard-or-mouse port.  The mouse is a PS/2 type.  It was connected to a USB port via an adapter.  I changed the keyboard to a USB type and moved the mouse to the combination port.  No adapters are now used.  The computer ran a couple of hours yesterday and 11 hours today without one freeze.  Lots of Firefox usage today.  The mouse response seems to be "crisper".

My System:
MB - Asus M3A78-T, 0802 bios
CPU - AMD Phenom II x4 810, 3.13 GHz
RAM - 2 GB Crucial PC8500
On-board Video - ATI Radeon HD 3300
On-board Audio - ATI RS780 Azalia / ATI Technologies Inc SBx00 Azalia (Intel HDA) / ALC1200
OS - ubuntu 9.04, kernel 2.6.29-4-generic
Video Driver &#8211; xserver-xorg-video-ati_6.9.0.91-1ubuntu1_amd64, FGLRX driver not activated

---

### Post by jcarr911 on 2009-08-01
my system will freeze as it starts POST. the first load, which is a old nvida gforce it freezes and the monitor shows an out of range error. i have disconnected my c drive,which is windows and gotten it to boot.this is a terrible introduction to linux. I had thought it might replace windows but not this way. has any solved this problem?

---

### Post by Caraibes on 2009-08-01
> **jcarr911 said:**
> my system will freeze as it starts POST. the first load, which is a old nvida gforce it freezes and the monitor shows an out of range error. i have disconnected my c drive,which is windows and gotten it to boot.this is a terrible introduction to linux. I had thought it might replace windows but not this way. has any solved this problem?
What you describe seems to be a ram problem. Grab a live-cd (Ubuntu, for instance), and run Memtest "to the end"... If you have a bunch of "red message error", go to your local computer store, and buy another ram stick, to replace the one inside your box...

---

### Post by ToFue on 2009-08-02
> **lowkey3d said:**
> Well I got it to hang in recovery mode. I'm now convinced
this is not Xorg related. But a kernel/network driver issue..

Same issue with My UbuntuStudio64 install.

I did clean install after I upgraded (had a security breach). The upgrade worked flawlessly, but the clean install crashes as mentioned [*here*](http://ubuntuforums.org/showthread.php?t=1228298)

---

### Post by jcpism on 2009-08-04
Add my system to the list of victims:
CPU       P4 HT, 2.6G
MB           MSI 865PE-Neo FIS2R
chipset   865PE / ICH5
video         Radeon 9200 (Xiai brand board)
No PCI cards installed. one HD. All instals are clean and use all default options.
keyboard -- ancient with mini adaptor (someone early in this thread brought this up)
512K RAM -- live CD memory test run with no errors. 
BIOS flashed with most recent version. 
All hardware runs xp fine on a daily basis.

A saga on three drives. :popcorn:

Drive the first -- 6G Fujitsu
Bought off the street used a few years ago and now makes that stuttering sound indicating some bad blocks. I installed 9.04 and ran it occasionally for about a month with no problems. I surfed net, installed applications, etc. Since the drive was failing I decided to reinstall.

Drive the second -- 15G WD
Took three tries to install as the partition manager froze twice
Finally it did install and seemed to work but only for 10 - 120 sec before needing reboot. sometimes the screen went black, sometimes the curser worked but everything unresponsive, and sometimes i got the timer and curser moved, but very very slow. I reinstalled, I verified from CD, I changed IDE cable, alwasy same result. 

Drive the third -- 30 G Seagate
This drive simpy would not get past the partition manager during instal. sometimes it was not recognized, sometimes it was recognized but froze. Drive was fine since if I left out the CD it would boot the old OS (FreeBSD) no problem.

Since everything was fine on first drive I was slow to suspect he SW. I checked both drives with e2fsck, bb, and ubcd and they were fine. then i suspected the BIOS options were a problem so i tweaked just about everything that looked relevant, but neither the 15G or 30G drive would improve. 

I have since loaded 8.10 on the 30G drive and so far (2 hours) it seems fine.

---

### Post by gizmobay on 2009-08-05
Add me to the list. I thought it was KDE so I upgraded to the latest from the ppa. This didn't help. I then started running gnome. This didn't help. I ran memory test overnight and it didn't show any errors. I'm not sure what is causing my freezes.

---

### Post by Caraibes on 2009-08-05
> **gizmobay said:**
> I'm not sure what is causing my freezes.
It took me a while, but I now discovered the reason for freezing in my main desktop:

You know the little metal covers for the available PCI slots on the case... My case is old, All available PCI had been at some point used... The empty slots were covered with those metal covers (you know, it kinda looks like a little blade...)

Looks like those blades were touching the motherboard somehow... I took them off, leaving empty "holes"...

Never had even 1 freeze this week !!! (keep in mind I had freezes in Jaunty, CentOS & winXP... it WAS hardware related, but not ram, as I have new ram...)

So for desktop users, have a look at your case...

---

### Post by jig on 2009-08-05
> **Caraibes said:**
> Looks like those blades were touching the motherboard somehow... I took them off, leaving empty "holes"...

Never had even 1 freeze this week !!! (keep in mind I had freezes in Jaunty, CentOS & winXP... it WAS hardware related, but not ram, as I have new ram...)

So for desktop users, have a look at your case...

that sounds a little more like a heat issue.

---

### Post by Caraibes on 2009-08-06
> **jig said:**
> that sounds a little more like a heat issue.
No, I checked that, at first.. Case is open all the time... I check the temperature every now & then... It's not a heat issue... It was a "contact issue"...

Those are what I am referring to, although this is not a photo from my own case: [http://icrontic.com/draco/images/articles/silverstone_ssttj04_pc_case/pci_slot_cu.jpg](http://icrontic.com/draco/images/articles/silverstone_ssttj04_pc_case/pci_slot_cu.jpg)

The idea is that I took off all the blades that were not originally still closed, and since that day: NO FREEZE :)

The case still sits open, as it is a very warm summer in the Caribbean, without air conditioned...

---

### Post by jig on 2009-08-06
wow.

most motherboards are supposed to have enough slack in the edge traces that incidental contact won't cause a short. i believe you, but that's a hard issue to find.

---

### Post by gizmobay on 2009-08-07
I looked at my case and I didn't see any loose pci covers. Seems like other people are running into the same issues so I don't know if it could be something else going on. I wish I could find a fix.

I have a nvidia Geforce 5200 and I'm running 96.43.10. Using ext3 file system

---

### Post by CrustyRatFink on 2009-08-08
Add mine to the list.  It's definitely not hardware.  I'm running a relatively oldish (but problem-free) Asus A8N-SLI board (AMD64 dual cores 2.2GHz) with 3GB RAM, an ATI X600 vid card... erm... a couple 400GB SATA drives... a cup of coffee... my cat...

Anyway, I can't run a session without a lock up.  It seems that it's Xorg related in my case.  I CAN actually ssh into the box when it does this and see that Xorg has gone nuts (100% CPU).  It won't respond to any kill signals.  It seems to be in an infinite loop or something.

The only recourse is a reboot.  Without ssh, the only recourse is a hard reset-- since there's no getting the box to respond from the outside.

Anyway, I post this to make the observation that this is happening on an otherwise completely stable machine with ATI (open source) drivers.  My gut says it's something upstream Xorg.  It's not nvidia, it's not loose covers, it's not an errant keyboard.  It's either the kernel or Xorg.  They are the only thing common in all situations and directly related to the release of jaunty.

Regardless, I guess I'll drop it and wait until it seems like Ubuntu returns to at least being usable.

As it is, it reminds me of Windows 3.1. :D

Best of luck to the developers in finding the problem (assuming it's *one* problem).  I've been cruising around and a very large number of people are experiencing this and wasting their time reinstalling and learning how to type Alt-PrtScn REISUB without hurting themselves.  Knowing that I'm risking a good talking to from one of the faithful, something of this severity making it into a release really gives linux a kick in the nuts.

---

### Post by psychoelf on 2009-08-08
I'm trying out Linux Mint 7 (based off Jaunty).

I updated to the latest Jaunty kernel 2.6.28.14 and grabbed the latest ATI driver from ATI's website (ati-driver-installer-9-7-x86.x86_64.run).  

I also completely uninstalled compiz and have had NO issues in a week. 

I used to love the compiz effects when I first used Ubuntu, but found they cause more problems then they are worth.

---

### Post by gizmobay on 2009-08-08
I have two Ubuntu systems with one being Mythbuntu. MyB is 64 bit on AMD and it's never freezes. The other comp is an older 386 computer and it freezes once a day.

---

### Post by martial on 2009-08-11
For anyone who has an nvidia card, you can try this solution.. seems to be working for me. The freezing was not just *buntu, when i tried fedora it froze a couple times, but this seems to have resolved it. [http://forums.fedoraforum.org/showthread.php?t=182085](http://forums.fedoraforum.org/showthread.php?t=182085)

---

### Post by gizmobay on 2009-08-14
> **martial said:**
> For anyone who has an nvidia card, you can try this solution.. seems to be working for me. The freezing was not just *buntu, when i tried fedora it froze a couple times, but this seems to have resolved it. [http://forums.fedoraforum.org/showthread.php?t=182085](http://forums.fedoraforum.org/showthread.php?t=182085)
This didn't work for me.

---

### Post by colau on 2009-08-15
Freeze in jaunty once..

---

### Post by tipiglen on 2009-08-15
I haven't had time to read right through the thread, but just wanted to say I don't get freezes (not since hardy), but I do get auto-shutdowns, probably always while using firefox (3.0.13 presently) and with flash on the go.  

What with that and problems using blogspot/blogger with firefox, I've almost abandoned firefox for the present (been a fan for longer than I can remember), and I'm using seamonkey.  I haven't had a shutdown except when I've had both browsers up at the same time. (fingers crossed)

Anybody know how to tell my system firefox ain't the default browser?

Hope this is of some use to some of y'all

ed

---

### Post by gizmobay on 2009-08-15
I removed the proprietary nvidia drivers so now I'm using the open source ones. So far no freeze but it's still early.

---

### Post by gizmobay on 2009-08-16
Froze again. I give up.

---

### Post by colau on 2009-08-16
> **gizmobay said:**
> Froze again. I give up.
Install graphics driver.

---

### Post by billdotson on 2009-08-18
I have been having terrible freezing issues and problems with applications not responding with Ubuntu 9.04. I have an Asus P5B Deluxe wifi-ap edition, an Intel Core 2 Duo E6600 overclocked to 3.05GHz with a VCore voltage of 1.35 or so, 2GB dual channel Corsair XMS2 DDR2 900 RAM running at around 600MHz (I think; voltage 2.1V, 4-4-4-12 timings), nVidia 8800GT 512MB with proprietary driver enabled, Seagate 7200.10 250GB hard drive, Maxtor 3200 7200RPM USB 2.0 hard drive (what I have been running Ubuntu off of for 2 years now), an old HP 7-in-1 media card reader (mostly SD type stuff and one USB 2.0 port) and soundblaster audigy 4 card.

I like Ubuntu and all but this is a show stopper. I simply cannot use this if it is going to freeze in the middle of huge file operations and make me corrupt my filesystems on a regular basis.

---

### Post by greg.9 on 2009-08-20
Finally got me too! I have used gutsy, then intrepid and now jaunty on 4 of my machines over the last couple of years, never had much trouble that couldnt be solved by these forums or google and some cut n paste into terminal. 

But these system freezes are awful! ran ok for a while, till the 2 6 28 13 kernel update i think, now running 2 6 29 kernel, still freezing on start up and occasionally during use and always needing hard reboot. have googled to no avail. cant complain because its free and i love the sentiment of ubuntu.

i may try to re install intrepid, but may try another distro to see if it suits my machine better.....................

---

### Post by psychoelf on 2009-08-20
I just reinstalled 9.04 and after first boot did all updates without rebooting.  This seems to bypass the buggy kernel and so far I have had no problems. [-o<

---

### Post by gizmobay on 2009-08-22
I'm starting to think my issue is related to firefox. If I leave it up and running, the freeze occurs. I shut down FF went away for a few days and came back and there wasn't any freeze.

---

### Post by Laysan_A on 2009-08-24
Just wanted to check in (it's been a while) and say that I'm still experiencing periodic freezes/crashes to black. While I had switched to a .30 kernel, I have since switched back to the .28. 

@Chemical Imbalance
I'm glad to hear you found your issue! I hope it's really real this time.

---

### Post by Chemical Imbalance on 2009-08-24
> **Laysan_A said:**
>  

@Chemical Imbalance
I'm glad to hear you found your issue! I hope it's really real this time.

Thanks.  Yeah, I definitely fixed it this time.  That was a few months ago I believe.  
IRQ-sharing issue.

Hope your issue gets resolved soon in jaunty or with karmic.

---

### Post by tipiglen on 2009-08-26
I keep getting shutdowns, but especially while trying to compress video files using Handbrake.```
26 11:38:56 ubuntu hald: mounted /dev/sdc1 on behalf of uid 1000
Aug 26 11:40:02 ubuntu /USR/SBIN/CRON[8129]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 26 11:40:19 ubuntu kernel: [  586.100037] usb 1-3: reset high speed USB device using ehci_hcd and address 2
Aug 26 11:40:37 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake 
Aug 26 11:40:37 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Aug 26 11:42:23 ubuntu kernel: [  710.633034] ACPI: EC: missing confirmations, switch off interrupt mode.
Aug 26 11:45:02 ubuntu /USR/SBIN/CRON[8407]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Aug 26 11:45:02 ubuntu pulseaudio[7533]: module-console-kit.c: GetUnixUser() call failed: org.freedesktop.DBus.Error.UnknownMethod: Method "GetUnixUser" with signature "" on interface "org.freedesktop.ConsoleKit.Session" doesn't exist
Aug 26 11:45:27 ubuntu hald: unmounted /dev/sdc1 from '/media/disk-8' on behalf of uid 1000
Aug 26 11:45:31 ubuntu kernel: [  898.797225] usb 1-1: USB disconnect, address 3
Aug 26 11:50:06 ubuntu /USR/SBIN/CRON[12752]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 26 11:55:05 ubuntu /USR/SBIN/CRON[16772]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Aug 26 11:56:19 ubuntu kernel: [ 1546.205718] ACPI: Critical trip point
Aug 26 11:56:19 ubuntu kernel: [ 1546.205755] Critical temperature reached (105 C), shutting down.
Aug 26 11:56:20 ubuntu init: tty4 main process (6518) killed by TERM signal
Aug 26 11:56:20 ubuntu init: tty5 main process (6519) killed by TERM signal
Aug 26 11:56:20 ubuntu init: tty2 main process (6522) killed by TERM signal
Aug 26 11:56:20 ubuntu init: tty3 main process (6525) killed by TERM signal
Aug 26 11:56:20 ubuntu init: tty6 main process (6526) killed by TERM signal
Aug 26 11:56:20 ubuntu init: tty1 main process (7438) killed by TERM signal
Aug 26 11:56:27 ubuntu kernel: [ 1554.982100] [drm] Num pipes: 1
Aug 26 11:56:29 ubuntu NetworkManager: <info>  (wlan0): device state change: 8 -> 3 
Aug 26 11:56:29 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 38). 
Aug 26 11:56:29 ubuntu kernel: [ 1556.438884] mtrr: MTRR 2 not used
Aug 26 11:56:29 ubuntu NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 7766 
Aug 26 11:56:29 ubuntu kernel: [ 1556.839428] wlan0: disassociating by local choice (reason=3)
Aug 26 11:56:30 ubuntu NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Aug 26 11:56:30 ubuntu avahi-daemon[7158]: Withdrawing address record for 192.168.1.100 on wlan0.
Aug 26 11:56:30 ubuntu avahi-daemon[7158]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.100.
Aug 26 11:56:30 ubuntu avahi-daemon[7158]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug 26 11:56:42 ubuntu exiting on signal 15
Aug 26 11:57:56 ubuntu syslogd 1.5.0#5ubuntu3: restart.
Aug 
```
I have set both cpus at lowest clock speed (1.86GHz) instead of the normal "on demand" setting, and there is no detectable heating up on the case, as has been evident many times before...

I have had this irritating shutdown four times in a row while trying to compress the same 7 minute .mov video.  Unfortunateely, Handbrake doesn't save its work, so every time is a complete re-start from the beginning.

Grrrr!
ed

---

### Post by schmidtbag on 2009-08-26
I think what we really need to focus on is something thats more in our reach.  After reading the first 15 pages and last few, people keep blaming the kernel, file system, and hardware for this.  This is clearly not any of those problems.  Someone was using intrepid and managed to use the same kernel that jaunty does with no issues on the same hardware and same file system, but the jaunty setup crashed.


my point is, what are we running?  i have very few processes running and i cannot figure out whats doing it.  from what i can tell, this is not a gnome related thing, its not compiz related, and its not internet related



by the way, crashes for me happen maybe twice or 3 times a day.  from what i can tell, it happens most when the hard drive, cpu, memory, and network all change their usage levels at the same time.  they don't have to be maxed, they just change

---

### Post by mkarnicki on 2009-08-26
I'm also experiencing freezes up to a couple daily, and after few months it already drives me nuts. I have HP Pavilion tx1320us, running 9.04 with 2.6.28-15, and I have no clue what causes that. But each time it hangs, if I manage to log-off or restart, it asks if it should close: gnome-panel , nautilus. It's always one of these two that ultimately hung, at least for me. I'm not blaming anything and anyone, I just wish we could solve the recent stability issues, because it's the main reason I've been using linux (ubuntu  in particular), because it (used to be) stable.

---

### Post by j.diddy on 2009-08-27
Add me to the chorus of frequently freezing jaunty users. I had the same issue when I first installed ubuntu (version 8.10) a few months back:

[http://ubuntuforums.org/showthread.php?p=6523656&mode=linear#post6523656](http://ubuntuforums.org/showthread.php?p=6523656&mode=linear#post6523656)

This was completely cleared up by installing the then-latest nvidia (v177 -> 180) driver. Unfortunately, I upgraded to 9.04 yesterday morning, and I'm seeing the same thing. Five system freeze incidents in about 5 working hours. This time, there's no later ubuntu-approved nvidia drivers for me to try. I have reverted to the previous listed nvidia driver (180 -> 173) and still freeze.

generic system: Intel DP43TF motherboard with Core2 Duo E8500 at 3.16GHz, nVidia XFX GeForce 8500 GT video board, etc.
OS: Ubuntu Jaunty 9.04 (kernel 2.6.28-15), 64-bit

---

### Post by schmidtbag on 2009-08-30
so... thanks to the terrible instability of jaunty, i no longer have a home folder.  thanks a lot canonical for wasting my time, if ubuntu 9.10 does not shape up, theres going to be a LOT of of new linux users who will never recommend linux to anyone.  as for now, 8.10 has never let me down so thats what i'll be using.


i hope someone finds the solution

---

### Post by uylug on 2009-08-30
A computer at home keeps freezing. It's got an NVIDIA 440MX, 768 Megs of ram and a Pentium 4 2.5Ghz

---

### Post by VastOne on 2009-08-30
> **schmidtbag said:**
> so... thanks to the terrible instability of jaunty, i no longer have a home folder.  thanks a lot canonical for wasting my time, if ubuntu 9.10 does not shape up, theres going to be a LOT of of new linux users who will never recommend linux to anyone.  as for now, 8.10 has never let me down so thats what i'll be using.


i hope someone finds the solution

Maybe you could explain what happened and we would have a better chance at helping you solve the problem.

---

### Post by billharris on 2009-09-01
Just a *bit* more data, perhaps.  I've got two machines running Jaunty, both with ext3.  One, a Toshiba Satellite A10 with Intel video, has Jaunty, but I don't update it often.  It's been amazingly stable; uptime is 45 days.  There are also 92 packages and 152 security updates awaiting me.

The other, an HP laptop with NVIDIA, has been getting worse and worse over the last month, give or take.  (It is kept pretty much up to date.)  Now it freezes randomly about every day -- sometimes twice.  I don't see a pattern: sometimes someone is using it, and sometimes it's sitting idle.  Sometimes FF is open, sometimes not.  

It is *not* apparently related to hibernate, for it seems to come out of hibernation just fine.  It is not apparently related to the time it's been running; I've had it freeze with as little as about 5 minutes uptime, although it's typically 1-3 days, it seems.  When it crashes, the text consoles are all dead.  The mouse usually moves the pointer, but it does nothing.  

Sometimes a few things work.  For example, I right-clicked on FF in the panel tonight and killed FF.  Then I was able to exit Gnus and Emacs properly.  I couldn't get anything else to work or any other windows to respond, so I did the AltSysReq REISUB to recover. 

Usually, it's not nearly this responsive.  Usually I can only move the pointer with the mouse but not do anything except the REISUB sequence.

So I suspect there's something in an update over the last 1-2 months that contributed to this instability, but I can't prove that, of course.  I do have different packages loaded on both, they are running different processors (a 32-bit P4M vs. a Core 2 Duo [64-bit, but running 32-bit Ubuntu]), and different RAM (1GB vs. 4GB).

It's tempting to switch back to 8.04LTS.  I don't really want to lose some of the upgrades such as OO.o 3.x, but I may, especially if Karmic has the same problems.  (Any links to good descriptions how to do that well?)

---

### Post by Ormente on 2009-09-02
I reported my problems with Jaunty here, and had to turn back to Intrepid to get my HP tx1240ef laptop to work.

Since alpha3 i switched to Karmic (32bits, ext4), and my laptop work extremely well since. As it's an alpha i experience some app breaks or glitch from time to time but nothing critical, and everything that break come back in a matter of days. So i wont recomand this for everyone, but finally UBUNTU get back in the right track (for me).

I hope it'll stay fine, as for Jaunty alpha worked well... the freezes appeared sometime near last beta or final release (can't remember).

These random frequent freezes will remain a mystery to me, but i can live with that.

---

### Post by schmidtbag on 2009-09-02
> **VastOne said:**
> Maybe you could explain what happened and we would have a better chance at helping you solve the problem.

this whole topic is about how jaunty crashes.  i was copying my home folder to another drive, ubuntu crashed, and everything was gone.  the drive i was copying to had less than half of what i copied.

due to not wanting to reinstall everything, i figured i could just re-create my home directory and save some time.  i finished doing that yesterday.  as i was typing this message, ubuntu crashed again.


i would like to point out that my netbook runs 9.04 (not the netbook remix) and that hasn't crashed yet, but obviously 9.04 doesn't crash for everyone or else this topic would have another several hundred posts

---

### Post by gizmobay on 2009-09-02
I agree with billharris I can't figure out a pattern as I thought I did and something different pops up. Today, I can't check my yahoo mail without Jaunty freezing. I also agree that something happened a month or two ago and it seems to be getting worse. This is a great distro but this issue is making it almost unusable. I hope someone can provide a solution.

---

### Post by elewis on 2009-09-02
I think it may have something to do with the screen saver settings. I recently installed Jaunty to a (new to me) Dell Dimension Core Duo 64 bit with two monitors. When I have the screen saver set to "random", the machine will likely freeze upon screen saver invocation and have to be unplugged (or hold the start switch for 5 sec) and then restarted. When I have the screen saver set to "blank screen" (a workaround), the machine seems to run fine. It uses a "radeon" card. I have been running Hardy on a Dell Latitude laptop (1 monitor, "random" screen saver), it has never crashed in over a year of intense business use.
I hope this helps.

---

### Post by billharris on 2009-09-03
I doubt it's screen savers.  For one, it rarely fails for me when the screen saver is on.  Actually, I don't think it's ever failed for me when the screen saver was active.

Second, I have my screen saver set to blank screen.

I could be wrong, but I think it's lower level than that.  If it had anything to do with the X display system, then the consoles should work, right?

---

### Post by Anybloodyid on 2009-09-03
I think the problem is Ubuntu recently my system changed after I uninstalled something, Ubuntu desktop went and XFCE appeared. 
When I played a game called Hex a Hop at full screen in Ubuntu it froze instantly but playing it in XFCE at full screen no problems at all.
Conclusion something is up with Jaunty Jackalope.

---

### Post by triplemaya on 2009-09-03
Hi. I'm using onboard intel video, so that's affected as well.


If no one experiences the freeze on ext4 I'd go over to that, but a lack of response on the forum doesn't mean much of course!

---

### Post by triplemaya on 2009-09-03
I'm getting freezes and using onboard intel graphics.

Very interested to see if no ext4 users post. Good to know if it seems to be a 'solution'. ( But of course negative info isn't a great help! )

---

### Post by P4man on 2009-09-03
triplemaya, Ext4 isn't going to make your ubuntu stop freezing. There could be a ton of problems in jaunty, but its *extremely* unlikely Ext3 is causing them. Ext3 about as old and stable and tested as it gets  (something one can't say about Ext4 yet).

FWIW, I tried Ext3 and 4 with jaunty on 3 different machines. 2 of those never gave any problem, one locked up about every hour (especially on heavy network traffic) regardless of filesystem. That machine, i found worked fine with kernel 2.6.28.11 (I think, or whatever kernel comes with a fresh jaunty install)  and it works fine with the unreleased 2.6.30.x kernel. But 2.6.28.15 and newer, would freeze faster than win 3.11.

---

### Post by schmidtbag on 2009-09-03
ext3 most certainly is NOT the problem.  if you read earlier in the posts, people are actually blaming ext4 for the problem, which i also don't think is the cause.  as ext4 is the most significant difference, people are running ext4 with no crashes, and besides, its just an update of ext3, look it up, theres not really any significant change in it.  for a fun fact, ext3 isn't any different than ext2 other than it has journaling added to it.

like i said before, people need to stop blaming hardware.  it could be drivers, but the drivers are used on other distros and they aren't affected by crashing.  i still believe its a process running.  remember when pulseaudio was first released?  loads of people had problems with that and didn't know that was the cause.  i'm fairly positive it isn't a user process, so what else could there be?

---

### Post by Haugesten on 2009-09-03
Installed the latest version of Jaunty on my newly bought Acer 751h few days ago. Ironically, my computer also having problems with randomly freezes. I can move the cursor, but nothing else is not responding and the only thing to do is to shut down the computer with the power-button.

As several other users have tried, I reinstalled Ubuntu with no luck.

Hoping for a solution soon!

---

### Post by Mirge on 2009-09-03
I've installed Ubuntu 9.04 on 4 comps... none had freezing issues (varying hardware) UNTIL I updated. I would be forced to re-install... then it finally dawned on me that one of the updates (I just updated it all) was triggering the freezing. No updates = no freezing on 4 comps. Just my .02 cents.

---

### Post by psychoelf on 2009-09-03
I used to reboot between kernel updates, but after all the crashing issues I had, I tried a reinstall and after the first boot I did all my updates *without* rebooting between.  So far I have not had a crash in weeks.

I read either on this thread or another that it has to do with one of the kernel updates corrupting the install.  This was just a theory, but after my experience I believe it to be true.

FYI I'm running ATI graphics and EXT4 and my uptime on my laptop has been nine days since last shutdown (which I initiated).

---

### Post by gizmobay on 2009-09-04
I still had the original jaunty kernel in grub so I booted into this. The system still froze. Some update somewhere caused this problem but I don't want to re-install since I have everything set the way I like it. I surely hope someone smarter than me can provide a solution.

---

### Post by dynamics on 2009-09-04
I installed Jaunty on 2nd week of July 09 and am not facing any freezing issues except the gnome-panel.... I noticed that this happens when I open Qt based applications (especially graphical-python interfaces - Qt4). 
Then I have to open a terminal (I have set a keyboard shot cut for this) and the 'ps -e' .... search for the 'gnome-panel' job number and then $kill -9 [job id of gnome-panel]

The panel starts working until the next freeze and I do not know when it would happen...

---

### Post by justinjoseph24 on 2009-09-04
I'm having half-hang issues in latest up-to-date Jaunty package set (5 days old.) The mouse will stop responding to clicks at random times. I only really use this computer for Firefox browsing. The only thing I can do is ctrl+alt+F4 to terminal and login/reboot. Then, the system will be stable for a day or so. 

Hardware: nvidia board, 2gb ram, athlon xp 4600+ dual core, nvidia pci-e card, 32 bit ubuntu OS, usb microsoft 5 button mouse. I'll post logs soon.

---

### Post by krendar on 2009-09-04
I have written in this thread before. On my desktop Jaunty is next to unusable since it freezes at least once every 2 hours (can only press the reset button, nothing else helps). I also have an Asus Netbook with Jaunty (not the Netbook-edition) and that one never freezes. My usage pattern is similar on the two computers and I have more or less same applications installed. I think its hardware-related somehow, or at least the freezing-experiences my system has.

Well, I am off to install Karmic Alpha. Hopefully its in a usable state despite the "Alpha" tag, and hopefully there is no freezes in it.

---

### Post by tipiglen on 2009-09-05
My machine simply shuts down whenever a long (ish) youtube video is playing.

That seems to be the principal cause in my case.  It has no problems playing videos with the various freeware players installed.
```
Sep  5 15:06:55 ubuntu kernel: [ 2827.148556] ACPI: Critical trip point
Sep  5 15:06:56 ubuntu kernel: [ 2827.148626] Critical temperature reached (105 C), shutting down.
Sep  5 15:06:56 ubuntu init: tty4 main process (2363) killed by TERM signal
Sep  5 15:06:56 ubuntu init: tty5 main process (2364) killed by TERM signal

```

claims to be temperature dependent, but 1.)  This computer hasn't got temp sensors, so far as I can tell, and, 2.)  I have added noacpi to the appropriate line in menu.lst.

running Linux ubuntu 2.6.28-15-generic i686 unknown

Using Seamonkey browser because firefox seems to have issues with blogspot sites...

I'm still puzzled.  Is there any way to get youtube videos to play using a different player than flash?  That might be an answer.

Grrrr!

---

### Post by P4man on 2009-09-05
> **tipiglen said:**
> My machine simply shuts down whenever a long (ish) youtube video is playing.

That seems to be the principal cause in my case.  It has no problems playing videos with the various freeware players installed.
```
Sep  5 15:06:55 ubuntu kernel: [ 2827.148556] ACPI: Critical trip point
Sep  5 15:06:56 ubuntu kernel: [ 2827.148626] **Critical temperature reached (105 C), shutting down.**
Sep  5 15:06:56 ubuntu init: tty4 main process (2363) killed by TERM signal
Sep  5 15:06:56 ubuntu init: tty5 main process (2364) killed by TERM signal

```

claims to be temperature dependent, but 1.)  This computer hasn't got temp sensors, so far as I can tell, and, 2.)  I have added noacpi to the appropriate line in menu.lst.

running Linux ubuntu 2.6.28-15-generic i686 unknown

Using Seamonkey browser because firefox seems to have issues with blogspot sites...

I'm still puzzled.  Is there any way to get youtube videos to play using a different player than flash?  That might be an answer.

Grrrr!

Woooha, i don't think its making that up. Just about every less-than-5 year old cpu has a thermal monitor. 

And who says it the cpu and not the GPU ? Something is cooking though, check your temps in bios, open the case and check if your fans are running and what's so hot!

---

### Post by tipiglen on 2009-09-05
Thanks for the response.> Woooha, i don't think its making that up. Just about every less-than-5 year old cpu has a thermal monitor. 

Not this one, it seems, and it is five years old.  ```
ed@ubuntu:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +75.0°C  (crit = +85.0°C)                  

ed@ubuntu:~$ 

```
Any way I can seek other sensors? What does "virtual device" mean in this context?
```
ed@ubuntu:~$ acpi -t
     Battery 0: Full, 56%
     Thermal 0: ok, 75.0 degrees C
ed@ubuntu:~$ 

```

Just like every time I try that command!  No variation from 75 degrees - NONE!

Then it stops, and tells me it's reached 105 degrees. 

> check your temps in bios,
How do I do that?

Fans are running.  case is warm, but not hot anywhere.  I'm not sure, but pegging cpu frequencies at 1.86 (as opposed to "on demand") may keep a crash at bay a bit.  Hard to be objective.  

Will try a run of the youtube vid which last crashed and see...

---

### Post by P4man on 2009-09-05
I dont know, you could try heating up your cpu simply by running calculator, put it in scientific mode, enter 9999 and then hit x! .

If you want a real test:

```
sudo apt-get install cpuburn
```

Then run it with burnK7. Keep a close eye on those temps.

It could be it has problems reading the temp, but it still receives an error when the temps pass a critical treshold. One way or another, im pretty sure your problem actually is a overheating cpu!

---

### Post by socool274 on 2009-09-05
I have Ubuntu 9.04 ext3. I used to have problems with freezing whenever I had eclipse open. Also, if I had firefox open with nautilus, and a terminal, and a couple other things, it would freeze. My mouse could move, but any key sequence was unresponsive. If I did anything to the windows, it would be a very delayed response. I reinstalled Ubuntu, with a somewhat older version, but still 9.04, it is working fine for me. I haven't had a crash in a week. Granted, I haven't opened eclipse, as I don't really want to restart my computer every time I open it. But, I do run multiple things while firefox is open.

---

### Post by tipiglen on 2009-09-05
> It could be it has problems reading the temp, but it still receives an error when the temps pass a critical treshold. One way or another, im pretty sure your problem actually is a overheating cpu!
Thanks.   I think you may be right.  > sudo apt-get install cpuburnI'll try that 

btw, It managed the youtube vid ok (if a tiny bit jerky) with the cpus held down.  I then opened the original vid (it was mine) in "Movie player" with the cpus set to "ondemand" and it shut down within a couple of minutes....

Immediately on restart after 15 minute wait:
```
ed@ubuntu:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +75.0°C  (crit = +85.0°C)                  

ed@ubuntu:~$ acpi -t
     Battery 0: Full, 56%
     Thermal 0: ok, 75.0 degrees C
ed@ubuntu:~$ 

```

It can't possibly still be at 75 degrees.  Ambient is about 15 degrees where I sit.

;-)

---

### Post by billharris on 2009-09-06
I've got another observation.  I was sitting at the computer when it began to freeze.  An email arrived in Thunderbird, and then Thunderbird began to act up...the email content pane would expand and shrink vertically, disappear, and then reappear.  (I wondered if it could be due to the email somehow, but I can see it fine now after a reboot.)

At this point, I couldn't get any response except that the pointer would follow the mouse.  Consoles came up blank.

Then I right-clicked on programs in the bottom (status) panel, and I could get a response from some of them, although the pop-up could be offset horizontally (leading me to address a window I didn't expect to address).  I managed to close most windows that way.  As I was doing that, other programs (e.g., Emacs) would sometimes let me type into them, so I could close them naturally.

By the time I got everything closed, I was able to select Restart from the Gnome panel.  Now things are back to normal.

I can't swear that it was leading up to a hard freeze, but similar events in the past (missing consoles, problems selecting or working with windows, etc.) have led to such.  I have noticed on occasion in the past that I had a window of opportunity to shut programs down, but the behavior was erratic.

---

### Post by billharris on 2009-09-06
In case it helps, here's a cut out my logs; you can see me killing tasks, and you can see the reboot.

daemon.log:

```
Sep  6 10:06:36 moenchweiler acpid: client 15509[0:0] has disconnected 
Sep  6 10:06:36 moenchweiler last message repeated 2 times
Sep  6 10:06:36 moenchweiler acpid: client connected from 15509[0:0] 
Sep  6 10:06:38 moenchweiler last message repeated 2 times
Sep  6 10:13:37 moenchweiler console-kit-daemon[3112]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Sep  6 10:13:37 moenchweiler last message repeated 17 times
Sep  6 10:13:37 moenchweiler init: tty4 main process (2495) killed by TERM signal
Sep  6 10:13:37 moenchweiler init: tty5 main process (2496) killed by TERM signal
Sep  6 10:13:37 moenchweiler init: tty2 main process (2503) killed by TERM signal
Sep  6 10:13:37 moenchweiler init: tty3 main process (2504) killed by TERM signal
Sep  6 10:13:37 moenchweiler init: tty6 main process (2505) killed by TERM signal
Sep  6 10:13:37 moenchweiler init: tty1 main process (3724) killed by TERM signal
Sep  6 10:13:37 moenchweiler console-kit-daemon[3112]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Sep  6 10:13:37 moenchweiler console-kit-daemon[3112]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Sep  6 10:14:48 moenchweiler ntpd[3060]: ntpd 4.2.4p4@1.1520-o Wed May 13 21:05:42 UTC 2009 (1)
Sep  6 10:14:48 moenchweiler ntpd[3061]: precision = 1.000 usec
Sep  6 10:14:48 moenchweiler ntpd[3061]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Sep  6 10:14:48 moenchweiler ntpd[3061]: Listening on interface #1 wildcard, ::#123 Disabled
Sep  6 10:14:48 moenchweiler ntpd[3061]: Listening on interface #2 lo, ::1#123 Enabled
Sep  6 10:14:48 moenchweiler ntpd[3061]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Sep  6 10:14:48 moenchweiler ntpd[3061]: kernel time sync status 0040
Sep  6 10:14:48 moenchweiler ntpd[3061]: frequency initialized -20.230 PPM from /var/lib/ntp/ntp.drift
Sep  6 10:14:49 moenchweiler acpid: client connected from 3241[111:123]
``` 

syslog:

```
Sep  6 10:06:36 moenchweiler acpid: client connected from 15509[0:0] 
Sep  6 10:06:38 moenchweiler last message repeated 2 times
Sep  6 10:09:01 moenchweiler /USR/SBIN/CRON[25455]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep  6 10:10:01 moenchweiler /USR/SBIN/CRON[25600]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep  6 10:13:37 moenchweiler console-kit-daemon[3112]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Sep  6 10:13:37 moenchweiler last message repeated 17 times
Sep  6 10:13:37 moenchweiler init: tty4 main process (2495) killed by TERM signal
Sep  6 10:13:37 moenchweiler init: tty5 main process (2496) killed by TERM signal
Sep  6 10:13:37 moenchweiler init: tty2 main process (2503) killed by TERM signal
Sep  6 10:13:37 moenchweiler init: tty3 main process (2504) killed by TERM signal
Sep  6 10:13:37 moenchweiler init: tty6 main process (2505) killed by TERM signal
Sep  6 10:13:37 moenchweiler init: tty1 main process (3724) killed by TERM signal
Sep  6 10:13:37 moenchweiler console-kit-daemon[3112]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Sep  6 10:13:37 moenchweiler console-kit-daemon[3112]: GLib-GObject-WARNING: IA__g_object_get_valist: value location for `gchararray' passed as NULL 
Sep  6 10:13:47 moenchweiler exiting on signal 15
Sep  6 10:14:42 moenchweiler syslogd 1.5.0#5ubuntu3: restart.


```

---

### Post by gizmobay on 2009-09-07
It feels like on my system three things is going on. I wake up in the morning and Ubuntu is prompting me for logging in so obviously x crashed. Secondly sometimes the computer just stops responding to mouse clicks and then just comes out of it. Lastly, sometimes the computer just stops responding all together then I have to alt-sys rq REISUB to get it to reboot.

Has anyone tried 9.10 alpha? I hope this solves these nasty problems.

---

### Post by schmidtbag on 2009-09-07
> **gizmobay said:**
> It feels like on my system three things is going on. I wake up in the morning and Ubuntu is prompting me for logging in so obviously x crashed. Secondly sometimes the computer just stops responding to mouse clicks and then just comes out of it. Lastly, sometimes the computer just stops responding all together then I have to alt-sys rq REISUB to get it to reboot.

Has anyone tried 9.10 alpha? I hope this solves these nasty problems.

i think this is an important topic to note - if your computer crashed before you even logged in, then this must be something x related.  as far as i'm aware, only ubuntu and some of those test distros are running the latest xserver, which is very different from about a year ago.  i think we should look into xserver, because 8.10 used a different version and from what i heard, 9.10 doesn't crash and that may have an xserver update


i myself am getting crashes less and less.  i've gone maybe 2 day without a crash and i'm on this computer a lot

---

### Post by schmidtbag on 2009-09-07
sorry i have no idea what happened, i really did not mean to do this

---

### Post by schmidtbag on 2009-09-07
sorry i have no idea what happened, i really did not mean to do this

---

### Post by schmidtbag on 2009-09-07
sorry i have no idea what happened, i really did not mean to do this

---

### Post by schmidtbag on 2009-09-07
sorry i have no idea what happened, i really did not mean to do this

---

### Post by schmidtbag on 2009-09-07
sorry i have no idea what happened, i really did not mean to do this

---

### Post by schmidtbag on 2009-09-07
sorry i have no idea what happened, i really did not mean to do this

---

### Post by schmidtbag on 2009-09-07
sorry i have no idea what happened, i really did not mean to do this

---

### Post by schmidtbag on 2009-09-07
sorry i have no idea what happened, i really did not mean to do this.  does anyone know how to delete these?

the forums weren't posting when i told it to


i really am sorry

---

### Post by keivanmoradi on 2009-09-08
My ubuntu freezes with a bug related to the screensaver. when I disable the screensaver problem stops. but the problem is now after restart if I don't run the gnomes screensaver without changing settings and close it, system freezes again?

---

### Post by j.diddy on 2009-09-09
> **j.diddy said:**
> Add me to the chorus of frequently freezing jaunty users. I had the same issue when I first installed ubuntu (version 8.10) a few months back:

[http://ubuntuforums.org/showthread.php?p=6523656&mode=linear#post6523656](http://ubuntuforums.org/showthread.php?p=6523656&mode=linear#post6523656)

This was completely cleared up by installing the then-latest nvidia (v177 -> 180) driver. Unfortunately, I upgraded to 9.04 yesterday morning, and I'm seeing the same thing. Five system freeze incidents in about 5 working hours. This time, there's no later ubuntu-approved nvidia drivers for me to try. I have reverted to the previous listed nvidia driver (180 -> 173) and still freeze.

generic system: Intel DP43TF motherboard with Core2 Duo E8500 at 3.16GHz, nVidia XFX GeForce 8500 GT video board, etc.
OS: Ubuntu Jaunty 9.04 (kernel 2.6.28-15), 64-bit

Update: Last Friday I installed 2.6.29.4, and the system has been up and running with no freezes ever since. This is after not being able to get through half a day without a complete system freeze or three(2.6.28-15). Previously I had tried all kinds of video driver and desktop settings to try to ameliorate the problem, with no luck.

I hope this issue gets resolved permanently...

---

### Post by gizmobay on 2009-09-09
Thanks for the info. How did you install the 2.6.29.4 kernel? I don't see it in the repo.

---

### Post by Guile21 on 2009-09-09
Ok, I've been experiencing those freeze troubles several months ago, and reinstalled 8.10 back

I was checking the forums to see if the whole random freezes had a solution, in order to finally get the 9.04 working.

Is the new kernel the holy grail ? Does it really fix the bug, and where to get it ?

I know my post isn't that usefull, but I'm really in need of this new version (to use the newest version of pitivi, among other things). And sorry for my english, I'm not a natural english speaker (if it can be told that way, lol).

---

### Post by klemzy on 2009-09-09
Well I have question about freezing. When I put my computer in hibernation, everything goes fine. However when I turn it on again, it works fine a couple of minutes, then it just freezes completely. Has anyone noticed similar problems?

---

### Post by billharris on 2009-09-10
I just REISUB'd, and I happened to check the consoles for the first time in a long time.  Ctrl-Alt F1 (or F2 or ...) gets me a blinking cursor on a black screen and nothing else, even when X (F7) seems to be working just fine. 

So, two observations:

[LIST]
[*]Is this a symptom that helps debug this freezing problem?
[*]Has something changed in the way one interacts with virtual consoles?
[/LIST]

Is the fact of a freeze and reboot stored somewhere?  It's random enough, so that I'd like to see if there's a pattern that I don't detect simply by observation (and I haven't been writing down all the details).

Has anyone here moved to Karmic?  I'm debating between living with it, moving ahead, or moving back (Hardy LTS perhaps).  With less than two months to Karmic, that's tempting; I don't really want to give up OO.o 3 and the ability to read .docx files on those occasions when I get one.

---

### Post by j.diddy on 2009-09-10
> **gizmobay said:**
> Thanks for the info. How did you install the 2.6.29.4 kernel? I don't see it in the repo.

I followed the instructions I found here:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/384639](https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/384639)

I did leave out an important piece of info-- I am not using the nvidia driver and am running in low graphics mode. That may (or may not) be very signififcant in not seeing system freeze, and may not be an option in your situation. (I use the machine for development, so don't need superfast/3D graphics. Things like scrolling are slow but better than putting up with frequent system hangs.)

Edit: Here's better documentation on installing a precompiled mainline kernel: 

[https://wiki.edubuntu.org/KernelTeam/MainlineBuilds](https://wiki.edubuntu.org/KernelTeam/MainlineBuilds)

---

### Post by billharris on 2009-09-11
In case it helps, I noticed something else.  At least when it froze 30 minutes or so ago, I could right-click on FF in the bottom panel, and I would sometimes get a pop-up menu associated with FF.  If I did, I could then select another window and do something in that window.  I didn't need to select anything on that pop-up; I just needed to activate it.

If I wanted to switch  to another window, I'd have to repeat the process.

Sometimes it wouldn't give me a pop-up.  When that happened, it was usually because the actual mouse position and the pointer seemed to be in different places. That is, I might get an onscreen reaction, but it wouldn't be for the panel icon I was trying to select.

Once I did a drag select in Emacs to copy some text that I wanted to paste in another window.  After doing that, any clicks with the mouse were intercepted by Emacs, no matter where the pointer was.

I'm not blaming FF or Emacs, and I'm not sure this is relevant.  The frequency of freezing is increasing, though (2-3 times today so far), and so it's a bit easier to note what is (and isn't) characteristic of the problem.

---

### Post by billharris on 2009-09-14
I tried maxcpus=1 yesterday, but my system froze within a couple of hours.  

Then I tried to switch from the nvidia 173 driver as installed by envyng to nouveau out of the universe repo.  That failed, but Ubuntu fell back to the generic drivers, and those are working okay for over 24 hours so far.  I've got virtual consoles back, too.

Hibernate seems not to work (it hibernates, but it never wakes up), the fan seems to run more on my laptop (no hard evidence, unfortunately), and the Gnome panel sensors applet doesn't show any temperature.  I think I can live with all that (especially if suspend works -- I'll find out tonight) as long as it doesn't crash.

Instead of separate X displays as I had before, I now have something similar to Twinview, except that there are no panels on the second display, and new windows don't open in the middle spanning both displays.  Given the problem that FF doesn't play nice on dual X displays if it's on one X display, email is on another, and you open a link in email, this is better.

Does anyone have any tips on Nouveau?  Of course, it claims not to have  a working suspend either.  Anyone got a link to working well with the generic driver?

---

### Post by billharris on 2009-09-15
Nevermind.  

It froze again about 36 hours after switching to the generic video driver.

---

### Post by gizmobay on 2009-09-15
I upgraded to the kernel suggested in another post and I haven't had any problems since I upgraded. The only thing is it hangs on dkms when booting due to some issue with the driver.

---

### Post by iiretepii on 2009-09-15
> **Stenico said:**
> My experience - 2 hard lock freezes in 20 minutes after upgrading to Jaunty.

Reading people's similar experiences, all I can say is that either Canonical's pre-release testing procedures are a joke, or they simply don't care.

I can't help but contrast this experience with my full-time use of Windows 7 *beta* during which I've experienced one serious crash in 3 months.

I would prefer to be using linux, but I won't be using Jaunty over my Win 7 install in a hurry :-(.

Windows 7 is a joke.  I used it and it consumed my machine twice.

---

### Post by col48 on 2009-09-16
> **Haugesten said:**
> Installed the latest version of Jaunty on my newly bought Acer 751h few days ago. Ironically, my computer also having problems with randomly freezes. I can move the cursor, but nothing else is not responding and the only thing to do is to shut down the computer with the power-button.

As several other users have tried, I reinstalled Ubuntu with no luck.

Hoping for a solution soon!
Running Hardy for about 8 months now (ext3 filesystem).  About 3 'freezes' in that time.  When it happened yesterday, no user applications were running and I was wanting to shut down.  I could move the mouse cursor round but all clicks were apparently ignored.  I do not have complex keyboard combinations at my fingertips (no pun intended!) but nothing I tried with the keyboard had any effect.

Is there something better to do than just power off?  When I powered on a minute or so later it started normally as if it had been a normal shutdown.

On the face of it this has the same symptoms as Haugesten had with Jaunty.

---

### Post by schmidtbag on 2009-09-16
ATTENTION EVERYONE:


it seems to me the latest release of the 2.6.28-15 kernel is the solution, or at least one of them.  Ever since I updated to that I never got a single crash.  Keep in mind that there is more than 1 release of this kernel, and I got crashes with an earlier version.

I don't expect this to help everyone, but it may be a solution to some

---

### Post by pveurshout on 2009-09-16
I have also been experiencing random lockups in Jaunty and had absolutely no idea what was causing them. I don't know if it's of any help to any of you (hopefully it is ;)), but my problems completely disappeared (fingers still crossed, though) when I reformatted my NTFS partition (which I heavily used for torrenting) to ext3..

---

### Post by pveurshout on 2009-09-18
OK, it just froze again (first time in about a week I had such a *complete* lockup, though) so unfortunately NTFS doesn't seem to be the problem. Maybe it's related, though, as I'm finally able to leave my bittorrent client running for more than just half an hour..

> **col48 said:**
> 
Is there something better to do than just power off?  When I powered on a minute or so later it started normally as if it had been a normal shutdown.


You can try using some Alt+SysRq+<key> combinations, which are a way to give some direct low-level commands to the kernel in case your system is messed up. Although it doesn't work if your system *entirely* freezes, I always try this before hitting the power button. It's definately worth the 'trouble'. Here's how it works:

Press Alt, then SysRq. If your computer has no SysRq button, try Print Screen instead. Also, if you're on a laptop, you might have to hold down the Fn-key as well (I do). Now hold these keys while you press R, then E, I, S, U, B (let go of each of these keys after typing them, don't end op holding down all 8 keys at the same time, lol)

What is does: (corrections welcome :))
R - gets keyboard control back from X (?)
E - end all processes
I - kill all processes (for those who don't want to end properly)
S - synchronize file systems
U - remount all file systems as read-only
B - immediate hard reboot without unmounting anything (which shouldn't be a problem, as you synchronized and mounted as read-only just before this step)

Be sure to wait a couple of seconds before pressing the next key in order to give your system some time to complete the operations. After pressing Alt+SysRq+B the screen should go blank immediately; if it doesn't you'll have to use your power button after all because your system is, unfortunately, entirely stuck.

This has worked for me quite often, though when it *really* freezes, it's *really* frozen and it won't work.

---

### Post by gizmobay on 2009-09-18
> **gizmobay said:**
> I upgraded to the kernel suggested in another post and I haven't had any problems since I upgraded. The only thing is it hangs on dkms when booting due to some issue with the driver.

Back to the drawing board. Frozen solid this morning.

---

### Post by pveurshout on 2009-09-19
> **gizmobay said:**
> Back to the drawing board. Frozen solid this morning.

I'm actually starting to wonder whether there are people at all who *don't* have their Jaunty freeze on them occasionally while doing 'normal stuff' :lol: There are just so many forum posts and bug reports mentioning 'random' crashes..

Based upon what I've read, I'm currently suspecting hardware timing to be the problem (mentioned in [this post]("http://ubuntuforums.org/showpost.php?p=7406928&postcount=360") in the current thread). Just applied a workaround, so I guess I'll know within a few days..

By the way, does anyone know 'how' Karmic is being created? I mean, can it be considered a new OS or is it based upon Jaunty? (Which might result in the same freezing-behaviour being 'copied', as I haven't found a single person yet who actually knows what causes it.)

---

### Post by tipiglen on 2009-09-19
As noted before, I seem to have mostly avoided the shutdowns (attributed to "overheating") by setting both cores to run at the lowest speed available, but last night, in the middle of a second seven minute video (Jackson Browne's before the Deluge"),  "beep - boop". and:
```
Sep 19 03:05:01 ubuntu /USR/SBIN/CRON[9064]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Sep 19 03:10:01 ubuntu /USR/SBIN/CRON[9123]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 19 03:15:01 ubuntu /USR/SBIN/CRON[9286]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Sep 19 03:17:01 ubuntu /USR/SBIN/CRON[9348]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 19 03:19:24 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake 
Sep 19 03:19:24 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Sep 19 03:20:01 ubuntu /USR/SBIN/CRON[9404]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 19 03:22:41 ubuntu kernel: [13164.537502] ACPI: Critical trip point
Sep 19 03:22:41 ubuntu kernel: [13164.537562] Critical temperature reached (105 C), shutting down.
Sep 19 03:22:41 ubuntu init: tty4 main process (2365) killed by TERM signal
Sep 19 03:22:41 ubuntu init: tty5 main process (2366) killed by TERM signal
Sep 19 03:22:41 ubuntu init: tty2 main process (2369) killed by TERM signal
Sep 19 03:22:41 ubuntu init: tty3 main process (2371) killed by TERM signal
Sep 19 03:22:41 ubuntu init: tty6 main process (2373) killed by TERM signal
Sep 19 03:22:41 ubuntu init: tty1 main process (3275) killed by TERM signal
Sep 19 03:22:53 ubuntu kernel: [13176.708269] [drm] Num pipes: 1
Sep 19 03:22:53 ubuntu NetworkManager: <info>  (wlan0): device state change: 8 -> 3 
Sep 19 03:22:53 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 38). 
Sep 19 03:22:54 ubuntu NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 3589 
Sep 19 03:22:54 ubuntu NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Sep 19 03:22:55 ubuntu avahi-daemon[3005]: Withdrawing address record for 192.168.1.100 on wlan0.
Sep 19 03:22:55 ubuntu avahi-daemon[3005]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.100.
Sep 19 03:22:55 ubuntu avahi-daemon[3005]: Interface wlan0.IPv4 no longer relevant for mDNS.
Sep 19 03:22:55 ubuntu kernel: [13179.080103] mtrr: MTRR 2 not used
Sep 19 03:23:08 ubuntu exiting on signal 15

```

(sleep, breakfast, dogs walked...... 
Sep 19 11:05:10 ubuntu syslogd 1.5.0#5ubuntu3: restart.
check email, etc.)

and, just now, with only Seamonkey and Thunderbird running, 
(no videos, and barely warmed up while typing the above:
```
Sep 19 11:10:01 ubuntu /USR/SBIN/CRON[3836]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 19 11:15:02 ubuntu /USR/SBIN/CRON[4049]: (root) CMD ([ -x /usr/lib/sysstat/sa1 ] && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; [ "$ENABLED" = "true" ] && exec /usr/lib/sysstat/sa1 $SA1_OPTIONS 1 1 ; })
Sep 19 11:15:03 ubuntu pulseaudio[3383]: module-console-kit.c: GetUnixUser() call failed: org.freedesktop.DBus.Error.UnknownMethod: Method "GetUnixUser" with signature "" on interface "org.freedesktop.ConsoleKit.Session" doesn't exist
Sep 19 11:17:01 ubuntu /USR/SBIN/CRON[4107]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 19 11:20:01 ubuntu /USR/SBIN/CRON[4166]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 19 11:22:54 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake 
Sep 19 11:22:54 ubuntu NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed 
Sep 19 11:23:53 ubuntu init: tty4 main process (2371) killed by TERM signal
Sep 19 11:23:53 ubuntu init: tty5 main process (2372) killed by TERM signal
Sep 19 11:23:53 ubuntu init: tty2 main process (2375) killed by TERM signal
Sep 19 11:23:53 ubuntu init: tty3 main process (2378) killed by TERM signal
Sep 19 11:23:53 ubuntu init: tty1 main process (3288) killed by TERM signal
Sep 19 11:23:53 ubuntu init: tty6 main process (2379) killed by TERM signal
Sep 19 11:23:53 ubuntu kernel: [ 1147.316717] ACPI: Critical trip point
Sep 19 11:23:54 ubuntu kernel: [ 1147.316777] Critical temperature reached (105 C), shutting down.
Sep 19 11:24:02 ubuntu NetworkManager: <info>  (wlan0): device state change: 8 -> 3 
Sep 19 11:24:02 ubuntu NetworkManager: <info>  (wlan0): deactivating device (reason: 38). 
Sep 19 11:24:02 ubuntu NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 3607 
Sep 19 11:24:02 ubuntu kernel: [ 1154.997333] wlan0: direct probe to AP 00:24:56:e7:5b:13 try 1
Sep 19 11:24:02 ubuntu kernel: [ 1155.002969] wlan0 direct probe responded
Sep 19 11:24:02 ubuntu kernel: [ 1155.002995] wlan0: authenticate with AP 00:24:56:e7:5b:13
Sep 19 11:24:02 ubuntu kernel: [ 1155.005153] wlan0: authenticated
Sep 19 11:24:02 ubuntu kernel: [ 1155.005178] wlan0: associate with AP 00:24:56:e7:5b:13
Sep 19 11:24:02 ubuntu kernel: [ 1155.009466] wlan0: RX AssocResp from 00:24:56:e7:5b:13 (capab=0xe31 status=0 aid=1)
Sep 19 11:24:02 ubuntu kernel: [ 1155.009482] wlan0: associated
Sep 19 11:24:02 ubuntu kernel: [ 1155.351479] wlan0: disassociating by local choice (reason=3)
Sep 19 11:24:03 ubuntu NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess  
Sep 19 11:24:03 ubuntu avahi-daemon[3011]: Withdrawing address record for 192.168.1.100 on wlan0.
Sep 19 11:24:03 ubuntu avahi-daemon[3011]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.100.
Sep 19 11:24:03 ubuntu avahi-daemon[3011]: Interface wlan0.IPv4 no longer relevant for mDNS.
Sep 19 11:24:04 ubuntu kernel: [ 1158.841038] [drm] Num pipes: 1
Sep 19 11:24:05 ubuntu kernel: [ 1159.578821] mtrr: MTRR 2 not used
Sep 19 11:24:18 ubuntu exiting on signal 15

```
I was going to suggest it had something to do with Youtube or CRON....

But the computer hasn't had time to get warm, never mind hot.

I'm at a loss to understand this.

---

### Post by VastOne on 2009-09-19
> **pveurshout said:**
> I'm actually starting to wonder whether there are people at all who *don't* have their Jaunty freeze on them occasionally while doing 'normal stuff' :lol: There are just so many forum posts and bug reports mentioning 'random' crashes..

Based upon what I've read, I'm currently suspecting hardware timing to be the problem (mentioned in [this post]("http://ubuntuforums.org/showpost.php?p=7406928&postcount=360") in the current thread). Just applied a workaround, so I guess I'll know within a few days..

By the way, does anyone know 'how' Karmic is being created? I mean, can it be considered a new OS or is it based upon Jaunty? (Which might result in the same freezing-behaviour being 'copied', as I haven't found a single person yet who actually knows what causes it.)


I have six machines that all at one time froze with Jaunty.  In all situations, I have had to go into bios level and tweak to the cpu and memory settings and voltage that worked best with each other. This took time and effort, but since then I have had 0 crashes or freezes over a 5 month period. I have different levels of 2.6 kernel and above, so I never saw a new kernel release solve any of my issues ( although I tried them ll). It was not until I adjusted my hardware that I saw improvement

I have a range of machines from HP, Gateway both Intel, and 4 built by me that have 1 with a MSI mobo, 3 with Gigabytes mobo's, all 4 are AMD quads.

The only common variable on all of this is nVidia graphics card, but I eliminated nvidia early on by removing the card on several machines and still seeing the freeze.

I have always thought this is hardware of timing related and with so little resolution seen or feedback from the developers, I cannot see it as kernel issue.  

6 machines and 0 freezes in 4 months of 24 hour per day use.

---

### Post by Mirge on 2009-09-19
As I've mentioned before... the freezing problem for me was UPDATES. I just went to the update manager & updated everything that had an update available. Upon doing that, FREEZE......... re-installed w/out updating... and here ya go:

mike@mike-kubuntu:~$ uname -a
Linux mike-kubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
mike@mike-kubuntu:~$ uptime
 11:01:10 up 39 days, 14:50,  1 user,  load average: 0.25, 0.08, 0.08
mike@mike-kubuntu:~$

Kubuntu 9.04, up 39 days 15 hrs...

---

### Post by pveurshout on 2009-09-19
> **VastOne said:**
> I have six machines that all at one time froze with Jaunty.  In all situations, I have had to go into bios level and tweak to the cpu and memory settings and voltage that worked best with each other. This took time and effort, but since then I have had 0 crashes or freezes over a 5 month period. I have different levels of 2.6 kernel and above, so I never saw a new kernel release solve any of my issues ( although I tried them ll). It was not until I adjusted my hardware that I saw improvement

That sounds interesting! I'm gonna look into that if I keep experiencing these problems with hpet=disable added as a boot option in grub (and if I have time lol)

> **VastOne said:**
> I have a range of machines from HP, Gateway both Intel, and 4 built by me that have 1 with a MSI mobo, 3 with Gigabytes mobo's, all 4 are AMD quads.

The only common variable on all of this is nVidia graphics card, but I eliminated nvidia early on by removing the card on several machines and still seeing the freeze.

I have always thought this is hardware of timing related and with so little resolution seen or feedback from the developers, I cannot see it as kernel issue.  

6 machines and 0 freezes in 4 months of 24 hour per day use.

Yeah, I tried using the previous kernel but it didn't make any difference (of course I should've tried more than just two, but unfortunately you can get a lot of stuff on Ebay except for time..) Anyway, with this hpet=disable-thing I'm really looking forward to having my system not freeze for like...well, two days would be awesome. Actually, today X crashed on me, but considering all other problems (varying from dmesg saying some process tainted the kernel or something, to the system *just* freezing) that was just a tiny inconvenience.

> **Mirge said:**
> As I've mentioned before... the freezing problem for me was UPDATES. I just went to the update manager & updated everything that had an update available. Upon doing that, FREEZE......... re-installed w/out updating... and here ya go:

mike@mike-kubuntu:~$ uname -a
Linux mike-kubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
mike@mike-kubuntu:~$ uptime
 11:01:10 up 39 days, 14:50,  1 user,  load average: 0.25, 0.08, 0.08
mike@mike-kubuntu:~$

Kubuntu 9.04, up 39 days 15 hrs...

That sounds interesting. Actually, I do believe it may have been getting worse over time, but I'm not really sure. Anyway, if it's really updates that cause system freezes then..that's bad, really, really bad.

---

### Post by col48 on 2009-09-21
Well, no more freezes since, but this (post 646 by pveurshout) looks very useful to stash away in my personal 'how-to' file - the master copy is on paper!

Thanks.

---

### Post by ezsit on 2009-09-21
> It's not a LTS (stable) release right?

Jaunty is a stable release, just not one with long term support. LTS does not mean stable, it just means that there are security fixes for a longer term than the regular STABLE releases.

---

### Post by billharris on 2009-09-21
FWIW: I just filed [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/434416](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/434416)  The symptoms with the generic driver looked different than I've seen reported before -- essentially all of memory getting used by xorg.  Perhaps that will help someone find the problem.

---

### Post by t0mm4n on 2009-09-22
Hate to say, but me too!

I did fresh install of Kubuntu Jaunty 9th or 10th of september. It worked OK about a week, until last saturday my computer froze totally. It has happened few times after first one. I used nvidia drivers, but rolled back to nv. No noticeable change.

Freezes happen quite randomly, alltough it happened twice when Amarok was scanning hard drives. I don't dare to run Amarok anymore, until problem is solved. Once freeze happened in login screen. Do you have freezes, if you kill X and kdm/gdm ? I use my setup mainly as samba and ssh server, so stability is an issue for me. If this won't be solved soon, I'll need to revert to 8.04. Or maybe upgrade to 9.10?

I had 8.04 LTS in my setup before, and it ran without problems over a year, usually 24/7, so I don't think it's hardware problem.

---

### Post by pveurshout on 2009-09-22
> **t0mm4n said:**
> 
Freezes happen quite randomly, alltough it happened twice when Amarok was scanning hard drives. I don't dare to run Amarok anymore, until problem is solved.


Are you scanning your music from an NTFS-formatted drive? I had LOTS of problems with that, like multiple-time daily random freezes with only one thing in common: usage of my NTFS drive, for example while running a bittorrent client. When I reformatted to ext3 it worked like a charm again, also under heavy (torrenting) usage. I do have to add that after about a week it did freeze up again, so either NTFS was not the cause (but it's definately related somehow, as it was perfectly fine for over a week) or the 'new' freeze was not related to it.

Anyway, for the sake of completeness, when it froze again I noticed some errors in dmesg ("CE: hpet increasing min_delta_ns to 15000/22500/30000/etc. ns") I'd had before. I disabled hpet as a hardware timer and it hasn't frozen since (except for X, but that's definately unrelated). It's been only 3 days, so can't say that it's fine yet, but I'm keeping my fingers crossed :)

---

### Post by dbutcher on 2009-09-23
> **billharris said:**
> FWIW: I just filed [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/434416](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/434416)  The symptoms with the generic driver looked different than I've seen reported before -- essentially all of memory getting used by xorg.  Perhaps that will help someone find the problem.

Bill,
just want to say a 'good on ya' for noticing the xorg behaviour and filing this bug.  I've read all the posts in this thread looking for a solution to the 'random crashes', and tried many of the suggestions, without success, and all with no actual facts in the way of log entries or other error reports.  Thank you for helping us break out of the endless go-around.

I filed a sister bug report here: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/435011]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/435011")  
I expect they'll mark it as a duplicate, but I wanted to report the same 100% CPU Xorg behaviour on 64-bit hardware using the 173 Nvidia driver.

Looking forward to the day when this is all behind us ...
Cheers,
Dave

---

### Post by zabrinaliang@gmail.com on 2009-09-23
You may just have to give it time to unfreeze.  The Ubuntu Jaunty Jackalope does it every once in a while with new users, but once you let the OS catch up, then you are good to go.

2.  force quit the application and start from where you left off?
3.  Force quit the application and game over, and start over with same application.
3.  Exit out and start over.

---

### Post by t0mm4n on 2009-09-23
> **pveurshout said:**
> Are you scanning your music from an NTFS-formatted drive? I had LOTS of problems with that, like multiple-time daily random freezes with only one thing in common: usage of my NTFS drive, for example while running a bittorrent client. When I reformatted to ext3 it worked like a charm again, also under heavy (torrenting) usage.

No, I have LUKS+LVM2+ext3, in that order. Oh, and I use cryptoswap too. So heavy disk activity means also heavy CPU load. 

I plan to leave my computer on without X and use it only as a server. See how long it stays up and running.

---

### Post by billharris on 2009-09-23
Thanks, Dave.  I think it's important to try to log bugs clearly so someone can fix them.

BTW, for the person who has advocated simply waiting for Jaunty to unfreeze, I've waited hours to no avail.  As is noted on the Ubuntu site about reporting crashes and freezes, there are many causes, and what causes your machine to freeze may be different than what affects me.  Data is important.

---

### Post by VastOne on 2009-09-23
> **billharris said:**
> Thanks, Dave.  I think it's important to try to log bugs clearly so someone can fix them.

BTW, for the person who has advocated simply waiting for Jaunty to unfreeze, I've waited hours to no avail.  As is noted on the Ubuntu site about reporting crashes and freezes, there are many causes, and what causes your machine to freeze may be different than what affects me.  Data is important.

So is feedback....

And I have yet to see any that even suggests that any development or solution is in order....

not trying to argue... I just wonder why there is so little information on such a broad issue...

---

### Post by billharris on 2009-09-24
VastOne, I'm not sure.  I suppose it's a combination of 

[LIST]
[*]People working on problems don't yet have enough cleaned defect information to fix the problem(s).
[*]Not enough people are fixing defects (this is FOSS).
[*]The Ubuntu approach means that security issues get fixed, not other things, at least until the next revision.  We may all want an exception for this one(s), I know.
[/LIST]

I don't intend this as a criticism of your question.  I just know a little about what it takes to get something like this fixed, as may you, and I'm conjecturing some answers.  

It would be great to see at least a workaround, but one has to understand the problem at least to a certain degree to get a workaround that is more than superstition.

BTW, I forgot to say: Dave, thanks to you, too, for filing a bug report.

---

### Post by VastOne on 2009-09-24
> **billharris said:**
> VastOne, I'm not sure.  I suppose it's a combination of 

[LIST]
[*]People working on problems don't yet have enough cleaned defect information to fix the problem(s).
[*]Not enough people are fixing defects (this is FOSS).
[*]The Ubuntu approach means that security issues get fixed, not other things, at least until the next revision.  We may all want an exception for this one(s), I know.
[/LIST]

I don't intend this as a criticism of your question.  I just know a little about what it takes to get something like this fixed, as may you, and I'm conjecturing some answers.  

It would be great to see at least a workaround, but one has to understand the problem at least to a certain degree to get a workaround that is more than superstition.

BTW, I forgot to say: Dave, thanks to you, too, for filing a bug report.

Well said Mr Harris.  I too am aware of the process and understand it and agree with it.  

It is the problem solver in me and a good majority of other folks that have an itch that we cannot reach.

No one ever said this would be easy and mayhap in the next iteration(s) we can all see it for what it is.  maybe it is the complexity of the whole problem that has me so discombobulated and in need of answers. As I have said in earlier posts, I have seen all of these issues on several machines but have been able to solve them with timing tweaks at the bios level. I believe that it is as much of a heat or heat sensor issue as anything, but I have no conviction or resource to confirm.

Thanks for your responses and I never saw it as a criticism but a very good explanation of the processes.

VastOne

---

### Post by thijsz on 2009-09-24
as many of you i've also had several freezes
my 'story' :

pc dell dektop P4 (service tag H680V1J) > intell onboard video

1) first dual boot : 
ubuntu studio (RT kernel, ext3) 8.04 / ubuntu studio 9.04 (RT kernel, ext4)
 > 0.0 freezes with 8.04 (as in never-Ever)
 > frequent freezes with 9.04 (average of 1 every 1-2 hours)
   > tried some things with older/newer drivers for the intel video > no luck

2) followed the 'ext4-is-to-blame' thread > refromatted to ext3 (although i'm not sure if it was actually formatted, or if it was just 'transformed' to ext3, because the reformat was really quick ... ? > i'm no expert).  installed ubuntu studio 9.04 again > freezes

3) installed standard 9.04 Xubuntu over the ubuntu studio 9.04 and added the ubuntu studio packages (not the desktop, not the video packages) >  runs a LOT more stable and kicks standard (gnome) ubuntu's *** when it comes to speed ! ... but .. snif .. i have had 1 freeze just like the ones i had before

4) on my XP laptop i have ubuntu 9.04 installed (Wubi install) with the ubuntu studio packages installed and have not experienced sys freezes

Just like numerous people here i'm trying to help as much as possible by providing info, but since i'm no linux expert it is sometimes hard to get the correct info.  i know i can check the logs check memory usage and 1 or 2 other thing, but is there some sort of structured and 'automated' way to get info out of my machine and post it here so 'all' relevant info (about hardware, kernel version, filesystem, video driver versions ...) is gathered in a correct way ?

btw : i find it very hard to beleive that hardware(timings) are causing this, why with 9.04 and not with 8.04 ??

let's not give up now guys !

---

### Post by dbutcher on 2009-09-24
>  ... is there some sort of structured and 'automated' way to get info out of my machine and post it here so 'all' relevant info (about hardware, kernel version, filesystem, video driver versions ...) is gathered in a correct way ?

I found this page very helpful:
[https://wiki.ubuntu.com/X/Reporting]("https://wiki.ubuntu.com/X/Reporting")

Cheers,
Dave

---

### Post by billharris on 2009-09-24
> **thijsz said:**
> as many of you i've also had several freezes

Just like numerous people here i'm trying to help as much as possible by providing info, but since i'm no linux expert it is sometimes hard to get the correct info.  i know i can check the logs check memory usage and 1 or 2 other thing, but is there some sort of structured and 'automated' way to get info out of my machine and post it here so 'all' relevant info (about hardware, kernel version, filesystem, video driver versions ...) is gathered in a correct way ?

let's not give up now guys !

Thanks for your help!  You may know this, but I think the help we provide each other here is more in the nature of workarounds and general tips.  If you want to get a bug resolved, you have to submit it in Launchpad, as someone just suggested.

---

### Post by thijsz on 2009-09-25
> **billharris said:**
> If you want to get a bug resolved, you have to submit it in Launchpad, as someone just suggested.

hmmm ... i thought we were all trying to get this bug fixed ;-)
i'll check out Launchpad (together with dbutcher's link), but still : to be able to help each other with tips you need to have relevant data available so it can be included when you post your findings.  right ?

another remark : since this is a place where a lot of 'regular' users (read people who just want to use ubuntu for typical day-to-day desktop tasks, and with no or limited programming/debugging skills) post their findings, it can be a hell of a job to read trough all these post hoping to find something that _might_ be the/a solution for them.  the fact that you can only find bits and pieces of info here does not make it any easier ...  

I also doubt that a 'regular' user will have the courage to actually file a bug (especially after reading this complete thread ;-) > bottom line : a lot of info that is in here will probably never find it's way to Launchpad...

BUT i'm gonna stop nagging now and file my first bug report !!!
(just took a look at [https://wiki.ubuntu.com/X/Reporting](https://wiki.ubuntu.com/X/Reporting) and i'll do my best )

grtzzz
thijszzz

---

### Post by VastOne on 2009-09-25
> **thijsz said:**
> 

btw : i find it very hard to beleive that hardware(timings) are causing this, why with 9.04 and not with 8.04 ??

let's not give up now guys !

I never said it was the cause, I said I resolved all of my issues by tweaking timings. 

When I was on Hardy, I never had any issues at all with freeze up (outs) at all. I also had gKellm monitors and lm-sensors working perfectly on each of them.

Once I upgraded to Juanty the first month or so was great. After a specific update I began to see the freeze like so many others and over this time, lm-sensors refuses to find the same things it did before on the same exact machines...Jaunty and it's updates are the only things that have changed. 

Change management is supporting the processing of changes and enabling traceability of changes, which should be possible through proper execution of the process. We are that traceability and anything we can supply is paramount to the resolution

Except for missing gKrellm, I am completely happy with these 6 production machines running 24-7 and no freeze outs. Until I made the changes I made, they were freezing 6-15 times a day. I know of no other changes or updates from Jaunty that fixed it but I do know what I did to resolve it:P

---

### Post by MKe2 on 2009-09-25
I am a a Linux noob:
I do have total crashes on Ubuntu 9.04. At random, the computer totally crashes, no mouse movement, capslock and numlock LEDs on my keyboard keep flashing. The one thing all these crashes have in common is that it always happens within 10 minutes of booting and always after a cold start. It's not one of the programs. It happened sometimes that I logged on, left and came back and the computer was crashed (screen showed my empty Gnome desktop). The strange thing is that it doesn't always crash. On average it crashes about once every 3 start-ups I think. If the system doesn't crash within 10 minutes after booting, I know it'll be fine.
I've been playing with the nvidia drivers, turning them off and one, no difference.
Being a newby I'm not sure what to do next.

My system:
- Intel Dualcore 6300 processor
- 2 GB RAM
- Geforce 7600
- 350 Gb HD
- Ext3
- Kernel: 2.6.28-15-generic

---

### Post by t0mm4n on 2009-09-26
No freeze for while. I've killed kdm (sudo /etc/init.d/kdm stop).

But I noticed strange processes, named [kdmflush] , with brackets... well you see:

```

ps aux | grep kdm
root      2077  0.0  0.0      0     0 ?        S<   Sep25   0:00 [kdmflush]
root      5114  0.0  0.0      0     0 ?        S<   Sep25   0:00 [kdmflush]
root      5149  0.0  0.0      0     0 ?        S<   Sep25   0:00 [kdmflush]
root      5185  0.0  0.0      0     0 ?        S<   Sep25   0:00 [kdmflush]
root      5204  0.0  0.0      0     0 ?        S<   Sep25   0:00 [kdmflush]
root      5211  0.0  0.0      0     0 ?        S<   Sep25   0:00 [kdmflush]
root      5219  0.0  0.0      0     0 ?        S<   Sep25   0:00 [kdmflush]

```

And they are pretty old too. Even sudo kill -KILL won't kill'em. But since gnome users suffer freezes also I don't really know.

:edit:
Never mind, those seems to be related with LUKS.

---

### Post by pveurshout on 2009-09-27
> **MKe2 said:**
> I am a a Linux noob:
I do have total crashes on Ubuntu 9.04. At random, the computer totally crashes, no mouse movement, capslock and numlock LEDs on my keyboard keep flashing. The one thing all these crashes have in common is that it always happens within 10 minutes of booting and always after a cold start. It's not one of the programs. It happened sometimes that I logged on, left and came back and the computer was crashed (screen showed my empty Gnome desktop). The strange thing is that it doesn't always crash. On average it crashes about once every 3 start-ups I think. If the system doesn't crash within 10 minutes after booting, I know it'll be fine.
I've been playing with the nvidia drivers, turning them off and one, no difference.
Being a newby I'm not sure what to do next.

My system:
- Intel Dualcore 6300 processor
- 2 GB RAM
- Geforce 7600
- 350 Gb HD
- Ext3
- Kernel: 2.6.28-15-generic

Your best shot (and the only shot I know, I'm afraid) is to check the logs right after it crashes and you reboot. This can be done by going to System -> Administration -> Log File Viewer (or manually look up the messages in /var/log). I usually find all the stuff I need in 'messages' and 'kern.log'. If there's anything you need help with: post the relevant contents in a new thread (or this one) and there might be someone who can tell you what your problems are all about (note: the bottom x-hundred lines are messages telling stuff about the last time you rebooted. You're generally looking for messages just before it crashed and you rebooted, so scroll up a little from the bottom of the file) (they're timestamped, by the way, so that should help).

---

### Post by MKe2 on 2009-09-28
Thanks, did that after having a crash this morning. Unfortunately the logs don't seem to register a problem. The messages seem to shift from 7 minutes before the crash (my first boot) to exactly the reboot.
For instance the kern.log:
```
Sep 28 06:19:22 LP kernel: [   21.676907] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Sep 28 06:19:22 LP kernel: [   21.676911] Bluetooth: BNEP filters: protocol multicast
Sep 28 06:19:22 LP kernel: [   21.696863] Bridge firewalling registered
Sep 28 06:19:27 LP kernel: [   26.429872] r8169: eth0: link up
Sep 28 06:19:28 LP kernel: [   28.289616] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Sep 28 06:19:39 LP kernel: [   37.216355] eth0: no IPv6 routers present
Sep 28 06:31:05 LP kernel: Inspecting /boot/System.map-2.6.28-15-generic
Sep 28 06:31:05 LP kernel: Cannot find map file.
Sep 28 06:31:05 LP kernel: Loaded 74443 symbols from 49 modules.
Sep 28 06:31:05 LP kernel: [    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
Sep 28 06:31:05 LP kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep 28 06:31:05 LP kernel: [    0.000000] Initializing cgroup subsys cpu
Sep 28 06:31:05 LP kernel: [    0.000000] Linux version 2.6.28-15-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 (Ubuntu 2.6.28-15.49-generic)
Sep 28 06:31:05 LP kernel: [    0.000000] KERNEL supported cpus:
```

---

### Post by FunkyRes on 2009-09-28
Just found this thread but have had no problems.

64 bit jaunty
ext3 filesystem
nvidia GeForce 6800 using closed source driver

I did however turn off desktop effects. Do people still having issues have the desktop effects eye candy turned on? they made my system slower, so it wouldn't surprise me if they were to blame.

---

### Post by pveurshout on 2009-09-28
> **MKe2 said:**
> Thanks, did that after having a crash this morning. Unfortunately the logs don't seem to register a problem. The messages seem to shift from 7 minutes before the crash (my first boot) to exactly the reboot.
For instance the kern.log:
```
(...)
Sep 28 06:19:28 LP kernel: [   28.289616] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
(...)

```

If it's always this message that's last before a freeze, it *may* be related. Although a quick search revealed that it doesn't generally seem to be a problem for most users, I do remember having read about (and having experienced myself) Jaunty in some cases having trouble with handling interrupt requests or something. Unfortunately I don't know enough about that stuff to help any further, sorry for that. Only advice I could give is to try and figure out whether there's some kind of pattern (specific (type of) error message) that makes the system crash, though I guess that advice is not really of much added value to you..

---

### Post by leonbravo on 2009-09-28
In my case, the freezing comes every time I plug or unplug usb memories or other usb device, or after a clean start. 

I takes some (long) time after unfreeze alone. The quickest option is killing gnome-panel. Sometimes, using the console mode Ctrl +F1. Then, after few seconds all click mouse respond well. 

Some data from my system: Linux leon 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux. Dell xps m1330.


It's a really SHAME, I cannot presume on front of my friend of having a GOOD OS, because sometimes I have to use estrange commands to have the system running smoothly again.  How can I convince others to use this OS if I don't. 

I have been waiting for a couple of months for something that really solve this problem.

---

### Post by MKe2 on 2009-09-29
> **pveurshout said:**
> If it's always this message that's last before a freeze, it *may* be related. Although a quick search revealed that it doesn't generally seem to be a problem for most users, I do remember having read about (and having experienced myself) Jaunty in some cases having trouble with handling interrupt requests or something. Unfortunately I don't know enough about that stuff to help any further, sorry for that. Only advice I could give is to try and figure out whether there's some kind of pattern (specific (type of) error message) that makes the system crash, though I guess that advice is not really of much added value to you..
Hi,

It's always one of the last messages in every boot. Not only just before a crash. I've asked several people about this message before, but nobody could relate it to the crashes. Doesn't mean there's no relation of course.

---

### Post by dbutcher on 2009-09-29
> **MKe2 said:**
> Hi,

It's always one of the last messages in every boot. Not only just before a crash. I've asked several people about this message before, but nobody could relate it to the crashes. Doesn't mean there's no relation of course.

The hda-intel message in the logs is discussed a bit here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267913]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267913")
The fix suggested in post #20 of that bug-report worked for me (no more hda-intel messages in the logs) but didn't solve the random freezing/crashing problem.  Maybe you'll have better luck.

---

### Post by MKe2 on 2009-09-29
> **dbutcher said:**
> The hda-intel message in the logs is discussed a bit here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267913](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267913)
The fix suggested in post #20 of that bug-report worked for me (no more hda-intel messages in the logs) but didn't solve the random freezing/crashing problem.  Maybe you'll have better luck.
Hi, sorry no luck.
did that and my Ubuntu installation refused to boot. Had a similar crash while booting (flashing leds).
Had to delete the /etc/modprobe.d/alsa-base file by using the live-CD. :(

---

### Post by mister_playboy on 2009-09-29
I've had many problem with total lockups recently.  In my case, the processor is apparently running, but all disk activity ceases.  Mouse, keyboard, screen all freeze solid.

The logs don't seem to contain any good info (for my purposes, anyway)... there is just an abrupt end and that's it. :confused:

---

### Post by MKe2 on 2009-09-30
I seem to have good results using the older 2.6.28-11 kernel instead of 2.6.28-15. No crashes sofar, but maybe to early to claim it a victory.

---

### Post by dbutcher on 2009-09-30
> **MKe2 said:**
> I seem to have good results using the older 2.6.28-11 kernel instead of 2.6.28-15. No crashes sofar, but maybe to early to claim it a victory.

How long have you been running the older kernel?  
I tried that approach also (based on Mirge's comments above), but maximum uptime was still only a day or so (if I turned the computer on, but didn't start any applications.)  On the next reboot, I just went back to 2.6.28-15 without thinking about it.

---

### Post by MKe2 on 2009-10-01
> **dbutcher said:**
> How long have you been running the older kernel?  
I tried that approach also (based on Mirge's comments above), but maximum uptime was still only a day or so (if I turned the computer on, but didn't start any applications.)  On the next reboot, I just went back to 2.6.28-15 without thinking about it.

It's been 2 days now, so I'm not overly excited as yet. If it doesn't crash for a week I'll let you know :)

---

### Post by Inaia on 2009-10-02
> **codeseer said:**
> Are those of you who are experiencing freezes using either an Intel video chip  or the new Ext4 file system?

I have a variety of Intel hardware, but using pure ext3 due to bugs in ext4.

---

### Post by greenlake-walker on 2009-10-03
[SIZE=1]Acer Aspire X1300-U1801A Problem Solved!
Thanks guys, I installed the 64-bit version of Jaunty,
and now ALT-F2 doesn't hang the computer!

Next, I'll install Mint 7 if has a 64-bit version.
Mint 7 32-bit had the ALT-F2 hang also.

[/SIZE]

---

### Post by misfitpierce on 2009-10-03
I tested Jaunty (not karmic this time, didn't have time this time) but anyways... been testing since alpha's on ATI 200 in laptop and have had no issues with it running on the opensource most up to date driver which is relatively new... So i'm not sure exactly. Maybe try changing out the graphics drivers in your computers to or from opensource ones or to the newest prop ones from the makers site aka Nvidia/ATI.

---

### Post by Hated On Mostly on 2009-10-08
Have you guys with freezing checked out this thread?

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Solutions in there might help some of you.

---

### Post by MKe2 on 2009-10-09
Still had several freezes the last few day's, so I switched back to 8.04 Hardy. Hope the 9.10 version will solve the problems.

---

### Post by dbutcher on 2009-10-11
I have at least 4 problems, possibly related, possibly not.  In order of frequency of occurrence:
1. Computer freeze, no audio output, no response to Alt-SysRq-R-E-I-S-U-B, no entries in syslog or elsewhere.  Hard reboot required, complete mystery.
2. Computer freeze, Xorg consuming 100% resources, Alt-SysRq-R-E-I-S-U-B resets computer, no log entries.  Bug report filed for my hardware here [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/435011]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/435011") and similar one with different hardware here [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/434416]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/434416")
3. As #1, but with audio "hammering" sound.  Hard reboot required.
4. Computer freeze, log entries about CPU#1 being stuck, similar to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/254326]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/254326"), except I'm using Jaunty, not Intrepid.

My set-up: AMD64, Jaunty, Nvidia (180 driver), 2.6.28-15 kernel
I've tried reverting to older kernel (2.6.28-11), and also older nvidia driver (173).  There is no apparent improvement by changing set-up, but with so many different problems happening, it's hard to be sure what's going on.

---

### Post by kisconstr@absamail.co.za on 2009-10-14
Sorry this question may not be in the correct place, but I cant find where to start a new question on the home page.

2 days ago I did an automatic update of the Ubuntu 9.04 and my system now gets as far as the log in screen but the screen is messed up with lines and colors.

How do ZI rectify if I can get onto the system?

Kind REgards

Russ

---

### Post by TheHimself on 2009-10-14
I have Ubuntu Netbook remix on a Lenovo laptop and experience frequent freezes. I'm using ext3. I've included the part of log file for one of the freezes. It includes the messages from when I woke up the computer until I forced it shut down. The freeze happened at  13:12. Can this reveal the source of the problem? 

Oct 14 13:09:26 rez-laptop kernel: [ 6495.737452] PM: Syncing filesystems ... done.
Oct 14 13:09:27 rez-laptop kernel: [ 6495.755655] Freezing user space processes ... (elapsed 0.00 seconds) done.
Oct 14 13:09:27 rez-laptop kernel: [ 6495.757076] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Oct 14 13:09:27 rez-laptop kernel: [ 6495.757268] Suspending console(s) (use no_console_suspend to debug)
Oct 14 13:09:27 rez-laptop kernel: [ 6495.757907] pci 0000:00:02.0: PCI INT A disabled
Oct 14 13:09:27 rez-laptop kernel: [ 6496.345216] sd 2:0:0:0: [sda] Synchronizing SCSI cache
Oct 14 13:09:27 rez-laptop kernel: [ 6496.345505] sd 2:0:0:0: [sda] Stopping disk
Oct 14 13:09:27 rez-laptop kernel: [ 6496.896611] wl 0000:05:00.0: PCI INT A disabled
Oct 14 13:09:27 rez-laptop kernel: [ 6496.912743] ata_piix 0000:00:1f.2: PCI INT B disabled
Oct 14 13:09:27 rez-laptop kernel: [ 6496.928457] ata_piix 0000:00:1f.1: PCI INT B disabled
Oct 14 13:09:27 rez-laptop kernel: [ 6496.928613] ehci_hcd 0000:00:1d.7: PCI INT A disabled
Oct 14 13:09:27 rez-laptop kernel: [ 6496.944235] uhci_hcd 0000:00:1d.3: PCI INT D disabled
Oct 14 13:09:27 rez-laptop kernel: [ 6496.944296] uhci_hcd 0000:00:1d.2: PCI INT C disabled
Oct 14 13:09:27 rez-laptop kernel: [ 6496.944354] uhci_hcd 0000:00:1d.1: PCI INT B disabled
Oct 14 13:09:27 rez-laptop kernel: [ 6496.944411] uhci_hcd 0000:00:1d.0: PCI INT A disabled
Oct 14 13:09:27 rez-laptop kernel: [ 6496.960177] HDA Intel 0000:00:1b.0: PCI INT A disabled
Oct 14 13:09:27 rez-laptop kernel: [ 6496.976333] PM: suspend devices took 1.220 seconds
Oct 14 13:09:27 rez-laptop kernel: [ 6496.976393] ACPI: Preparing to enter system sleep state S3
Oct 14 13:09:27 rez-laptop kernel: [ 6497.011915] Disabling non-boot CPUs ...
Oct 14 13:09:27 rez-laptop kernel: [ 6497.116064] CPU 1 is now offline
Oct 14 13:09:27 rez-laptop kernel: [ 6497.116075] SMP alternatives: switching to UP code
Oct 14 13:09:27 rez-laptop kernel: [ 6497.438314] CPU1 is down
Oct 14 13:09:27 rez-laptop kernel: [ 6497.438419] Extended CMOS year: 2000
Oct 14 13:09:27 rez-laptop kernel: [ 6497.438419] Extended CMOS year: 2000
Oct 14 13:09:27 rez-laptop kernel: [ 6497.438419] Enabling non-boot CPUs ...
Oct 14 13:09:27 rez-laptop kernel: [ 6497.438419] SMP alternatives: switching to SMP code
Oct 14 13:09:27 rez-laptop kernel: [ 6497.756877] Booting processor 1 APIC 0x1 ip 0x6000
Oct 14 13:09:27 rez-laptop kernel: [ 6497.437155] Initializing CPU#1
Oct 14 13:09:27 rez-laptop kernel: [ 6497.437155] Calibrating delay using timer specific routine.. 3192.02 BogoMIPS (lpj=6384046)
Oct 14 13:09:27 rez-laptop kernel: [ 6497.437155] CPU: L1 I cache: 32K, L1 D cache: 24K
Oct 14 13:09:27 rez-laptop kernel: [ 6497.437155] CPU: L2 cache: 512K
Oct 14 13:09:27 rez-laptop kernel: [ 6497.437155] CPU: Physical Processor ID: 0
Oct 14 13:09:27 rez-laptop kernel: [ 6497.437155] CPU: Processor Core ID: 0
Oct 14 13:09:27 rez-laptop kernel: [ 6497.844282] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
Oct 14 13:09:27 rez-laptop kernel: [ 6497.857038] CPU1 is up
Oct 14 13:09:27 rez-laptop kernel: [ 6497.857043] ACPI: Waking up from system sleep state S3
Oct 14 13:09:27 rez-laptop kernel: [ 6498.172291] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Oct 14 13:09:27 rez-laptop kernel: [ 6498.172819] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Oct 14 13:09:27 rez-laptop kernel: [ 6498.172891] usb usb2: root hub lost power or was reset
Oct 14 13:09:27 rez-laptop kernel: [ 6498.172916] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Oct 14 13:09:27 rez-laptop kernel: [ 6498.172984] usb usb3: root hub lost power or was reset
Oct 14 13:09:27 rez-laptop kernel: [ 6498.173008] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Oct 14 13:09:27 rez-laptop kernel: [ 6498.173118] usb usb4: root hub lost power or was reset
Oct 14 13:09:27 rez-laptop kernel: [ 6498.173145] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
Oct 14 13:09:27 rez-laptop kernel: [ 6498.173213] usb usb5: root hub lost power or was reset
Oct 14 13:09:27 rez-laptop kernel: [ 6498.188161] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Oct 14 13:09:27 rez-laptop kernel: [ 6498.188510] ata_piix 0000:00:1f.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Oct 14 13:09:27 rez-laptop kernel: [ 6498.204254] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Oct 14 13:09:27 rez-laptop kernel: [ 6498.220611] wl 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Oct 14 13:09:27 rez-laptop kernel: [ 6498.220838] sd 2:0:0:0: [sda] Starting disk
Oct 14 13:09:27 rez-laptop kernel: [ 6499.401067] ata3.00: configured for UDMA/133
Oct 14 13:09:27 rez-laptop kernel: [ 6499.421476] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
Oct 14 13:09:27 rez-laptop kernel: [ 6499.421583] sd 2:0:0:0: [sda] Write Protect is off
Oct 14 13:09:27 rez-laptop kernel: [ 6499.421725] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 14 13:09:27 rez-laptop kernel: [ 6499.688187] usb 1-3: reset high speed USB device using ehci_hcd and address 2
Oct 14 13:09:27 rez-laptop kernel: [ 6500.076139] usb 1-5: reset high speed USB device using ehci_hcd and address 3
Oct 14 13:09:27 rez-laptop kernel: [ 6500.232169] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Oct 14 13:09:27 rez-laptop kernel: [ 6500.233534] PM: resume devices took 2.340 seconds
Oct 14 13:09:27 rez-laptop kernel: [ 6500.233603] Restarting tasks ... <6>synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
Oct 14 13:09:27 rez-laptop kernel: [ 6500.398417] done.
Oct 14 13:09:27 rez-laptop kernel: [ 6500.941067] ACPI: EC: missing confirmations, switch off interrupt mode.
Oct 14 13:09:28 rez-laptop kernel: [ 6501.316842] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 14 13:09:29 rez-laptop kernel: [ 6502.969836] tg3: eth0: Link is up at 100 Mbps, full duplex.
Oct 14 13:09:29 rez-laptop kernel: [ 6502.969846] tg3: eth0: Flow control is on for TX and on for RX.
Oct 14 13:09:29 rez-laptop kernel: [ 6502.978738] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 14 13:13:50 rez-laptop kernel: [ 6763.292134] CE: hpet increasing min_delta_ns to 22500 nsec
Oct 14 13:14:16 rez-laptop kernel: [ 6789.538913] tg3: eth0: Link is down.
Oct 14 13:14:31 rez-laptop kernel: [ 6804.344625] usb 1-3: USB disconnect, address 2
Oct 14 13:14:40 rez-laptop kernel: [ 6813.300186] usb 1-3: new high speed USB device using ehci_hcd and address 4
Oct 14 13:14:40 rez-laptop kernel: [ 6813.615937] usb 1-3: configuration #1 chosen from 1 choice
Oct 14 13:14:40 rez-laptop kernel: [ 6813.617790] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (5986:0241)
Oct 14 13:14:40 rez-laptop kernel: [ 6813.619364] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/input/input10
Oct 14 13:15:28 rez-laptop kernel: [ 6861.556754] tg3: eth0: Link is up at 100 Mbps, full duplex.
Oct 14 13:15:28 rez-laptop kernel: [ 6861.556767] tg3: eth0: Flow control is on for TX and on for RX.
Oct 14 13:21:08 rez-laptop syslogd 1.5.0#5ubuntu3: restart.

---

### Post by Wazzag on 2009-10-16
I have stumbled on a fix for my system freezing

When it freezes I plug a USB device in (bluetooth or just a drive) and presto! back to normal

I have been searching for a fix for this for a long while and have tried a few of the magic fixes to no avail, Jaunty still freezes randomly but at least now I can 'un-freeze' it without a re-boot

---

### Post by pveurshout on 2009-10-17
> **Wazzag said:**
> I have stumbled on a fix for my system freezing

When it freezes I plug a USB device in (bluetooth or just a drive) and presto! back to normal

I have been searching for a fix for this for a long while and have tried a few of the magic fixes to no avail, Jaunty still freezes randomly but at least now I can 'un-freeze' it without a re-boot

Extraordinary problems require uncommon solutions, I guess ;) I'm gonna remember that one, thanks. My system hasn't frozen since I disabled hpet in the boot options, though, so I hope it won't be necessary.

---

### Post by Wazzag on 2009-10-18
> **pveurshout said:**
> Extraordinary problems require uncommon solutions, I guess ;) I'm gonna remember that one, thanks.

Hehe
yeah it's extraordinary alright

I tried it out of pure frustration, no keyboard, no mouse, so I thought I'd just plug something in to see what happened
And it worked!!!!

I get a freeze on average about once a week I guess, I might go a couple of weeks then get frozen twice in a day (sometimes), sometimes it fixes itself if I just leave it alone for 5-10 minutes, other times it just stays frozen, I did leave it one evening, it was frozen for about four hours before I went to bed, the next day it was fine (fixed itself)

So my brain figured the thing just needed a poke, can't poke it with the keyboard, can't poke it with the mouse, what else is there.......USB!!!

And it worked!

I have frozen about six times since then, every time plugging something into USB has kicked it into gear

I know it's not a proper fix, but it has worked every time (so far)

---

### Post by billharris on 2009-10-22
Just an update: I've tried disabling hpet and switching to the 2.6.31 kernel on Jaunty, but I still get freezes multiple times a day.  I tried the USB idea, and it did not help me.  (I do sometimes see that I can provoke a seemingly frozen Jaunty by right-clicking on Firefox in the bottom panel, and that lets me do a little bit until it freezes again; the second time almost always requires a reboot.  Perhaps the USB trick is in the same category.)

Has anyone got any multi-day experience with Karmic who has experienced the freezing problem with Jaunty?  I grabbed a daily build of the beta last week, and it seemed to work okay as a Live CD, but I only ran it for a short while.  I'm hopeful that the released Karmic will fix the freezes.  If it doesn't, I'll probably switch back to Debian.

---

### Post by Dougga on 2009-10-22
I'm seeing the same thing.

Ubuntu 9.04 fully patched
Linux tc 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/

I get perpetual freezes which is driving me nuts.  I'm too busy to spend too much time on this, I'll be moving off 9.04 to the 8.04 LTS and Win9 if that fails.

From my experience the freezes come from two different sources.
1. The Alt-Tab application switcher
2. Evolution

In the #1 case where I suspect Alt-Tab as the culprit, the UI locks up completely with no mouse movement.  I can access the machine using ssh from another machine and force a reboot.  Requesting a restart to GDM has no effect.

In case #2 which I suspect Evolution problem, the mouse appears to move across the screen but cannot interact with anything shown on the screen.  I've had some success killing the evolution task from a terminal session - but only occasionally does this work.

I'll have to add that 9.04 is not ready for prime time (for professionals who value their time) and the suggestion of launching a new version suggests that these releases are essentially only betas and will not be much more unless something significant changes in the release or testing model.  I have no real experience with LTS so I'll be looking to this next to evaluate.  I may have a look at Suse as well. Their's is a business model that is based on enterprise productivity.

Thanks for everyones input.

~Doug

---

### Post by Hated On Mostly on 2009-10-22
> **Dougga said:**
> I'm seeing the same thing.

Ubuntu 9.04 fully patched
Linux tc 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/

I get perpetual freezes which is driving me nuts.  I'm too busy to spend too much time on this, I'll be moving off 9.04 to the 8.04 LTS and Win9 if that fails.

From my experience the freezes come from two different sources.
1. The Alt-Tab application switcher
2. Evolution

In the #1 case where I suspect Alt-Tab as the culprit, the UI locks up completely with no mouse movement.  I can access the machine using ssh from another machine and force a reboot.  Requesting a restart to GDM has no effect.

In case #2 which I suspect Evolution problem, the mouse appears to move across the screen but cannot interact with anything shown on the screen.  I've had some success killing the evolution task from a terminal session - but only occasionally does this work.

I'll have to add that 9.04 is not ready for prime time (for professionals who value their time) and the suggestion of launching a new version suggests that these releases are essentially only betas and will not be much more unless something significant changes in the release or testing model.  I have no real experience with LTS so I'll be looking to this next to evaluate.  I may have a look at Suse as well. Their's is a business model that is based on enterprise productivity.

Thanks for everyones input.

~Doug


openSUSE is a good choice. I tested both of them out very recently as well as Fedora due to Jaunty's instability. They don't exhibit the same problems that Ubuntu does and are much more stable. Their alpha, beta, and release candidates are much more stable than Ubuntu's as well.

The next version of openSUSE (11.2) will be released November 12, 2009. The next version of Fedora (12) will be released November 17, 2009. I would go with openSUSE over Fedora as it is easier to use.

Ubuntu has very unique bugs that other Linux distributions don't have. I am going to give the official Karmic Koala a try, but if I have problems I am switching permanently. I want a stable machine, not a machine that I am constantly looking up how to workaround bugs for it.

---

### Post by Dougga on 2009-10-22
Excellent post.  thanks

I believe I'll follow the identical path to system and emotional stability.  I'm looking forward to the extra time in my days.

Looking into this specific bug I found evidence that it existed when Jaunty was originally launched back in '07.

Here is an excerpt from the release notes under "known Issues" [one of my favorite terms in systems parlance].

[QUOTE]
Display freezes with Intel graphics cards

Users of various Intel video chipsets reported freezes under various conditions (e. g. a few minutes after suspend on the i945, see 339091). In many cases, switching off desktop effects in System &#8594; Preferences &#8594; Appearance was reported to help.

If it still happens without desktop effects, you can add Option "DRI" "off" to the Device section of /etc/X11/xorg.conf, as described above. This will disable 3D acceleration and desktop effects, but makes suspend work reliably again and also avoid many types of crashes.

These freezes happen particularly often on the i965 chips (359392). For that reason, desktop effects were disabled by default on this chipset in the final release. They will be re-enabled in a 9.04 Update once the problem has been fixed. 
[QUOTE]

More hints to things I can disable or remove to get my machines to work as designed.

Here are the details of my graphics subsystems:

00:00.0 Host bridge: Intel Corporation 82G35 Express DRAM Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 8295
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 8276
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 2299
	Region 0: Memory at fdd00000 (32-bit, non-prefetchable) [size=1M]
	Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at cc00 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
		Address: fee0300c  Data: 41a1
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:02.1 Display controller: Intel Corporation 82G35 Express Integrated Graphics Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 8276
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at fde00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

---

### Post by Hated On Mostly on 2009-10-22
> **Dougga said:**
> Excellent post.  thanks

I believe I'll follow the identical path to system and emotional stability.  I'm looking forward to the extra time in my days.

Looking into this specific bug I found evidence that it existed when Jaunty was originally launched back in '07.

There is nothing wrong with wanting a stable system that you don't have to fight with even if you are more than capable of doing so. I use my computer to get work done and have fun, not to fix problems with the system itself. Not to mention, most of these critical bugs on Ubuntu have no workarounds as this thread demonstrates!

---

### Post by MKe2 on 2009-10-23
I must say 8.04 is rock-stable. Since I installed it I haven't had anything remotely to a crash.

---

### Post by Dougga on 2009-10-23
I just attempted the OpenSuse-x64 DVD... installation started stuck with a black screen.  Not a good omen.

---

### Post by Dougga on 2009-10-23
> **Hated On Mostly said:**
> openSUSE is a good choice. I tested both of them out very recently 

I tried OpenSuse 11.1 32 & 64 bit. Both installations fail to load.
- Memory tests check out fine.
- The system tests ok for memory and other functions so I don't think it's hardware faults.

I may be stuck with Windows.  Win9 came out yesterday, perhaps I have no other option.

---

### Post by georgelenzer on 2009-10-23
Just curious because I discovered something on a new laptop.  Is your DVD drive SATA or IDE?  My new laptop has a SATA DVD drive and many installers and live CDs fail on it.  I still haven't figured out if there is a workaround for SATA DVD drive installations, but the usual symptoms are that the system will boot most of the way off the DVD and then hang either after the kernel hands off to init, or later when squashfs is being opened from the disk.

> **Dougga said:**
> I tried OpenSuse 11.1 32 & 64 bit. Both installations fail to load.
- Memory tests check out fine.
- The system tests ok for memory and other functions so I don't think it's hardware faults.

I may be stuck with Windows.  Win9 came out yesterday, perhaps I have no other option.

---

### Post by dbutcher on 2009-10-24
> **billharris said:**
> Just an update: I've tried disabling hpet and switching to the 2.6.31 kernel on Jaunty, but I still get freezes multiple times a day.  I tried the USB idea, and it did not help me.  (I do sometimes see that I can provoke a seemingly frozen Jaunty by right-clicking on Firefox in the bottom panel, and that lets me do a little bit until it freezes again; the second time almost always requires a reboot.  Perhaps the USB trick is in the same category.)

Has anyone got any multi-day experience with Karmic who has experienced the freezing problem with Jaunty?  I grabbed a daily build of the beta last week, and it seemed to work okay as a Live CD, but I only ran it for a short while.  I'm hopeful that the released Karmic will fix the freezes.  If it doesn't, I'll probably switch back to Debian.

I upgraded to Karmic-RC overnight, but had an Xorg = 100% CPU failure after less than 3 hours uptime.  I know it's not official Karmic yet, but initial indications do not inspire.

---

### Post by Irishpolyglot on 2009-10-24
What a frustrating 6 months!!
My question to anyone on 9.10 RC is... has this issue been resolved?? i.e. for those whose comp kept freezing in 9.04.
The above-mentioned USB drive trick doesn't work for me. I'm hoping that an upgrade to 9.10 next week will solve the issue, but I haven't come across any discussions about it (scrolled through several pages of this thread since I last posted and didn't see anything; might have missed it).
Thanks for any thoughts on it!!

---

### Post by billharris on 2009-10-24
dbutcher, Irishpolyglot, thanks for the updates, and keep them coming.  The primary reason I use *nux is that it's rock solid.  Second is that it's relatively lean, fast, and low memory.  Third is that it's FLOSS.  This has been a frustrating six months with far too much wasted time (on the same order of magnitude of wasted time that I've experienced on Windows).  

I'm looking forward either to Karmic or to Debian unstable in the next week or two.

---

### Post by pveurshout on 2009-10-26
> **Irishpolyglot said:**
> What a frustrating 6 months!!
My question to anyone on 9.10 RC is... has this issue been resolved?? i.e. for those whose comp kept freezing in 9.04.
The above-mentioned USB drive trick doesn't work for me. I'm hoping that an upgrade to 9.10 next week will solve the issue, but I haven't come across any discussions about it (scrolled through several pages of this thread since I last posted and didn't see anything; might have missed it).
Thanks for any thoughts on it!!

I'm REALLY curious about this as well. Anybody got any experiences yet? :)

(BTW: after having gone for over a month without any freezes my Jaunty just froze on me again without any specific reason. It had just finished downloading four large, 2.1 GB files using Deluge and seemed to be nicely seeding them, but a couple minutes later it just froze when I tried to navigate to a simple webpage (which I visit almost daily) using Firefox..:cry:)

edit:

> **Dougga said:**
> I'm seeing the same thing.

Ubuntu 9.04 fully patched
Linux tc 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/

I get perpetual freezes which is driving me nuts.  I'm too busy to spend too much time on this, I'll be moving off 9.04 to the 8.04 LTS and Win9 if that fails.

From my experience the freezes come from two different sources.
1. The Alt-Tab application switcher
2. Evolution

In the #1 case where I suspect Alt-Tab as the culprit, the UI locks up completely with no mouse movement.  I can access the machine using ssh from another machine and force a reboot.  Requesting a restart to GDM has no effect.

In case #2 which I suspect Evolution problem, the mouse appears to move across the screen but cannot interact with anything shown on the screen.  I've had some success killing the evolution task from a terminal session - but only occasionally does this work.

I'll have to add that 9.04 is not ready for prime time (for professionals who value their time) and the suggestion of launching a new version suggests that these releases are essentially only betas and will not be much more unless something significant changes in the release or testing model.  I have no real experience with LTS so I'll be looking to this next to evaluate.  I may have a look at Suse as well. Their's is a business model that is based on enterprise productivity.

Thanks for everyones input.

~Doug

Did you see the same kind of behavior when using the 2.6.28-15 kernel? I upgraded to 2.6.28-16 this weekend and got two freezes today, after having used the previous kernel without any problems (I think..not sure when that one came out..at least it ran fine for over a month after I had trouble using -11, -13 and -14). It's either that or the handling of large files. I'm using 2.6.28-15 now and I'm gonna try copying a large file over my home network again (which resulted in a freeze when it was about halfway through the last time on 2.6.28-16). **Update:** Yeah, using 2.6.28-15 it seems to be fine..

---

### Post by dspisak on 2009-10-27
With 8.10 I had no problems for many months.  I then upgrade to 9.04 by using Update Manager plus the suggested upgrades.  That is when my problems started.  No matter which kernel or xserver-xorg-etc. I tried nothing worked.

Next I created a partition on the HDD and did a clean install of Linux Mint Gloria x64 which is based on 9.04.  It was at least as easy to install as ubuntu.  It has worked without a hitch.  What's better is that Flash and java were already added to Firefox.

While reading the Mint installation guide I noticed the statement to the effect of "don't upgrade the kernel for a particular installation".  I have heeded this admonishment have not upgraded the kernel.  As I said Mint has worked without a hitch.

I then decided to give ubuntu one last try.  I downloaded the 9.04 x64 iso file.  However, before loading ubuntu I used the Gparted disk to reformat the old ubuntu partition.  I then did a clean install and so far all is well.  I did apply all of the recommended upgrades EXCEPT for the kernel and related upgeades.  So far, ubuntu 9.04 has worked without a hitch.

From my perspective the solution is: a clean install on a freshly formatted partition and DO NOT upgrade the kernel.

I hope this works for you as well.

PS As you know 9.04 used kernel 2.6.28-11.  Mint Gloria also uses 2.6.28-11.

---

### Post by pveurshout on 2009-10-28
> **dspisak said:**
> With 8.10 I had no problems for many months.  I then upgrade to 9.04 by using Update Manager plus the suggested upgrades.  That is when my problems started.  No matter which kernel or xserver-xorg-etc. I tried nothing worked.

Next I created a partition on the HDD and did a clean install of Linux Mint Gloria x64 which is based on 9.04.  It was at least as easy to install as ubuntu.  It has worked without a hitch.  What's better is that Flash and java were already added to Firefox.

While reading the Mint installation guide I noticed the statement to the effect of "don't upgrade the kernel for a particular installation".  I have heeded this admonishment have not upgraded the kernel.  As I said Mint has worked without a hitch.

I then decided to give ubuntu one last try.  I downloaded the 9.04 x64 iso file.  However, before loading ubuntu I used the Gparted disk to reformat the old ubuntu partition.  I then did a clean install and so far all is well.  I did apply all of the recommended upgrades EXCEPT for the kernel and related upgeades.  So far, ubuntu 9.04 has worked without a hitch.

From my perspective the solution is: a clean install on a freshly formatted partition and DO NOT upgrade the kernel.

I hope this works for you as well.

PS As you know 9.04 used kernel 2.6.28-11.  Mint Gloria also uses 2.6.28-11.

Highly interesting finding which may apply in my case as well. Although I never really used the 2.6.28-11 kernel (the day I installed Jaunty it already updated to 2.6.28-13) I have found that, in my case, the 2.6.28-15 kernel works fine, whereas 2.6.28-13, -14 and -16 ALL result in regular freezes occurring. I'm gonna remember your advice for Karmic: as soon as I get a working kernel I'll stop updating it :)

---

### Post by gizmobay on 2009-10-28
Ever since I updated the kernel to 2.6.28-15, I haven't had one freeze. I saw 28-16 came out but I did not dare try this one.

---

### Post by joeray on 2009-10-30
I am having the same problem with the display freeze. I thought it was a problem with my intel 945 chipset like in 9.04. My problem started in the beta live cd freezing up making installation unlikely. I tried a wubi install with yesterday's final release with a successful installation. Opening up the desktop I had a freeze-up after about 20 seconds. I'm stuck at this point like everyone else. Best to all.

---

### Post by billharris on 2009-10-30
I'm running 2.6.31.  What are the risks in moving back to 2.6.28-15 or 2.6.28-11?  I am using the NVIDIA modules, so I suspect that could be a challenge.  Is that true?  Is there anything else?

If that would work without a lot of effort, I might try it.  I'm reluctant to keep searching for the latest and greatest; if that doesn't sound promising and if Karmic doesn't have stellar reviews in this regard, I might install the Debian unstable I downloaded.

---

### Post by billharris on 2009-10-31
Nevermind; I've now frozen with both of those kernels.

---

### Post by agniruc on 2009-10-31
KARMIC solved the issue for me.

Hello, I installed 9.10 yesterday and everything worked fine, without any freeze so far.

---

### Post by Irishpolyglot on 2009-10-31
I've been using Karmic non stop for a day and left it on overnight. So far no freezes - I won't start celebrating until it has survived a few days though (I had had several days with no freezes in Jaunty). Nevertheless, I'm confident that we can put the last 6 months behind us and enjoy a fully operational distro once more :)

---

### Post by dbutcher on 2009-10-31
I've been running Karmic for a week now since I upgraded from Jaunty.  It's definitely *not* an improvement for me.  I haven't had an uptime longer than 5 hours.

Just to be clear in my own mind as to what my next steps should be, are the "success" experiences based on a clean install or an upgrade from jaunty?

---

### Post by dbutcher on 2009-10-31
For those NVidia users out there, I've just stumbled across this older posting which seems like it may still be relevant in my case.  Too early to say whether this will solve my problems, but I thought I would share here anyway.

[http://www.nvnews.net/vbulletin/showthread.php?t=58498]("http://www.nvnews.net/vbulletin/showthread.php?t=58498")

I'll post again once I know results.

---

### Post by Irishpolyglot on 2009-10-31
Mine was just an upgrade from Jaunty. It's disappointing to hear that the new distro hasn't solved this issue for everyone and I really hope that it isn't general. I will update after a week if I have no freezes at all, or as soon as it does freeze otherwise. So far so good... fingers crossed!
If you've been on it a week already, I presume you mean the RC. Have you upgraded to the final release? Not sure if it makes any difference.

---

### Post by dbutcher on 2009-10-31
> **Irishpolyglot said:**
> Mine was just an upgrade from Jaunty. It's disappointing to hear that the new distro hasn't solved this issue for everyone and I really hope that it isn't general. I will update after a week if I have no freezes at all, or as soon as it does freeze otherwise. So far so good... fingers crossed!
If you've been on it a week already, I presume you mean the RC. Have you upgraded to the final release? Not sure if it makes any difference.

Yes, I upgraded to the RC last weekend hoping to find some improvement.  And I have upgraded since, so I'm completely up-to-date with Karmic.  

The official nvidia driver for Karmic is 185 (which I have), but I notice here [http://www.nvnews.net/vbulletin/showthread.php?t=140136]("http://www.nvnews.net/vbulletin/showthread.php?t=140136") that the latest 190 driver fixes "a randomly occuring X server crash".  Obviously I'm pretty intrigued by that.

Meanwhile, "disappointing" is a good word for it...

---

### Post by pveurshout on 2009-10-31
> **dbutcher said:**
> I've been running Karmic for a week now since I upgraded from Jaunty.  It's definitely *not* an improvement for me.  I haven't had an uptime longer than 5 hours.

Just to be clear in my own mind as to what my next steps should be, are the "success" experiences based on a clean install or an upgrade from jaunty?

From what I've heard there are many problems with the upgrade, whereas the clean install should be fine. I haven't tried it myself yet, though, and neither have I found any other experiences from users who had Jaunty randomly freeze on them all the time.

---

### Post by ProphetOfDoom on 2009-11-03
I upgraded (ie not a clean install) to Karmic last week hoping to escape the dreaded system freeze in Jaunty. Thought all was well until this morning. Just froze on me again so seems Karmic inherits this problem. :(

---

### Post by pveurshout on 2009-11-03
> **ProphetOfDoom said:**
> I upgraded (ie not a clean install) to Karmic last week hoping to escape the dreaded system freeze in Jaunty. Thought all was well until this morning. Just froze on me again so seems Karmic inherits this problem. :(

Please tell me you're kidding.. :cry:

---

### Post by Dougga on 2009-11-03
Yes I went through hell to upgrade and finally have a Karmic installation that claims to be fully updated... I'm seeing fatal freezes at least once a day.

From the logs:

yelp[2728] segfault at 0 ip <large number> sp <large number> error 4 in librarian.so.0.0.0 [large number]

gnome_screensav[5262] segfault at 0 ip <large number> sp <large number> error 4 in libGL.so.185.36

gnometris[<no.>]...segfault... error 4 in libGL.so.185.18.36


This distribution appears to be a real mess with a lack of discipline and quality control on the part of management.

---

### Post by Dougga on 2009-11-03
I have a SATA DVD drive.  This is an interesting theory but a major problem in that SATA seems to be the big kahuna in disk periperhals these days.  I have a USB/external around here.  I might give that a try.

---

### Post by wea3el on 2009-11-04
> **ProphetOfDoom said:**
> I upgraded (ie not a clean install) to Karmic last week hoping to escape the dreaded system freeze in Jaunty. Thought all was well until this morning. Just froze on me again so seems Karmic inherits this problem. :(

I did a fresh install cause upgrade didn't work well for me. No problems at all with freeze on Kubuntu Karmic. Maybe you should try clean install.

---

### Post by pveurshout on 2009-11-04
> **wea3el said:**
> I did a fresh install cause upgrade didn't work well for me. No problems at all with freeze on Kubuntu Karmic. Maybe you should try clean install.

Second that. The upgrade also causes problems with people who had no freezes in Jaunty, whereas all clean installs seem to work fine in those cases. I'm excited to hear your findings! :)

---

### Post by wea3el on 2009-11-04
> **pveurshout said:**
> Second that. The upgrade also causes problems with people who had no freezes in Jaunty, whereas all clean installs seem to work fine in those cases. I'm excited to hear your findings! :)


For me personally this is the best Kubuntu ever!  O:)

Everything works after clean install. Desktop effects are very fast on my weak laptop. It's very stable. Many programs that were problematic in 9.04 now seems very "finished". Power up and shut down are very fast 50/9 sec.

---

### Post by dbutcher on 2009-11-04
> **wea3el said:**
> I did a fresh install cause upgrade didn't work well for me. No problems at all with freeze on Kubuntu Karmic. Maybe you should try clean install.

Guys, I'm excited to hear the good news.  
However, after experiencing many "fixes" myself that turned out to be short-lived, I don't want to start the victory parade too early.  What kind of uptime are we seeing with a fresh install?

Please forgive me if my question seems negative.  I'm just looking for the end ...

---

### Post by wea3el on 2009-11-05
> **dbutcher said:**
> Guys, I'm excited to hear the good news.  
However, after experiencing many "fixes" myself that turned out to be short-lived, I don't want to start the victory parade too early.  What kind of uptime are we seeing with a fresh install?

Please forgive me if my question seems negative.  I'm just looking for the end ...

I've installed Karmic as soon as it became available and had no freezes since then.
For the uptime: I never had it turned on for more than 30 hours but no freezes.
I'll test the uptime soon and be back with statistic.

edit:

Turned the computer today; 5.November around 11:30 AM and will keep you inform in next posts...

---

### Post by Irishpolyglot on 2009-11-05
I have followed this thread since I installed 9.04, and as I said about a week ago, I would update my status for those curious.
I have had NO FREEZES at all! (After 6 months of consistent infuriating freezes) I installed 9.10 on Saturday and the computer was on for over 4 days without hibernation or restarts. I can leave it on at night to upload/download without coming back to the flashing capslock of doom! :D :D
I believe the problem has indeed been solved for me. For those who aren't as lucky, check out the [new nvida driver]("http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html") (I haven't installed it yet).
On the other hand I am having a completely different issue with my [screen being completely off for reboot]("http://ubuntuforums.org/showthread.php?t=1315243") (rebooted the first time yesterday). Not sure if it's related or not, or if using the latest nvidia drivers will help. But at least it's not freezing; that was infinitely more annoying :)

---

### Post by MKe2 on 2009-11-05
Upgraded to Karmic final last friday, haven't had a crash since (had 2 crashes every day on Jaunty), so Karmic seems to be the sollution. I suspect it's the NVidia bug with 2.6 kernels that was the problem on my machine but I won't investigate any more and just continue with Karmic

---

### Post by wea3el on 2009-11-08
Today I had to shut down my computer but not because of the freeze ;)

So, my computer was on for 3 days and nights and no troubles at all...

I think that Karmic solved freeze we had in Jaunty :D

---

### Post by pveurshout on 2009-11-10
Congratulations to all of you who saw their problems melt away because of Karmic! :D

I'm looking forward to installing it myself, after all these positive experiences.

---

### Post by dbutcher on 2009-11-15
So, am I the only one still with problems?

In frustration, I went all the way back to Hardy 8.04.  Same Xorg lockup with 100% CPU.  So it's not jaunty/karmic/whatever after all, at least for me.

If anybody else is still struggling, I found this today:  [http://magazine.redhat.com/2007/11/20/tips-and-tricks-why-does-xorgs-cpu-usage-shoot-up-when-using-nvidias-driver/](http://magazine.redhat.com/2007/11/20/tips-and-tricks-why-does-xorgs-cpu-usage-shoot-up-when-using-nvidias-driver/)

I just added this option now, so it's too early to say if it helps.  I'll report back if/when I find anything conclusive.

---

### Post by dbutcher on 2009-11-17
well, 2 days later and I'm still alive.  Yippee!

As I reported in the previous post (see link there), I had to add
   Option	   "UseEvents" "true"
to the "Device" section of xorg.conf

An outsider might not understand what the big deal about 2 days of uptime is, but I know you guys get it.  May we all meet again under happier circumstances.

Cheers,
Dave

---

### Post by bwdease on 2009-11-17
OK!  I have had this "freeze" problem for about 2 weeks now.  I upgraded from 9.04 to 9.10 Ubuntu.  It did not have a specific pattern, but I noticed that it was mostly while on Firefox.  It did the freeze with other programs as well:  The keyboard froze;  the x server froze; but the mouse was still able to be moved.  

     I will try this addition, Option "UseEvents" "true", to the .xorg file.
I will report back if this fixed it for me.  

Dell-2400
1gb ram
Ubuntu 9.10
inter-grated graphics card

---

### Post by dbutcher on 2009-11-17
bwdease,
good luck with your issue.  I should have perhaps been more clear - I'm using an nvidia graphics card.  I'm not sure if the solution I posted will apply in your case.
Cheers,
Dave

---

### Post by rori on 2009-11-29
Hello,

after having big issues on my Dell XPSM1330 (A14 BIOS) with NVIDIA 8400M GS under 8.04.3, 9.04 and also 9.10 I found a solution that worked for me:

Under Karmic I updated to the latest NVIDIA driver 190.42:
[http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)

Then I followed the instructions here:
[http://www.nvnews.net/vbulletin/showthread.php?t=58498](http://www.nvnews.net/vbulletin/showthread.php?t=58498)

and changed my grub to
```

linux   /boot/vmlinuz-2.6.31-15-generic root=UUID=[yourhardriveUUIDhere] ro   quiet splash pci=nommconf idle=poll clocksource=hpet

```

Seems to run stable now.

Maybe this helps others.

Regards

---

### Post by billharris on 2009-11-29
I just upgraded to Karmic last night, and it froze within 2-3 hours. :-(.  I, too, noticed that FF use seemed related somehow, but I don't know what yet.  Oh, and, when it's frozen, xwininfo can't grab the mouse.

I'm trying a fresh Karmic install soon, followed by reloading the packages I want.  I'm hopeful that works; sid is likely the next step.  I do appreciate everyone's suggestions for things to try (this NVIDIA driver, that whatever), but I've spent _far_ too much time over the last 6 months; I need to get real work done now.  I'm hopeful it works; I like Ubuntu quite a bit as long as it's rock-solid stable.

---

### Post by SR_ELPIRATA on 2009-12-07
Good to know Im not the only one. Im experiencing lock-ups mostly when Rhythmbox gets into trouble, all areas become unresponsive and I can't even do the Control+Alt+Backspace that I used in 8.10 if I had problems like this.

This and the nightmare that now is configuring the network..... but unlike the many of you... 9.10 gives me huge sound problems and since this is my HTPC system... sound is the most important thing I need, so I'll have to live with the freezes or return to 8.10, which to me is still the best.

ELP

---

### Post by Caraibes on 2009-12-07
No more freeze since upgrading to 9.10... I actually also apt-get installed xubuntu-desktop... I am enjoying it...
No problem with sound, except that it is mute by default when the PC just boot. Don't know why ???
I am using Exaile for my music needs, as I too was disappointed by the evolution of Rhythmbox, who used to be my music player of choice in the past...
Exaile is ok...
I am a bit in nostalgic mood these days, as I made Xfce with a single panel, and a win2k look... Plain blue background... I guess I'll change over time...
But, no... no more freeze...

---

### Post by dspisak on 2009-12-08
Hello.  I feel I should add my experiences with 64-bit ubuntu.

Initially I used 8.10.  It was a clean install after I redid my partitions with GParted.  It worked without any problems.  After a while I upgraded to 9.04 through the Upgrade Manager.  This worked for several weeks then the freezes started.  I tried different kernels, different xserver-xorg versions, ATI's FGLX.  Nothing worked, always freezes.  I then used GParted live to reformat the ubuntu partition and install 9.04 from the CD.  Success!  No freezes, no problems.  Later, Upgrade Manager suggested that I update the kernel which I did.  The freezes returned.  I again used GParted to reformat the partition and reinstalled 9.04 with the CD.  Again, no problems.  Since then, I did not upgrade any file that started with "linux".

Next I tried to upgrade to 9.10.  I used GParted to format a partition and tried to install 9.10 from the CD.  9.10 froze even during installation.  After thinking about the situation I went to the ASUS website and discovered that there were several bios upgrades since I purchased the motherboard.  I then installed the latest bios, reformatted the partition, and reinstalled 9.10 from the CD.  Success!  No freezes, no problems.  Even citrix version 11 runs perfectly.  I have been using 9.10 for several weeks without any problems.  Citrix runs without dropping me from my company's remote desktop, streaming audio and video work, 64-bit 9.10 appears to run smoother than the version of Windows 7 RC 64-bit that I was using.

Moral of the story:
- Make sure your MB has the latest bios,
- format the partition before installing ubuntu,
- install from the CD (also format the partition again),
- do not upgrade the kernel or any file that starts with "linux".

My System:
MB - Asus M3A78-T, 1504 bios
CPU - AMD Phenom II x4 810, 3.13 GHz
RAM - 2 GB Crucial PC8500
On-board Video - ATI Radeon HD 3300
On-board Audio - ATI RS780 Azalia / ATI Technologies Inc SBx00 Azalia (Intel HDA) / ALC1200
OS - ubuntu 9.10 x86_64, kernel 2.6.31-14-generic
Video Driver – xserver-xorg-video-ati&radeon 1:6.12.99+git20090929.7968e1fb-0ubuntu1, FGLRX driver not activated

---

### Post by pveurshout on 2009-12-27
I completely agree! Yesterday I finally installed Karmic myself. I'm excited to see whether it'll work without freezing :)

---

### Post by alexlaban on 2010-01-01
I'm running Ubuntu Server 9.10 Karmic Koala and have huge problem with these freezes, it seems to be related to high network traffic since the freezes doesn't seem to happen when I'm not using the network or not using it much but a server without network is kind of useless especially on a 100/100Mbit line.

Edit: Actually when thinking about it I can only remember it happening when downloading at high speed with the server but never when uploading.

---

### Post by pveurshout on 2010-01-03
> **alexlaban said:**
> I'm running Ubuntu Server 9.10 Karmic Koala and have huge problem with these freezes, it seems to be related to high network traffic since the freezes doesn't seem to happen when I'm not using the network or not using it much but a server without network is kind of useless especially on a 100/100Mbit line.

Edit: Actually when thinking about it I can only remember it happening when downloading at high speed with the server but never when uploading.

I don't know if it's of any help, but I had a similar problem in Jaunty: when I'd transmit some larger file (>100s MBs) over my home network, the system would entirely freeze up (hard reboot necessary). Although I never found out what caused it in the first place, it did turn out to be highly dependent on the kernel used: some worked perfectly (2.6.28-15, -17), some didn't (-13, -14, -16). Anyway, good luck.. these freezes really are a pain in the *** because they seem so unsolvable :(

---

### Post by anubis3000bc on 2010-02-06
I have ubuntu server 9.04 and it's freezing, is yours giving you any problems?

---

### Post by dspisak on 2010-02-07
Anubis, I have the desktop version not the server but my solution may help you.  I had freezing problems with 9.04, and 9.10 froze even during the installation.  After trying many "fixes" I downloaded and installed the latest bios from the motherboard manufacturer, ASUS, and all of the freezing problems disappeared.  Also, I am running the distribution's ATI drivers, not the proprietary FGLRX driver.  Good luck to you.

Dan

---

### Post by anubis3000bc on 2010-02-07
Well it's kinda hard to upgrade a server motherboard drivers,and the mother board is a foxconn with ATI gpu onboard so right now i can't tell what the problem is at all.

---

### Post by lightbeing on 2010-02-23
> **pveurshout said:**
> I don't know if it's of any help, but I had a similar problem in Jaunty: when I'd transmit some larger file (>100s MBs) over my home network, the system would entirely freeze up (hard reboot necessary). Although I never found out what caused it in the first place, it did turn out to be highly dependent on the kernel used: some worked perfectly (2.6.28-15, -17), some didn't (-13, -14, -16). Anyway, good luck.. these freezes really are a pain in the *** because they seem so unsolvable :(

I am having exactly the same problem with 9.10, any file transfer of a large file across the lan will most certainly put it to freeze and would require a reboot to recover. Any ideas as to what I need to try please. I am very new to ubuntu and getting very frustrated with this problem, thanks!

---

### Post by anubis3000bc on 2010-02-24
Well i fixed my problem the server up and running good now with no problems and I'm using Ubuntu 9.04 server it's more stable, my teacher at ITT tech is like a linux guru so he always keeping me up to date.

---

### Post by Laysan_A on 2010-03-01
Hi,

I just upgraded to karmic yesterday. I had my first "freeze to black" today, as I was making another post in this forum, as a matter of fact. I was hoping I was done with all that. Oh well. I can't believe I've allowed myself to actually get used to and expect the occasional crash! I can barely remember what it was like before, to just run and run with no instability. But I can't imagine myself going back to windows either.

I spent a lot of time in this thread early on with jaunty, and I finally just lost heart. The one thing I didn't do (though there were others here who did - to no avail) was to wipe it clean and start over. I'm an idiot, well, inexperienced, and I didn't format my drive to have a separate home partition. Now I have almost 300GB of stuff on it that I don't want to lose. It's mostly pictures and videos. It will take me forever to migrate it off at 4.5GB a pop (no, I don't see a usb drive in my immediate future).

@dspisak
I did one bios upgrade about a year ago, but I'll go check again. You haven't had any luck with fglrx? I haven't since intrepid (which worked great all around). 

I notice you're from the east bay. I lived in concord years ago - I was stationed near the naval weapons station. I miss the short winters, but I don't miss the too dry summers or the constant earthquakes. :)

---

### Post by billharris on 2010-03-01
I do feel for you.  I went to Linux because I like *ux systems and because I really like extremely stable systems.  Hardy and Intrepid were stable.  Jaunty started stable and went downhill.  I was pretty frustrated near the end.

When I upgraded to Karmic, I, too, still had crashes.  At someone's suggestion, I reinstalled from scratch, and it's been quite stable ever since.

That was made easier by having a separate /home.

Even if you think Ubuntu is the ultimate stable system, hard drives don't last forever, so an external backup drive is a very good idea for anyone.  I use rsync-backup for backup, and that could make it easy for you to dump off your /home and start over.  I know: money does matter.

---

### Post by Laysan_A on 2010-03-02
Yeah, that sounds like my idea of heaven - painless migration of my entire directory. I really should just start over. I'm having problems with my apt system too, so I can't even reliably update.

---

### Post by pveurshout on 2010-03-19
> **lightbeing said:**
> I am having exactly the same problem with 9.10, any file transfer of a large file across the lan will most certainly put it to freeze and would require a reboot to recover. Any ideas as to what I need to try please. I am very new to ubuntu and getting very frustrated with this problem, thanks!

Have you tried using different kernel versions? I haven't had this problem with 9.10, but for 9.04 some kernels worked whereas others locked up all the time.

---

### Post by Laysan_A on 2011-01-18
I thought I should update this thread, since I'm a pretty big part of it, and because I finally resolved my issue. 

I was still experiencing my characteristic freezes to black through karmic and into lucid. I still couldn't figure out how to even debug them. On the day I finally fixed them I had two or three crashes in a row, just before I applied the fix (of course I didn't know it was a fix at the time ;) ).

I had been using gkrellm for years. For a long time, I was satisfied enough with the k8 sensor output for my temps. that I didn't bother trying to configure for the atk0110 sensors, even though they're more accurate. I lived with the less than accurate numbers of the k8, relying on the tendency of rising and falling to keep me aware of what was going on.

When I installed lucid I decided to finally get on the ball and get it done because I found I could get perfectly good atk0110 readings from ksensors (actually discovered that in karmic). So I started looking. I found out by running gkrellm in konsole that it hadn't been compiled with libsensors support. I couldn't figure out why. So I went on the web to look for answers.

It turns out that ubuntu stopped compiling gkrellm with libsensors support in 2007, apparently because there was a short window where libsensors had done a major update and gkrellm had not updated to accommodate  the libsensors update. This was a smart move, however, when gkrellm was patched, a week or two later, ubuntu failed to re-include libsensors support in its compiled versions. The original decision stands, that it was done for "safety reasons". 

I found a bug report on this in launchpad, along with the recommendation to compile myself. I went to the gkrellm site and downloaded the tarball, compiled it on my machine (libsensor support is the default), and voila, atk0110 sensor support - and not a single crash since.

So, something about having gkrellm installed without libsensor support when I had libsensors configured for both k8 and atk0110, caused the crashes. Interestingly (or not...), when I was using the k8 output I would continually have to re-enable them in gkrellm (go to the configuration dialogue and tic the boxes) because they would disappear each time I shut my machine off.

(It seems the removal of libsensor support in gkrellm now has just the opposite effect to the one intended.)

So...my particular issue is RESOLVED!!!!!:D

---

### Post by DarkTide on 2011-03-30
I have an HP Pavilion DV7-1006TX (FN374PA ) . I have been running every release since Gutsy  Gibbon till Intrepid Ibex. I've tried to install Jaunty on ext4 as it  comes after some work in GIMP the system freeze out for 5-10 seconds.  this didn't happened in the older release, no sir! I thought is because  of the ATI driver and I've installed the ATI driver X.Org from the  Add/Remove... and after my restart I couldn't get into the desktop any  more.

---

### Post by Caraibes on 2011-03-31
Since I had posted in this thread about 2 or 3 years ago, back when I had issues with Jaunty, I am still receiving updates in my email inbox.

So I have to be honest, and give you a sincere feedback, right ?

I am now running Lucid (10.04.x), single-boot on an older MacBook 2.1 (the white one, from early 2007, a hand-me-down). This is my main computer.

I have some PPA enabled (Libre Office, Firefox Stable, Google Stable & Testing, Pidgin etc...), running mostly Gnome, sometimes Xfce, Fluxbox, Lxde...

I removed all Mono apps, Evolution, Ubuntu One, Empathy etc...

I never had a single problem since I "inherited" this laptop, back in November... I gladly wiped OSX 10.4, which was totally obsolete...

No freeze whatsoever, hence my post today in this thread !

---

### Post by Laysan_A on 2011-04-09
@DarkTide

If I may give a little advice...

This is an old thread about an issue that really doesn't match yours very well. You likely won't get any help in this thread.

Why don't you start your own thread in the beginner's forum, then come back and edit your post here to include a link to your new, main post, so people won't think you're just cross posting. I think you'll have much better luck with you own thread.

---

