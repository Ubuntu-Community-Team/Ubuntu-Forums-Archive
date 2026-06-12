---
title: "Which is the utility for configuring sound in Ubuntu?"
date: 2006-07-09
forum: Desktop Environments
---

### Post by vinayasurya on 2006-07-09
Which program detect and configures sound in Ubuntu? Also i want to know how can I change the default VCD player from totem to something like vlc which can play VCDs?

---

### Post by vinayasurya on 2006-07-13
give me a reply plz....

---

### Post by jordilin on 2006-07-13
In order to configure the sound, I use alsamixer. Just type $alsamixer.

---

### Post by kpkeerthi on 2006-07-13
Go to System -> Preferences -> Sound. Select your sound device and see if something is muted.

---

### Post by Ramses de Norre on 2006-07-13
For the VCD thing (I assume VCD is a video format?) right click on such a file in nautilus and select 'properties' then pick the "open with" tab and select the application you want to open the file with. This is saved for all files of the same format then (as long as you open them with nautilus, which includes the desktop).

---

### Post by vinayasurya on 2006-07-13
> **Ramses de Norre said:**
> For the VCD thing (I assume VCD is a video format?) right click on such a file in nautilus and select 'properties' then pick the "open with" tab and select the application you want to open the file with. This is saved for all files of the same format then (as long as you open them with nautilus, which includes the desktop).

That technique didn't work for me. I want to change application launched when vcd is inserted to  something like vlc.

---

### Post by vinayasurya on 2006-07-13
> **kpkeerthi said:**
> Go to System -> Preferences -> Sound. Select your sound device and see if something is muted.

Is there any command line utility for detecting and configuring sound cards.

---

### Post by Ramses de Norre on 2006-07-13
So a vcd is a kind of disc (I don't know vcd's..), ok this is a shot in the dark but it might work, in terminal do ```
gnome-volume-properties
``` and select the Multimedia tab, there is an option for video dvd discs which is by default set to open with totem. You could try setting this to vlc. But it don't use this myself and I don't know whether it recognizes vcd's as video dvd's. Try it out I'd say ;)

---

