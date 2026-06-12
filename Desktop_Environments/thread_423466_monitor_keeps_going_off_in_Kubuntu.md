---
title: "monitor keeps going off in Kubuntu"
date: 2007-04-25
forum: Desktop Environments
---

### Post by jtx472 on 2007-04-25
I can't seem to find power management anywhere.  My monitor keeps turning off after about 20 or 30 minutes.  I would prefer to always see my screensaver. Power management is  easily accessible in Ubuntu but I can't find it anywhere in Kubuntu.  Thanks

---

### Post by disturbedite on 2007-04-26
> **jtx472 said:**
> I can't seem to find power management anywhere.  My monitor keeps turning off after about 20 or 30 minutes.  I would prefer to always see my screensaver. Power management is  easily accessible in Ubuntu but I can't find it anywhere in Kubuntu.  Thanks
i've noticed this too after a fresh install of kubuntu feisty.  i switched off power management but it doesn't work.  i haven't restarted x yet but maybe the changes will take affect after i do that.

---

### Post by jtx472 on 2007-04-26
How did you even access power management?  Where is it?  Thanks

---

### Post by disturbedite on 2007-04-26
its the last tab of the monitor & display module in kcontrol or system settings.

---

### Post by jtx472 on 2007-04-27
Where?

[http://img01.picoodle.com/img/img01/8/4/27/f_ScreenshotCm_3affb30.png]("http://img01.picoodle.com/img/img01/8/4/27/f_ScreenshotCm_3affb30.png")

---

### Post by disturbedite on 2007-04-27
dude, LOOK YOURSELF.  its right there under peripherals, if you 're never gonna bother to click on stuff to look around why ask about it?

sorry for the rant, but yeah...

---

### Post by jtx472 on 2007-04-27
Here ya go my friend.  Show me.

[http://www.freeimagehost.eu/image/61af25286943]("http://www.freeimagehost.eu/image/61af25286943")

---

### Post by disturbedite on 2007-04-27
ohhhhhhhh!  no wonder, you didn't say it wasn't there!  i guess i should have figured that out tho.  anyway, you prolly don't have the kde-guidance package installed.  install it from your package manager.

---

### Post by jtx472 on 2007-04-27
That  did  the trick.  Man  I been messin' with this for over a week.  Even the guys on Launchpad couldn't find the  solution.    Thanks for hangin in there  with me.  God bless

---

### Post by disturbedite on 2007-04-27
no prob.  thats what the forums are for.  sorry for the rant before, but i didn't realize it wasn't showing up for you.

the reason you didn't have the "Monitor & Display" kcm module (and the "Disk & Filesystems module) was cuz they depend on the kde-guidance package.

---

