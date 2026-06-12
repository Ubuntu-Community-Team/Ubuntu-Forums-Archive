---
title: "New in Kubuntu - where's the network?"
date: 2009-01-18
forum: General Help
---

### Post by gregorydearth on 2009-01-18
I can't figure out how to get my computer to connect to the wireless home network. The computer is a poweredge dell 4300 server running kubuntu. All of my other wireless computers work except my linux one. 

I know for a fact that I have an unsecured wireless network. No passwords. No essid needed. So why can't the linux computer connect?

Furthermore, after going around in circles in the menu system of kubuntu I have yet to find a wireless utility. What the heck am I to do with a computer with no wireless utility? I know the card works because it worked with windows 2000 pro that was on the computer just an hour ago. SO I guess my questions are:
How do I select the wireless router to connect to?
Where is the utility for viewing available routers (networks)?
And how would I install a windows-based driver for the wireless card if needed?

---

### Post by x33a on 2009-01-18
type knetworkmanager in the terminal, or alt+f2 , then knetworkmanager, and you'll be able to see and configure your network using this utility.

and, i don't think you'll need any additional driver, but anyway you can't install a windows driver on linux.

if you do need a driver, then search for it on google.

---

### Post by cptr13 on 2009-01-18
Assuming you're connected to the internet via ethernet for the time being.  Go into the package manager (adept) and install knetworkmanager.
You can also do this manually via the konsole terminal but typing: sudo apt-get install knetworkmanager
You should see a little globe in the system tray (you may have to log out/back in, I'm not positive).  You can click on that and connect to your wifi.

Hope that helps.

---

