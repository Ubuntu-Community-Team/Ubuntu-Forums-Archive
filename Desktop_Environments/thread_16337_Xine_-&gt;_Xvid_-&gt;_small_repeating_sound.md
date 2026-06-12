---
title: "Xine -&gt; Xvid -&gt; small repeating sound"
date: 2005-02-20
forum: Desktop Environments
---

### Post by tromik on 2005-02-20
Wile watching Xvids with Xine I hear these sounds like someone is slowly crunching a ball of cellaphane, which the only way I can describe it.

The drivers for my MSI onboard AC97 sound card is correct, and I don't hear it in XMMS, so I'm guessing it's not a hardware issue.

Think it's the codec, or is there a patch for Xine?

I installed Xine with apt-get.

---

### Post by kassetra on 2005-02-20
Are you using the alsa drivers/output for xine?
 
 Also, check which output xmms is using because I'm betting it's not using alsa.

---

### Post by tromik on 2005-02-20
XMMS is using OSS, and it looks like Xine is using alsa, but I'm not sure how to change it. In the Audio tab do you make the by actually typing in "OSS" manually?

If possible, could you post a SS of where I should make this change?

---

### Post by kassetra on 2005-02-20
ok, that would explain the crackling noises.  I too experienced crackling noises using the alsa driver in xine, xmms, etc.
 
 Here's how you change xine:
 1. open /home/username/.xine/config in gedit
 2. change this code:
  ```
# audio driver to use
 # { auto  null  alsa  oss  esd  file  none }, default: 0
 audio.driver:auto
``` 
 to this:
  ```
# audio driver to use
 # { auto  null  alsa  oss  esd  file  none }, default: 0
 audio.driver:oss
``` 
 3. save and restart xine.  :)
 
 You could also use esd... I tend to prefer esd over oss.

---

### Post by tromik on 2005-02-21
[QUOTE=kassetra]ok, that would explain the crackling noises.  I too experienced crackling noises using the alsa driver in xine, xmms, etc.
 
 Here's how you change xine:
 1. open /home/username/.xine/config in gedit
 2. change this code:
  ```
# audio driver to use
 # { auto  null  alsa  oss  esd  file  none }, default: 0
 audio.driver:auto
``` 
 to this:
  ```
# audio driver to use
 # { auto  null  alsa  oss  esd  file  none }, default: 0
 audio.driver:oss
``` 
 3. save and restart xine.  :)
 
 You could also use esd... I tend to prefer esd over oss.[/QUOTE]

Thanks, worked perfectly. Oddly enough, using the GUI I couldn't find the .xine filder in home/name, is it not visible by default? 

Also, how would I open it in a terminal? I'd rather open in a terminal so I can just paste it, and if I need permissions I can do that there.

Thanks again. I went with ESD and it's perfect now.

---

### Post by kassetra on 2005-02-21
[QUOTE=tromik]Thanks, worked perfectly. Oddly enough, using the GUI I couldn't find the .xine filder in home/name, is it not visible by default? 

Also, how would I open it in a terminal? I'd rather open in a terminal so I can just paste it, and if I need permissions I can do that there.

Thanks again. I went with ESD and it's perfect now.[/QUOTE]

Oh yeah, you didn't see it in the gui because most likely you don't have the preference to show hidden and backup files turned on:
Computer->Home->Edit->Preferences
Checkmark Show hidden and backup files

On the command line, there are at least two ways to edit files:
gedit /home/name/.xine  (which will open gedit)  or
vi /home/name/.xine (which will open the vi editor...)

---

