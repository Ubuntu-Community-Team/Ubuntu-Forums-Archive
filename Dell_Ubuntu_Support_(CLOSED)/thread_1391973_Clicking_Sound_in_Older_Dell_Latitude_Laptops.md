---
title: "Clicking Sound in Older Dell Latitude Laptops"
date: 2010-01-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kixtosh on 2010-01-27
I've been struggling with the sound in a new installation of Karmic Koala on an old Dell laptop, and it seems as though I'm not the only one.

What's happening is that sounds are produced, more or less normally, but there's a horrible clicking sound at the same time, that drowns out the normal sounds. I've been trying to troubleshoot the issue with no success. 

The problem seems to come from a Neomagic sound card that worked under OSS, but does not work properly with ALSA.

Details:

- Dell Latitude CPi R400GT
- Ubuntu 9.10
- Sound card identified as the Neomagic NM2360 [MagicMedia 256ZX Audio]

These are the listings for Neomagic from ALSA: 

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Neomagic](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Neomagic)

Here's a thread in the general section (not DELL) that mentions the problem:

[http://ubuntuforums.org/showthread.php?t=1335395](http://ubuntuforums.org/showthread.php?t=1335395)

So, should I be reporting a bug? Is there a fix I could try? Can I just use OSS instead? I'm baffled .... HELP!!

---

### Post by mörgæs on 2010-01-28
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by Kixtosh on 2010-01-28
> **mörgæs said:**
> [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Thank you sir! Now why didn't I find that myself, when I was searching all over the support area? I'll try it out, and post back here with the results ... maybe later today, if I can get finished in time.

This problem has been around for a while, since I tried the Live CD of Hardy Heron (8.04, with LTS) last night, and got the same clicking sound. That makes sense, of course, if it's ALSA related.

---

### Post by Kixtosh on 2010-01-28
Okay, so I've already hit a speed bump. Following that link, I followed the link here, to check what ALSA version I had, and how to upgrade:

[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

Sure enough, I had the wrong version, and need the upgrade. Fine. I followed the instructions, and got to this command:

> cd ~
rm -rf ~/alsa* ~/.pulse*
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.1.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.22.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.22.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.22.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.22.tar.bz2)Which led to this unfortunate demise:

> Resolving ftp.alsa-project.org... 212.20.107.51
Connecting to ftp.alsa-project.org|212.20.107.51|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/driver ... done.
==> SIZE alsa-driver-1.0.22.1.tar.bz2 ... 3218678
==> PASV ... couldn't connect to 212.20.107.51 port 21666: Connection timed out
Retrying.
So that's where I'm at. I'm trying to figure out if I can find another way to upgrade ALSA, before I get back to my troubleshooting ... Ugh! Most notably, I've been attempting to digest this Sound Solutions sticky thread:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Oh well, at least I'm learning all the intricate pathways of the support community forum!

---

### Post by mörgæs on 2010-01-29
This is only a download problem. 

You don't have to use wget. If you just copy [ftp://ftp.alsa-project](ftp://ftp.alsa-project)... to the address field in a browser, can you download the three files?

---

### Post by Kixtosh on 2010-01-29
> **mörgæs said:**
> This is only a download problem. ...Thank you again! I was hoping that was all it was. I'll try the other method you suggest later this morning (it is morning here, although I think you're on GMT). ;)

---

### Post by Kixtosh on 2010-01-29
Okay, so I've made a little progress. I couldn't use the link in the alternative solution, for whatever reason, but I figured out why I was not getting the downloads, I think: I just turned off the hardware firewall on my wireless router, and everything started up immediately in the Terminal console, which was going through multiple retries, just like yesterday.
 
I got all the files, and I've moved them into the right directory, and they're being installed right now.
 
More updates later!

---

### Post by Kixtosh on 2010-01-29
Although I have been able to complete the entire process described to upgrade to ALSA 1.0.22.1, without any obvious errors that I could determine, it hasn't worked.

When I type a command line in Terminal:
> cat /proc/asound/version

I get the dreaded:
> Advanced Linux Sound Architecture Driver Version 1.0.20.
Compiled on Jan 28 2010 for kernel 2.6.31-17-generic (SMP).

So, how on earth am I going to get upgraded to 1.0.22.1?! What a mess!

---

### Post by mörgæs on 2010-01-30
There are more advice here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

---

### Post by Kixtosh on 2010-02-01
Well, I just tried this procedure on my other newly installed Ubuntu relic (the worthy Toshiba Portégé 3490CT), as outlined in the same procedure I already tried on the DELL:

