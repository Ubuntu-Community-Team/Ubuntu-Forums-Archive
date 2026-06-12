---
title: "ubuntu classic gnome panel white background problem"
date: 2012-04-16
forum: Desktop Environments
---

### Post by cokabear on 2012-04-16
im used the gnome-fallback-session from 12.04's unity to gnome classic. once i did it a problem occured.

This is a very annoying problem and im trying to figure out why its happening. i have a screenshot below to show my desktop. as you can see the applets at the bottom are white, no matter what theme i use. i tried this [http://www.omgubuntu.co.uk/2011/02/gnome-panel-transparency-fix-ubuntu/](http://www.omgubuntu.co.uk/2011/02/gnome-panel-transparency-fix-ubuntu/) but it didnt work.

any ideas?

---

### Post by dbutcher on 2012-05-03
I had the same issue after upgrading from 11.10 to 12.04
However, I noticed that the white backgrounds (and grey on grey font for 'Applications' and 'Places') only occurs when using Gnome Classic.
If I log in using Gnome Classic (no effects), the panel background follows the theme colours correctly (I'm using Ambiance).

I don't mind giving up the effects to get a more readable and usable desktop.  Maybe this will help you too.

---

### Post by jedimasterk on 2012-05-12
Same here. Fresh install of Ubuntu 12.04. Need to use Gnome classic (No Effects) to get it to look consistent. I wonder how you can get Gnome classic (With Effects) to render top fonts (Applications Places)and bottom panel desktop switcher properly. Hopefully update will fix it. Seems worthless to use with effects, vs without effects.

---

### Post by ibozzie on 2012-05-23
Yup, same here. Gonna dredge through the forums and see if anyone's found a way to fix this.

---

### Post by ibozzie on 2012-06-03
OK so my guess right now is that it's caused by a bizarre design decision that somehow gets distorted by using Classic. Scroll down to the sixth post [here.]("http://ubuntuforums.org/showthread.php?t=1968155&highlight=precise+crash") I'll post again if I can fix it.

---

### Post by traditionalist on 2012-06-03
It doesn't happen on my machine. I have two panels on the second desktop top and bottom and they use my theme.

---

### Post by Joan A. on 2012-06-17
Hi everybody!

There is a bug reported on launchpad: [https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/981289](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/981289)

Here you are the solution to fix this issue. Just follow this step by step: [http://ubuntuforums.org/showthread.php?t=1970390](http://ubuntuforums.org/showthread.php?t=1970390)

If you prefer a better option you can install a .deb package from launchpad that was built for Ubuntu 12.10 (Quantal). Here you are the link: [https://launchpad.net/ubuntu/+source/light-themes/0.1.9.2-0ubuntu1/+build/3536752](https://launchpad.net/ubuntu/+source/light-themes/0.1.9.2-0ubuntu1/+build/3536752)

On the other hand you can wait for the official update, even though it seems to be delayed for unknown reasons.

---

