---
title: "File/print sharing setup info please"
date: 2005-01-04
forum: General Help
---

### Post by pmshoop on 2005-01-04
Hey there,

I'm trying to get my printer recognized by my wifes laptop running win XP.  I've got samba set up and I can see her computer/ shared files.  What do I need to do in ubuntu so she can see a file/files and share my printer?

Paul.

---

### Post by makhand on 2005-01-05
Hey man, I want to do the same exact thing (except i have no wife). Let me know if you figure it out.

---

### Post by makhand on 2005-01-05
Well, now I am able to browse from the XP laptop, and see the ubuntu machine, along with the printer. I tried to add a printer from within XP and takes a very long time, then finally outputs an error about 'Windows cannot connect to the printer'.

I do have to also note that when I tried to print a test page from within ubuntu, to my (in this case) local printer, it was in pretty bad shape.  I have an HP Deskjet 710C and cant seen to print anything that looks any good. its all a bunch of jumbled mess. It usually ends up with the lights (power, error, inklevel) blinking frantically. 

So either, i need to get a different printer, or something in ubuntu/gnome/hpijs needs to be fixed. 

actually, as an update to that. it seems like it prints less complex files just fine, but with a bigger file, it screws up pretty randomly. 

well, if someone could help, this would be appreciated. For now, i must go do something more productive

---

### Post by nocturn on 2005-01-05
[QUOTE=pmshoop]Hey there,

I'm trying to get my printer recognized by my wifes laptop running win XP.  I've got samba set up and I can see her computer/ shared files.  What do I need to do in ubuntu so she can see a file/files and share my printer?

Paul.[/QUOTE]

You will need to set up Samba as a server on your system.
You can put shares in /etc/smb.conf, but there are frontends for this.

---

### Post by pmshoop on 2005-01-05
[QUOTE=nocturn]You will need to set up Samba as a server on your system.
You can put shares in /etc/smb.conf, but there are frontends for this.[/QUOTE]
I got Samba up and running.  My wife, using XP on her laptop, can see and read/write to my Ubuntu box.  She can even print (although I do need to find a way to update the printer driver in Ubuntu).  I just can't read / write to her box.  I can see her, the windows network, and her folders that are shared... just can't get them to open.  <<shrug>> 

Its ok for now since I really don't need to read/write anythign from her computer.  And since the printer is on my box and thats working fine she's happy.  But if anyone has any ideas why I can't get into her files plz let me know.... I see someone above posted the exact same problem.

maybe its a problem with XP.

---

### Post by pmshoop on 2005-01-05
[QUOTE=makhand]Well, now I am able to browse from the XP laptop, and see the ubuntu machine, along with the printer. I tried to add a printer from within XP and takes a very long time, then finally outputs an error about 'Windows cannot connect to the printer'.

I think its the printer driver causing you to have glitches printing... I have an HP officejet t45 and I can print just fine... but my wife (coming from XP) can only print 1 copy at a time (not a big deal just an inconvenience).  Heres how I got Win XP to recognize the network printer...

GOTO> Network Places
GOTO> View entire network.
IF you see the printer (and you should) then RIGHT CLICK on it.  
CHOOSE 'CONNECT'
It might ask you to install a driver.  Click thru that process.

After I did all that I was printing 'ok' from win XP.  As an alternative just have dump your win XP files over to your Ubuntu box and print from there.

Paul.

---

