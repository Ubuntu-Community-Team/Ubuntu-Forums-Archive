---
title: "Unable to change number_of_desktops. Fixed to 1"
date: 2010-04-15
forum: Desktop Environments
---

### Post by marioja on 2010-04-15
Hi I am running ubuntu 9.10 and in compiz general desktop size setting the slider for number of desktops is fixed at 1.

If I invoke gconf-editor and I look under apps/compiz/general/screen0 the value for number_of_desktops is set to 1 and if I change it to 2 and reboot, the number in compiz will still show as 1.  Also, in gconf-editor when I click on the number_of_desktops in parenthesis it says (1:1) which seems to indicate the minimum and maximum value.

How can I increase this configuration parameter.  Also, what is the effect of doing this.

Thanks,
Mario

---

### Post by mister_p_1998 on 2010-04-16
Cant you right button on the workspace switcher (bottom right of taskbar) and select four workspaces?

---

### Post by marioja on 2010-04-16
[mister_p_1998]("http://ubuntuforums.org/member.php?u=84016"), doing this increase the horizontal virtual size not the number of desktops.  Look at compiz/general/desktop size tab.  Can anyone help here? How does one change the number of desktops and what is the effect of doing so.

---

### Post by hugin0 on 2010-04-16
my gconf also shows 1-1 as the number of desktops... but I am running 4 currently.  The setting you want to change is the hsize, i believe, not number_of_desktops.  I should say that you should be able to change the number of desktops by right clicking the switcher applet and going into the preferences. 

-hugin0-

---

### Post by d1ma5 on 2010-09-11
My number of desktops is also fixed at one. I created a new user and it couldn't change the number_of_desktops either. I want another  [viewport]("http://wiki.compiz.org/GeneralOptions#Desktop_Size"). Does anybody have any idea?

---

### Post by andymorton on 2010-09-11
You change the number of desktops using Advanced Desktop Effect Settings (from the software centre). I haven't used it for a while but if I remember rightly the option for the number of desktops is in the General Settings section. 

andy

---

