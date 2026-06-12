---
title: "sound stops working :: howto restart??"
date: 2009-01-17
forum: General Help
---

### Post by Salute on 2009-01-17
as per [http://ubuntuforums.org/showthread.php?t=786953&highlight=Sound+stops+working+completely+playing+music+files](http://ubuntuforums.org/showthread.php?t=786953&highlight=Sound+stops+working+completely+playing+music+files)
I boot up and play a song in xmms etc, then fire up a youtube page and get <no sound> and if I reboot I get youtube again (until I use xmms etc that is)
xubuntu gutsy here

how can I reset sound??
(ps: I've tried $sudo /etc/init.d/alsa-utils restart ,with no luck)

---

### Post by Tim Sharitt on 2009-01-17
Are you using alsa or pulseaudio? I'm not sure, but if if your using pulseaudio you might try
```
sudo /etc/init.d/pulseaudio restart
```

---

### Post by Salute on 2009-01-17
I've upgraded to Hardy and no longer have this problem >apparently only a gutsy issue >hooray! It's all in perfect order!

---

