---
title: "Where to find applets..."
date: 2005-06-05
forum: Desktop Environments
---

### Post by iammike on 2005-06-05
I've been searching and not really finding any good places that have applets for the Gnome panel.  Could someone point me in the right direction?

Also, even more specifically...I'm looking for a Gmail checker that is a Gnome panel applet....I found word of one on the net but every link I find to get it is just dead.

---

### Post by drummer on 2005-06-05
[QUOTE=iammike]I've been searching and not really finding any good places that have applets for the Gnome panel.  Could someone point me in the right direction?

Also, even more specifically...I'm looking for a Gmail checker that is a Gnome panel applet....I found word of one on the net but every link I find to get it is just dead.[/QUOTE]
 Hi, the mail-notification package supports gmail accounts. It displays an icon in the sys tray when new mail arrives, a popup tool-tip has header info (sender/subject). It's in the universe repository.

---

### Post by iammike on 2005-06-05
Thanks a lot, had no idea, that really helps.  :)

---

### Post by iamkmaniam on 2005-06-06
Have you tried gdesklets? If not 
sudo apt-get install gdesklets
sudo apt-get install gdesklets-data

then go the gdesklets web site and drag the tar files into the gdesklets counsol 'Viola' you have the best applets around.

---

### Post by iammike on 2005-06-06
I tried gDesklets but for some reason I had stability problems with it on both my desktop and my laptop...not sure why.

---

### Post by 23meg on 2005-06-06
[QUOTE=iamkmaniam]Have you tried gdesklets? If not 
sudo apt-get install gdesklets
sudo apt-get install gdesklets-data[/QUOTE]

for what i know, the desklets in the gdesklets-data package are obsolete and cause stability problems with the latest version. to be safe, just install gdesklets itself via apt, and get the newest versions of desklets from the official site.

iammike: this might be the source of your problems.

---

### Post by iammike on 2005-06-06
I was getting my desklets from the web and not from the repositories though.

---

