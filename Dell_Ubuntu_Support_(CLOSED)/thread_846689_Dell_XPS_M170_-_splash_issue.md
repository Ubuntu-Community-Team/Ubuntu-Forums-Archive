---
title: "Dell XPS M170 - splash issue"
date: 2008-07-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by t3hparad0x on 2008-07-01
Foreward: I've attempted to check all forums I can to find this issue and resolve it but have failed to find any worthwhile. Hence: I'm making this post... and yes I am a n00b to Ubuntu/Linux in general.

Laptop: Dell XPS M170 - Fresh Install - Ubuntu 8.04 Hardy (only)
NO tweaks to resolution, drivers, etc... only basic updates downloaded and installed.

Problem: Upon booting into Ubuntu, splash screen displays terribly. It's stretched horizontally across the screen, and doesn't appear to be following any specific resolution. The splash isn't discernable as anything more than multiple colors stretched. It appears choppy, cut up in even strips, and fileted for my screen... like shreaded paper strands. Terrible. This is also displayed the same when logging off.

I have thought the drivers may have been out-dated, but Ubuntu appears to have updated those during the "update" process run through the terminal. 

If anyone has any suggestions, please feel free to response.

---

### Post by csa3d on 2008-08-13
I am having a similar issue on the exact same kind of setup.  Is there a config file or some place where you can set the resolution of the ubuntu splash logo screen?  The issue looks as though the splash screen is using a resolution the laptop doesn't support, and therefore becomes distorted beyond readability.

Thanks
-csa

---

### Post by csa3d on 2008-08-14
So doing a search, I ran across [http://ubuntuforums.org/showpost.php?p=3447061&postcount=18]("http://ubuntuforums.org/showpost.php?p=3447061&postcount=18") which talks about adding a "Modes" section to your xorg.conf file to correct this issue.

I thought I remember reading however, that the splash screen is not 24bit, that it was 16?  Can anyone confirm

1.  That editing the xorg.conf to include screen resolution and modes is actually going to affect the splash screen

and

2. What screen depth do we actually need to worry about configuring if this is indeed the fix.

Thanks!
-csa

---

### Post by Dennis N on 2008-08-14
You might try installing the startup manager package. My Ubuntu splash screen was left justified and 640 x 480 on a pre-installed Ubuntu (maybe because I did not buy a monitor with the system (desktop) and it could not be set up by Dell). Startup manager found the possible resolutions, and configured the usplash to be centered.

---

### Post by csa3d on 2008-08-15
> **Dennis N said:**
> You might try installing the startup manager package. My Ubuntu splash screen was left justified and 640 x 480 on a pre-installed Ubuntu (maybe because I did not buy a monitor with the system (desktop) and it could not be set up by Dell). Startup manager found the possible resolutions, and configured the usplash to be centered.

Thanks for this suggestion, it worked perfectly!

---

