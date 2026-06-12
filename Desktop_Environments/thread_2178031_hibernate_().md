---
title: "hibernate (?)"
date: 2013-10-01
forum: Desktop Environments
---

### Post by dovah on 2013-10-01
Hello! 

I have a little problem when closing the lid of my laptop: in gnome-tweak-tool > shell > laptop lid close action on battery(AC), the "hibernate" action is selected. 

However, when I simply close the lid, it seems that my pc goes "suspend", not hibernate.And, it doesn't require the password on waking up, even if:  in application > system tools > all settings > brightness and lock, the "require my password from waking up from suspend" is selected.
 So I have to either sudo pm-hibernate or hibernate manually before closing the lid, which is quite annoying. In these two last cases, password is required on waking up.

So, do you have any ideas to reach the hibernation state simply by closing the lid (and requiring the password on wake up)? 

Thanks and good evening everyone!

---

### Post by tgalati4 on 2013-10-01
Three things to consider:

1. Some laptops' BIOS have a switch to allow hibernate, so boot into BIOS and look around in the Power Management section.
2. Some laptops require a special partition to write the RAM to disk, typically a hidden partition at the top or bottom of the partition table.  That you will have to research.
3.  You need a swap file or swap partition that is as large (or slightly larger) than your RAM size.  Your RAM gets written to swap as one, giant file.  This file then gets read back when you come out of hibernation to get you back to your work session.  This is also known as *checkpointing*.  

Don't get excited.  It takes just as long to read the hibernation file and wake up as it does to do a cold boot.  So I never use hibernate.  I always use suspend and the wake cycle only takes 3-5 seconds.  The screen lock can be found in your Power Management preferences.

---

### Post by DuckHook on 2013-10-01
> **tgalati4 said:**
> It takes just as long to read the hibernation file and wake up as it does to do a cold boot.  So I never use hibernate.  I always use suspend and the wake cycle only takes 3-5 seconds.

I agree with your observation with only one additional note: it is marginally safer to use hibernate because it writes everything to disk whereas suspend is at the mercy of your battery. I took out a battery once while suspended and lost some work. I know, I know... stupid. But not the first time I've been guilty of stupidity, so now I hibernate. Slightly more stupid-resistant.

---

### Post by dovah on 2013-10-01
I'll try the BIOS way, I know that these new UEFIs seems born to be hacked. 
I'll let you know, and thank you for the anwers. 

(I use the hibernate mode as much as possible, it saves on hd and I feel safer.. then the reboot time is 5secs as well, and battery life is preserved longer!)

---

### Post by ajgreeny on 2013-10-01
There is also a hybrid suspend mode which will start in and then move from suspend to hibernate after a time interval you can set to your own choice.
[Hybrid Suspend Ubuntu]("http://www.webupd8.org/2012/11/how-to-use-hybrid-suspend-in-ubuntu.html")

However, hibernate was removed as an option from ubuntu 12.04 and later as it very often does not work safely on many machines, so you need to check that it does work first (it seems you've already done that).  I did try the hybrid suspend for a while, but it then took a longer time to start-up again from hibernate, so now I don't bother; I go only to suspend, and often do that using a suspend key on my keyboard (you can set your own keyboard shortcut if you want to).

---

### Post by tgalati4 on 2013-10-01
I have experienced the same with hybrid mode--slow return from suspend.  It's a good idea on paper, but it's just too slow and annoying to use in practice.  As far as losing work, most programs have auto-save, so make sure that each application that you use has auto-save turned on.  And yes, you need to watch power, but my thinkpad will go 8 to 10 days in suspend mode, so usually power is not a problem.  If you have a weak battery, then suspend can be risky.

---

### Post by dovah on 2013-12-15
Guys, it seems there was a bug in the last update of the **gnome-power-manager** package, so I just reinstalled it to the previous version, now every setting came back to normality. 

Thank you for your answers. 
(Yes, I still want to hibernate when closing the lid :p )

---

