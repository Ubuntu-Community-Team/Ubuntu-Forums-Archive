---
title: "Drivers"
date: 2009-03-06
forum: General Help
---

### Post by SuperIntense on 2009-03-06
How do i know if my drivers for hardware are up to date such as the video or CD\DVD player

---

### Post by entr3p on 2009-03-06
> **SuperIntense said:**
> How do i know if my drivers for hardware are up to date such as the video or CD\DVD player

Go the Terminal and type in:
```
sudo apt-get update && sudo apt-get upgrade
```
This will upgrade everything.
After that check out "System --> Administration --> Hardware Drivers" and tell me what you see.

---

### Post by SuperIntense on 2009-03-06
No new drivers other than my video card which was already there. My CD?DVD is not playing. What am I missing?

---

### Post by SuperIntense on 2009-03-06
Where od you guys get all of these commands for terminal

---

### Post by entr3p on 2009-03-06
> **SuperIntense said:**
> Where od you guys get all of these commands for terminal

By years of exploring and learning ;). Well...what program do you use? I recommend using VLC for dvds..and it maybe you didn't install the dvd decryption program. You will first have to add the Medibuntu repitiore to download the dvd decryption program. So type these in now:
**sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list**
**wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update**
**sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc**

---

### Post by SuperIntense on 2009-03-06
I ran the file and now am downloading VLC. Instead of years to learn is there anyway to maximize my knowledge of Ubunto so it doesn't take years.

---

### Post by SuperIntense on 2009-03-06
How come I can't mount my CD drive or check its files?

---

### Post by oldsoundguy on 2009-03-06
SuperIntense, this should give you a kickstart:
[http://www.ubuntupocketguide.com/download2.html](http://www.ubuntupocketguide.com/download2.html) ... but most programs can now be installed from add/remove or from synaptic package manager and do not require work in terminal (that is what the window that is like the CMD window in Windows is called.)

---

### Post by oldsoundguy on 2009-03-06
and those three menus at the top in the panel will lead you to lots of places without commands at all.

For instance places>computer> will lead you to your optical drives.

---

### Post by entr3p on 2009-03-06
> **SuperIntense said:**
> I ran the file and now am downloading VLC. Instead of years to learn is there anyway to maximize my knowledge of Ubunto so it doesn't take years.

No offense..but it's impossible to suddenly "download" all the information to your brain but my future website will have guides with many explanations so you can some day become a guru. [www.learningubuntu.com](www.learningubuntu.com) ubuntu guides to learn from will soon be there.

---

### Post by SuperIntense on 2009-03-06
Thank You for your responses. I truly appreciate it!

---

