---
title: "launching shell script from the panel"
date: 2016-08-18
forum: Desktop Environments
---

### Post by Nosphky on 2016-08-18
I installed a shell script for backup of files onto the panel1 in UbuntuStudio1404. Unfortunately I did not record how I did it and now I cannot get the correct formulation on the launcher in UbuntuStudio 16.04.

I have seen and read thread 1818196 in this forum but nothing there helps.

My scripts are in '/home/me/bin' and they work fine when called in a terminal. I can easily get another terminal to launch from panel1 using the standard "exo-open --launch TerminalEmulator" on the launcher's command line.  But every attempt at editing that command line produces some error like "Unable to detect the URI-scheme of [whatever I put in]" and the script doesn't run.

Looking for a little help here, please.

---

### Post by Nosphky on 2016-08-18
Sorry about that !  All the stuff in the command box "exo-open --launch TerminalEmulator" when I added the TerminalEmulator to the panel1 new item caused me to concentrate on adding a parameter to the end of that line.

All I needed to do was delete what was there and replace it simply with the name of my script - my bin directory being present in the PATH.

Sometimes I get looking for stupid complications when I really should just go simple.

---

