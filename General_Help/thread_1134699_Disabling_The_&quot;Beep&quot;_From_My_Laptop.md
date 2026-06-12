---
title: "Disabling The &quot;Beep&quot; From My Laptop"
date: 2009-04-23
forum: General Help
---

### Post by jlacroix on 2009-04-23
The system beep sound is really driving me nuts! It happens when I click something in Open Office that can't be edited, when I press backspace too many times in Konsole, or other inopportune times. This thing has made me jump out of my seat more times than I can count and scared the bejeazus out of me just a few minutes ago.

Does anyone know how to turn off this beep in KDE4/Kubuntu? I Googled it but everything I found didn't work. I vaguely remember a System Settings option but I can't find it.

Thanks!

---

### Post by Darkshade on 2009-04-23
```
sudo gedit /etc/modprobe.d/blacklist.conf
```

On a new line in the end of the file add
```
blacklist pcspkr
```

And reboot your PC.

---

### Post by jlacroix on 2009-04-24
I might try that, but I think that my laptop doesn't have an actual PC speaker, because when I turn my volume down, I can't hear the beep, so would it still be the same fix, or is there a pc speaker emulation somewhere? I remember there being a setting right in KDE for this but I can't remember where...

---

### Post by jlacroix on 2009-04-30
I think that did it. Thank you!

---

