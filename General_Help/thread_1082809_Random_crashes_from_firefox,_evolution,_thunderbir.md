---
title: "Random crashes from firefox, evolution, thunderbird"
date: 2009-02-28
forum: General Help
---

### Post by Rackstar on 2009-02-28
Hi everyone,

I have been using ubuntu for over a year now, and I really love it, but sometimes it's tough-love.

At a certain point Evolution started to crash randomly. Just after an undefined amount of time it closes with no errors. Then I switched to Thunderbird, but surprise, surprise, same thing happens.

Firefox also crashes randomly with no errors, mostly on big websites (like facebook).

Last week I had to reinstall ubuntu due to some messing around with nvidia drivers. Thinking that the random crashes would also stop. But it didn't.

I have my /home/ on a different partition, I did not format this partition, only the one with ubuntu.

The only connection I see, is that they all need connection to the internet. Firefox and Thunderbird both being from Mozilla.

I'm not a linux-expert, but really interested. Does anyone have an idea?

I'm running ubuntu 8.10 on a Acer Aspire 9423.

I tried doing dmesg | tail after such crash, but I don't think that in the output there is something useful.

```
[   78.612170] CPU1 attaching sched-domain:
[   78.612176]  domain 0: span 0-1 level MC
[   78.612182]   groups: 1 0
[   87.408900] iwl3945 0000:05:00.0: PCI INT A disabled

```

Thanks!

---

### Post by Mayfairy on 2009-02-28
I'm doing a linkback here. :D 
You just linked this topic on another thread I had answered. What struck me is that you also mentioned Facebook here, which I suspect is at least a part of my problem.

EDIT: Oh, the link: [http://ubuntuforums.org/showthread.php?t=1082766](http://ubuntuforums.org/showthread.php?t=1082766)

EDIT: Desktop effects don't seem to matter. I have them on normally except when I'm playing something when I turn them off. Crashes occur on both.

---

### Post by Exile29 on 2009-02-28
Most posts about this issue (which I am experiencing as well running Heron) seem to blame Adobe Shockwave. I don't know... I've completely removed Shockwave and reinstalled it several times but that hasn't fixed the problem. I've got a laptop running Heron and I've never had it crash on me. The only difference is that I have desktop effects turned off on my laptop.

---

### Post by Rackstar on 2009-02-28
Thx for the reply. I do not have shockwave installed (or do you mean flash?) and desktop effects are off.

I do have the lightning plugin on TB and a plugin to hide TB in tray. But the crashes of TB, FF and evolution seem related some how. 

TB can crash up to 10 times a day, (today is rather a good day, with only 4 crashes). FF can crash every 5 minutes while heavy browsing. Not using evolution no more, but it was quite the same as TB.

But you can understand it drives me insane sometimes.

Is there a way to trace the problem?

Thanks

EDIT: make that 7 crashes today.

---

### Post by Rackstar on 2009-03-01
Another morning, another two crashes. Somebody?

---

### Post by Rackstar on 2009-03-01
Bump, three crashes later...

---

### Post by Rackstar on 2009-03-01
I tried to make a new profile for firefox by renaming the .mozilla folder, then it creates a new one. But same stuff happens. It only crashes when changing pages.

I reinstalled the flash-plugin, but I doubt that it's the fault of the flash plugin.

Further still a lot of TB crashes. TB crashes quietly.

Any help would be hugely appreciated.

Thanks!

---

### Post by Ben Crisford on 2009-03-01
Have you bug-reported this yet?

If not then doing so would be very helpful to the development team.  Visit this link for a guide to reporting the bug and links to the appropriate launchpad page: [http://www.ubuntu.com/community/reportproblem](http://www.ubuntu.com/community/reportproblem)

If you do still need to report this as a bug then try and make sure your post is complete.  I am a member of the bug-squad, and I get 1000 emails per day of reports to check that they are valid (obviously im not expected to do the, all myself, there are around 2000 bug-squad members) but if they are complete it saves so much time for bug squad and bug management team members.

Remember that for your report to be considered it must have:
-The version of Ubuntu that you are running
-The version of the package you are using
-The actions taken to produce the problem
-Whether or not it is possible for you to reproduce the bug
-The expected result of these actions
-The actual result of these actions

Also remember to make your report clear and well worded.  If the same report has been posted by someone else do not post yours, instead go on the existing report and change the status to "confirmed".

---

### Post by Rackstar on 2009-03-01
Thank you! I'll try to do so.
Any other suggestions or workarounds still may be posted here.

---

### Post by jwbrase on 2009-03-01
This is the second such thread I've seen in the last few minutes.

Firefox gave me the same behavior, and I could never get it working. I tried one of the browsers that starts with an E too (I think it was Epiphany, may have been evolution), and had the same trouble.

[Opera]("http://www.opera.com/browser/"), on the other hand, works fine, and I really like some of its features too.

---

### Post by Rackstar on 2009-03-01
Thank you for confirming the FF issue. I filed a bug-report on:
[https://bugs.launchpad.net/ubuntu/+bug/336423](https://bugs.launchpad.net/ubuntu/+bug/336423)

If you could confirm it, it will be noticed.

(Beware that Evolution and TB are not browsers, but e-mail clients)

Thanks!

---

### Post by Rackstar on 2009-03-06
I found a way to reproduce the crash on TB! If I do File->compress folders. (Could be a bad translation, I have mine installed in dutch), it will ALWAYS crash.

Anybody?

---

### Post by Rackstar on 2009-04-12
Got it!

Had to disable WINS resolution in Samba.

See my blogpost for more information:
[http://ninetynine.be/blog/2009/04/fix-random-crashes-firefox-thunderbird-and-evolution-on-ubuntu-810/](http://ninetynine.be/blog/2009/04/fix-random-crashes-firefox-thunderbird-and-evolution-on-ubuntu-810/)

---

