---
title: "Suspend, Hibernate and WOL woes"
date: 2009-02-08
forum: General Help
---

### Post by BuntuFreak on 2009-02-08
What is the difference between Suspend and Hibernate. In windows, I understood, "Put the computer to sleep", i.e. it suspended (or did it hibernate?) after the specified number of minutes. I simply press the Power button and I'm back in action.

So now, I'm trying to do the same thing with my Ubuntu 7.10 Gutsy Gibbon desktop. First, when I'm at the Logon screen, Options->Suspend does JACK. It asks me a question, "Do you want to Suspend". I say (H***) Yes. And it effectively shows me the middle finger, i.e. doesn't do anything, just sits at the Logon screen.

When I'm logged on, and hit the "Running Man" on the top right corner of my desktop which gives me so many good options, like "Suspend" and "Hibernate", I select "Suspend". My display blanks out, then suddenly I get a dialog box prompting me for my Password and 4 options : Leave Message, Switch User, Cancel, Unlock.

I don't want to leave no message. I'm the only user. Cancel simply cancels my intent. Unlock? WTF? Before I can select any of these options, I have to enter my password, but it does diddly squat. ](*,)

How in heaven's name do I get my computer to suspend? I will not ask anything about Hibernate yet? I assume it is more "radical" than suspend. I'll be happy with the power saving Suspend will give me for now. Assuming I can get it to work. :???:

Dunno if this has anything to do with my hardware. I have an old intel board. I went to BIOS and enabled "Wake up on LAN" and "Wake up on PME" options. The idea of course is to "unsuspend" my computer when another computer on my network accesses my shared drive.

This seems so basic, I'm ashamed of myself for not being able to figure out. Someone please oblige and set me straight.

---

### Post by camper365 on 2009-02-10
When you Suspend (sleep or Stand By) you are keeping the computer on, but running on minimal power (very minimal, my battery that normally lasts 2 hours lasted 12 on Suspend)
When you hibernate, everything on your RAM is copied to your hard drive (I think your swap space) and your computer turns off completely, running on no power. When you turn it back on, if you boot the same operating system that hibernated, it puts the hibernation file back on the RAM and all your files and programs are open, just as they were before you hibernated.
It probably is just that your motherboard is old, a lot of old ones have problems waking up from suspend.
Are you using a laptop or a desktop?

---

### Post by BuntuFreak on 2009-02-14
> **camper365 said:**
> When you Suspend (sleep or Stand By) you are keeping the computer on, but running on minimal power (very minimal, my battery that normally lasts 2 hours lasted 12 on Suspend)
When you hibernate, everything on your RAM is copied to your hard drive (I think your swap space) and your computer turns off completely, running on no power. When you turn it back on, if you boot the same operating system that hibernated, it puts the hibernation file back on the RAM and all your files and programs are open, just as they were before you hibernated.
It probably is just that your motherboard is old, a lot of old ones have problems waking up from suspend.
Are you using a laptop or a desktop?

I'm using a desktop. It's a Intel Motherboard with PIII 800 MHz and 512 RAM. The BIOS does have those settings for WOL.

My problem is not waking up from Suspend. My problem is I cannot get it to suspend in the first place. Any ideas?

Thanks.

---

