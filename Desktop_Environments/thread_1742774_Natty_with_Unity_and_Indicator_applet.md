---
title: "Natty with Unity and Indicator applet"
date: 2011-04-29
forum: Desktop Environments
---

### Post by hashcode on 2011-04-29
I am having few problems with new natty distro with Unity:

1. Why is Pidgin not showing in indicator applet? (I have checked always show in it's settings)
2. How do I simply add custom launcher to left unity panel?
3. How do I change icon of launcher in unity panel?
4. How do I add new indicators? I followed following tutorial, but after installing applet (cpufreq) nothing more appears in my indicator applet :/ [http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/](http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/)

Thanks

---

### Post by hashcode on 2011-04-29
Pidgin issue solved like this:

[COLOR=#000000][FONT=Times New Roman][COLOR=#555555][FONT=Arial]gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by Zetheroo on 2011-04-29
> **hashcode said:**
> I am having few problems with new natty distro with Unity:

1. Why is Pidgin not showing in indicator applet? (I have checked always show in it's settings)
2. How do I simply add custom launcher to left unity panel?
3. How do I change icon of launcher in unity panel?
4. How do I add new indicators? I followed following tutorial, but after installing applet (cpufreq) nothing more appears in my indicator applet :/ [http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/](http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/)

Thanks

1. Pidgin is located in the menu selected by clicking on the envelope.
2. Add launchers to the sidebar by drag-n-drop.
3. Changing the icon is not easily done.
4. Try installing "indicator-weather", add it to "Startup Applications" and logout/login.

---

### Post by hashcode on 2011-04-29
1. solved
2. works, but what about custom command (f.e. I don't use eclipse from repo, but downloaded myself) ?
3. too bad :(
4. works :) (I needed to manually add command like indicator-cpufreq to startup apps)

---

### Post by Zetheroo on 2011-04-29
> **hashcode said:**
> 1. solved
2. works, but what about custom command (f.e. I don't use eclipse from repo, but downloaded myself) ?
3. too bad :(
4. works :) (I needed to manually add command like indicator-cpufreq to startup apps)

2. Check out the 4th post in this thread: [http://ubuntuforums.org/showthread.php?t=1578379]("http://ubuntuforums.org/showthread.php?t=1578379")

---

### Post by hashcode on 2011-04-29
ah that's not so bad, thanks

---

### Post by Zetheroo on 2011-04-29
> **hashcode said:**
> ah that's not so bad, thanks

Ha. Hopefully we will be able to customize Unity in the future without terminals, config files etc ... just a nice clean gui is what we really need!

---

### Post by geazzy on 2011-05-10
a few days ago I was confused because I did not showing pidgin in indicator aplets ...
and in fact I turn off libnotify plugins in pidgin 
Now I activate it and my pidgin has appeared in indicator aplets

:D

---

