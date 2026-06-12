---
title: "Disk thrashing, unresponsive, dead!"
date: 2009-04-27
forum: General Help
---

### Post by vaughany on 2009-04-27
Hi all. Been getting into Intrepid when Jaunty arrived, so upgraded (Friday) without probolems.

Today, after about an hour AFK, I come back to find the computer won't wake up (set to screen saver after 10 mins and low power mode after 20) and the disk is being thrashed like mad. I push all the usual keys to wake it up on both the laptop keyboard and the 'external' keyboard and wobble the mouse and still no good. :confused:

I press and hold power button (I didn't know about the SysRq key combos at this point), shut it off and then power up again, and now it freezes when booting, way before I have to log in. Recovery mode is broken too. :!:

I can't do a lot with the system as it was installed using Wubi and I can't find a way to mount the 30gb file as a drive within Windows.

Any and all ideas appreciated.

---

### Post by aikiwolfie on 2009-04-27
have you tried running chkdsk?

[https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu]("https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu")

---

### Post by aikiwolfie on 2009-04-27
> 
Any gotcha?

Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.

[http://wubi-installer.org/faq.php]("http://wubi-installer.org/faq.php")

---

### Post by wolfen69 on 2009-04-27
how old is your computer? could be a bad hard drive.

---

### Post by vaughany on 2009-04-28
> **aikiwolfie said:**
> have you tried running chkdsk?

[https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu]("https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu")
Thanks for reply. Windows error checks reported no errors and nothing else worked, so I gave it up for dead and reinstalled it. Now it's on a seperate partition and not via Wubi, which should make life easier.

---

### Post by vaughany on 2009-04-28
> **wolfen69 said:**
> how old is your computer? could be a bad hard drive.
Good point. The lappy is <18 months old and I'm very aware of how much stress a breaking hard drive can cause (I had 3 go on me last year!) so I'll keep an eye on it. Suggestions for a good hard-disk housekeeping utility most welcome!

---

### Post by vaughany on 2009-04-28
> **aikiwolfie said:**
> [http://wubi-installer.org/faq.php]("http://wubi-installer.org/faq.php")
Yeah, I know that now! :)

Thankfully I have a very open minded employer who is happy with me 'experimenting' with Linux. Thanks for the reply.

---

