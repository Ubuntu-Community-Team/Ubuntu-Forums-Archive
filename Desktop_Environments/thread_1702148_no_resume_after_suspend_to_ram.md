---
title: "no resume after suspend to ram"
date: 2011-03-07
forum: Desktop Environments
---

### Post by holmziep on 2011-03-07
Have Ubunto 10.10 from a Live CD and  receive updates regularly.  Standard Dell keyboard with no suspend or resume buttons.

After much looked and searched here and on the net, seems most similar problems were in reference to laptops, or for different distributions or previous versions of Ubuntu.

This is a revived Dell dimension 8300, 1 gig ram, Ubuntu drive installed at primary master PATA  position, video: Nvidia FX5200 , Ubuntu updated video driver to 173,13.28.  Have an XP system hard drive in primary SATA postion,   I can change boot by selecting hard drives.  Ubuntu runs GREAT but for the RESUME from suspend to ram.  Need to hold the power button down for 8 seconds to start over or set power management to "NEVER".   Light (num lock) on keyboard but can't change Caps Lock, mouse buttonsunresponsive, optical light off, ACPI works fine in WIN XP.  

I am a beginner, but learned to use terminal to do a bunch of things so far, like gedit to change clock to LOCAL TIME vs UTC so my clocks read the same on both XP and Ubuntu.  

I did try something I saw in one of the threads, by adding this command to the grub:
GRUB_CMDLINE_LINUX="acpi_sleep=nonvs" that didn't work so I changed it back. 

I also ran "quirk-checker.sh" from Launchpad Librarian, and came up with a message, "***CRITICAL ERROR: Using nvidia binary driver. This is not supported!***"

I had read that video drivers can cause trouble, but I don't exactly know what the above means.  I now noticed the fancy 3D desktop curser "blooms" and other 3D changes after the driver was updated, but that stuff I can do without and I don't run games in Linux.  I really think I had this problem BEFORE any update, thought I can't be sure.  I fixed it in XP first after just fusing with it.

I did read, "**HowTo: Debug Suspend, Resume, Hibernate issues"** and started the recommendations, but stopped after the because I noticed the date 2008 and the references didn't match what was on my screen.  Though I must say it was similar...hmmm...

I am a beginner, but I may be capable, with your kind patience, to carry out your suggestions and be your eyes and fingers.  I appreciate any help I can get.   I hope to contribute in one form or another when I get a job or just get better.

Thanks!
holmziep  N2EXG

---

### Post by holmziep on 2011-03-07
I have since re-posted this message to a more appropriate location (?) at the **[[B]Dell Ubuntu Support**]("http://ubuntuforums.org/forumdisplay.php?f=342")[/B] forum, I guess this was the wrong place?  someone help me out here?!?
like I said, I'm a beginner.

---

