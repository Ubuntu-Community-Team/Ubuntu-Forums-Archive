---
title: "Unity Will Not boot 12.04"
date: 2012-05-09
forum: Desktop Environments
---

### Post by chazdg24 on 2012-05-09
I switched to GDM and restarted. No problem. Waited several days and my system is working well, except for a minor bug in Gnome 3.4. I install Ubuntu Tweak and make a few tweaks. Reboot and all is well. I run Cleanup in Ubuntu Tweak and clean everything up except for the previous kernel. Reboot and for the third time installing 12.04, Unity will not load. Log out and try Gnome. Gnome 3.4 will not load but Gnome classic does. The ATI video card is humming away.

I pull up a terminal and try Unity --reset, but I get numerous error messages and then it freezes.

Is there any way to fix this issue? Third time this has happened - I should have left it alone and not installed Ubuntu Tweak. Any help would really be appreciated.  

Please help...

---

### Post by chazdg24 on 2012-05-10
I figured out the issue. Ubuntu Tweak seems to mess with the fglrx driver. I was about to give up hope but decided to remove the driver and reboot. Still no Unity or Gnome 3.4. I installed the ATI Proprietary Driver 12.4. It took 3 trys as the first two installs insisted that fglrx was still installed. 3rd try installed flawlessly. Reboot and Unity and Gnome 3.4 work better than ever. 

This is an issue I have seen on Google numerous times with no real answer. Beware of Cleanup Janitor in Ubuntu Tweak if you have an ATI card. It will cause you trouble. I have gone back to lightdm and it works perfectly.

---

### Post by HanDez on 2012-05-27
This happened to me also.....I fixed it in recovery mode by checking the fglrx installation, which showed fglrx was not even there....so I reinstalled with apt-get and after sudo reboot all was well again.  Use bleachbit...I have had no issues with it.

---

