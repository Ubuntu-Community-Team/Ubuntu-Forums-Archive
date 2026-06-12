---
title: "plasma-desktop error Invalid D-BUS interface name 'org.kde.plasma-desktop.PlasmaApp'"
date: 2009-12-15
forum: Desktop Environments
---

### Post by of_darkness on 2009-12-15
The problem began as i added the kde 4.4 beta kubuntu ppa repo and upgraded kde to kde 4.4beta 1.

i have moved all .kde to a backup folder
removed all kde and reinstalled
purged kde again and unchecked the kde 4.4beta 1 repo and reinstalld kde-workspace-bin

But still i get the error 
> "Invalid D-BUS interface name 'org.kde.plasma-desktop.PlasmaApp' found while parsing introspection" site:[http://ubuntuforums.org/](http://ubuntuforums.org/)searched my system for any file whith org.kde.plasma-desktop.PlasmaApp but no no souch file..

looked att dbus config files in /etc but no info there...

cant remove dbus as all of gnome is depending of it

and i have googled the error message for some hours now but now real info other then some gento i think user solved it by downgrading hal but i have only one version.

karmic 64bit is os.

what to do now?

---

### Post by pixel :-) on 2009-12-15
In synaptic>settings>preferences>distribution>prefer versions from

hope that fixes your mess, beta means "unstable", its "normal", you got problems.

---

### Post by of_darkness on 2009-12-16
> **pixel :-) said:**
> In synaptic>settings>preferences>distribution>prefer versions from

hope that fixes your mess, beta means "unstable", its "normal", you got problems.

Uhm > purged kde again and unchecked the kde 4.4beta 1 repo and reinstalld kde-workspace-bin

But still i get the error  and it was kde from karmic main stable kde 4.3 repo that i installed but whit no luck.

---

### Post by pixel :-) on 2009-12-16
you don't know synaptic?Install it with

sudo apt-get install synaptic

run it, and do what i tell you. By default, it prefers the highest version, with this you'll get to chose witch versions of packages you want. When you fix everything, don't forget to revert back to the highest version.

---

### Post by of_darkness on 2009-12-16
> **pixel :-) said:**
> you don't know synaptic?Install it with

sudo apt-get install synaptic

run it, and do what i tell you. By default, it prefers the highest version, with this you'll get to chose witch versions of packages you want. When you fix everything, don't forget to revert back to the highest version.

Uhm i have ben using synaptic and ubuntu for some years now...

and strangly enough it sorted it self by a restart of x.. i dident think dbus was connected to 
ones x-session.. but yeah now i know..

and i think the problem where in my old kde settings that became screwed when uppdating to kde4.4 beta , but now kde 4.4 beta runs... i started figuring it out when i came upp whit the longshot of running plasma-desktop as sudo...

---

