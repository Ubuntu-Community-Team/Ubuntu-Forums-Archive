---
title: "hp 1100 psc dosen't print (ubuntu 8.10)"
date: 2009-02-23
forum: General Help
---

### Post by Anxious Nut on 2009-02-23
I've been using HP 1100 psc for a long time, it used to work properly with my old 10.4, I've recently installed 8.10 but it has a problem with my printer. It scans like it used to, and everything appears ok, even the pop up still works saying that a printer is found. But when it comes to printing (in 8.10) the problem appears, once I press the print button it starts (normal) it stuff and take the paper in and starts printing without printing anything, i mean the process works but it doesn't write/put anything on the paper. so I need help, please, and thanx!

---

### Post by ashwinhgtx on 2009-02-23
Are you sure that the printer is ok? Does it work with any other computer?

---

### Post by Anxious Nut on 2009-02-23
Yes I'm sure, just tried it with Vista, it prints with no problems!

---

### Post by ashwinhgtx on 2009-02-23
Can you print out a test page at least? I'm on Kubuntu so I don't really know the menu options to get you to do that. :(

---

### Post by Anxious Nut on 2009-02-23
Tried it, but as i said it takes the paper in and out but there's nothing on it!

---

### Post by ashwinhgtx on 2009-02-23
Did your printer 'just work' in 8.04 or did you have to install any extra drivers? Did you install the hp drivers in 8.10?

---

### Post by Anxious Nut on 2009-02-23
In 8.4 i haven't, it worked automatically, i think it was pre-installed or something. and Yes, I've installed hplip yesterday for my 8.10 (and as it is written, 1100 driver is included in hplip)

[http://hplipopensource.com/hplip-web/downloads.html]("http://hplipopensource.com/hplip-web/downloads.html")

---

### Post by ashwinhgtx on 2009-02-24
Have you tried reinstalling the drivers? Did you install the drivers from the hp website or through Synaptic?

---

### Post by Anxious Nut on 2009-02-24
Yes I have but the problem remains, and I have installed it from downloading the .tar.gz from the site and then compiled it. and still the problem remains.

---

### Post by ashwinhgtx on 2009-02-24
Can't you install it from the repositories through Synaptic? Why did you compile it from source?

---

### Post by roccivic on 2009-02-24
I have exactly the same printer and used to have exactly the same problem. 
Do you have a color cartridge installed? By default hplip is set up for using the color cartridge only, so if you don't have one (or it is empty) it will print an empty page. If this might be the case, open the hplip configuration utility and set it up to print using the black cartridge only.

Indeed do install "hplip" through Synaptic.

Peace

---

### Post by Anxious Nut on 2009-02-24
because the version that I've downloaded is newer than the one that is in the repository

---

### Post by ashwinhgtx on 2009-02-24
Why don't you try to install the old version from the repositories? It might work. Just give it a try. And as stated by roccivic try changing the configuration settings of hplip

---

### Post by Anxious Nut on 2009-02-24
just did that, I've installed the older version but he problem still remains :(

---

### Post by ashwinhgtx on 2009-02-25
Any luck there buddy? I really can't think of anything to help you out. Did you try the hp customer care? They are the ones that made the drivers right?

---

### Post by Anxious Nut on 2009-02-25
Yeah.. Okay, I guess i'll go there, thanks for your time, i really appreciate it ;)

---

