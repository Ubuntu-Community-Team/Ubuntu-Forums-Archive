---
title: "system-level problem"
date: 2007-02-05
forum: Development CD/DVD Image Testing
---

### Post by jerrybee on 2007-02-05
Newbie here.  This, I think, is a system-level problem that has showed up in Dapper, Edgy, and now Feisty, but not in Breezy.  Please bear with an abbreviated description, and accept my posting it here as I don't know where the best place to post it is.
    The problem shows up as very slow sound, but other system responses are slow too.  I'll just refer to the problem as being "slow sound".
    The sound is normal in Windows2000, Linspire, and Ubuntu Breezy.  In Dapper, Edgy, and Feisty, the drum-roll during the boot process, which normally takes maybe a half-second, will go on for maybe an hour (I kid you not).  Trying to play a CD, each note will last for a half-minute or more.  I just looked in Edgy to see if the displayed time was crazy too, but it looked like it was incrementing normally.  
     Yesterday I downloaded Feisty and burned a CD.  I tried to boot it to see if this problem had been corrected -- I got the "usual" slow drum-roll during boot, got some normal boot screens, but then got a blank screen and the slow sound for the next 15 minutes, at which time I gave up and re-booted.
    Being a newbie, I have no idea what sorts of things to try to track down what's going wrong or where the problem lies.  Since Breezy works normally, I figure something was changed between it and subsequent versions.  Breezy and Edgy are installed to the HDD while Feisty is still in live CD status.  As best I can recall, I also booted Dapper and Edgy as live CDs and got the problem too.
    I'll be more than happy to work with the developers to run more tests and provide more info, and help in any way I can to sort this out.  Please just correspond and ask.

---

### Post by Disa on 2007-02-05
Is your sound just slow, or is it stuttering, where each half-second or so of your audio repeats itself over and over again for about a half a minute to a minute or so before doing the same with the next half-second of audio?  If it's the stuttering, I'm having that problem too, with system sounds (no matter how I configure it under the Sounds preferences), yet xmms plays fine using OSS (but not with other output modes, even ALSA), and VLC runs fine.  I turned off system sounds to deal with it for now, leaving the only real problem with the mpg123 mp3 hover-over previews stuttering.

Oh yeah, and the problem started once before, after upgrading my video card from a GeForce Ti4800 to a GeForce 5200, but then went away when I went to the Sounds Preferences and hit one of the Test buttons and then clicked Finish.  This time, it started after I got done watching a video in VLC, and hasn't gone away since, no matter what I do.

Unfortunately, I have yet to get a definate answer to this, even though I've found a few other similar forum posts, which have gone unanswered.  Maybe this one will get lucky.. *crosses fingers*

---

### Post by jerrybee on 2007-02-05
Thanks for the response, the only one I've gotten so far.
     You've done a better job of describing the sound than I did -- a throbbing repeat of the same note for a long time, then a move to the next note.
     In the interest of shortening my first message, I omitted hardware info.  The mobo is a MachSpeed V4MDMP with AMD Athlon 1900MHz processor , 752MB of RAM, and onboard VIA VT8235 sound.  I installed a sound card as a check, but that didn't fix the problem.
     I forgot to mention that I had the same problem with a Fedora Core 6 installation on the HDD.
     I, too, keep hoping that the folks who develop Ubuntu will see my messages and either contact me directly or advise that they're aware of the problem and are working on it.  No such acknowledgement of the problem has happened so far.  Let's hope for the best.

---

### Post by Disa on 2007-02-05
I run an Athlon Thunderbird 750MHz with 512MB of RAM, a GeForce 5200, and a SoundBlaster Live.

I just noticed that I do have some stuttering problems in VLC as well...but it depends on what file format I'm trying to play.  DiVX seems to run fine, but .WMV files have problems, for example.  I tried reinstalling all of the gstreamer packages, all of the alsa packages, and the linux sound base, but the problem remains.

[rant]I know that a reinstallation of the OS would fix the problem for me, but then, I also know that the problem will inevitably come back...and I don't think I should have to reinstall my OS every couple weeks to a month just to keep the sound working.  Linux may have a lot higher uptime potential than Windows, but it sure seems like I have to reinstall it a lot more often because of little problems showing up for no reason whatsoever, and nobody having a solution to said problems.  I'm done with Windows.. but maybe I should be done with PCs in general as well, and just go to MacOSX...at least it works..[/rant]

---

