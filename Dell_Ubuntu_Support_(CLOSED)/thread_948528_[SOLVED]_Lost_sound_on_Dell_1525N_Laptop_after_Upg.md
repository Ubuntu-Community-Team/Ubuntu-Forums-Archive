---
title: "[SOLVED] Lost sound on Dell 1525N Laptop after Upgrade to Linux kernel 2.6.24-21-gene"
date: 2008-10-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by StewartM on 2008-10-15
Greetings all,

I have a Dell Inspiron 1525N I purchased with Gusty pre-installed. I upgraded it to Hardy 8.04.1, and ran into the expected problems, listed on the Dell Wiki:

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Known_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Known_Issues)

This morning, I was prompted to upgrade the kernel on both my (Zareason) desktop and also my Dell 1525N laptop. The desktop upgrade went smoothly. The laptop upgrade broke the sound. (On the restart, I could see the OS recognizing the hsfmodem and loading new drivers for it...I should have just removed it as I don't need the modem).

Ergo, I went back to the Dell wiki, and repeated the instructions save that I entered in:

$ sudo dpkg -r linux-backports-modules-2.6.24-19-generic

Instead of "linux-backports-modules-2.6.22-14-generic"

as the last working system was 2.6.24-19-generic not 2.6.22-14-generic.

All the other steps I repeated as listed (save of course that the remaining steps are done in the 2.6.24-21 /lib/modules subdirectories).

Still no work. I suspect that this is not a hard problem to solve, I'm just missing something. I'm currently making do by booting to Linux kernel 2.6.24-19-generic for the time being.

Any ideas on how to fix this?

StewartM

---

### Post by clearshot on 2008-10-15
I just upgraded to Ibex on the Dell 1525N (never buy it)

-Speakers crackle on mute when there is a sound event. (Music, sign in etc)
-Touchpad options are not applying (Disable touchpad click doesn't work)
-I had trouble with Compiz in Hardy... I haven't tried using it again.
-Wolfenstein: Enemy Territory, graphics are fine and then they randomly break
-Battery life sucks
-Most other problems I have fixed

---

### Post by Gaudentius on 2008-10-15
I got the same problem here.

I remember reading something at the re-start about the audio may be screwed up and something about ALSA.  But that's as far as I got.  I glanced at it too late.

Being I'm still a n00b, I'm S.O.L. until I find a fix here.

I'll be looking around . . .

GD

---

### Post by Gaudentius on 2008-10-15
I got the sound working!!!

[URL="http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade"]
***_Dell Sound Issues_***[/URL]

Follow the link above and at the bottom of the page there is a section that says **If already running Ubuntu 8.04 and upgrading to kernel 2.6.24-17-generic**.

Follow the instructions, except instead of **2.6.24-17-generic**, type in **2.6.24-21-generic**

**FROM WIKI**
Restore name of sound driver that old modem driver renamed:

$ cd /lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/pci/hda
$ sudo mv snd-hda-intel.ko.REPLACEDBYhsfmodem snd-hda-intel.ko

Remove old sound drivers from kernel module directory:

$ cd /lib/modules/2.6.24-21-generic/updates
$ sudo rm snd-hda-intel.ko
$ sudo rm snd-hda-codec.ko

Rebuild initrd and reboot:

$ sudo depmod -a
$ sudo update-initramfs -u
$ sudo reboot

The modem should now be recognized and fully functional. 


GD:guitar:

---

### Post by StewartM on 2008-10-15
> **Gaudentius said:**
> I got the sound working!!!

[URL="http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade"]
***_Dell Sound Issues_***[/URL]

Follow the link above and at the bottom of the page there is a section that says **If already running Ubuntu 8.04 and upgrading to kernel 2.6.24-17-generic**.

Follow the instructions, except instead of **2.6.24-17-generic**, type in **2.6.24-21-generic**

**FROM WIKI**
Restore name of sound driver that old modem driver renamed:

$ cd /lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/pci/hda
$ sudo mv snd-hda-intel.ko.REPLACEDBYhsfmodem snd-hda-intel.ko

Remove old sound drivers from kernel module directory:

$ cd /lib/modules/2.6.24-21-generic/updates
$ sudo rm snd-hda-intel.ko
$ sudo rm snd-hda-codec.ko

Rebuild initrd and reboot:

$ sudo depmod -a
$ sudo update-initramfs -u
$ sudo reboot

The modem should now be recognized and fully functional. 


GD:guitar:

I am now up and running too; same fix. 

I initially tried this fix from the get-go, but made a simple typo in renaming the file. I have also been on the Dell Community forum, and when someone said he gotten it to work by the above-listed procedure, I rechecked my handiwork and spotted my typo. Ergo, problem solved.

I'll mark this thread as solved, it is still useful because it will help any others who encounter this problem.

StewartM

---

### Post by scampiuk on 2008-10-16
Fantastic, worked perfectly on my 1525

Cheers!

---

### Post by tom56 on 2008-10-17
Is there another way of fixing this? My sister is having the same problem and isn't comfortable using the command line. I've told her to call Dell but I'm not sure how much help they'll be.

Stuff like this really shouldn't happen - I'm surprised Dell don't do their own testing of updates (especially big ones like the kernel).

---

### Post by henrydurham on 2008-10-17
It isn't solved! I don't know/dare use the command line and since the last upgrade my computer the sound hasn't worked. It says that there is no sound card driver installed and generally refuses to work. If anyone can talk me through the process in plain English that would be fantastic! Thanks, Henry

btw, it's a Dell Inspiron 1525 running the latest version of Ubuntu.

---

### Post by h00pla on 2008-10-17
> **tom56 said:**
> Is there another way of fixing this? My sister is having the same problem and isn't comfortable using the command line. I've told her to call Dell but I'm not sure how much help they'll be.

Stuff like this really shouldn't happen - I'm surprised Dell don't do their own testing of updates (especially big ones like the kernel).
I don't think that there is another way of fixing this. If you basically just cut and paste from Gaudentius' post above (everything with a dollar sign $ in front of it) into a terminal emulator (GNOME terminal, xterm, etc), you will be able to fix it.

But I definitely agree with you that stuff like this shouldn't happen. I have been using Linux since 1997, and way back then, I had to do stuff like this on a regular basis, but in 2008, you'd think that this type of breakage would be way behind us. I bought a Dell Inspiron 1525 with Ubuntu pre-installed, basically out of curiousity. I had hoped that this would be a machine that I could recommend to several of my friends that are thinking of transitioning from Windoze to Linux. But when stuff like this happens, you go out on a limb recommending a Linux machine like this. I have been active in the Linux movement for a long time, and I must say that there should be better communication between the Ubuntu people and the Dell people. In the end, this kind of issue hurts Linux a lot.

---

### Post by henrydurham on 2008-10-17
I bought a linux machine because I was told that it wouldn't freeze, wouldn't come down with spyware and viruses, and was more stable generally than Windows. However, it appears that there is no simple fix when a problem occurs, certainly if you don't know that much about computers.

I can see the solution above, do I just copy and paste all the commands into the terminal at once, or in sequence?

---

### Post by h00pla on 2008-10-17
> **henrydurham said:**
> It isn't solved! I don't know/dare use the command line and since the last upgrade my computer the sound hasn't worked. It says that there is no sound card driver installed and generally refuses to work. If anyone can talk me through the process in plain English that would be fantastic! Thanks, Henry

btw, it's a Dell Inspiron 1525 running the latest version of Ubuntu.
henrydurham

A couple of comments. 1)You're going to have to use the command line, but it is not as scary as you think. 2)If this pisses you off, you're totally right to be. This stuff should *not* be happening at this stage of the Linux game. As a long-time Linux enthusiast, I apologize. 

That said....


What you have to do is start a terminal (click on Applications --> Accessories and you will find 'terminal'). One line at a time, just cut and paste everything with a dollar sign $ (but don't include it) in front of it from Gaudentius' post above (will either start with 'cd' or 'sudo') With the first 'sudo' line, you'll have to type your password here and probably not be asked again. The last line reboots your laptop instantly, so don't be alarmed. If you do all of this, you will have sound when the machine reboots.   

Again, in 2008, we shouldn't have to be doing this. This kind of problem is a deal breaker when you're trying to get people to switch to Linux.

---

### Post by h00pla on 2008-10-17
> **henrydurham said:**
> I bought a linux machine because I was told that it wouldn't freeze, wouldn't come down with spyware and viruses, and was more stable generally than Windows. However, it appears that there is no simple fix when a problem occurs, certainly if you don't know that much about computers.

I can see the solution above, do I just copy and paste all the commands into the terminal at once, or in sequence?
Paste it one line at a time. (See  my comment #11)

FWIW, what you were told is right. Linux hardly ever freezes, it is both spyware and adware free and is the most stable operating system out there. Due to the decentralized nature of Linux development, these kinds of things can happen. It's looks like a bit of poor communication in the chain of Linux kernel developers, Ubuntu maintainers and Dell. But stay with Linux. You won't regret it.

---

### Post by henrydurham on 2008-10-17
Wow, my first bit of computer programming :lolflag:My sound now works, and I shall shortly be watching a dvd. 

I have to say that I much prefer open source software to windows. It *is * quicker, more "predictable" (especially if you overload it with loads of windows open at the same time) and looks a bit better I think. 

Thankyou so much for helping me with it, it worked brilliantly. I'm glad there are forums and support out there for me if I get stuck. Have a good weekend! Henry

---

### Post by raynedanser on 2008-10-17
Hm. Well.

Also running a 1525N and I had that happen as well, but *didn't* have to go through the command line. I went through system -> administration -> start up manager and selected to have it start on kernel 19 through there and got my sound back. 

Mostly. No AVI file audio unless I'm using VLC.

Den

---

### Post by henrydurham on 2008-10-17
I don't have that in my system menu, what release do you have?

---

### Post by raynedanser on 2008-10-17
I had to install it - look in Synaptic for start up manager. ;-)

---

### Post by ChimpofDOOM on 2008-10-17
Hmmm, i'm communicating with a friend via SMS, she now lost wireless after doing this fix.. says she cant get a wired connection.. any idea's anyone?

---

### Post by StewartM on 2008-10-17
> **tom56 said:**
> Is there another way of fixing this? My sister is having the same problem and isn't comfortable using the command line. I've told her to call Dell but I'm not sure how much help they'll be.

Stuff like this really shouldn't happen - I'm surprised Dell don't do their own testing of updates (especially big ones like the kernel).

There is the Dell Linux wiki:

[http://linux.dell.com/wiki/index.php/Wiki_Main_Page](http://linux.dell.com/wiki/index.php/Wiki_Main_Page)

What I plan to do with my 1525N I own (and the 530N I help some friends maintain) is to put off the major upgrades until the wiki is updated to list any known problems which occur with that upgrade.

If you don't like to do things by the command line, there are two options to cut this down quite a bit.

First Way:

Download and install GNOME Commander, which is a simple two-paned file manager for GNOME. Since you want to be able to use GNOME Commander with admin privileges to do this kind of work, either open up a terminal and type in:

gksudo gnome-commander

or simply edit the menu icon for it to prefix "gksudo" in front of the command gnome-commander. Either way, when you open it a box will open up asking for your password, and you can point and click your way through directories and copy and rename and move files without all that typing.

Second Way:

Open up a terminal and type in:

gksudo nautilus

Again, a box will open up prompting you for your password. Then a window will open, and within this window (only) you'll have admin privileges. You can (once again) navigate through directories, copy, rename, move files, etc. without typing a directory path 8 directories deep.

For something like this problem, what you're essentially doing is 

a) restoring a name of a file that got renamed in the upgrade;

b) deleting two files which were wrongly substituted.

Pretty simple stuff, though it looks more daunting than it actually is.

Then you type in the last three lines and you're done.

StewartM

---

### Post by busgeek on 2008-10-21
Hmm.  I'm stuck on this too just now on my new 1525n

I'm happy using the commandline - but the file mentioned does not exist
snd-hda-intel.ko.REPLACEDBYhsfmodem snd-hda-intel.ko
The upgrade hasn't renamed it - I have a file called snd-hda-intel.ko 
which I have taken a copy of.  (But no file called snd-hda-codec.ko)

Ubuntu (or ALSA at least) doesn't detect the soundcard.

Any ideas please?

Howard

---

### Post by tom56 on 2008-10-22
You can follow this bug here - [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/283790](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/283790)

---

### Post by ludentic on 2008-11-03
I did what Gaudentius suggested and I got sound working... until I updated to Intrepid. Now it has no output at all, though it recognises the soundcard.

---

### Post by 94114 on 2008-11-20
Thank you Gaudentius for your 1525 sound fix post.  My sound is working better than ever (louder).  I was close to scratching Ubuntu and loading winXP... You saved me from the dark side.

---

### Post by henrydurham on 2008-12-01
Hi, this has happened again with the latest update. Thought I would resurrect this thread.

---

### Post by kavoura on 2008-12-02
I also have the same problem. Just bought a Dell Inspiron 1525 with Ubuntu, did some package installing and minor updates, now no sound. 

I tried following the instructions given for the CLI, but it gave me an error message as the file or directory does not exist.

If there is no such file or directory, then what is causing the sound to disappear?

---

### Post by henrydurham on 2008-12-02
Use the solution on the new thread I started about this problem. That has solved it.

---

### Post by kavoura on 2008-12-02
Do you have a link to the new thread?

---

### Post by kavoura on 2008-12-02
Not to worry, I found it. I allowed Ubuntu to update everything including the kernel via the automatic updater, then tried the instructions again (now with kernel number ending 22) and it all worked and I have sound again.

---

### Post by tofuweenie on 2008-12-02
I'm having a lot of the same issues with the sound/volume control on my new (less than a week old) Dell Inspiron 1525 running Ubuntu 8.04.  I'm VERY new to ubuntu, and I'm trying to be a big kid and figure this out on my own before I pester my friend to help me -- I've tried to use some of the solutions I've been reading about in these forums, but I still have no sound!  Please help me!

the two error messages i get are:

1. "The volume control did not find any elements and/or devices to control.  This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."

2. "No volume control GStreamer plugins and/or devices found."

Please respond in as idiot-proof of a manner as possible!

---

