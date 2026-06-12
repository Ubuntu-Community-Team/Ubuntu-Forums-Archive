---
title: "How do I terminate the X server?"
date: 2008-09-18
forum: Desktop Environments
---

### Post by brodae on 2008-09-18
I'm running 8.04 LTS

---

### Post by sisco311 on 2008-09-18
```
sudo /etc/init.d/gdm stop
```

---

### Post by Coab on 2008-09-19
If you want to restart the x server then the key combination ctrl+alt+backspace will force a restart of the xserver.

---

### Post by brodae on 2008-09-26
See, I'm trying to update my nVidia drivers, but once I type in what you said I should, I don't know what to do afterwards. Agh!

---

### Post by Marshal0505 on 2008-09-26
> **brodae said:**
> See, I'm trying to update my nVidia drivers, but once I type in what you said I should, I don't know what to do afterwards. Agh!

```
sudo /etc/init.d/gdm stop
```

This will allow you to continue the installation process

started by typing 
```
sudo sh NVIDIA-INSTALLER-FILE.sh
```
or ```
sudo ./NVIDIA-INSTALLER-FILE.sh
```

If you get lost I suggest you go back to the nvidia download page and reread instructions there.It's quite easy as long as you take the time to read instructions.

---

### Post by sisco311 on 2008-09-26
Follow this guid: [https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

If you have any questions feel free to ask.

---

### Post by SuperSonic4 on 2008-09-26
You might have to press Ctrl+Alt+F1 to drop to a command line before putting in what Marshal said

---

### Post by brodae on 2008-10-06
Ok, I changed my mind. I tryed doing it, and it just screwed up my X server. I reverted back to an old driver, but I want my old restricted driver back. How do I do that?

---

### Post by brodae on 2008-10-07
Posting to bring up noticability.

---

### Post by brodae on 2008-10-09
Does anyone know how to do this?

---