### Post by spd106 on 2007-02-06
Have you been through this guide [http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

I have found it to be the best guide to sound issues in Ubuntu. It should at least give you some ideas of where the problem lies.

---

### Post by Disa on 2007-02-07
Problem is, that thread seems dedicated solely to problems involving sound not playing at all.  That's not the case in our situation.  Also, all of the tests came back normal, and unstalling/purging the linux sound base and alsa and then reinstalling them did nothing to solve the problem...and frankly, I'm surprised that nothing blew up in the process...I've witnessed how much other linux distros retaliate against any sort of change.. ;)

Sadly, this whole situation does little to raise linux up to the level of "viable operating system" in my mind, from its current level of "experimental hobby kit."  Too bad the only other real alternative on a PC is.. well.. you know.. *that*.

---

### Post by grazie on 2007-02-07
I'd guess the sound is stuttering due the system being heavily loaded. Once logged in, run top in a terminal to see what's hogging the system. If you can't figure it out yourself, take a snapshot of the terminal window while playing sound that's stuttering. Better still, install and run htop (rather than top). Post the snapshot here and we'll have a look.

---

### Post by Disa on 2007-02-07
Well, here it is.  No real difference in loads between playing a file with audio stutter problems, playing a file that has no stutter problems, and not doing anything.  As far as CPU time goes, moving my mouse around uses more CPU time than playing media.

---

### Post by jerrybee on 2007-02-07
Thanks -- I'll give it a try.

---

### Post by jerrybee on 2007-02-07
Here's the results of running top.  Recall that the drum-roll that sounds as a part of the boot process continues for maybe an hour, so it was "sounding" when I ran top.  If you want me to submit a screenshot showing top results after the sound stops, let me know and I'll do it -- it'll just take some time.

---

### Post by jerrybee on 2007-02-07
On second thought, It's now been an hour and the sound has stopped.  So I just ran top again and here's the screenshot of the result.

---

### Post by grazie on 2007-02-07
Well both of those screenshots show that your systems are hardly loaded at all. I'd therefore speculate you may have some kind of kernel and/or driver problems. If you boot with your Live CDs, do you get the same audio problem with them?

---

### Post by jerrybee on 2007-02-08
Yes, booting with both the Dapper and Edgy live CDs result in the same problems -- these include not only the pulsating audio but slow system responses, such as a 30-second delay after clicking on the Quit button before the various quit option icons are displayed, and then another 30-second delay after clicking on an icon before any further system action is seen.

The initial pulsating audio during boot is the sound that normally takes maybe 12 seconds to play, and now pulsates for over a half hour.  I believe I saw today (wasn't noting events then) that after the initial pulsating audio had finally stopped, the 30-second system delays had gone away too.  I'll verify this tomorrow, and post.

These long system delays lead this newbie to again suggest that this problem involves more than just the sound -- in my ignorance of details of the system operation, I could be wrong.

In trying to run the Feisty live CD, I get the pulsating audio during the boot process and a blank screen that lasts forever, or at least until I got tired of waiting and shut the box down. Tomorrow I'll boot the Feisty live CD and let things run until the pulsating audio stops, and then see if the boot process continues on to a desktop and icons and such.

Which reminds me -- when booting Edgy from the HDD, and the pulsating audio has begun, the desktop and icons appear but there are no labels or icons in either the top or bottom "bars" .  After about 30 seconds, the labels and icons appear in both bars, but the top-right icons and time display don't appear for another 30 seconds.  Surely that means something to someone, but nothing to me.  The pulsating audio begins after I've logged in.

The kernel in Breezy is 2.6.12-10, and the kernel in Edgy is 2.6.17-10 .

---

### Post by jerrybee on 2007-02-09
Now I have again tried the Feisty live CD, plus installed Feisty onto the HDD -- both yield the same audio and system-delay problems as Dapper and Edgy.

---

### Post by Disa on 2007-02-12
For some reason, having a USB pen drive plugged in makes the stuttering go faster (takes fewer repititions of each fragment before it goes to the next).  Also, plugging in one of my usb external hard drives will "refresh" the sound to where it should be if it's stuttering (in other words, get to the where the audio should be during playback, but then resume stuttering problem), or stop it if the sound should be done playing...but will only do it once, unlike the pen drive, which seems to have a more repetitive "refresh" effect.  Mounting, unmounting, or unplugging the drive will have the same effect on the audio as plugging it in.

Apparently until this gets fixed, most .avi files and .mp4 files play alright, and some .wmv (probably something to do with audio codecs), but so far all .ogm and .mkv files are unplayable due to this nasty audio stuttering problem.  Also, XMMS works alright for playing MP3s, but Amarok is nonfunctional (I use one of those two for music.. the players that come with Gnome just suck, IMO).

---

### Post by jerrybee on 2007-02-16
Success! ! !  I posted a bug report and got help.   Adding "irqpoll" to the end of the kernel boot line in /boot/grub/menu.lst cured the problem, at least for now.  I did this in the Feisty install, then went back and edited the kernel boot lines for Edgy and Fedora Core 6, and all distros now have good sound and don't exhibit the system delay I described before.

I can't find irqpoll in my Linux or Ubuntu books, as I'd like to find out what this change really does. A Google search on irqpoll gets lots of hits, so I'll dig deeper there.

Thanks again to all who responded here to my plea for help.

Jerry

---

