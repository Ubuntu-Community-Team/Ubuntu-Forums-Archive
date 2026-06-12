---
title: "Please explain"
date: 2005-09-14
forum: Desktop Environments
---

### Post by philpot on 2005-09-14
Will someone explain some things to me please?

1. If one installs Kubuntu on a Mac (or indeed any other platform), does the installer install a full version of Ubuntu, and then put the KDE desktop environment on top? 

2. If I have Kubuntu installed and working, can I "convert" it to Ubuntu, by installing Gnome over the top?

3. If I download the "Breezy Badger" preview, will this essentially be the same as the release version reportedly being available in October? i.e, what is the difference between a release version and a preview version?

4. When a Kubuntu (or Ubuntu) installer starts, after the language/hardware selection process, it does a DHCP Network discovery routine. If I want to configure the network manually, I have to diconnect the network cable so that the DHCP process fails, and the installer allows me to manually enter IP addresses etc. Is there a way to launch this manual configuration process after the installation is complete? The KControl panel: Network component seems awfully buggy to me. I have messed about with /etc/network/interfaces and then /etc/init.d/networking restart, but the settings still don't seem to "stick" (i have seen this issue before on this forum).

5. There is no question 5.

6. How can I configure Firestarter (or something else) to run in "stealth mode" and  serve websites via port 80? Is there a command to open/close various ports (I want to close everything except 80)

Many thanks.

Phil

---

### Post by snowjunkie on 2005-09-14
I can answer some of these...

2. Yes.  Use ```
sudo apt-get install gnome-desktop
```

3. You could expect a preview release to be in an unfinished state.  For example, have features yet unimplemented, or still have a few bugs that need ironed out.

Hope that helps.

---

### Post by agm642 on 2005-09-14
2.Or, if this fails, use: ```
sudo apt-get install ubuntu-desktop
```
4.I am not on my Kubuntu box now, but I think you can go K Menu -> System -> Networking, or something like that...

---

### Post by snowjunkie on 2005-09-14
[QUOTE=agm642]2.Or, if this fails, use: ```
sudo apt-get install ubuntu-desktop
```[/QUOTE]

That's what I meant, sorry!

---

### Post by agm642 on 2005-09-14
It's OK, I wasn't sure about the correct one myself.

---

