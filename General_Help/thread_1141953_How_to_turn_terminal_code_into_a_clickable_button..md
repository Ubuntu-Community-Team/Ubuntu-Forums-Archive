---
title: "How to turn terminal code into a clickable button."
date: 2009-04-28
forum: General Help
---

### Post by noseforsharpies on 2009-04-28
Anyone know how to transform a line or two of terminal code into a clickable button? The lines are:

killall pulseaudio

sudo alsa force-reload 

pulseaudio -D

Thanks for the help.

---

### Post by spiderbatdad on 2009-04-28
i think the first problem you'll have is the use of sudo...this would require a password to execute. Instead try your script without sudo. Make the file owned by root and place it in /usr/local/sbin. Give the files permissions like 755. Then create your launcher by right click on desktop or panel. For the launcher command, point to the file: /usr/local/sbin/your_file.sh

Also I think your script needs a little modification, but I'm not much with bash...i think something like this:

#!/bin/bash
sleep2
killall pulseaudio &&
alsa force-reload &&
pulseaudio -D
exit

---

