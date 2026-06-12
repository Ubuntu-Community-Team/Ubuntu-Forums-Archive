---
title: "Banshee 2.0 autostarts when plugging in a device!"
date: 2011-05-12
forum: Desktop Environments
---

### Post by Pontus Ohman on 2011-05-12
Hello folks!

Have tried to find an answer over at over LoCo (Sweden) with no result...
Does anyone know how to stop Banshee from autostarts when I plug in a USB-drive, my iPhone or what-so-ever! Banshee even autostarts when I'm doing a "Connect to server" O_o

Have even googled for it, with no result and it's bugging me off real hard that Banshee autostarts!

Edit: If I remove Banshee, and still plugs a device in it now autostarts in qmmp! :S

Best regards
Pontus "Kirill" Ohman
Team Contact Ubuntu Sweden

---

### Post by coffeecat on 2011-05-12
It sounds as though Banshee has been accidentally set as the default app for opening a nautilus window. It's a common problem. Try this.

Right-click on desktop and choose "Create Folder". Don't bother to rename it. Now right-click on the folder and choose "Open with Other Application". Scroll down the list and select "File Browser" but also make sure the "remember this application" tickbox is ticked. Once you've opened the folder and tested that everything else is working as it should you can delete the temporary desktop folder.

---

### Post by Pontus Ohman on 2011-05-12
Ha! That did the trick :)
No more irritation of Banshee or even QMMP showing up as fast as a put in a device...

Cheers
Kirill

---

### Post by fjgaude on 2011-05-12
> **coffeecat said:**
> It sounds as though Banshee has been accidentally set as the default app for opening a nautilus window. It's a common problem. Try this.

Right-click on desktop and choose "Create Folder". Don't bother to rename it. Now right-click on the folder and choose "Open with Other Application". Scroll down the list and select "File Browser" but also make sure the "remember this application" tickbox is ticked. Once you've opened the folder and tested that everything else is working as it should you can delete the temporary desktop folder.

Very interesting, and useful! Thank you!

---

### Post by keef123 on 2012-01-07
I have this same problem for any USB pen drive, external hard drive or phone. It's infuriating - I un-installed Banshee (2.2.1) but then realised there is no other way to buy MP3's from the Amazon store so re-installed. Same problem. 

I've tried the solution listed here but in 11.10 there's no way to select Remember This Application.

I've also changed the Default Application setting to make sure that Banshee isn't selected for anything (Rhythmbox is now the default Music app.

Anyone else tried the solution here and had it fail? Any one got any other ideas?

---

