---
title: "Flash is installed... but Facebook can't see it"
date: 2008-12-07
forum: General Help
---

### Post by Old Pink on 2008-12-07
Flash is, and always has been installed on my setup. I've made no changes to flash, and it still works on other sites such as YouTube, but facebook has started prompting me with:
> Flash Player upgrade requiredYou must download and install the latest version of the Adobe Flash Player to view this content.I'd go on the flash website and download the .deb for Ubuntu 8.04 but I'm stuck on 7.04. Any ideas?

---

### Post by SPr on 2008-12-07
Is javascript enabled? If not enable it.

---

### Post by mhh91 on 2008-12-07
if you're using firefox,click on "tools" menu,then click on "add-ons",then choose "plugins"


do you see "shockwave flash" there?

---

### Post by Old Pink on 2008-12-07
Javascript is and always has been enabled. 

There isn't a "plugins" menu in "add-ons", possibly because I'm only on Firefox 2.0.0.8?

---

### Post by SPr on 2008-12-07
Update to Firefox 3. FF2 has security issues and flash may work with it. Out of curiosity which version of Ubuntu do you run?

---

### Post by Old Pink on 2008-12-07
> **SPr said:**
> Update to Firefox 3. FF2 has security issues and flash may work with it. Out of curiosity which version of Ubuntu do you run?

I have FF3 Beta, which has the same problems. Just checked and YouTube runs using Adobe Flash Player 9. Maybe the issue is I just need to update to 10 or whatever the latest version is. I've tried updating to 7.10, 8.04, and 8.10 but each time the installer freezes when trying to work with (format/partition) my hard drive. 

As for what I'm on now, Feisty Fawn...

> **Old Pink said:**
> I'm stuck on 7.04.

---

### Post by mhh91 on 2008-12-08
isn't there any way to upgrade to 8.04??

---

### Post by Old Pink on 2008-12-09
I could maybe go 7.04 > 7.10 > 8.04 > 8.10 

But my 7.04 isn't up to date, and it's end of life, so chances are I couldn't even move to 7.10. 

And Ubuntu simply won't fresh install any more. It used to, and did in the past, for this installation and many others, but now it refuses.

---

### Post by SPr on 2008-12-10
Perhaps you ought to start a new thread explaining why Ubuntu wont install.

---

... You were caught in the crossfire of childhood and stardom,
Blown on the steel breeze... :guitar:

---

### Post by swoosh on 2008-12-10
> **Old Pink said:**
> Flash is, and always has been installed on my setup. I've made no changes to flash, and it still works on other sites such as YouTube, but facebook has started prompting me with:
I'd go on the flash website and download the .deb for Ubuntu 8.04 but I'm stuck on 7.04. Any ideas?

I am experiencing the same thing. I am thinking maybe it is related to the Koobface Virus (google this) that was reported when using facebook. I am not sure so not installing anything is the safest thing to do.

---

### Post by Old Pink on 2008-12-17
I've already made a "ubuntu won't install" thread a couple times, nobody can help, I think it's a hardware fault to be honest.

> **swoosh said:**
> I am experiencing the same thing. I am thinking maybe it is related to the Koobface Virus (google this) that was reported when using facebook. I am not sure so not installing anything is the safest thing to do.

You're talking about a Windows virus. I'm on Ubuntu. And the link to the update is [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) - official.

---

### Post by Ayuthia on 2008-12-17
> **Old Pink said:**
> Flash is, and always has been installed on my setup. I've made no changes to flash, and it still works on other sites such as YouTube, but facebook has started prompting me with:
I'd go on the flash website and download the .deb for Ubuntu 8.04 but I'm stuck on 7.04. Any ideas?

Have you tried using the tar.gz file?  You should only have to download the file, extract it:
```
tar xvvf install_flash*.tar.gz
```
Then copy the libflashpler.so file over to /usr/lib/mozilla/plugins[/code]
You should probably uninstall flashplayer-nonfree first though.

---

