---
title: "Lots of little Problems Id like fixed."
date: 2009-03-22
forum: General Help
---

### Post by BrandonND on 2009-03-22
I am generally new to Ubuntu and Linux in general and I have finally got my computer the way I'd like it, but there are a few little things Id like to fix, I figured the best way to make sure you have all the info you need is to list the vents of my boot and through an average day of my computer usage. 

I am doing this so that I can make a perfectly customized backup of my system to avoid going through this again :\

________________________

I press the button on my Dell Optiplex Gx260. 

My Dell Xplio 15" flatscreen comes to life,

It passes the bios in about 5 seconds.

After 15 seconds of streaming white text, this **includes the word Warn and Networking on the same line about 15 times,**

It comes to a short pause as it waits 1 second for me to press esc to get into the menu.

Lacking this, it streams a little more white text including **"vbox0 failed t initialze br0"** or something of the like. 

We are now at the login, I type in my credentials and wait as my screen loads. 

I open up the menu and start Skype and Firefox as well as Gimp, they get put on seperate workspaces. **(anyway to automate this?) **

I look on my desktop at the icons and wish I could get rid of some of them.(**help?)** especially the Server and Home ones. 

My memory is running at 31%, but the cache takes up all the rest, my 2 gb swap is not touched. **(why is this happening?)**

I boot up a terminal in one of my workspaces and drop it to root immediatly. **(severe security risk?)**

Oh but my parents call me over, I lock my screen and press ctrl+alt+f2 i apply office lock and walk away. **(again, security risk?) **

I come back, get back into the desktop and open gmail **(can i do this via my desktop?) **

I do some homework in openoffice.org, save it to my network server running Apache2 then go to the printer and the pc hooked up to it, contact my server and print **(is there a way to connect to a printer on a windows pc?) **

Now I play some flash games, in opera, as it doesnt work in firefox (**any reason for this?) **

I hope you all can help me with this relativly minor problems.

---

### Post by BrandonND on 2009-03-22
very sorry for this, but BUMP

---

### Post by sgosnell on 2009-03-22
To open programs automatically, open System, Preferences, Sessions and add a launcher for each.

Swap is only used for hibernation, AFAIK.  As long as you have RAM available, swap won't be used.

I wouldn't advise opening a terminal as root routinely.  Sudo works.  As root, you can destroy anything.

You can put a direct link to gmail on the desktop.  Look at the offline mode.

You can connect to a printer on a Windows machine.  You need samba installed to do it.

Have you installed the flash driver for firefox?

---

### Post by hyperdude111 on 2009-03-22
For gmail on desktop you can go to the Add-Remove apps and search gmail. There is a prism app which starts gmail in its own window quite good.

Or install transmission and install the gmail addon (like firefox with addons) and use it as an email client.

---

### Post by BrandonND on 2009-03-22
Thank youu for your help, I have flash installed, and the gmail and startup problems are fixed. Samba on the windows pc? as my dad wouldnt go for that

---

### Post by sgosnell on 2009-03-23
No, samba is a Linux thing.  Install samba on your Linux box, set the sharing on the Windows box, and you should be able to access the shared folders on it.

---

