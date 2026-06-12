---
title: "installing beryl on ubuntu 6.06 and having some troubles"
date: 2007-06-29
forum: Desktop Effects &amp; Customization
---

### Post by Nyxess on 2007-06-29
first, id like to say that ubuntu is very new to me, so stick with me. thanks =)

following the directions at [http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851) i ran into these problems.

during step 1, after i wrote "sudo apt-get upgrade" i get this:

The following packages have been kept back:
libwnck18 xserver-xgl
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

and after the "sudo apt-get install beryl emerald-themes" i get this

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
beryl: Depends: beryl-core but it is not going to be installed
Depends: libberylsettings0 but it is not going to be installed
Depends: libberyldecoration0 but it is not going to be installed
Depends: beryl-plugins but it is not going to be installed
Depends: beryl-settings but it is not going to be installed
Depends: beryl-manager but it is not going to be installed
emerald-themes: Depends: emerald (>= 0.1) but it is not going to be installed
E: Broken packages

im assuming the last step failed because of the two "kept back" packages. how do i stop them from being held back?

---

### Post by avik on 2007-06-29
Try going to System->Administration->Software Sources and enabling the universe and multiverse repositories.

---

