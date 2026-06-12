---
title: "Graphics driver change now boots to terminal; can't access GUI"
date: 2016-06-15
forum: Desktop Environments
---

### Post by Wadcutter on 2016-06-15
It's a desktop running the latest Linux kernal on Ubuntu 12.04 with a Nvidia GE Force 8400GS graphics card Having a lot of crashes and Compiz "closing unexpectedly" lately, I thought there might be a driver problem so I changed the graphic driver in the System Settings from one version of the listed "Nvidia accelerated graphics driver (ver 304) to a different listing of the same driver that was "recommended". Upon reboot, I now find myself in a terminal prompt with no clue of how to get back into my familiar GUI.  I sniffed around a bit online (with this different computer) and tried entering "startx" to no avail and also cntrl+alt+ F7. There were just wild stabs in the dark with no comprehension on my part. I'm lost. I lack the knowledge to even figure out logic that would get me back in to where I might change the driver back. For some reason this one doesn't want to work (even though it's also described as a "Nvidia accelerated graphics drive (ver 304). Booting into recovery mode also just gave me a black and white fullscreen terminal after I enter my name and PW. I really messed up this time.

---

### Post by Wadcutter on 2016-06-16
I apologize; I believe I should have posted this to the beginner forum since I am apparently asking for some basic help with terminal commands that I don't know enough about. Would a Moderator be willing to move this post to that forum? Thank you.

---

### Post by Wadcutter on 2016-06-17
I'd like to just close this thread and forget about it. I can't mark it "Solved". Quite the contrary, I've managed to totally wipe out all monitor display now. I do greatly appreciate these forums although no one offered any suggestions at this time. So here's a rundown of what I tried on my own--maybe it will be of some help to someone else down the road.

1) Searched through all these forums and online for similar problem.
2) Tried several suggestions revolving around removing the offending driver and replacing. Tried commands such as "sudo apt-get remove nvidia-current" or perhaps it was "purge-remove". (Disclaimer--I'm not trying to state exact syntax here--just giving a general idea of what I was trying to do.) After it seemed the driver was gone, I then tried several different commands to install the correct current driver. Again, general: "sudo apt-get install nvidia-current" and a whole host of other commands involving acquiring the correct ppa and then trying to install. The problems piled up. My commands weren't recognized, couldn't be found or my system was locked into some read-only mode involving /var/something/dpkg/lock. Went around in circles for about 5 hours.
3) I downloaded the proprietary Nvidia driver from their site with the thought of installing it from a thumb drive. I figured I could later switch back to the official Ubuntu one. But I couldn't access the thumb drive from the terminal.  Online info was useless: "sudo fdisk -1" did not identify it for me and when I did finally find what it was called, I couldn't access it due to some other quirk. My OS has more dependencies and quirks than a U.N. policy debate.
4) Six hours later I gave up and started studying the info about re-installing my whole OS (12.04) without trashing my files. Confident that I knew what I was doing (I knew all my usernames and passwords) I went for it. After 2 hours of re-installation I re-booted and found I had totally lost all video display. The bios starts and then just before the Grub menu comes up, a bright colored band appears across the screen for 5 seconds and then the monitor goes black and shuts down.

So now I don't even have a terminal prompt to play with (send me around in circles). I have no video to do anything with other than tweak the
bios. (yes, I though of going there to try to activate the on-board video, but this mobo has none). So I'm trying to come up Plans B, C and D. No point in covering that here as it will benefit no one. (I should mention that booting from an old Knoppix disk brings up perfect monitor video so the graphic card is not lunched--it's a total Ubuntu OS/driver problem, I would think).

Is there a lesson here?  Don't believe everything you read (including the system setting "recommending" one video driver over another that caused the trouble in the first place)? Don't believe fix-it suggestions found online? Don't own complex electronics gizmos if you can't accept the bad with the good? Maybe the biggest lesson is just learn to live with imperfect situations with minor problems instead of trying to fix them and perhaps ending up with MAJOR problems.

Hope this helps someone else from stepping into it. Thanks again for all the useful help and info that is in these forums. I hope that someday I'll actually be able to solve something on my own and then be able to give something back by sharing it here instead of always just asking someone else to help me.

---

### Post by howefield on 2016-06-17
So where are you know, do you still need help ?

Do you have a working installation ?

---

### Post by Wadcutter on 2016-06-17
I definitely need help even though the situation is entirely of my own making.  I have no monitor display beyond the start-up just before Grub boot, so that makes me feel like driving a car with a blindfold. I have no idea how I would restore video to even see a terminal, let alone the GUI desktop. I'm now thinking along the lines of pulling my 2 hard drives from the computer and trying to access the files on them from another working ubuntu computer (which I have). I do have thumb drive backups of my important data files, but there are other things I would like to access (music, photos, emails etc). The second of my 2 HDs has a backup of the first drive that would be nice to access. I did try to open those drives from the 12.04 live install disk but ran into permissions that locked me out. gksudo nautillus was no help there, either. So I may not be able to access from a different computer either.   As a final resort if I can't get into the HDs and can't restore any video, I can just go for a clean install of perhaps 14.04 or 15.04 and kiss everything not saved onto those thumb drives goodbye.

Long answer to a short question. Do you know of any way to restore monitor display when there is nothing to see?

---

### Post by howefield on 2016-06-18
To be honest, were it mine and unless there was an educational element to fixing the problem I would take the path of least resistence. Given that you are using 12.04 which is in the final year of of support (10 months left) I'd suggest using this as an opportunity to move to 14.04 (supported till 2019) or the recently released 16.04 (supported till 2021). Forget 15.04 as it is already end of life and 15.10 goes end of life next month. Unless you have hosed the hard disk which is unlikely, you will be able to retrieve your data prior to installation.

