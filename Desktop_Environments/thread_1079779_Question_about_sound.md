---
title: "Question about sound"
date: 2009-02-24
forum: Desktop Environments
---

### Post by rwpage on 2009-02-24
I have encountered this problem only a few times. There are times that I randomly lose sound and the only way to get it back is to restart the computer. I can't really duplicate the problem either. I was just wondering if maybe there was a way to reload sound or something.

---

### Post by phantom3113 on 2009-02-24
I have a similar issue (I need to reload the sound whenever I plug my headphones in) and this works for me:

```
killall pulseaudio

sudo alsa force-reload

pulseaudio -D
```

That basically does the same thing for the sound as rebooting the computer. Sometimes, I find that if I'm running Rhythmbox or something while doing this, (rhythmbox paused) rhythmbox will freeze and the sound won't actually reboot. If this happens, close anything that's using sound and run those commands again. Also, the volume control tray icon may not respond correctly (shows sound is muted when it's not).

---

### Post by rwpage on 2009-02-24
I think before you run those commands you could do
```
lsof | grep pcm
```
to get a list of processes using audio, and then you could choose to kill them or not. And thanks for the help I'll try it next time I have a problem.

---

### Post by rwpage on 2009-02-24
Just did a bit of searching, came up with this.

If the above doesn't work (for other people searching and finding this post) maybe you could try:
```
sudo /etc/init.d/alsa-utils restart
```
If anyone has any feedback let me know.

---