[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

And, on the Toshiba ... it worked perfectly ... but the Toshiba wasn't having any audio problems! Anyway, at least it means that I understood the procedure correctly. I'm trying a few more of those steps again on the DELL, now that I have a comparison fresh in my mind, just in case I did something wrong the first time. We'll see how it turns out.

---

### Post by Kixtosh on 2010-02-01
Well, I tried this procedure on the DELL, from the link suggested above:

[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

Intended to "*... Install the "[linux-backports-modules-alsa-karmic-generic]("apt://linux-backports-modules-alsa-karmic-generic")" package ...*", which I also did on the Toshiba already. Well, since I was already using the Synaptic Package Manager to achieve this, I also removed every package with a reference to ALSA and version 1.0.20 as well (probably a very bad idea when you don't really know what you're doing, but oh well ...).

Then I went ahead and followed the remaining ALSA version upgrade steps, from this page, as mentioned above:

[http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/](http://monespaceperso.org/blog-en/2009/12/17/upgrade-alsa-1-0-22-on-ubuntu-karmic-koala-9-10/)

Starting with these commands, and onwards from there, since I already had the "tar" files downloaded: 

> sudo rm -rf /usr/src/alsa
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/alsa* .Well, that's all very nice, and I've got rid of version 1.0.20, it seems, but I've only got to version 1.0.21, not 1.0.22! I can only suppose the 1.0.21 version installed itself by default, since I removed the packages for 1.0.20, but the installation of the 1.0.22 upgrade seems to have failed, just as it did before, and even though everything seems to proceed perfectly normally during the process.

At this point, I'm wondering if I should not completely reinstall the kernel, to erase any manipulations errors I may have introduced by now. I just cannot get ALSA version 1.0.22 to install, even though it worked flawlessly on the Toshiba.

---

### Post by Kixtosh on 2010-02-02
Well, I wanted to be sure about what was going on, and if I'd made any user manipulation errors that were disrupting the upgrade process, so I've done something crazy: I wiped the partition clean using the Live CD. Oops! It was so easy I could not believe it!

I'm going to reinstall Karmic Koala fresh. Before I do anything else, I'll then try to upgrade ALSA. Probably even before I upgrade the kernel from version x.14 to version x.17. Yes, I know: it sounds like madness, and it's probably like taking stick of dynamite to remove a speck of dust, but I didn't have any useful files on this drive yet, so it shouldn't really be a big deal, and I wanted to get it started tonight. This way, I'll be ready to try the upgrade as soon as I have free time tomorrow.

---

### Post by Kixtosh on 2010-02-02
> **Kixtosh said:**
> ... This way, I'll be ready to try the upgrade as soon as I have free time tomorrow.Well, this hasn't quite worked out as planned so far. This morning, when I went to start the upgrade process, following the usual procedure ...

> We must then install the necessary tools to compile along with the kernel headers :... with the commands:

 > sudo apt-get -y install build-essential ncurses-dev gettext xmlto libasound2-dev
sudo apt-get -y install linux-headers-`uname -r` libncursesw5-dev
I simply get the error message:

> E: Couldn't find package libncursesw5-dev
E: Couldn't find package build-essentialI'm guessing that this is because I haven't allowed the update utility to run yet, so I'm going to get that running now, and then try again later.

---

### Post by Kixtosh on 2010-02-02
> **Kixtosh said:**
> ... I'm guessing that this is because I haven't allowed the update utility to run yet, so I'm going to get that running now, and then try again later.Yes, allowing the Update Manager to download 214 updates, thereby installing Kernel version "2.6.31-17-generic", has now enabled me to start the process, and it's working  ... I just have to wait for the fairly monstrous download to finish before continuing with the *tar* files download (an even larger download).

---

### Post by Kixtosh on 2010-02-02
Well, after going through all of that, I finally got to see this:

> Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Feb  2 2010 for kernel 2.6.31-17-generic (SMP).This time, when I went to download the *tar* files, they were much smaller. Not even 10% of their previous size (rough guess, I haven't checked exactly), so not only was the download much faster, but the contents may have been different as well. In any case, it worked.

However, before anyone gets too joyous, the nasty clicking sound is still there ... but at least I can continue troubleshooting normally now.

---

### Post by Kixtosh on 2010-02-04
Well, I seem to have solved this problem ... at least 95%! It was almost by accident in the end, but here goes:

**(1)** From reading in the forums, it seemed to me that many woes were being blamed on PulseAudio, especially in this thread: *[http://ubuntuforums.org/showthread.php?t=1368141](http://ubuntuforums.org/showthread.php?t=1368141)*, so I decided to try removing PulseAudio with this command (from that thread, and verified elsewhere) in Applications/Accessories/Terminal:

[I]sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio
[/I]
**(2)** Unfortunately, at that stage I couldn't find any way to adjust the sound at all. The ALSA mixer was still there (Applications Menu), but there was no sound at all and I couldn't seem to figure out how to turn it on with no speaker applet icon in the top panel any more.
[B]
(3)[/B] So I decided this was even worse, and that I had no option but to add PulseAudio back again. So I used this command, also from the thread in the link above.

*sudo apt-get install ubuntu-desktop*

**(4)** Well, everything now seems to be working about 95% normally (see one known exception below). I don't know if I accidentally updated to a newer version of PulseAudio or what.

_Remarks:_

(A) During start-up, I still hear the horrible clicking sound when the "ubuntu" splash screen displays, but the sound animation for the desktop plays normally when the desktop starts to load up (session login, maybe?). I'll have to figure out a way to **mute the splash screen sequence** to avoid this.

(B) I hope I can reproduce this result, since I really want to install Xubuntu on this laptop (because of the rather modest resources). I also intend to install Xubuntu 10.4 when it is available (rather than 9.04) and keep using it until the next LTS release. Being able to reproduce the result as necessary would be very useful indeed if I am to succeed in this endeavor! It might also help others who read this thread to understand exactly why this solution worked at all ... and I certainly have no definite idea why it did!

Thanks to all for your interest and support!

---

### Post by Kixtosh on 2010-02-09
More information on this topic:

Well, I've actually switched my old DELL to Xubuntu 9.10, and my one remaining sound issue with the regular Ubuntu install (clicking noise during the startup splash screen) has been entirely solved. _I did not have to do anything with Xubuntu to get the sound working_, neither upgrading ALSA nor fiddling around with PulseAudio in the Terminal Console. It worked flawlessly (so far) out of the box.

---

