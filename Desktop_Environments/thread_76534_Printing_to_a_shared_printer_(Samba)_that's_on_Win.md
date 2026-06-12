---
title: "Printing to a shared printer (Samba) that's on Windows XP Home"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Bigglez on 2005-10-15
Hello. Hope this is the right place to ask this question. 

I have been googling and searching this forum too, but so far I can find no clear information on this subject:

We have an HP psc 3xx0 (I forget the code now, but there is a driver for it in the list when you add a printer) that is attached to a Windows XP Home computer in another room.

The network comprises a D-Link switch which all the computers plug into. One of those ethernet cables goes into an aerial for the wireless connection to the ISP. That connection is a VPN.
All the machines are assigned IPs by DHCP from the ISP.

We can (with ease) print to the printer from any machine that's booted into Windows. (The machine running the printer is always Win XP Home, the printer is shared as 'printer')

When we try from one booted into Ubu, well that's where I simply can't get it to work. 
I tried the Samba network printer, but there is no help to assist me filling-in those fields (and googling did not help).

I tried the "detect LAN printers" thing - that did squat.

I keep getting an error something like "NT_UNSUCCESSFUL" I think, I'm not at that location and I forgot to write it down.

If anyone can help me, and that help actually works - I will pull my finger out and create a Wiki page about it.

Thanks.

---

### Post by Bigglez on 2005-10-15
bump

---

### Post by Bigglez on 2005-10-16
Aw, c'mon. I can't believe that I'm the only person who cannot figure printing out on Ubuntu! 
Please drop a hint! Else, lemme know where a better place is to ask this question.

---

### Post by racecat on 2005-10-17
I don't remember how I set it up on my first box with Gnome, but I recently set one up with Xfce and added Kde and Gnome components. What I ended up with was kdeprint, then I started adding smbclient, samba, and then smbfs. I had to reboot to get the network selection to show up in the kdeprint wizard, but it works great. I have a printer on a Win2000 box and my Ubuntu boxes are the only ones I don't have to manually log into the printer's machine before printing.

Have fun,
Bill

---

### Post by Bigglez on 2005-10-20
Well, thanks Bill for your input. 

I am a more than a little let down by the lack of help within Ubuntu and on this forum for someting as vital as printing. I will try the new version of Ubu and see if things have improved.

---

### Post by racecat on 2005-10-20
[QUOTE=Bigglez]Well, thanks Bill for your input. 

I am a more than a little let down by the lack of help within Ubuntu and on this forum for someting as vital as printing. I will try the new version of Ubu and see if things have improved.[/QUOTE]

It seems like the heavy hitters have their hands full now that Breezy's out.

Bill

Edit-P.S. You might try reposting on the absolute beginners forum. I get lots of good stuff there and this question seems perfectly appropriate for that area.

Good luck,
Bill

---

### Post by Alexander Kirillov on 2005-10-20
[QUOTE=Bigglez]Aw, c'mon. I can't believe that I'm the only person who cannot figure printing out on Ubuntu! 
Please drop a hint! Else, lemme know where a better place is to ask this question.[/QUOTE]
Have you tried suggestions here?
[http://ubuntuforums.org/showthread.php?t=32190](http://ubuntuforums.org/showthread.php?t=32190)

---

### Post by Bigglez on 2005-10-20
Alexander - thanks for that link. I don't know why my search did not find that thread. It looks like I will have a lot of things I can try. I'll go and haunt that thread now.

---

