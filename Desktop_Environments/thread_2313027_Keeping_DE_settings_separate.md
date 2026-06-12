---
title: "Keeping DE settings separate"
date: 2016-02-09
forum: Desktop Environments
---

### Post by pzgriffin on 2016-02-09
I like to try new things. Especially Desktop Environments. The problem is being able to keep the appearance settings separate. If I log into Mate I want it to look like Mate and if I log into Gnome I want it to look like Gnome. I believe they access the same folder for the appearance settings which would be a problem. 

Is there a way to keep these settings separate for the same user? Or would it be easier/better to have separate user accounts for each DE? I imagine this is not a problem most people have or even think about. 

Thanks for any help.

---

### Post by vasa1 on 2016-02-09
Even if you have separate users, there still could be some issues. Your GRUB and splash screens may be modified. You may see a more complicated menu: two text editors, two file managers, etc.

---

### Post by grahammechanical on 2016-02-09
You should be aware that many users who have installed alternative desktops have found that getting back to what they consider a "pure" system is not so easy. I found that the only way to clear up the mess that came about by installing several alternative desktops was to re-install. Be prepared for that.

The alternative desktop will take over. It will set its own greeter or login screen that then becomes very difficult to remove. I never tried this with separate users as you are thinking of doing but, in my opinion, you will be disappointed. Different users still share the same OS. You will have to select what desktop session to load before logging in as a user.

Regards.


Regards

---

### Post by buzzingrobot on 2016-02-09
Standardizations used in Linux make that easier said than done.

Menus, including Gnome's Overview and Unity's Dash, populate themselves by reference to files maintained in /usr/share/applications.  If, for example, you install KDE on a Gnome system, each new KDE application will put a file in /usr/share/applications.  Those applications will appear in KDE's menu, Gnome's Overview, MATE's menu, etc.

Themes go in standard locations, as well, and so are available to any interface. For a variety of reasons, a theme that's designed for one environment may nor may not play well with another, or even a different release version of the same, environment. (Themes are sensitive to version changes in the GUI toolkits used to create desktops.)

The configuration changes we make to individual applications are maintained in our home directory, another standard location. If we tweak an app to look acceptable in one desktop environment,  the app will use that configuration in other desktop environments.

The safest way to sample a different desktop environment is to boot an Ubuntu flavor, or another distribution, in live mode.  You can get a more realistic and longer term perspective by installing into a virtual machine.

---

