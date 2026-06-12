---
title: "Breezy - Very strange suspend (to RAM) problem"
date: 2005-10-17
forum: Desktop Environments
---

### Post by tbraun on 2005-10-17
Hello!

I upgraded from Hoary to Breezy, and suspend to RAM is actually working now on my HP Compaq nc6000 laptop. Yeah! Well, almost...

Suspending and coming back is fast, and seemed to work every time. However, I then discovered that it does not come back up when it was suspended for a longer period of time! How strange is that?

So, if I suspend it for a few minutes, everything will wake up and restore, no problem. If it is suspended for half an hour or longer (I did not measure exact times, but that's a rought impression), then it will not come back.

In that latter case, what happens is that I press the powerbutton briefly to get the compputer to wake up again. The disk briefly spins up, as it always does when the computer wakes up. But then, instead of a login prompt, the screen just remains completely black. Even entering the password into the 'dark' does not cause any further activity, so there is more going on than just the screen being turned off.

I was wondering if it might have to do with the power-saving options in the screensaver, and some weird timing issues when the screen comes back on. So I disabled all power-saving stuff, but it does not make a difference.


Help!

Tom

---

### Post by zenodaddy on 2005-10-17
I have had the same problem. If the screen saver comes on for more than 30 minutes the system will just hang. Alt+Ctrl+Backspace doesn't kill the server and always has to reboot. I figure tonight I will just kill the suspend option and see if that controls the issue, if not then I am guessing it is an issue with my ATI 9200 drivers

---

### Post by grj on 2005-10-17
I have the same problem with a Toshiba that has an NVidia card. If I close the lid it will keep it from going into the coma.

---

### Post by tbraun on 2005-10-17
Closing the lid, or keeping it open does not make a difference. The behavior always stays the same. Also, in my case, I can keep the screensaver on for a long time, and I don't have the problem. It's just when i try to wake up from suspend after more than just a few minutes.

So far, we have found out that there are obviously some issues in this area still. I hope that not only people with problems, but maybe also someone with a solution might read this and reply to it...  :-)

Tom

---

### Post by kashms on 2005-10-17
There were some people in the laptop-testing team with similar problem. They might have a fix.

[http://lists.ubuntu.com/archives/laptop-testing-team/2005-October/thread.html](http://lists.ubuntu.com/archives/laptop-testing-team/2005-October/thread.html)

---

### Post by zenodaddy on 2005-10-19
The issue was with the built-in graphic drivers inUbuntu.. I downloaded the latest Linux ATI drivers and once installed and fglrxconfig was ran it works perfectly..

---

