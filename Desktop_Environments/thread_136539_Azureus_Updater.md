---
title: "Azureus Updater"
date: 2006-02-26
forum: Desktop Environments
---

### Post by twoseids on 2006-02-26
I have been getting a pop-up on Azureus telling me that I need an update for **SWT Library for gtk** (version 3139, it says). I have, on several occasions, run the update which appears to be successful, but I continue to get this pop-up when I run Azureus at a later time.

How can I make this pop-up go away? Or perhaps this update actually hasn't successfully taken place?

---

### Post by Joey French on 2006-02-26
I am gonna venture a guess and say you need to run azureus as root, then do the update. I finally got mine to update after it did the same things you describe for months.

```
sudo azureus
```

---

### Post by twoseids on 2006-02-26
[QUOTE=Joey French]I am gonna venture a guess and say you need to run azureus as root, then do the update. I finally got mine to update after it did the same things you describe for months.

```
sudo azureus
```[/QUOTE]
I gave that a go and checked for updates, and it didn't find any available. We'll see what happens tomorrow when I log back in as a regular user!

Interestingly, when I ran Azureus as root, it acted like it was my first time ever using it - I got all of the first-time dialogue boxes, and had to reopen my torrents as it was entirely empty.

---

### Post by OlineSixtyOne on 2006-02-26
Thats because Azureus keeps its configuration stuff in ~/.Azureus and when you run as root it uses root's home directory instead of yours, where your configuration is stored. 

I have noticed that the repository and the Automatix azureus versions do not auto update correctly, so I just download from the Azureus site and install to /opt/azureus/.

---

### Post by Perfect Storm on 2006-02-26
Uninstall azureus then:

download Azureus here: [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php) Pick Linux version 2.4.0.0.

```

cd /to/the/folder/where/you/saved/azureus
sudo tar jxvf Azureus_2.4.0.0_linux.tar.bz2 -C /opt/
sudo chown -R root:root /opt/azureus/
smeg

```

Pick **Internet** and click **New Entry**

Name: Azureus
Command: /opt/azureus/azureus
Icon: /opt/azureus/Azureus.png

press ok.
Now Azureus will work perfectly.

---

### Post by twoseids on 2006-02-26
Excellent! Thanks so much for your help.

---

### Post by risknothin on 2006-02-26
what folder is azureus in if automatix installed it?

---

