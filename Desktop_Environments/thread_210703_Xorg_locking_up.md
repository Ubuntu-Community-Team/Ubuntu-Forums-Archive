---
title: "Xorg locking up"
date: 2006-07-07
forum: Desktop Environments
---

### Post by apoth on 2006-07-07
GDM loads fine but if I log in then before the desktop loads up it freezes. SSH'ing in remotely tells me that the CPU is being thrashed by Xorg. Also, I have fluxbox installed and I tried 'Select Session' to see if it was Gnome causing it but just hitting 'Select Session' freezes everything too.

Anyone else suffering from this? It's only happened in the last 24 hours, I'm not sure if there's been any Xorg updates recently - the box has probably been up 1-2 weeks until it was rebooted yesterday.

Any suggestions would be appreciated, thanks.

---

### Post by jvictor on 2006-07-07
Not sure if this can be of help, but I used to get random freezes in Dapper and had to disable AGP for my nvidia card.

Use the 

Option "NvAGP" "0"

in xorg.conf

---

### Post by apoth on 2006-07-07
Thanks for the suggestion. That didn't make any difference (the Device section I assume it's meant for?) but changing the driver to the nv one instead of nvidia has let me in, obviously it's not desirable but it's a damn sight better than no X.

---

