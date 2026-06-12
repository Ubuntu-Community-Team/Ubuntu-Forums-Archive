---
title: "Need Assistance with Safe Boot"
date: 2009-02-27
forum: General Help
---

### Post by dazzler on 2009-02-27
Hi all, back again :(

I cant seem to boot into Ubuntus gui, i can get to the fail safe shell prompt and input, my username and password then im stumped.

Basically the only thing i changed before powering down last and all seemed good was change my xorg.conf (as below) because i wanted to run virtualbox in fullscreen.

Everything worked great, didnt realise there was a problem till this morning.

The only other thing i did was set grpahic effects to none as it caused google earth and Zatoo to flash on playback.

> sudo gedit /etc/X11/xorg.conf
(space after gedit and X11 must be capital X)

5. You now need to hunt through the text until you see the display resolutions listed. The ones you will be concerned about will be listed under bit depth 24 or bit depth 16 (as these depths are the ones that give you a large amount of colors.)
6. Next, either replace the existing resolution, or add another listed resolution in the exact same manner. Your resolution must be equal to or less than what the host machine is capable of (see step 2).
7. Restart the guest machine. Your resolution should be what you have specified or allow it to be changed.

---

### Post by smani on 2009-02-27
Try to rename your xorg.conf to something else (so that you still have it for backup, but X creates a default one next time it starts). This should get your gui back. Concerning virtualbox, it's odd that you need to edit the xorg.conf file for that - if the actual screen resolution is okay, virtualbox should be able to go to full-screen normally, without requiring any additional configuration...

---

### Post by pedro_orange on 2009-02-27
You've probably done something to your xorg.conf. 

Presumably you've entered a resolution your monitor or graphics card can't handle. 

Before you make system changes like that, you should always make a copy (backup!) of the old working one to revert to if things do go wrong.

---

### Post by philinux on 2009-02-27
No need to touch xorg to get full screen in virtualbox.

While you have you're guest OS running select "install guest additions" from the devices menu. Reboot when prompted and when it comes back up host + F should take it to full screen. You may need to readjust you resolution and color depth.

Download the user manual from the virtualbox website too.

---

### Post by dazzler on 2009-02-27
Cheers lads, i did a sudo dpkg-reconfigure xserver-xorg to reset it and im back in, now to check what damage i've done ;)

---

### Post by andrew.46 on 2009-02-27
Hi philinux,

> **philinux said:**
> While you have you're guest OS running select "install guest additions" from the devices menu. 

I have had to reinstall these additions with every kernel update in Ubuntu (Ubuntu is the guest). Is there a way around this?

Andrew

---

