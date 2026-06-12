---
title: "Help!"
date: 2009-05-13
forum: General Help
---

### Post by Geekkit on 2009-05-13
Sorry for cross posting but in recent days I've posted requests for help in the other forum rooms and have had no responses - this room seems to always answer questions.

======================================================
I just did an upgrade (auto updates) in 8.10 and unfortunately I didn't read what the updates were. Anyways it asked to restart and I did and now after seeing the 8.10 status bar showing OS loading, it shows a screen with garbage graphics on it and then it goes blank and freezes.

I've tried booting in safe mode with kernel 2.6.27-14, 2.6.27-11, and 2.6.27-7 and I still get the frozen screen. I tried to use the menu options to "fix packages" and "fix xorg" but none of those options worked either. I've also typed:

sudo dpkg-reconfigure -phigh xserver-xorg

But it still doesn't boot up properly and displays junk on the screen in some sort of graphics mode. The barrage of status text at boot time is hard to read but one thing that I did notice was that Virtualbox reported to have "failed!". I just got this system going last week after removing 9.04 due to problems with it.

I've even tried and sudo rm -rf ~/.config ... but didn't work.

I'm really at the end of my rope and patience for Ubuntu and Linux in general here since I just spent the last week purging 9.04 which, at first, seemed to work but then caused all kind of problems like CPU fan running at full tilt, loading wrong printer drivers, suspend/hibernate not working, compositing not working, Skype not working, Amarok not working, and a bunch of other issues. I really want to use this OS but I simply cannot be reinstalling every week when things break like this.

If you've not come across this problem and you're reading this, is there another distro that you would recommend that doesn't break when performing updates and that offers users stability?

---

### Post by upbeat.linux on 2009-05-13
Sounds like you should salvage your files, wipe your drive, and reinstall from there.  That might save you a few head aches.

If you're getting a command prompt you may want to try:

```
sudo apt-get clean
sudo apt-get update
```

Removing gnome, xserver, its dependencies, cleaning apt, and then reinstalling might help.

How did you down grade from 9.04 to 8.10?

If you can post a copy of your [dmesg]("http://www.linfo.org/dmesg.html") output in this thread:

```
dmesg > boot.messages
```

or just cut and paste:

```
dmesg
```

if you can't scp the file anywhere.

I do understand your frustration, but I don't think you should look for a new distribution but rather seek out the appropriate sources to help guide you in troubleshooting this issue.

---

### Post by Geekkit on 2009-05-13
> **upbeat.linux said:**
> Sounds like you should salvage your files, wipe your drive, and reinstall from there.  That might save you a few head aches.

If you're getting a command prompt you may want to try:

```
sudo apt-get clean
sudo apt-get update
```

Removing gnome, xserver, its dependencies, cleaning apt, and then reinstalling might help.

How did you down grade from 9.04 to 8.10?

If you can post a copy of your [dmesg]("http://www.linfo.org/dmesg.html") output in this thread:

```
dmesg > boot.messages
```

or just cut and paste:

```
dmesg
```

if you can't scp the file anywhere.

I do understand your frustration, but I don't think you should look for a new distribution but rather seek out the appropriate sources to help guide you in troubleshooting this issue.

upbeat.linux, thank you very much for your response (this forum room is always the one to turn to :)

Anyways, I did look through the logs but I did not see anything funny. I`ve since reinstalled 8.10. As for your question, I didn`t downgrade from 8.10 to 9.04 with some auto feature, I simply wiped the drive by reinstalling.

I think this 8.10 install is going to be a "no frills" install: no compiz, no extra drivers, very plain with some devel software. I will be checking updates to watch and see what gets updated. However, if this breaks again I really don`t think I can handle another Ubuntu Linux install since doing so eats up too much time and I don t remember XP being this much of a headache. 

Anyways, thanks again for your help and time, much appreciated.

---

### Post by Ericyzfr1 on 2009-05-13
Did you experience any issues with 804? Granted you were using it?

---

### Post by Geekkit on 2009-05-13
> **Ericyzfr1 said:**
> Did you experience any issues with 804? Granted you were using it?

Ericyzfr1: A few but there were workarounds (wireless was a bit of an issue). I'll see if 8.10 works and then (as you've implied) try to revert back to 8.04 for a safety net, thanks.

---

### Post by bodhi.zazen on 2009-05-13
Moved to general help :)

---

### Post by Geekkit on 2009-05-13
> **bodhi.zazen said:**
> Moved to general help :)

Thanks but the last few times I posted in this forum no one responded.

---

### Post by bodhi.zazen on 2009-05-13
> **Geekkit said:**
> Thanks but the last few times I posted in this forum no one responded.

Yes, sometimes you are asking a question and not immediate answer is available.

Best just wait, we do have an unanswered posts team to look into these more difficult threads.

Crating multiple threads or bumping *sometimes* gets results, but more often creates confusion and duplication of effort.

It is a fine line between bumping because you need help (legitimate bump) and bumping too often (perceived as rude).

---

### Post by upbeat.linux on 2009-05-14
Before doing anymore installs I would take a good look at your hardware then check the compatibility list:

**_[https://wiki.ubuntu.com/HardwareSupport/]("https://wiki.ubuntu.com/HardwareSupport/")_**

I had quite a few hardware issues with 7.10 that were resolved in 8.04.

---

