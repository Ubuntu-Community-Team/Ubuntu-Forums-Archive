---
title: "Zoom?"
date: 2020-04-29
forum: Desktop Environments
---

### Post by rsteinmetz70112 on 2020-04-29
Since I've been working form home using Ubuntu 18.04 I've had a number of video conferences using various services. I usually take them using a browser but an increasing number use soom. That service offers a Ubuntu desktop package but it only offers 2 Ubuntu versions once for 12.04 and one for 14.04 obviously both are pretty old. Has any one used those and do they work or am I missing something and are there newer debs out there somewhere?

---

### Post by CelticWarrior on 2020-04-29
The 14.04+ version should be also for any release newer than 14.04.

---

### Post by Autodave on 2020-04-29
Been running the 14.04 version here on 3 different machines with no issues.

---

### Post by ajgreeny on 2020-04-29
> **Autodave said:**
> Been running the 14.04 version here on 3 different machines with no issues.
Same here, where I've been using it for meetings since Covid-19 appeared on the scene.

If you use xscreensaver watch out for zoom taking over the screensaver and autostarting whenever the screensaver should have done.
There is a thread on the forum with a workaround for this problem here on the forum at [https://ubuntuforums.org/showthread.php?t=2441407](https://ubuntuforums.org/showthread.php?t=2441407) by editing the configuration file for xscreensaver.

---

### Post by rsteinmetz70112 on 2020-04-29
Thanks.

---

### Post by DuckHook on 2020-04-29
Many forum members know the irredeemably deplorable opinion I have of Zoom on both the security and the tracking front. That said, for some, it is simply unavoidable. If you must run it, then the latest version is your best choice because it has more of its myriad security holes filled. The latest Zoom client can be installed as a snap.
```
duckhook@Zeus:~$ snap info zoom-client
name:      zoom-client
summary:   ZOOM Cloud Meetings
publisher: Oliver Grawert (ogra)
store-url: https://snapcraft.io/zoom-client
contact:   ogra@ubuntu.com?subject=zoom-client
license:   Proprietary
description: |
  Video conferencing with real-time messaging and content sharing
  
  https://zoom.us provides simplified video conferencing, whiteboard sharing
  and messaging across any device. This is an unofficial re-pack of the debian
  package provided by zoom.us
  
  The source code for the snap package can be found at https://github.com/ogra1/zoom-snap
  
  Please file issues under https://github.com/ogra1/zoom-snap/issues
snap-id: 76rrD7USwCJrZgepbRk7UdFEWON3tVKX
channels:
  latest/stable:    5.0.398100.0427 2020-04-29 (74) 148MB -
  latest/candidate: 3.5.392530.0421 2020-04-29 (71) 185MB -
  latest/beta:      3.5.392530.0421 2020-04-29 (71) 185MB -
  latest/edge:      5.0.398100.0427 2020-04-29 (74) 148MB -
```
You are far, far better off with this Snap than you are with the five-year-old version in the repos. That one is likely to have more security holes than Swiss cheese.
```
sudo snap install zoom-client
```

---

### Post by iamjiwjr on 2020-04-30
Flatpak has the most recent version, Version 5, that was just released. It claims to have a lot of new security features. I'm not smart enough to know if that's accurate or not, but that's what they claim. The UI, at least, has readily identifiable changes you can make in that regard.

---

### Post by DuckHook on 2020-04-30
> **iamjiwjr said:**
> Flatpak has the most recent version, Version 5, that was just released. It claims to have a lot of new security features. I'm not smart enough to know if that's accurate or not, but that's what they claim. The UI, at least, has readily identifiable changes you can make in that regard.
As you can see from my post above, the Snap version is also version 5.0.```
…
channels:
  latest/stable:    5.0.398100.0427 2020-04-29 (74) 148MB -
…
```
Just make sure to install the stable channel.

Since snapd is installed by default in every current version of 'buntu, I don't see the advantage in installing yet another package system like flatpak to avail oneself of an already current and existent app. The less attack surface, the better, and flatpak increases attack surface by a lot.

Re Zoom: given how much flak they have taken over their security holes, I'm sure the more recent the package, the better. This is generally true of any app.

---

### Post by andrew.46 on 2020-05-01
I must have missed Zoom version 4 :)

---

### Post by grahammechanical on 2020-05-02
zoom-client is proprietary software so the snap developer cannot change any of the code but I think that he has made use of some possibilities of the snap format to give users some more control and may be a bit more security.

When the snap version is installed the snap store will provide a settings dialog giving greater control of the application. 

P.S. it works but sometimes due to the amount of data coming down my non-fibre broadband line the app freezes leaving just the audio working. There have been times when a reboot and a rejoin was necessary to get into the meeting

Regards

---

### Post by andreabur123 on 2021-04-03
I am still using this platform for video conferences. It's the easiest to use. From my point of view, the Zoom platform had evolved a lot last years. Due to the COVID-19 pandemic situation, a lot of people starting to use it. I think that is a great step in digital evolution. Recently, I had a great experience with the platform from [brightvisionevents.co.uk]("https://brightvisionevents.co.uk/conferences/live-conference-streaming/"). We had there a lot of interesting team-building games where we met a lot of new and interesting people. From my point of view, such games must be implemented on the zoom platform.

---

