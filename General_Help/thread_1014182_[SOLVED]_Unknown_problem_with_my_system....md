---
title: "[SOLVED] Unknown problem with my system..."
date: 2008-12-17
forum: General Help
---

### Post by xeriouxi on 2008-12-17
Hi!

I have a problem with my system that's just randomly occured and I can't figure out why.

The bookmarks in my 'Places' menu have all gone, Firefox lost its bookmarks (though when I tried it a little later on it seemed to work fine for one session) and some of my applications are just not starting up at all (though one of them did start up at one point when Firefox started to work again, I think) and this happens if I select the application using the Gnome menu or I try and run it using Alt+F2, so it might be a (frequent) random sporadic issue of some sort, perhaps?

Does anyone have any ideas as to why this has happened all of a sudden? Any information is much appreciated! I'm currently running on my Windows OS (dual-booting on a seperate HDD) until I can try and find out what's wrong with Ubuntu.

Thanks! =)

---

### Post by Sam Lars on 2008-12-18
This sounds like a problem with your /home directory... have you done anything that would have affected that?
Try running the programs from a terminal and see if they give any info on why they won't start.

---

### Post by xeriouxi on 2008-12-19
Thanks for your reply, Sam Lars!

I booted back into Ubuntu before and the 'Places' bookmarks seemed to have come back, and Firefox seemed to be working okay. I tried running Transmission (one of the applications I couldn't get to work) via the terminal and it came up with an error relating to the settings.json file in the .config/transmission folder. It turns out that the file was 0 bytes for some reason. I made a backup of the .config folder (incase there were any other programs in there that had strangely suffered from what Transmission had) and then deleted .config/, hoping that the system would create a new one and be able to still run okay and then I restarted the system. It all seems to be working fine now! I guess that the settings.json file (and some other file(s) somewhere because of the other problems with Firefox etc.) got corrupted somehow but I guess the system managed to recover the bookmarks for Nautilus and Firefox by itself. Letting the system create a new .config folder seemed to sort out the applications. I can't remember if I found any other issues than the ones that I mentioned in my first post but everything, as said, seems to be running as it should be.

I noticed an entry for 'Control Centre' in my 'System' menu and also that all of the Wine applications I had installed had been moved to 'Other' in the 'Applications' menu, but after restoring the 'menus' folder in my backup of .config/ it seems to have been restored to its normal state again without any issues. Thanks for your push in the right direction! =)

---

