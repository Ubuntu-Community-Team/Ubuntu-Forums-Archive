---
title: "I dont want GRUB!!"
date: 2006-08-31
forum: Desktop Environments
---

### Post by galego on 2006-08-31
to make a long story short, i deleted my primary partition by accident and totally jacked grub. i was able to restore it and get two of three entries back (windows, SLED 10) but i cannot seem to able to get ubuntu back. i think i killed the root file. anyways i would like to re-install but i do not want to replace the grub that i am currently using from SLED10. i dont recall from the original install if i had a choice of installing grub (i dont think i did), so that is my question; can i install ubuntu and choose NOT to install grub?

---

### Post by bernied on 2006-08-31
You might need to use the alternate install cd to have this option.

---

### Post by John.Michael.Kane on 2006-08-31
Ubuntu is going to detect the prior installs,and ask to add them to ubuntu grub loader.

What i would suggest you try is to reinstall windows,ubuntu,ect.

Make sled10 the last Os installed. this should allow the suse grub to add the OS's you installed before it.

---

### Post by galego on 2006-08-31
> **SD-Plissken said:**
> Ubuntu is going to detect the prior installs,and ask to add them to ubuntu grub loader.

What i would suggest you try is to reinstall windows,ubuntu,ect.

Make sled10 the last Os installed. this should allow the suse grub to add the OS's you installed before it.

yeah i realize that, i just rather not reinstall 3 OS's. there has to be a way not to bring in grub.... :idea: oh i cant believe i did not think of this - i could go ahead and reinstall ubuntu like you said and it will detect the other OS's but it will not address windows properly (which is no big deal) but then i can re-install grub from SLED 10 and it should see ubuntu and just add it in.!?

is this acorrect assumption? :rolleyes:

---

### Post by John.Michael.Kane on 2006-08-31
If suse is the last os to be installed it should pick up the other two OS's. 

If you reinstall ubuntu it too should see the windows filesystem,and give you the option to add that to it's grub loader.  

As long as the last os is suse you should endup with the graphical grub that you want.

---

### Post by galego on 2006-08-31
> **SD-Plissken said:**
> If suse is the last os to be installed it should pick up the other two OS's. 

If you reinstall ubuntu it too should see the windows filesystem,and give you the option to add that to it's grub loader.  

As long as the last os is suse you should endup with the graphical grub that you want.

yep i know, but what i was thinking is, only reinstall ubuntu - it will do its thing (in the past it has not addressed windows properly and i've to manualy add it in) any who, then once it is all done; log into SLED 10 and re-install grub which then should notice the new addition (ubuntu) and added it. this is what i am assuming to be correct. 

yes/no?

---

### Post by John.Michael.Kane on 2006-08-31
galego you can try it,and see. i never triple booted only dual booted,and both OS's was linux based.

---

### Post by steve.horsley on 2006-08-31
I seem to remember that the alternate installer for Dapper gives the option to install to the root partition (/) rather than to the MBR. If you do this, you then have to "chainload" that partition from another boot manager - the Fedora one perhaps. In fact I also happen to chainload my Dapper root partition from the GRUB of an old Breezy installation (which I keep as a rescue option). I added the stanza to boot Dapper to the menu.lst of the old Breezy manually, and it looks kinda like this:
```
title           Linux Dapper
root            (hd0,6)
chainloader     +1
boot

```

---

### Post by Metacarpal on 2006-08-31
I've not used SLED10 - is the grub from that significantly different from the Ubuntu grub?

---

### Post by bernied on 2006-08-31
Why not just keep a copy of the current grub menu.lst handy, then if ubuntu re-installs grub, add those other options to it? If the two other OS's haven't moved (ie still in (hd0,0) or wherever), then the entries will work the same. The only issue you will have is when you update your kernels. But you'll always have to manage your own menu.lst when your booting more than one linux (because the automagic stuff only looks in one partition for boot files), so you may as well get used to it.

I don't think ubuntu (it's actually grub-update we are talking about here) will reliably pick up the other linux install. As mentioned, it doesn't always get the windows entries right. 

Just write down 3-4 lines for each of the two entries - for windows and for SLED10. Then reinstate them in your new grub menu.lst.

You do not have to reinstall 3 operating systems.

---

### Post by Ramses de Norre on 2006-08-31
Two ways: install ubuntu with alternate cd, you can choose not to install grub (which will give you a fancy red warning screen).

Or: install ubuntu with grub, boot into sled and reinstall grub.
```
sudo grub
root (hd0,0)
setup (hd0)
quit
sudo update-grub
```
Replace (hd0,0) with the correct partition (in grub numbering) which contains your SLED /boot/ folder, (hd0) is your MBR where you'll probably want grub.

Your menu.lst is preserved when doing this.

---

### Post by galego on 2006-08-31
Ramses de Norre, 
that is what i was trying to find out. if i understand you correctly once i reinstall grub from SLED10, SLED will recognize that there is a new OS and make entries or will it just give back the original and then i would have to update manually to boot ubuntu?

---

