---
title: "Ubuntu 9.04 on Inspiron 1545"
date: 2009-10-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kalos on 2009-10-18
I've been writing this down for a while and realised I should post in case it helps anyone else who picked up an Inspiron 1545.

Most things work without fiddling with config files: webcam, wireless, suspend/hibernate, external monitors, compiz. My wireless occasionally drops out (keeps trying to connect and wants a new password), but suspending usually fixes that.

Gnome-do, banshee, cheese, and others have made my transition from my old iBook and back to Ubuntu pretty comfortable.


Problems:
Volume really quiet
[list]
    [*] sudo aptitude remove pulseaudio
    [*] [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7361601](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7361601)
    [*] run alsamixer and pump up the Front volume level all the way to 100.
    [*] sudo aptitude install ubuntu-restricted-extras
    [*] It's usable now, but still fairly quiet.
[/list]

Gmail font looks bad
    * [http://www.kilobitspersecond.com/2009/04/24/liberation-the-new-arial-sans-serif-substitute-in-jaunty/](http://www.kilobitspersecond.com/2009/04/24/liberation-the-new-arial-sans-serif-substitute-in-jaunty/)

Mic doesn't work
[list]
    [*] fix: [http://ubuntuforums.org/showthread.php?p=7683999#post7683999](http://ubuntuforums.org/showthread.php?p=7683999#post7683999)
    [*] possibly have to do this: echo options snd-hda-intel model=auto >> /etc/modprobe.d/alsa-base.conf 
    [list=1]
    [*] Goto mixer applet (volume control in top panel)
    [*] Left click and select Volume Control
    [*] Click Preferences and enable "Capture" and "Capture 1"
    [*] Switch to Recording tab and unmute "Capture" and "Capture 1"
    [*] Now alsamixer shows some red stuff and "L R" around the bottom of Capture
    [/list]
[/list]

Partition has silly label (110 GB volume)
    * I mounted 110 GB as a data partition (I mount it inside of home and have everything in there instead of having a home partition). Since I did that, Ubuntu shows it on the desktop as "110 GB volume"
    * install gparted and use that to unmount, label, and apply, then restart ubuntu

Codecs are missing
    * aptitude install non-free-codecs



Some fun things I added:

Two finger scrolling
[list]
    [*] [http://ubuntuforums.org/showthread.php?t=1127095&page=2](http://ubuntuforums.org/showthread.php?t=1127095&page=2)
    [*] to prevent two-finger middle click:
    [*][list]
    [*] [http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html](http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html)
    [*] sudo gvim /etc/hal/fdi/policy/11-x11-synaptics.fdi
    [*] add <merge key="input.x11_options.TapButton2" type="string">0</merge>  <!--two finger tap -> nothing(0) -->
    [/list]
[/list]
Install skype
    * add Medibuntu repository [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
    * apt-get install skype

Remove the numbered weeks on calendar:
    * gconf-editor under /apps/panel/applets/clock_screen0/prefs deselecting show_week_numbers.

---

### Post by LinnyLappyNooby on 2009-11-16
Hi Kalos, I want to get a Dell like yours and put Ubuntu on it but I need to know if I can post videos to YouTube with it as that's all I do on the computer really. Could you perhaps test this for me (and others who may be wondering)? If you're not familiar, while logged in at youtube.com you click "Upload" and then "Record from Webcam" and it uses Flash to access your cam and mic so you can record directly to the site without making videos on the computer and then uploading them. (If there's working software to do it the other way that's fine but I'd prefer the easy way; I don't make fancy videos with edits, I just vlog.) No need to link to your video if you don't want to; I just want to hear that it works. :-)

I don't have my own computer (yet!) so I can't install Ubuntu on here to test if it even works with the OS, let alone the Dell. I'll have to get it with Windows as the pre-installed Ubuntus no longer have webcams! (Grrr!) But when I finally get my own computer I want to escape from Windows with all its troubles, so I'll delete it if Ubuntu on the Dell can do YouTube vlogs.

Thanks even if you can't help me out, you already did with this info which I'm sure I'll find useful at some point if I take the plunge. :-)

---

### Post by kalos on 2010-01-28
You may have already got your new computer, but I finally tried...


I tried to upload to youtube like you described and it failed:
```
Failed (unable to convert video file)
```

I'm not sure if this is a problem with flash or ubuntu drivers. I'm able to take videos no problem with [Cheese]("http://projects.gnome.org/cheese/").

I _[uploaded a video]("http://www.youtube.com/watch?v=PAZ1037XXLg")_ so you can see the video quality. It doesn't seem to be as good as the [same camera on Windows]("http://www.youtube.com/results?search_query=inspiron+1545+webcam"). It looks a bit grainier and a lot laggier, but it could be my lighting conditions.

---

