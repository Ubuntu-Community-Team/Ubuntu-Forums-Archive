---
title: "Installation error using Wubi"
date: 2009-06-09
forum: General Help
---

### Post by KaOSoFt on 2009-06-09
Hello, I keep getting the error I attached whenever I try installing Ubuntu through WUBI. I also attached the error log.

The last lines of the error log indicate that (I think) it's trying to access a nonexistent drive on MY computer.

I hope you can help me sort out this problem. Thank you very much for your support.

PS: I'm using Windows XP SP3, and I'm trying to install Ubuntu 9.04 x86.

---

### Post by Tipped OuT on 2009-06-09
Here's what I do when ever I install Ubuntu with Wubi.

1. Download your Ubuntu ISO from here:[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
2. When the download is finished, create an empty folder and move the ISO in there.
3. Download the Wubi installer from here: [http://wubi-installer.org/](http://wubi-installer.org/)  and move it in the same folder as your ISO.
4. Proceed with normal installation using Wubi.

---

### Post by ActiveFrost on 2009-06-09
Do you really need to use Wubi ? Can't you just boot from your CD & install without copying all the files to your PC ( which is kind of stupid feature .. copying installation CD to your PC without asking whether I want it or not ) ?

---

### Post by KaOSoFt on 2009-06-09
> **Tipped OuT said:**
> Here's what I do when ever I install Ubuntu with Wubi.

1. Download your Ubuntu ISO from here:[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
2. When the download is finished, create an empty folder and move the ISO in there.
3. Download the Wubi installer from here: [http://wubi-installer.org/](http://wubi-installer.org/)  and move it in the same folder as your ISO.
4. Proceed with normal installation using Wubi.
Nope, it didn't work. I did it at home the same way as here (at work). I tried placing them both in C:\WUBI\, to no avail. My ISO is called ubuntu-9.04-desktop-i386.iso, and it's 732 909 568 bytes in size.

What else could it be?

---

### Post by Tipped OuT on 2009-06-09
Maybe because your system is in another language? But you know all you got to do is mount the ISO and there's an option to "install inside Windows", which is the same exact thing Wubi does. You don't need Wubi.

---

### Post by KaOSoFt on 2009-06-09
> **Tipped OuT said:**
> But you know all you got to do is mount the ISO and there's an option to "install inside Windows", which is the same exact thing Wubi does. You don't need Wubi.
Huh? I didn't know that... it creates a virtual disk as well?

I'll try it that way, then. Thank you.

---

### Post by KaOSoFt on 2009-06-11
Hello.

I would like to know if the "Install inside Windows" option of Ubuntu's installation package is the same as installing it using [WUBI]("http://wubi-installer.org/")? I mean, it uses a virtual disk as well?

Thank you very much for your support.

PS: This is based on what people told me on [this post]("http://ubuntuforums.org/showthread.php?t=1182878").

---

### Post by pmlxuser on 2009-06-11
Yes indeed its the same...
and yes it uses virtual disk.

---

### Post by Tipped OuT on 2009-06-11
Yeah it's the same. The only difference is, WUBI downloads the ISO for you, so there is no disk needed.

---

### Post by KaOSoFt on 2009-06-11
> **Tipped OuT said:**
> Yeah it's the same. The only difference is, WUBI downloads the ISO for you, so there is no disk needed.
I've already downloaded the ISO.

Thank you very much you all.

---

### Post by aysiu on 2009-06-11
> **KaOSoFt said:**
> I've already downloaded the ISO.

Thank you very much you all.
In that case, just make sure the .iso is in the same directory as Wubi so that Wubi doesn't try to redownload it.

---

### Post by KaOSoFt on 2009-06-11
> **aysiu said:**
> In that case, just make sure the .iso is in the same directory as Wubi so that Wubi doesn't try to redownload it.
Like I said in [another thread]("http://ubuntuforums.org/showthread.php?t=1182878"), WUBI shows an error, that's why I was looking for another option.

Thank you!

---

### Post by aysiu on 2009-06-11
> **KaOSoFt said:**
> Like I said in [another thread]("http://ubuntuforums.org/showthread.php?t=1182878"), WUBI shows an error, that's why I was looking for another option.

Thank you!
I've merged your two threads. Really the main issue is you need help with Wubi.

---

