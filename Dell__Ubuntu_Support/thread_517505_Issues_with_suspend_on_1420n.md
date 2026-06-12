---
title: "Issues with suspend on 1420n"
date: 2007-08-04
forum: Dell  Ubuntu Support
---

### Post by lynchman on 2007-08-04
One thing that is the 'most broken' with my 1420n + Ubuntu is resuming from suspend.  I have the laptop set to suspend whenever the lid is closed and running on battery OR AC power.  

I've noticed that about 60% of the time it resumes correctly.  However there are times where when it resumes and prompts me for my password it will just lock - mouse and keyboard.  If I let it sit for a minute and then close the lid again so it suspends, and wake it back up it sometimes works (about 50% of the time in this instance).  Other times it is still locked and I'll just have to force a reboot.

When I am able to resume correctly, I've noticed that my password almost always fails the 1st time.  I used to think that I just mis-typed it, but it happens too often for that.  I wonder if it is because I'm using a non-default keymapping (dvorak) and maybe the first time it doesn't load the right mapping?  I dunno - just a thought - it is hard to tell since the password is masked.  :)

I've also noticed some weird behavior when returning from hibernation.  It is usually fine, but once it is back sometimes I cannot hibernate again for a second time.  I don't hibernate that often so I haven't figured out if there is a pattern yet or not.

Also, whenever I successfully resume I get an error that the Volume Control applet needs to be restarted.  It's not really that big a deal but annoying.

Anyone else experience this / have any solutions? 

Thanks!

---

### Post by notwen on 2007-08-04
+1 for having similar difficulties

---

### Post by notwen on 2007-08-06
I'm not having too many issues w/ suspend, but hibernate often results in my 1420n shutting completely down or not returning to active state once I open it up again or hit a key.  My suspend does come up w/ the password prompt and sometimes it does not accept it on the first attempt to log back in, but my main concern is getting the hibernate function to work properly.  Some discussions here on the forum state that hibernate/suspend work fine out of the box, but not for me.  Anyone else having better luck w/ the suspend and/or hibernate functions on their Dellbuntu Inspiron 1420n ?

---

### Post by strabes on 2007-08-09
Maybe try [url=http://ubuntuforums.org/showpost.php?p=2690982&postcount=14[/url]this procedure?

---

### Post by notwen on 2007-08-09
This looks to be a fix for returning from Suspend, my suspend seems to be working properly while Hibernate will just shut the laptop down completely.  Any other ideas? =]

---

### Post by Mach1US on 2007-08-09
This one has fix it for me 100% in both counts.
[http://ubuntuforums.org/showpost.php?p=2690982](http://ubuntuforums.org/showpost.php?p=2690982) &postcount=14[/url]this procedure?

---

### Post by sciurus on 2007-08-10
> **lynchman said:**
> 
  However there are times where when it resumes and prompts me for my password it will just lock - mouse and keyboard!

The same here.

---

### Post by munozdj on 2007-09-10
Hi, I´m in an inspiron 1520, and when it enters in suspend mode, it doesn´t come back, it doesn´t even turn the screen on. Any ideas on what´s happening?
Running kubuntu feisty with an nVidia GeForce 8600M
Thanks!

---

