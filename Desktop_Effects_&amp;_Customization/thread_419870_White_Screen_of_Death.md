---
title: "White Screen of Death"
date: 2007-04-23
forum: Desktop Effects &amp; Customization
---

### Post by avantgardaclue on 2007-04-23
Sorry guys if this is in danger of becoming yet another **white screen of death** posting but i can't see a resolution that will work for me.

Anyhow here's my story...

Upgraded from 6.10 to 7.04, as always everything went fantastically smoothly, ubuntu has never let me down! Went to see what these desktop effects were. System loaded (**now these are my approx memories so might not be 100% accurate but bear with me!**) 'unsupported nvidia' driver (?). OK still working fine & get some sort of computer card icon in the top right corner system tray. Enabled it to do box things and shiver things, a bit of transparency there too. Hmmmm all very clever but frankly pretty useless as far as i was concerned. When i had a number of applications open and i opened a new window sometimes that window opened completely black. The other windows were fine.

I decided, in a completely unscientific way, that this was probably/possibly to do with memory, or lack of it (I only have 256 m). The desktop effects were frankly leaving me cold so decided to undo what i had done, the nvidia driver thing was uninstalled/deleted... i then had to reboot.

It went thru its usual process, the beige background showed, the music played, the loading panel appeared and a few icons like nautilus showed, then it all went black with a white mouse pointer then it changed to white with a black pointer... and there it stayed until i did a hard reboot.

Tried starting up with the 'safety' mode in grub and a whole load of technical lines appeared culminating in something like simon@desktop# . Clearly there now is something to key in to boot the system up but what?

This is really annoying and am having to type this from my, shock horror, windows drive!

all help gratefully appreciated

thanks... simon

---

### Post by hyperair on 2007-04-23
The black window bug is a bug of the nVidia drivers that occur when the video card runs out of memory. It occurs on both Beryl and Compiz (which you are using).

I had the white screen problem, but that was what happened when I tried to use the "nv" drivers for the X server instead of the "nvidia" drivers. To at least get back into Ubuntu's GUI you can run these commands in the terminal (don't log in from the login screen, type ctrl+alt+f1 and login from there instead) to disable desktop effects.

sudo apt-get remove --reinstall --purge desktop-effects
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart

Then log in via the graphical login screen.

---

### Post by avantgardaclue on 2007-04-24
Thanks for the reply and help. Together with other gems of help unfortuneatly I was still not able to solve the problem sooooooo...... Last week when i upgraded i took a back up of my home directory onto my new 2 gig flash drive so i just did a completely new install!! Way hey it works all proper like now and definitely no desktop effects for me.

thanks for your help anyway....Simon

---

