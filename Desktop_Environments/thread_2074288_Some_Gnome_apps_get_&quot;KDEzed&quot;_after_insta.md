---
title: "Some Gnome apps get &quot;KDEzed&quot; after installing KDE"
date: 2012-10-21
forum: Desktop Environments
---

### Post by enemotrop on 2012-10-21
Hello,

I use Ubuntu 12.04 with Unity as my default and original desktop environment, and I have added the KDE desktop environment to the system recently. Since that, some apps  (Firefox, Chromium, Thunderbird, LibreOffice, as far as I've noticed) have changed their internal decoration (controls, colours, even sometimes the mouse cursors), different to the rest of GTK apps originally included or installed into the Unity desktop environment. It's like if this apps has been 'forced' to use qt instead of gtk to decorate them.

I can assume that this behaviour can or must be normal in KDE native apps (Amarok, Konqueror...), even ran at Unity desktop environment (for instance, if I select the Oxygen theme in KDE, these apps are shown with the same effects under Unity), but, what about that independent apps that were originally installed into the Unity environment? Is there a way to force them to be drawn as the rest of the apps, whith the gtk decoration engine?

Thanks in advance

---

### Post by buzzingrobot on 2012-10-21
It's been some time, but I recall a GTK/Gnome option within the Apperances setting widget that might need to be turned on.

---

### Post by enemotrop on 2012-10-21
The Appearance menu in Ubuntu 12.04 has only a few options... Now it doesn't allow you to change separatedly all the theme elements like controls, icons, etc. You can only select a theme, and I've the default Ambience chosen.

There is no option to force the system to use GTK/Gnome or something like that, as far as I know.

I've tried also with apps like MyUnity, Unsettings or Ubuntu Tweak with no results. There must be some package available to switch on/off qt4 under Gnome, I guess... but I'm afraid I'm lost at this point.

Can you be more specific, please?

---

### Post by enemotrop on 2012-10-22
I realized that not only some apps are using the KDE decoration, but most of the Unity environment is 'contaminated'. 

If I open gcalctool, for instance, and do a right-click over its main textbox control (that which displays the results), the pop-up menu is drawed with the Unity theme: 

[IMG]http://imageshack.us/a/img204/1378/formqf.png[/IMG]



But, if I do a right-click over the window titlebar, the pop-up is shown in the KDE selected theme (in this case, Ozone):

[IMG]http://imageshack.us/a/img545/354/titlebari.png[/IMG]


I don't want to use the same themes in KDE and in Unity/Gnome... it's supposed to be easy to get uniformity in each desktop environment.

---

### Post by cmcanulty on 2012-10-22
I have had a lot of trouble with classic, gnome, xfce , and kde interfering with each other. I keep trying something that will keep me as happy as gnome 2 but hard to compare when they don't stay separate

---

### Post by enemotrop on 2012-10-22
UPDATE: the problem with the windows decoration is PARTIALLY solved. I've:

 renamed ~/.config/gtk-3.0/settings.ini
renamed ~/.config/Trolltech.conf
deleted all subfolders under ~/.config/ relative to KDE or the Oxygen theme.
uninstalled al gtk-oxygen* packages present on the system (I thought they were already gone).
 
At this moment, al Mozilla apps and the LibreOffice suite have return  to its normal appearance and the contextual menus of all apps have been  restored to the nice and default Ambiance Unity theme.
 
The only remaining issue I've noticed at this point is the scrollbar  in every apps (even the distro's natives like gnome-terminal or  nautilus). It's not the typical minimalistic orange scroll bar of Unity,  buf a conventional (although stylish) scrollbar. I'll keep trying to  solve this, but any further help is welcomed, of course.
 
Thanks!

---

### Post by enemotrop on 2012-10-23
At this moment,  I've got the overlay scrollbars running in a few apps. The major part of  the system is using the old fashioned scrollbars, although I've tried  with several possible solutions to restore the overlay -Ayatana-  scrollbars.
 In any case, I think that the main question of the topic has been  solved, and mark this thread like that. I'll open another one more  specific with the scrollbars issue.
 Thank you!

---

