---
title: "Unable to bring up 64-bit Desktop in trial mode"
date: 2008-06-02
forum: Desktop Environments
---

### Post by DBell5 on 2008-06-02
I downloaded and burned a CD of Desktop 8.04 this weekend, for my HP Athlon 64-bit dual-core PC. Before full installation, I want to test it in live boot trial mode.

When I boot from the CD, the kernel loads, all the boot graphics come up normally, the startup music plays, and the login screen shows, with "User Ubuntu will log in in ... seconds."

But when I let the timer run out, the system restarts, monitor shows 'no signal', and it repeats the same cycle indefinitely.

I checked the CD for integrity, and even burned another copy at slower speed (16X minimum for this drive under XP), but still the same.

Are there any known issues with particular hardware, or any other suggestions?

Thanks!

Dave

---

### Post by overdrank on 2008-06-02
> **DBell5 said:**
> I downloaded and burned a CD of Desktop 8.04 this weekend, for my HP Athlon 64-bit dual-core PC. Before full installation, I want to test it in live boot trial mode.

When I boot from the CD, the kernel loads, all the boot graphics come up normally, the startup music plays, and the login screen shows, with "User Ubuntu will log in in ... seconds."

But when I let the timer run out, the system restarts, monitor shows 'no signal', and it repeats the same cycle indefinitely.

I checked the CD for integrity, and even burned another copy at slower speed (16X minimum for this drive under XP), but still the same.

Are there any known issues with particular hardware, or any other suggestions?

Thanks!

Dave

Hi and I see you check the cd for errors but you may check the MD5SUM
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by DBell5 on 2008-06-02
> **overdrank said:**
> Hi and I see you check the cd for errors but you may check the MD5SUM
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I'll check that this evening, certainly worth a try.
If the download checksums, the CD test OK, and write speed is reasonably low (and I'm booting from the same drive that wrote it!), where should I go from thee?

Thanks,

Dave

---

### Post by overdrank on 2008-06-02
> **DBell5 said:**
> I'll check that this evening, certainly worth a try.
If the download checksums, the CD test OK, and write speed is reasonably low (and I'm booting from the same drive that wrote it!), where should I go from thee?

Thanks,

Dave

If it were I, would change locations of download iso and then may try the 32 bit.

---

### Post by DBell5 on 2008-06-02
> **overdrank said:**
> If it were I, would change locations of download iso and then may try the 32 bit.

I have a second download, from a different mirror site.
I'll MD5 both, for comparison. Haven't burned the second one to CD, yet.

I never thought to try the 32-bit version! Should it work, as backwards-compatibility?

Thanks!

---

### Post by DBell5 on 2008-06-03
> **DBell5 said:**
> I have a second download, from a different mirror site.
I'll MD5 both, for comparison. Haven't burned the second one to CD, yet.

I never thought to try the 32-bit version! Should it work, as backwards-compatibility?

Thanks!

Well, I have:
* Verified MD5 sums
* Re-burned
* Downloaded from another mirror site
* Verified CDs
* Finally, even installed the 32-bit Desktop, "inside" Windows, with Wubi

In every case, I get the same result - Ubuntu will boot, the logo graphic and startup music will come up, and the sign-in page displays.
When I sign in (either by letting a bare install auto-log as "Ubuntu", or sign in with the username and password I set up for Wubi), the Heron graphic doesn't come up; instead, the spinning dot works for a second, the screen blanks, and Ubuntu boots again, or returns to the login. (It even recognizes un:pw correctly, as it will reject a wrong one.)

Is there possibly some hardware problem that could be causing this? I did run at least 5 minutes' worth of the extensive RAM test from the boot menu once, with no errors. XP has been  running for over a year with no real problems (sluggish, but what's new?, and possibly hijacked as a spambot at least once or twice). Could the hardware simply be incompatible with Ubuntu?!?

(Ref: HP small form factor desktop, Athlon 64-bit dual core, 1GB RAM, 160 GB HDD with 120 free, defragged and partitionable...)

Still puzzled, and very frustrated,

Dave

---

### Post by overdrank on 2008-06-03
Ok I am at a loss so what is the model of the graphics card? Have you tried to boot into recovery mode? When you are prompted to boot either windows or Ubuntu, press the esp key and choose recovery mode then login with user name and password. Then try the command startx

---

### Post by DBell5 on 2008-06-03
> **overdrank said:**
> Ok I am at a loss so what is the model of the graphics card?

I don't recall; it's embedded on the mainboard.
Basic video functions seem to be working correctly, as I have seen it all the way to the Heron desktop (but not to the point the menu bar displays.)

> **overdrank said:**
> Have you tried to boot into recovery mode? When you are prompted to boot either windows or Ubuntu, press the esp key and choose recovery mode then login with user name and password. Then try the command startx

I'll try that tonight. Hopefully, I can do that from the live CD boot?
I really don't feel like yet another install...

Thanks!

Dave

---

### Post by overdrank on 2008-06-03
> **DBell5 said:**
> I don't recall; it's embedded on the mainboard.
Basic video functions seem to be working correctly, as I have seen it all the way to the Heron desktop (but not to the point the menu bar displays.)



I'll try that tonight. Hopefully, I can do that from the live CD boot?
I really don't feel like yet another install...

Thanks!

Dave

Hi and no that will not work from the live cd. The direction I gave is from the install. The only time I have encounter that time of issue with the login screen from the live cd is a bad disc. But you have ruled that out.

---

