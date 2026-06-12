---
title: "Audio indicator plugin on panel not showing anything on click"
date: 2013-10-19
forum: Desktop Environments
---

### Post by chockopocko on 2013-10-19
On Xubuntu 13.04, when I clicked A on the upper panel (shown below), there was a horizontal slider bar that would control the volume, and a button that  said "Sound Preferences" that would open PulseAudio Volume Control. There was no B. 

Now that I upgraded to Xubuntu 13.10, there is now a B icon that opens up to a vertical slider bar that controls volume. Hovering over it opens a black box that says "Output: X% (where X is a whole number), the decibel level, and "Built-in Audio Analog Stereo"). Hovering over A, part of the Indicator Plugin, shows nothing, and click on it opens a small grey, empty box. B is not removable off the panel - right clicking it shows only "Mute" and a button that says "Sound Preferences," the latter of which actually just opens up to a "System Settings" box with only buttons for "Language Support," "Online Accounts," "Printers," and "Software & Updates." 

What I would like to know is how to have the configuration I had on Xubuntu 13.04 back. On my hard drive, I have Xubuntu 13.10 alongside Windows 7, if that makes a difference. 

Thanks in advance!
[IMG]http://i41.tinypic.com/28w1en4.jpg[/IMG]

---

### Post by Toz on 2013-10-20
A is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/indicator-sound/+bug/1208204"). Post #5 in that bug report contains a temporary workaround until its properly fixed. 

As for B, you wouldn't happen to have Xfce's Audio Mixer plugin enabled (added to the panel)?

---

### Post by Yellow Pasque on 2013-10-21
I forget exactly which package it was (may have been gnome-settings-daemon), but when I installed some gnome- package, that's when B appeared.

---

### Post by Toz on 2013-10-21
> **Temüjin said:**
> I forget exactly which package it was (may have been gnome-settings-daemon), but when I installed some gnome- package, that's when B appeared.

Check with ps to see which process is running:
```
ps -ef | grep $USER
ps -ef | grep $USER | grep -i sound
ps -ef | grep $USER | grep -i mixer
```
See if you can identify it and either remove or disable it.

---

### Post by stinkeye on 2013-10-21
Don't use Xubuntu but just came across this in one of my Rss feeds.
[**_[COLOR="#B22222"]Xubuntu 13.10 Sound Indicator Fix[/COLOR]_**]("http://www.webupd8.org/2013/10/xubuntu-1310-sound-indicator-fix.html")

---

### Post by illage2 on 2013-10-28
> **stinkeye said:**
> Don't use Xubuntu but just came across this in one of my Rss feeds.
[**_[COLOR=#B22222]Xubuntu 13.10 Sound Indicator Fix[/COLOR]_**]("http://www.webupd8.org/2013/10/xubuntu-1310-sound-indicator-fix.html")

I tried doing that but it wouldn't work.  Need another fix for it.

---

### Post by Toz on 2013-10-28
> **illage2 said:**
> I tried doing that but it wouldn't work.  Need another fix for it.
Are you also using Xubuntu 13.10? 

Can you post back the contents of your **/usr/share/dbus-1/services/indicator-sound.service** file?

---

