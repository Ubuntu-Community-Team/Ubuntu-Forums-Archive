---
title: "How to change screen resolution from 640x480?"
date: 2006-08-27
forum: Desktop Environments
---

### Post by DiscoSamurai on 2006-08-27
I bet this thread's already been made before but I can't seem to find it and I'll need a bit more personal help. I just want to know how to change my resolution from the default, there are no options except default. Can anyone redirect me to the already made thread or help me?

---

### Post by aysiu on 2006-08-27
[This](http://ubuntuforums.org/showpost.php?p=129379&postcount=21) might help.

---

### Post by DiscoSamurai on 2006-08-27
> **aysiu said:**
> [This](http://ubuntuforums.org/showpost.php?p=129379&postcount=21) might help.

That stuff confuses me, I have no clue what it means and there's no one to help  me there.

---

### Post by aysiu on 2006-08-28
What's your monitor?

---

### Post by DiscoSamurai on 2006-08-28
> **aysiu said:**
> What's your monitor?

Gateway EV700 17-inch Monitor with 15.9-inch Viewable Area?

1,280 dots maximum horizontal
1,024 lines maximum vertical

---

### Post by aysiu on 2006-08-28
Okay. Not 100% sure this will work, but we'll keep a backup copy of your old config file, just in case.

Paste this command into the terminal: ```
sudo nano -B /etc/X11/xorg.conf
``` Look for the monitor section of the file. If there are already HorizSync and VertRefresh lines in there, modify them. If there aren't those lines in there, add them.

According to [this page](http://support.gateway.com/s/MONITOR/7003421/700342102.shtml) (please verify that is, in fact, your monitor), it should read: ```
[b]HorizSync 31-69
VertRefresh 50-160[/b]
``` Then save (Control-X, Y, Enter).

Finally, restart your X server (note--this will close all your programs and log you out... save anything you have open): Control-Alt-Backspace.

Should work.

P.S. As an example of what it looks like, here's the relevant section of my xorg.conf file: ```
Section "Monitor"
        Identifier      "FPD1960"
        Option          "DPMS"
        HorizSync       30-80
        VertRefresh     60-75
EndSection
``` The HorizSync and VertRefresh values for my monitor are different, of course, but that's the format it should be in.

---

### Post by DiscoSamurai on 2006-08-28
okay I did all that stuff but now, It says (when i go to my system settings>Display) The module display could not be loaded.

---

### Post by aysiu on 2006-08-28
So the Control-Alt-Backspace didn't do anything?

Can you post the output of this command, so I can see that the formatting is correct on the Monitor section? ```
cat /etc/X11/xorg.conf
```

---

### Post by DiscoSamurai on 2006-08-28
DUDE. I think something is terribly wrong. I accidently (in a mindless state) Restarted instead of logging out, and now it's kinda stuck at the Kubuntu screen where it goes through the checklist. And it every 3-5 minutes checks each thing off. It's stuck at "restarting system log" at the moment.

---

