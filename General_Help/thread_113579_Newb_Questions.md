---
title: "Newb Questions"
date: 2006-01-06
forum: General Help
---

### Post by Sopranosmainman on 2006-01-06
1. How do i unistall programs/packages that were not downloaded from ADEPT.... such as from Automatix or through rpms.....or even programs preinstalled that i have no use for but are not found in ADEPT to be uninstalled

2. I have mplayer and the plugin for firefox 1.07 for kubuntu..... but when i have to play streaming wmv video... or streaming Real Audio music or video.... it doest play..... and for the wmv's it will load and buffer then stop.. and not even play. 

3. For programs installed through rpms... if a new updated version comes out, do i just download and intall the rpm and it will update the program or do i have to unistall the program frist and install the new version. THanks

4. Does Kubuntu not support sleep/hibernation mode... i used it the today on my laptop, turned it on and it was just frozen on a black screen.

---

### Post by flight_master on 2006-01-06
Hi,

1.
```
sudo apt-get remove <program name>
``` will remove the application.

2.
Do you have the MP3 support installed? It's a Gstreamer plugin but the name escapes me.

3. K/Ubuntu uses *.DEB files, not *.RPM ;) best practice is to apt-get remove, and then apt-get install, if the application is in the repository. If it isn't, you need to ALWAYS remove the old app, as there may be conflicts.

4. What laptop is it? What about your video card?

Regards,
Christian

---

### Post by Sopranosmainman on 2006-01-06
[QUOTE=flight_master]Hi,

1.
```
sudo apt-get remove <program name>
``` will remove the application.

2.
Do you have the MP3 support installed? It's a Gstreamer plugin but the name escapes me.

3. K/Ubuntu uses *.DEB files, not *.RPM ;) best practice is to apt-get remove, and then apt-get install, if the application is in the repository. If it isn't, you need to ALWAYS remove the old app, as there may be conflicts.

4. What laptop is it? What about your video card?

Regards,
Christian[/QUOTE]

3. Your right.. i meant to say deb... but they start off as rpms sometimes :)

4. IBM Thinkpad R40.... its ATI Mobility Radeon 7500 ..... dont know if Kubuntu auto decected this... and if i dont have it... how do i download and isntall the drivers. Thanks

---

### Post by flight_master on 2006-01-06
Hi,

Follow these two topics for the ATI drivers:

[Easy to Install / Older] [http://ubuntuforums.org/showthread.php?t=75378](http://ubuntuforums.org/showthread.php?t=75378)
[Harder to Install / Newer] [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)


Regards,
Christian

---

