---
title: "Piping a command to Notify-OSD"
date: 2016-02-21
forum: Desktop Environments
---

### Post by mrb_101 on 2016-02-21
Hey.
I was wondering how would i be able to send a notification from a shell command to pop-up a notification using the Notify-OSD.
for example increasing the volume through a command line:

$ pactl set-sink-volume 1 +5%

How can i make the notification window pop-up with an indicator of volume ?
Thanks

---

### Post by CantankRus on 2016-02-22
You could use amixer.
eg
```
pactl set-sink-volume 1 +5% && **notify-send -i multimedia-volume-control "Volume" "$(awk -F"[][]" '/dB/ { print $2 }' <(amixer sget Master))"**
```

---

