---
title: "Gnome extremely high CPU usage"
date: 2015-08-12
forum: Desktop Environments
---

### Post by PWMKzzJ on 2015-08-12
I'm hoping that someone can help explain this to me. I have Ubuntu GNOME (14.04.3) installed on an Intel DCCP847DYE to use as a small, quiet, low power server. It's only really used for Samba, MySQL, FTP and Transmission-deamon. I normally use SSH or Webmin to do anything with it, however I didn't use the server ISO since it is sometimes a lot easier to be able to use the GUI or take advantage of X11 forwarding through SSH. I wanted it to boot to the console by default and only use X when needed, I did this by editing /etc/default/grub and changing the entry "GRUB_CMDLINE_LINUX_DEFAULT" from "quiet-splash" to "text" like a lot of forums online recommend. However if I do that and then run the command "startx" after logging in, I've noticed that gnome-shell goes from using an average of 6-8% of my CPU to about 60-80%. After some research it seems that it's doing that because its not using any hardware acceleration on the GPU and running everything on the CPU. 

I would like to know if;
1) that is in fact the reason for the high processor usage
2) if there is a way to stop that and still boot to console by default
and
3) Why is that the case

I really liked the fact that I could only run Xserver when needed (locally or using x2go) and spare my little system the overhead of a GUI, but I can't stand the fact that it can't even scroll through a web page in Chrome of Firefox without it jumping all over and giving me a headache.
Thanks for the help.

---

### Post by workshopsystems on 2015-08-13
```

ps -Ao comm,pcpu --sort=-pcpu | head -n 6

```

check what applicatoion is using most memory and debug there might be a memory leak

---

