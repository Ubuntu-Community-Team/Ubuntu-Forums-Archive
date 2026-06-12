---
title: "How to Install policykit-kde in Ubuntu GNOME 14.04 amd64"
date: 2014-05-19
forum: Desktop Environments
---

### Post by lambdafox on 2014-05-19
I am trying to install GStyle.  I have been able to install all required packages except:  policykit-kde

new info:  I have cloned the repository from gitorius, but am pretty clueless about how to build / install the package

I see a CMakeLists.txt file in the root directory of the repo.  After googling, I installed cmake.  If I run cmake in that directory, nothing happens.  Looking inside the file, I see there is no minimum cmake required, it first cheks for the following:

polkit>=0.8
polkit-dbus>=0.8
polkit-grant>=0.8

man polkit opens a manpage for polkit, but it does not say the version number
man polkit-dbus -- cannot be found
man polkit-grant -- cannot be found

dpkg -s polkit-dbus | grep 'Version' -- not installed
dpkg -s polkit-grant | grep 'Version' -- not installed

Synaptic finds nothing when I search for either.




I am a Linux newbie / Tech oldie...

---

