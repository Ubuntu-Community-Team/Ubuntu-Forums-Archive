---
title: "Hardy: ACPI Issues (Why is this still such an issue?)"
date: 2008-12-10
forum: General Help
---

### Post by chez17 on 2008-12-10
I have had this issue for months and months and have spent countless hours tinkering to get this to work. All I want to do is boot my computer. I get the usual "file DSDT.aml not found" error. There are a bunch of threads on the forums that address this but not one has fixed this. I am using a Thinkpad T60 and I can't figure this out. I would really really appreciate it if someone could help me out.

I have tried everything.

If I use acpi=off then my mouse doesn't work and my computer is extremely slow.

If I use apm the computer shuts down randomly

I have used options like nolapic_timer which seems to work sometimes. Just out of curiousity, how is it possible for it to work sometimes. Isn't it booting from the same sequence every time? Why does it not find the file sometimes and find it other times?

As I said, any help is most appreciated by me and the many others who have this same issue, if you solve this, I will name a country after you when I rule the world.

---

### Post by chez17 on 2008-12-11
Anyone?

---

### Post by sdennie on 2008-12-11
I'm not sure what you are trying to fix.  Are you just trying to get rid of the error message or does your machine not work correctly unless you use certain boot options?

---

### Post by chez17 on 2008-12-11
Yea, my computer won't boot. And that's the frustrating thing. In the bug reports you have devs saying it's not a bug, and the issue is closed because they say the message is harmless. But I can't boot because of it, it says it can't find the DSDT.aml file. I have literally tried every option I can think of or have come across and nothing works. I know many other people have this issue and certain solutions have worked for certain people, but I just can't figure this one out.

---

### Post by sdennie on 2008-12-11
That error message actually is harmless.  The Ubuntu kernel is patched with a DSDT patch for people that may need to load custom DSDT tables to get their machine to work.  If a custom DSDT table hasn't been installed into your init image (and, it's very rare for someone to need to do this), you'll get that error message but, it's not actually an error.  Just a poorly worded status message.

Having said that, your problem may be ACPI related and so fixing your DSDT may actually be the solution (and would have the side effect of getting rid of that error).  It's not trivial to do but, google for "fix dsdt" and read about it.  Before doing that though, see if there is a BIOS update for your machine.  A custom DSDT is similar to fixing the BIOS and so a BIOS update may fix your problem without having to go through all the pain.

---

### Post by lswb on 2008-12-11
Your boot problem is likely not related to the DSDT.aml error message. Probably most systems have that message at boot. DSDT.aml is an (optional) file that can be installed in the initrd.img to patch a running BIOS at boot, so the OS will use the patch code rather than the code that is flashed into the computer ROM. (From my limited understanding; you can find more info about this with google)

Have your tried [http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki) ? There's lots of good info about thinkpads and linux on that site.

---

### Post by chez17 on 2008-12-12
"That error message actually is harmless."

This is what is frustrating. This message is not harmless, in fact, it's the most harmful issue any computer can have. My computer won't boot because of it. What could be more harmful than that?

I will keep looking but I doubt I will find anything new. I have googled the error many times and I still can't find a solution. I will post a solution if I find it.

---

### Post by sdennie on 2008-12-12
> **chez17 said:**
> "That error message actually is harmless."

This is what is frustrating. This message is not harmless, in fact, it's the most harmful issue any computer can have. My computer won't boot because of it. What could be more harmful than that?

I will keep looking but I doubt I will find anything new. I have googled the error many times and I still can't find a solution. I will post a solution if I find it.

No, the error message is actually 100% harmless.  I would guess that 99% of Ubuntu users would find it in their logs if they looked.  Thinking more about what you've described, I'm almost positive that the problem is a BIOS problem.  That error message appears when the kernel tries to open a custom DSDT (BIOS) that you've provided it and one doesn't exist.  That itself is not even slightly fatal but, the next thing it tries to do is load the actual DSDT that your machine has sitting in hardware.  As such, it would appear to you as if that error message was causing the problem but, in reality, it's the loading of the DSDT that's in hardware that is the problem.

I again recommend trying to upgrade the BIOS or, if you are completely up to date, using one of the methods you described above to get into the machine and then following my advice to fix your DSDT.

---

### Post by chez17 on 2008-12-12
Here is a thread that talks about this issue for Acer laptops, but it is an intel machine. Is it safe to try and install this DSDT file on my computer(Thinkpad T60)? Could you take a second and look?

[http://ubuntuforums.org/showthread.php?t=609925](http://ubuntuforums.org/showthread.php?t=609925)

Thanks.
Dave

---

### Post by chez17 on 2008-12-12
So I found some ways to take my DSDT file, deconstruct it, recompile it, and grab the DSDT.aml file. I did that and put the file where it told me to. Now when I boot I get a the error

"ACPI: DSDT override uses original SSDTS unless "acpi_no_auto_ssdt"

If I put that in my kernel boot line I get:

SSDT ignored due to "acpi_no_auto_ssdt"

I just can't win with this. Of course any help is most appreciated. I've been struggling with this for months, please don't tell me these errors are harmless, my sanity depends on it.

---

### Post by kerry_s on 2008-12-12
are you sure it's not a bad install/burn?
have you tried the check cd option?

---

### Post by markbuntu on 2008-12-12
ACPI is not properly implemented by many OEMs and vendors and they are not telling. That is why there are so many problems with it.

---

