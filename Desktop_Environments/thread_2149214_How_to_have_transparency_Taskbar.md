---
title: "How to have transparency Taskbar ?"
date: 2013-05-28
forum: Desktop Environments
---

### Post by kamrava on 2013-05-28
Hi there
How can i have a transparency taskbar ?

Like this :

[IMG]http://up.vbiran.ir/uploads/13697239608569_1GlossyTaskbar.jpg[/IMG]

Thank You

---

### Post by TenPlus1 on 2013-05-28
Install either Ubuntu Tweak or Unity Tweak and you will find an option for making the top bar translucent...

---

### Post by kamrava on 2013-05-28
I tried below command to get Unity tweak for Ubuntu 12.0.4.2 :

```
sudo add-apt-repository ppa:freyja-dev/unity-tweak-tool-daily
  sudo apt-get update && sudo apt-get install unity-tweak-tool
```

but i get below error :
```
.
.
.
Err http://ppa.launchpad.net precise/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
W: Failed to fetch http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by zombifier25 on 2013-05-28
unity-tweak-tool is not available for Precise. Use something else instead, like Ubuntu Tweak.

---

### Post by Frogs Hair on 2013-05-28
Edit: See above .

---

### Post by grahammechanical on 2013-05-28
With 12.04 we install Compiz Configuration Settings Manager (CCSM) and load it and open the Ubuntu Unity Plugin and on the General tab we see the label Panel Opacity. Lower the setting to 0.0000 or 0.0001 and that should give you a transparent top panel.

You can also reduce the opacity of the Launcher background by going to the Launcher tab (it may be called Experimental in 12.04) and lowering the Launcher Opacity from there.

With 13.04 it is a little trickiery because there is a limit to how low the top panel transparency will go and this is because the top panel is connected to the Dash. So, you will not get it completely transparent unless we use CCSM to lower the Dash background colour to 2. You do this under the General tab. Click on panel labelled Background Color and Pick a Color dialog will appear and you will see an Opacity slider.

Regards.

---

### Post by deadflowr on 2013-05-28
Are you really running Kubuntu anyway?

Then I'd go looking in system settings and Desktop Effects.

---