Are you able to download a copy of either the current or last LTS and create a Live media.

If you however, want to persevere with the current installation, can you get to a recovery mode, by pressing and holding the Shift key on power on and selecting the option from the grub screen ?

---

### Post by Wadcutter on 2016-06-18
Memory lapse (mine, not hardware) about using Shift to force boot menu.  I can now get a terminal prompt but don&#8217;t know what to do with it.

[LIST=1]
[*]I agree: path of least resistance ; but
[*]If I can get back to my current installation and do a little extra backing up before upgrading to 14.04 that might be wise.
[*]I don&#8217;t want to spend a lot of your time or mine trying to get back to 12.04 if it can&#8217;t be done  in one or two tries.  If it gets complicated, then I will opt for a straight upgrade and not fret about more backups. Downloading update and burning a thumb drive seems like best option.
[*]Since re-installing 12.04 didn&#8217;t fix the aberrant graphics driver,  will upgrading to 14.04 do it? Or is there something else happening that needs to be addressed?
[/LIST]
I have been thinking of upgrading anyway but wonder about the compatibility of 14.04 with  2008 vintage hardware?  It does have a 64-bit AMD chip, 4 GB of memory, and a somewhat newer Nvidia graphics card that I installed about 4 years ago. I like the apps that Ubuntu supports and prefer not to go to Xubuntu or Lubuntu just to deal with older hardware. Prefer to skip 16.04 until it&#8217;s been around awhile and the gremlins shaken out. Am budgeting for a newer computer.
Thanks for options/advice.

---

### Post by him610 on 2016-06-18
> wonder about the compatibility of 14.04 with 2008 vintage hardware? It does have a 64-bit AMD chip, 4 GB of memory, and a somewhat newer Nvidia graphics card
Not to worry. LTS 14.04 or 16.04 will run just fine on your system. I have four systems, all from the same era. I have encountered no problems with LTS 14.04 running on any of them.

---

### Post by Wadcutter on 2016-06-19
Thanks, him610. One less worry and I can put a new computer farther back on the back burner.

---

### Post by howefield on 2016-06-19
OK, so you have a terminal prompt, so log in with your username and password, and remove the nvidia drivers with

```
sudo apt-get purge nvidia*
```

You may have to mount / as writable first..

```
sudo mount -o remount,rw /
```

See where that takes you.

Incidentally if it gets close to last resort, you should be able to install 12.04 (or 14.04 for that matter) straight over the current installation and partitions and as long as you don't mark the partitions for formatting, your /home folder should be preserved. You'd end up with a clean 12.04 with your current /home intact. I'm assuming that your /home folder is on the same partition as /.

---

### Post by Wadcutter on 2016-06-19
What you suggest here is pretty much what I spent about 8 hours doing 3 days ago. I remember these two specific commands. After purging nvidia, I tried to reinstall with something like &#8220;sudo apt-get install nvidia-current&#8221; and a few other variations like &#8220;sudo apt-get install nvidia-current-update&#8221;. In general,  it seemed there were some missing files or dependencies that always thwarted me.
  After 5 hours of that, I did go to the last resort and reinstalled 12.04 over the same partitions (not formatted) with my same username and password. What I got from that is what I have now&#8212;the monitor screen automatically shuts off just before Grub (an after a couple of colored bands appear across the display). The computer seems to boot up and go on its merry way until I manually shut it down with the power switch.  Your commands suggested  here didn&#8217;t change anything.
  I originally installed 12.04 about 4 years ago with 4 partitions on one HD and one partition on the second (to be used strictly to back up the first drive).  The four are a tiny boot partition, followed by a +/-25 GB  root (/) partition, followed by a +/- 210 GB home (/home)  partition and finally a small swap partition. My thinking was that I could re-install (if need be) on the root one and not disturb my doc files on the /home one. I&#8217;m wondering if perhaps I should have formatted the root partition and let the re-install write everything new there, including a necessary Nvidia graphics driver.  By preserving it, wouldn&#8217;t that have effectively kept it the way it was (broken) and not have allowed the re-install to overwrite with a driver?
  If a 12.04 re-install couldn&#8217;t fix the graphics, I&#8217;m wondering if an update to a newer version will fare any better  unless something else changes. What that &#8220;something else&#8221; is seems above my pay grade.

---

### Post by Wadcutter on 2016-06-23
Updating to 14.04 gave me a new Grub menu, but allowing it to just boot to the new 14.04 kernal (4.2-27, I think) resulted in the monitor screen shutting down AGAIN. Tried again, but this time reverted to a previous version (3.2-99). It booted into 12.04 with an incorrect resolution (1280 X 10 xx—don’t have any of these numbers in front of me, but you get the idea). I could see at least parts of my old desktop enlarged.

  I then tried to copy some files that missed my routine backup to a thumb drive, but there was no thumb drive. The system would not recognize one. Plan B: I was finally able to get into a terminal, so  I entered “sudo apt-get install nvidia-current-updates”. It did that, installed a new driver and after reboot, I am now in a 14.04 kernal with a 14.04 desktop at the correct resolution for my wide monitor (1920 X whatever). The monitor is no longer going black when I attempt to boot.

  All previous attempts to install a new driver had failed because I never had a working terminal in front of me, but was trying to do it from the command prompt that I got from using the recovery menu. That prompt apparently didn’t recognize me as a valid user or some such thing and every attempt to install a Nvidia driver resulted in error messages.

  Everything is NOT fine now, but I, at least, have a terminal window that I can work with. 14.04 has trashed half of my applications including KeePass and my VPN. Worst of all, thumb drives still don’t work. I am going to start a new thread to deal with the thumb drive issue and any other things I can’t fix, but I did want to conclude this thread with what little knowledge I’ve gained and hope it might help someone else.

---

