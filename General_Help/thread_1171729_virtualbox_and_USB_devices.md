---
title: "virtualbox and USB devices"
date: 2009-05-27
forum: General Help
---

### Post by zero777zero on 2009-05-27
hello i am looking for a way to get virtualbox to use USB devices such as a controller or external hard drive. i read a guide online however it was step-by-step and i failed to get any progress.

---

### Post by semitone36 on 2009-05-27
If you got virtualbox from the repositories you got the open source edition (OSE) which does not come with USB support.  You need to go to virtualbox's [website]("http://www.virtualbox.org/wiki/Downloads") and download the Personal Use and Evaluation License (PUEL) version which DOES have USB support and a few other things

---

### Post by kyphi on 2009-05-27
You do not say which version of VirtualBox you are referring to.

Unless something has changed, the OSE version available via Synaptic does not have USB support whereas the Sun version does.

One way around that is to set up a shared folder for Ubuntu and a VirtualBox installed operating system.  Then you can use USB in Ubuntu and transfer files to the shared folder.

If you want to install the Sun version, you will have to completely uninstall the OSE version first.

URL: [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by semitone36 on 2009-05-27
If youve already done that then check out the [virtualization megathread]("http://ubuntuforums.org/showthread.php?t=973756") in the virtualization section on the forums.  Thats where I learned how to used virtualbox :)

---

### Post by zero777zero on 2009-05-27
i looked at the about window and it doesnt say anything about open source but i prob got it from the respositories. installing the closed source version now

---

