---
title: "I have a theme installed but it seems to reset each time I reboot"
date: 2022-06-12
forum: Desktop Environments
---

### Post by mikber18 on 2022-06-12
Hi Guys, 

I'm running Ubuntu 22.04 LTS I installed a theme called **Papirus Icon Theme**however when I reboot my system the theme disapppeaars and resets to default. 

I have to go into Gnome Tweaks and select it again from the drop-downs. 

Once I do this it will be fine until later. 

Any ideas what might be resetting the icon set and how to make it more 'permanent'?

Many Thanks,

---

### Post by yancek on 2022-06-12
If you have installed Ubuntu 22.04 to your hard drive on your computer, it should not reset.  Most actions require root permissions (use sudo).  If you are 'running' Ubuntu which you have written to a 'live' USB, that is expected behavior.

---

### Post by Dennis N on 2022-06-12
I would check with dconf-editor utility to verify that the theme has been correctly registered in the system settings. If it's set correctly here by the Tweaks tool, it should be permanent until changed again by the user. You can also set it in this dialog if you wish.

dconf-editor may need to be installed with Ubuntu Software.

---

### Post by mikber18 on 2022-06-14
> **Dennis N said:**
> I would check with dconf-editor utility to verify that the theme has been correctly registered in the system settings. If it's set correctly here by the Tweaks tool, it should be permanent until changed again by the user. You can also set it in this dialog if you wish.

dconf-editor may need to be installed with Ubuntu Software.


I installed dconf-editor and I was able to update the theme via there. It was not registered correctly by the tweaks tool though. I will try reinstalling the tweaks tool see if that helps.

---

### Post by web-user on 2022-06-18
dconf-editor seems to do the job. If not, I would try editing the config files manually

---

