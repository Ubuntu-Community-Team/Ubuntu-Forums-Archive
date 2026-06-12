---
title: "X session error"
date: 2008-11-05
forum: Desktop Environments
---

### Post by dakkar9999 on 2008-11-05
Hello,

to solve a problem with my audio card (M-Audio Revolution)  I had installed all the modules of Pulse Audio.  Using it in my Ubuntu 8.04 was ok.But after installing 8.10, Pulse audio did not work anymore.  I ended up removing Pulse Audio as per instructions on this site[http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html]("http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html")

Now my sound works fine, but I get an error at login.

"could'nt exec /usr/bin/pulse_session no such file or directory"

I can't log in normally I have to login gnome failsafe.

How can I fix this?

Thanks!

---

### Post by edyeeh on 2008-11-09
same here. I did the same thing with pulse audio. 

hope someone have a solution on this since I don't want to install from scratch.

maybe i'll try installing some of the files I removed although I don't remember any of them

---

### Post by edyeeh on 2008-11-09
got it. I installed Pulse Audio again from the terminal

```
sudo apt-get install pulseaudio
```

I'm not sure if the its the only requirement for the session. If it doesn't work, try installing other packages on the packages site.

[http://packages.ubuntu.com/intrepid/sound/pulseaudio](http://packages.ubuntu.com/intrepid/sound/pulseaudio)

---

