---
title: "Sound not recognized by gnome"
date: 2013-07-18
forum: Desktop Environments
---

### Post by doublerainbow64 on 2013-07-18
Hello,

first of all, I'm pretty new to this forum and gnome3. :-)

I'm running Ubuntu GNOME 13.04 (raring) on my Sony Vaio VPCSE1V9E. My sound is working perfectly and I can control everything using alsamixer. However, there is no sound icon in my top bar and in System Settings -> Sound underneath where it says "Choose a device for sound output:" there is no element in the listbox. I also cannot use my volume-up and -down buttons on my keyboard which used to work on Kubuntu.

Thank you in advance,
doublerainbow64

---

### Post by dino99 on 2013-07-18
[http://askubuntu.com/questions/182711/how-do-i-reinstall-the-sound-icon-sound-menu](http://askubuntu.com/questions/182711/how-do-i-reinstall-the-sound-icon-sound-menu)

---

### Post by doublerainbow64 on 2013-07-18
Thanks for you help! I just tried that out. indicator-sound installs without any problems and I rebooted afterwards. However, the problem persists. Something else I'm supposed to do? In the thread, you mentioned, the guy says he cannot open gnome-volume-control-applet. I have the same problem, the command is not recognized by my system.

---

### Post by doublerainbow64 on 2013-07-19
I tried this:

```

sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload

```

And this:

```

sudo adduser my-login-name audio

```

No effect.

---

### Post by dino99 on 2013-07-19
the logs might help you find what is wrong : /var/log/ & .xsession-errors (ctrl+h to unhide it)
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by doublerainbow64 on 2013-07-20
I'll take a look at that.

Another hint, that might help: When I  log out from my user account, the sound-icon in the top bar reappears  and is working properly. I created a new user account and logged in, the  sound icon disappeared.
In addition, when I try to open gnome-sound-applet in terminal, it says:

```
(gnome-sound-applet:5125): sound-cc-panel-WARNING **: Failed to connect context: Connection refused
```

In  another thread I found somebody complaining, that KDE apps cause this  problem and deactivating sound notifications in KDE System Settings  helped. I did so, but this did not have any effect either.

---

### Post by doublerainbow64 on 2013-07-31
I'm still here, I hope somebody else is with me. :-)

---

### Post by doublerainbow64 on 2013-07-31
I think I know, what the problem might be. When I run pulseaudio in terminal it returns:

```
$ pulseaudio
E: [pulseaudio] core-util.c: Home directory not accessible: Permission denied
```

I moved my home directory to a NTFS partition _after_ installing Ubuntu GNOME. This could have caused some trouble. Any ideas, how to fix that?

EDIT: Seems like [this]("http://askubuntu.com/questions/63485/problem-with-pulse-audio-with-ntfs-partition") is the problem. Anybody any suggestions?

---

### Post by doublerainbow64 on 2013-08-01
Well, I just reinstalled my system, using an EXT4 as /home directory. Thanks for your help anyway.

---

