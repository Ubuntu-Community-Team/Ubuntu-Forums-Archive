---
title: "Change default for opening mounted volumes in Unity launcher"
date: 2011-04-29
forum: Desktop Environments
---

### Post by TheCat on 2011-04-29
I automount two NTFS volumes on login.  These display in both the desktop and the Unity launcher.

The first time I clicked one of them in the Unity launcher, it asked if I wanted to use Nautilus or Thunar.  I chose Thunar.

Now, when I open the volumes in the Unity launcher, it always uses Thunar.  When I open the volumes on my desktop, it always uses Nautilus.

Is there any way to standardize these, so that I use either Thunar or Nautilus, but not both?  And how do I switch back and forth?  Where can I reset the Unity launcher to use Nautilus again?

---

### Post by Krytarik on 2011-04-30
Please post the content of "~/.local/share/applications/mimeapps.list".

Greetings.

---

### Post by TheCat on 2011-04-30
```
[Added Associations]
application/x-ms-dos-executable=wine.desktop;
application/octet-stream=gedit.desktop;
text/plain=gedit.desktop;wine-extension-txt.desktop;openoffice.org-writer.desktop;
application/x-wine-extension-ini=wine-extension-ini.desktop;gedit.desktop;
application/x-java-archive=sun-java6-java.desktop;openjdk-6-java.desktop;
application/pdf=evince.desktop;gimp.desktop;userapp-evince-9AR0HV.desktop;
application/x-cisco-vpn-settings=gedit.desktop;
application/xml=bluefish.desktop;
x-scheme-handler/file=exo-file-manager.desktop
x-scheme-handler/trash=exo-file-manager.desktop
x-scheme-handler/http=google-chrome.desktop;
x-scheme-handler/https=google-chrome.desktop;

[Default Applications]
x-scheme-handler/http=google-chrome.desktop
x-scheme-handler/https=google-chrome.desktop
```

---

### Post by Krytarik on 2011-04-30
I marked the only ones that may be related. Backup these settings, remove them, and relogin.
```
[Added Associations]
application/x-ms-dos-executable=wine.desktop;
application/octet-stream=gedit.desktop;
text/plain=gedit.desktop;wine-extension-txt.desktop;openoffice.org-writer.desktop;
application/x-wine-extension-ini=wine-extension-ini.desktop;gedit.desktop;
application/x-java-archive=sun-java6-java.desktop;openjdk-6-java.desktop;
application/pdf=evince.desktop;gimp.desktop;userapp-evince-9AR0HV.desktop;
application/x-cisco-vpn-settings=gedit.desktop;
application/xml=bluefish.desktop;[B][COLOR=Red]
x-scheme-handler/file=exo-file-manager.desktop
x-scheme-handler/trash=exo-file-manager.desktop[/COLOR][/B]
x-scheme-handler/http=google-chrome.desktop;
x-scheme-handler/https=google-chrome.desktop;

[Default Applications]
x-scheme-handler/http=google-chrome.desktop
x-scheme-handler/https=google-chrome.desktop
```

---

### Post by TheCat on 2011-04-30
That doesn't seem to have had an effect.

---

### Post by Krytarik on 2011-04-30
> **TheCat said:**
> That doesn't seem to have had an effect.
Then restore the settings as they were.

---

### Post by TheCat on 2011-04-30
:d

---

### Post by Krytarik on 2011-04-30
Since I have no Natty install running, I can only guess now:

Check the settings in "dconf-editor", see this guide on how to install it, and more:
[http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html](http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html)

---

### Post by TheCat on 2011-04-30
Did that already, no answers appear there.

---

### Post by TheCat on 2011-05-01
So, in a backhanded fashion, I solved this by removing Thunar from my system.  Clicking on a mounted volume in the Unity launcher after removing Thunar caused it to re-prompt me to ask which file manager I wanted to use, and I was able to choose Nautilus.

---

