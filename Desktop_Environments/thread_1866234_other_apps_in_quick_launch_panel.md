---
title: "other apps in quick launch panel"
date: 2011-10-21
forum: Desktop Environments
---

### Post by vonkad on 2011-10-21
Hello,

I got this intellij idea application, which installs by simply unpacking a tar. somewhere. It contains a script, which starts it (idea.sh) and a set of icons. 

I'd like to add this app to the launchbar in lxpanel.

My current solution is to 
1) copy a sample .desktop file from /usr/share/applications/, place it somewhere in my home and modify it to suit my app
2) edit ~/.config/lxpanel/default/panels/panel, the launchbar part, to include my .desktop
3) logout/login or kill and start lxpanel

Obviously, this is not too user friendly. Is there a GUI way ?

Thanks,
David Vonka

---

### Post by count.zero on 2011-10-21
Hi David,


[LIST]
[*]copy the .desktop file you created to  ~/.local/share/applications (or with sudo to /usr/share/applications to make it available for all users, you could also take a look at [desktop-file-utilities]("http://www.freedesktop.org/wiki/Software/desktop-file-utils") then)
[*]right-click lxpanel -> choose * "Application Launch Bar" Settings*
[*]you should find your app in the category provided in your .desktop-file (Categories=...)
[*]mark it and click *+Add* ;)
[/LIST]
 Hope this helps.
Regards

---

