---
title: "Help!!!!!!!!!!!!!!!"
date: 2005-12-30
forum: General Help
---

### Post by t_ras on 2005-12-30
I accidently moved fstab to / folder and now I can only start ubuntu terminal and with READONLY FILE SYSTEM (which means I cant fix it), any ideas?

I wouldn like ot reinstall since I allready had contumed it.

---

### Post by soulestream on 2005-12-30
boot up with a livecd, chroot to the new system and move it back. 

Do some googling its not hard.

Basically you boot up and mount the harddrive

you chroot into the drive. 


then make changes, exit and reboot.

btw, putting a title that has some description other that "blaaahhhhhhh", will always get a better response. 

soule

---

### Post by t_ras on 2005-12-30
Thanks for the help.
I'll try downloading liveCD.
thanks.

---

### Post by soulestream on 2005-12-30
you probaby wont need to chroot, just mount it and move it.

soule

---

### Post by steve.horsley on 2005-12-30
I'm not sure you need a live CD. I have read that the installer CD has a rescue mode (type "rescue" instead of just hitting enter as you start). That said, the live CD is well worth keeping as a rescue CD.

---

### Post by t_ras on 2005-12-30
worked fine (through chroot needed)
thanks! :)

---

