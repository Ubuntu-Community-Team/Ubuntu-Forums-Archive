---
title: "Monitor problem - dark spot"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Tingmo on 2005-10-14
Can anyone help me with my monitor problem? When I restarted my computer, a part of the left side of the monitor is completely dark. There is like 2 or 3 inches dark spot running vertically. It seems like everything has shifted few inches to the right. 
Please show some lights to me. How should I fix it?

---

### Post by pmj on 2005-10-14
Enter the monitor menu, find the position controls and move the image to the left.

Your monitor probably has separate settings for every resolution and refresh rate so it might be that one or both of these settings has changed since everything was looking good. If that's the case, going back to the resolution and refresh rate you used to use should make it good again.

---

### Post by xyzzyman on 2005-10-14
I have a dell with onboard 915g graphics and a 17" Dell E773 monitor that exhibits a similiar behavior. I had to manually set refresh rates in the xorg.conf file, because the refresh rate was a bit higher than it should have been, but not high enough to have the monitor reject it. Under windows, it does 85 just right at 1024x768, but in ubuntu I've had to turn it down to 81. I'm still playing with the settings for mine. If you want I'll post the relevant parts of the xorg.conf to maybe help you get on your way. Between that and use 'sudo gtf' to generate the appropriate lines, I'm sure that'll take care of your problem.

---

### Post by Tingmo on 2005-10-15
For the sake of newbie like me, can you show all the nuances of fixing it in xorg.conf?

---

### Post by tschweg on 2005-10-15
[QUOTE=Tingmo]For the sake of newbie like me, can you show all the nuances of fixing it in xorg.conf?[/QUOTE]

Check this thread here: [Howto solve some of the resolution problems]("http://ubuntuforums.org/showpost.php?p=129379&postcount=21")



Make sure to place the gtf ModeLine entries into the **Monitor Section**

---

