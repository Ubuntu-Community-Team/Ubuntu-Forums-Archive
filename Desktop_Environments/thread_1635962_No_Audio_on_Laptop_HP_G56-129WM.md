---
title: "No Audio on Laptop HP G56-129WM"
date: 2010-12-02
forum: Desktop Environments
---

### Post by sbarrow on 2010-12-02
I just purchased an HP G56-129WM laptop with Windows 7. Audio worked great under Windows. I've removed windows and installed Ubuntu 10.04 and fully patched it. Now my audio doesn't work at all. I don't recall if it worked prior to patching it after the Ubuntu install because I patched it immediately. Does anyone have any insight on getting my audio to work?

Thanks

---

### Post by Jahid65 on 2010-12-02
Did you check out Sound Preference=>Hardware tab? There may be profiles in hardware tab. Check it by clicking sound icon. Or System=>Preference=>Sound.

---

### Post by sbarrow on 2010-12-02
yes. I checked that. Still no audio

---

### Post by sbarrow on 2010-12-03
Fixed it. In Synaptic Package Manager, under Settings, Repositories on the Updates tab; enable 'Recommended updates (lucid-proposed)' and 'Pre-released updates (lucid-proposed)'. Reload the packages then install linux-backports-modules-alsa-2.6.32-26-generic (2.6.32-26.25) and linux-backports-modules-alsa-lucid-generic (2.6.32.26.28).
Rebooted and I had my audio back.

---

### Post by notebookshopper on 2010-12-03
[COLOR=#000000][FONT=Times New Roman][COLOR=#333333][FONT=arial]Might be a driver problem. Try installing the driver. If this doesn't seem easy enough...

If you don't have many important files, back up your files and use the recovery discs that come with your computer. Just put them in and that will wipe out the partition and reinstall the software, operating system, and drivers.

Thanks :D

[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by sbarrow on 2011-01-29
At some point in the last 2-3 weeks after I installed updates, the sound quite working again. Backtracked my steps last time and nothing worked yet. Any ideas?

---

### Post by zatanzen on 2011-06-02
hi, im new on this forum, and in this OS, this OS is really AMAZING, I prefered too much against windows, well, i got the same trouble dont get audio, but i see something, i install the x64 version, and ubuntu install 2 OS, i dont kno why, one finish on 28, other on 32, i use the first time the number 32, and this OS update, and stop working the sound, the other one, i never was updating, and still working the audio, i think was a update from ubuntu, please check it, because i want wireless and audio lol

---

