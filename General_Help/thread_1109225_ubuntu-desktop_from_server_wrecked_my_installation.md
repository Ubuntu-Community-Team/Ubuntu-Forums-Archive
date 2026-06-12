---
title: "ubuntu-desktop from server wrecked my installation !"
date: 2009-03-28
forum: General Help
---

### Post by linuxvacuum on 2009-03-28
I have ubuntu 8.10 server installed. I typed
```
sudo apt-get install ubuntu-desktop
```
to try GNOME.

Here are my results :

1. Boot directly to **BusyBox** with an error I didn't understand.
I fixed it by loading 2.6.27-9-generic instead of 2.6.27-11-generic kernel. What does a desktop have to do with the kernel ???

2. Every application is **so much slower**. Changing from one video to another in SMplayer takes a full 8 seconds! Before is was instantaneous. Loading StepMania with wine has a lot of seconds to wait at the beginning and nothing seems to happen then it loads.

Please help me as this is really infuriating. :shock:

---

### Post by kubug on 2009-03-28
Did you already have the gnome desktop installed? Or did you have a command line installation, and then tried that command?
Did you issue that "apt-get" command via ssh?

---

### Post by linuxvacuum on 2009-03-28
I did not have gnome desktop installed. I typed the command locally not with ssh. Before, I had minimalist window managers.

---

### Post by linuxvacuum on 2009-03-28
Thanks to lykwydchykyn from this post, [http://ubuntuforums.org/showthread.php?t=1108721](http://ubuntuforums.org/showthread.php?t=1108721) and this command ```
sudo aptitude reinstall linux-image-2.6.27-11-generic
```

I am back with kernel 2.6.27-11-generic. Now what is left to fix is the slow problem.

---

### Post by kubug on 2009-03-28
May I ask for some hardware specs? Do you think you have enough memory?

Of course, that doesn't solve the busybox problem. Can you post your error here? Usually you will be able to find it under System->Administation->System Log or using a terminal type "dmesg" and post it here.

---

### Post by kubug on 2009-03-28
I have found in the past, whenever a program seems to "act up", it is good to start it in a terminal and check for error output there.

---

### Post by linuxvacuum on 2009-03-28
Yeah kubug, that's some good advice. I started SMPlayer and StepMania from the terminal but there are no errors, only a long pause between 2 normal steps. I think it is related to the audio server. I solved the busybox error.

---

### Post by kubug on 2009-03-28
It could be that the minimal desktop (fluxbox?) you used before could have used ALSA instead of PulseAudio. I really don't know enough about PulseAudio to know what is really that much better about it. 
I know there are a few people that have switched back to ALSA. 
The following article made mention of that (switching back) and of a problem of having a 10 second delay when playing any sound. Could this be your problem?

[http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/]("http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/")

I think maybe your pulseaudio isn't configured right. Here is the solution from the article above:

> TROUBLESHOOTING: 10 second time out solution below in the comment :P

I finally figure out the 10second lag. Those applications will first look for Pulseaudio, but it is gone, so the 10 second time out before alsa kicks in.

=======
Solution:
=======

+ Edit /etc/mplayer/mplayer.conf, line 74, change the order to the order below (original pulse,alsa)
# Specify default audio driver (see -ao help for a list).
ao=alsa,pulse

+ Totem-gstreamer i can&#8217;t find the config for it yet, so work around is use totem-xine, then check that ~/.config/totem/xine_config , pulseaudio is comment out.

+ System-wide config (so far I only tested with mpg123-alsa, aplay, moc). Backup your /usr/share/alsa/alsa.conf. Then on the very top. Chage it to the following: (alternatively you can comment out /usr/share/alsa/pulse.conf or move it down the list, I prefer remove it anyway since we got a backup)

# pre-load the configuration files

@hooks [
{
func load
files [
"/usr/share/alsa/bluetooth.conf"
"/etc/asound.conf"
"~/.asoundrc"
]
errors false
}
]

---

### Post by linuxvacuum on 2009-03-30
Thanks a bunch kubug! :KS

That was the problem. With my server I had pulseaudio removed in favor of alsa. So pulseaudio retook priority over alsa when I installed ubuntu-desktop.
I commented out the line **"/usr/share/alsa/pulse.conf"** in the file you told me. Thanks again!

---

### Post by kubug on 2009-03-30
Good to hear you good it working. Your welcome.

---

