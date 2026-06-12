---
title: "Suspend/hibernate not always available"
date: 2009-01-26
forum: General Help
---

### Post by Dirjel on 2009-01-26
When my computer had Windows on it, suspend worked fine.  After I put Ubuntu on, though, the option for suspend/hibernate would not always show up in the options on the shutdown menu.  When it DID show up, I tried it, and my computer would not resume afterwards.  I just had a black screen, and eventually I'd just have to force my computer to power down, and reboot.

After following this guide:
[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)
I was able to get my computer to resume after suspending/hibernating.  However, the options still do not always appear in the System --> Shutdown options.  I only have Shutdown and Restart roughly 3/4 times.  It's weird, because it's inconsistent.  Any idea how to fix it?

---

### Post by Dirjel on 2009-01-29
After the last updates I installed, my computer had to restart.  After that, I haven't gotten Suspend or Hibernate to appear in my shutdown menu at all.

sudo pm-suspend works, though.  TBQH, I wouldn't mind just making a launcher for the suspend command, but I don't want to have to enter my password in every time I want to leave my computer.

What do I have to do to put the option back into my shutdown menu?

---

### Post by bishman on 2009-02-03
*bump

I have the same problem, the suspend and hibernate options used to appear on occasions, but now they don't appear at all. I am using a Laptop - Compaq Evo N610c.

Any ideas?

---

### Post by Dirjel on 2009-02-03
Actually, I just figured out something that helps; at least, it helped this time and my last reboot.

If you run update-manager, for some reason that makes suspend appear in the shutdown menu (I turned off hibernate, because I don't use it).  You don't have to actually DO anything in the Update Manager; just opening it, and letting it load up before closing it again seems to work.

I'll post again if I can figure out something else, or if this stops working later.

---

### Post by Dirjel on 2009-02-04
Alright, I had to reboot my computer today, and I lost Suspend again.  I ran update-manager, and it I still didn't have suspend, so I clicked the check for updates button.  Voila, life is good, suspend is available.

You might also want to try and install Ubuntu Tweaks, and add suspend using that.  It didn't help for me, but it might work for you.  I don't know if it's in the repos, since I just grabbed it off of a link someone posted on here.
[https://launchpad.net/ubuntu-tweak](https://launchpad.net/ubuntu-tweak)

---

### Post by bishman on 2009-02-04
Nice work.

A solution that seems to be working for me at the moment is to create a launcher on the desktop with the command: gnome-power-manager restart

'run in terminal' selected. Call the launcher something nice like 'enable suspend' :)

(or just run the command in the terminal yourself, of course)

Suspend appears for the rest of the session and works (and I have yet to see it disappear!)

Thanks for the ubuntu tweak link - will take a look

---

### Post by Dirjel on 2009-02-04
> **bishman said:**
> Nice work.

A solution that seems to be working for me at the moment is to create a launcher on the desktop with the command: gnome-power-manager restart

FANTASTIC.

I'll take it one step further, and add it to System --> Preferences --> Sessions, so it enters the command automatically when I logon.

I've only rebooted once since I added the command, but it worked.  Suspend was available immediately.

Thanks for the tip!

---

### Post by ronewolf on 2009-02-05
> **bishman said:**
> Nice work.

A solution that seems to be working for me at the moment is to create a launcher on the desktop with the command: gnome-power-manager restart

Similar problem here but just with the hibernate. Suspend is stable, Setting up a new system(Dell Mini 12). For whatever, reason, it didn't come with hibernate enabled. I'm still working to get hibernate working from the command line. In the meantime, I checked can_hibernate in the apps -> gnome-power-manager -> general config. The hibernate button cooperated and appeared when I next brought up the gnome shutdown & logoff screen.

Then I tried to use it - clicked hibernate - the process started, but then failed. Since then, the hibernate button doesn't appear. Tried the gnome-power-manager restart, didn't make a difference. can_hibernate is still checked. Very puzzeling that the button would show up and then disappear.

---

