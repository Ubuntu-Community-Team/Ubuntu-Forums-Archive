---
title: "Sound icon flat - no volume in Xubuntu 13.10"
date: 2013-11-04
forum: Desktop Environments
---

### Post by geovino on 2013-11-04
The sound icon is flat showing no volume, a thread mentioned downgrading the indicator-sound. But how do you downgrade indicator-sound_12.10.2daily13.04.12-0ubuntu1_amd64 in Xubuntu 13.10 ?

---

### Post by Toz on 2013-11-04
[See here]("http://www.webupd8.org/2013/10/xubuntu-1310-sound-indicator-fix.html") for temporary workaround.

---

### Post by geovino on 2013-11-04
I followed the instructions and rebooted, but still no sound icon showing any volume. But the sound does work, just not the icon.

---

### Post by Toz on 2013-11-05
Can you post back the contents of the **/usr/share/dbus-1/services/indicator-sound.service** file?

---

### Post by geovino on 2013-11-05
here it is:

[D-BUS Service]
Name=com.canonical.indicator.sound
#Exec=/usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service
Exec=/bin/sh -c 'if [ -n "$(ps -U $USER | grep xfce4-panel)" ]; then /usr/lib/i$

---

### Post by Toz on 2013-11-05
> **geovino said:**
> here it is:

[D-BUS Service]
Name=com.canonical.indicator.sound
#Exec=/usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service
Exec=/bin/sh -c 'if [ -n "$(ps -U $USER | grep xfce4-panel)" ]; then /usr/lib/i$

That file should read:
```
[D-BUS Service]
Name=com.canonical.indicator.sound
#Exec=/usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service
Exec=/bin/sh -c 'if [ -n "$(ps -U $USER | grep xfce4-panel)" ]; then /usr/lib/indicator-sound-gtk2/indicator-sound-service;else /usr/lib/$(arch)-linux-gnu/indicator-sound/indicator-sound-service;fi'
```
...you're missing a large part of it.

---

### Post by geovino on 2013-11-05
I'll try again. Seems like its not pasting in all of it.

---

### Post by geovino on 2013-11-05
Now it's working... Thanks :)

---

### Post by infamous.9 on 2013-11-12
Hi, I am extremely new to Xubuntu and am having this problem as well. I found the file to change, but it says i do  have the permissions to save the file. Any help on editing this file and being able to apply it?
Thanks
-Matt

---

### Post by Toz on 2013-11-12
> **infamous.9 said:**
> Hi, I am extremely new to Xubuntu and am having this problem as well. I found the file to change, but it says i do  have the permissions to save the file. Any help on editing this file and being able to apply it?
Thanks
-Matt

Hello Matt and welcome to the forums.

This file is protected and requires root access to edit. The good news is that your account, if it was the first one created, should have the ability to edit this file using the [sudo]("https://help.ubuntu.com/community/RootSudo") command. To do so, first open a terminal window then run the command:
```
sudo -i mousepad /usr/share/dbus-1/services/indicator-sound.service
```
...and it will prompt you for a password. Enter your login password. When the file opens, make the necessary changes and save the file. You'll need to log out and back in again to see the change.

---

### Post by infamous.9 on 2013-11-13
Thank you soo much! It works prefectly now. Using Xubuntu on a old pc and so far making this computer run like a new computer! And this forum is a great place for answers, great work
Thanks!

---

### Post by pqwoerituytrueiwoq on 2013-11-13
> **Toz said:**
> That file should read:
```
[D-BUS Service]
Name=com.canonical.indicator.sound
#Exec=/usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service
Exec=/bin/sh -c 'if [ -n "$(ps -U $USER | grep xfce4-panel)" ]; then /usr/lib/indicator-sound-gtk2/indicator-sound-service;else /usr/lib/$(arch)-linux-gnu/indicator-sound/indicator-sound-service;fi'
```
...you're missing a large part of it.

that is just how nano shows what does not fit on the visible line

---

