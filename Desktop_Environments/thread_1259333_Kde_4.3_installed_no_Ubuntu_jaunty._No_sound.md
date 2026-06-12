---
title: "Kde 4.3 installed no Ubuntu jaunty. No sound"
date: 2009-09-06
forum: Desktop Environments
---

### Post by praveesh on 2009-09-06
I have installed kde 4.3.1 on my Ubuntu jaunty . Now there is no sound in the kde apps(dolphin , amarok,juk etc). No problem with the Gnome apps. Everytime when I log in , the kde informs that the default sound device is not working and is falling back to the next device. Still there is no sound. In the kde controlpanel, the backend is shown as gstreamer(i have installed the kde-backend-gstreamer). For the kde , the packages I have installed are kde-standard , plasma-widgets-addons, kde-multimedia , gtk-qt-engine and their dependancies. Is there any need to install more packages. IN KUBUNTU , THERE IS NO PROBLEM. I have googled and searched in this forum ,but didn't get any good results.

---

### Post by simonyee on 2009-09-06
> **praveesh said:**
> I have installed kde 4.3.1 on my Ubuntu jaunty . Now there is no sound in the kde apps(dolphin , amarok,juk etc). No problem with the Gnome apps. Everytime when I log in , the kde informs that the default sound device is not working and is falling back to the next device. Still there is no sound. In the kde controlpanel, the backend is shown as gstreamer(i have installed the kde-backend-gstreamer). For the kde , the packages I have installed are kde-standard , plasma-widgets-addons, kde-multimedia , gtk-qt-engine and their dependancies. Is there any need to install more packages. IN KUBUNTU , THERE IS NO PROBLEM. I have googled and searched in this forum ,but didn't get any good results.

check what is the sound card model first and post here

Open terminal and type lspci

---

### Post by jacksaff on 2009-09-06
Click the speaker icon in the system tray and open the mixer. For some reason some of my volume sliders keep getting reset to middling values which are inaudible with the volume I set my actual speakers...

---

### Post by praveesh on 2009-09-06
> **simonyee said:**
> check what is the sound card model first and post here

Open terminal and type lspci

Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

---

### Post by praveesh on 2009-09-06
> **jacksaff said:**
> Click the speaker icon in the system tray and open the mixer. For some reason some of my volume sliders keep getting reset to middling values which are inaudible with the volume I set my actual speakers...

That isn't the problem . The kmixer slider is at the maximum. More over there is sound in the Gnome apps(rhythmbox) and Iam able to control their sound with the kmixer

---

### Post by praveesh on 2009-09-07
Please help

---

### Post by praveesh on 2009-09-08
Will installing phonon-backend-xine  solve the problem? If I do so, will I able to play sound using Gnome applications that use gstreamer? While using xine as backend, is it possible to control the sound of the applications that use gstreamer by kmix?

---

### Post by praveesh on 2009-09-13
Succeeded . Installing phonon backend xine and changing the audio device to pulseaudio (could not find alsa) enabled the qt /kde apps to produce sound.

---

