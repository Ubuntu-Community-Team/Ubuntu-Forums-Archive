---
title: "Standby trouble with HP nc6120 Notebook"
date: 2006-01-15
forum: General Help
---

### Post by mario.rimann on 2006-01-15
Hi all

I'm new to linux and ubuntu. I've installed Ubuntu 5.10 Breezy on a HP nc6120 Notebook with an Intel Wireless 2200 BG Wireless Card.

The actual problem is the standby functionality: I'm triggering it via Gnome standby function (not by closing the lid). It goes down to sleep well - and comes up again. Everything except the network connection is working well then!

I need to reactivate the network connection in the settings.

How can I change this behaviour?? I searched google and ubuntuforums - but didn't find the solution yet. Any help is very appreciated!

Greetings,
Mario

---

### Post by stults on 2006-01-23
I'm still pretty new but have been doing a lot of research to get my suspend to work.  You could try to put your network card module in the /etc/default/acpi-support file.  Add it to the section called MODULES or MODULES_WHITELIST.  Let me know if this works for you.  Cheers!

Oh, don't forget to restart the computer!

---

### Post by mario.rimann on 2006-01-23
Hi stults
Thanks for your help. I found the mentioned file and looked into it. There are many sections and I could also find the sections you mentioned.

But what do I need to enter there?

---

### Post by stults on 2006-01-24
Here's the step-by-step that got my wireless card working after suspend:

Open System-->Administration-->Device Manager.
Find your network card on the left and open the Advanced Tab on the right.
Find "info.linux.driver" to see what driver your network card is using.
Add that driver (mine was airo) to the MODULES_WHITELIST section inside the parenthesis ("airo") in the file /etc/default/acpi-support.
Restart the computer to be sure it takes.  
Keep your fingers crossed.
If this doesn't work try adding the driver to MODULES section in the same file.

Good luck and let me know!

---

### Post by mario.rimann on 2006-01-27
Hi!

I did as you recommended. The driver used is "ipw2200".

Now after reboot and suspend (memory), the problem doesn't seem to be solved. I'm new to linux so I'm not sure if what I tell now is correct. But as I see, the network DRIVER itself is ready directly after recovering from suspend. But the eth0 interface is down and has no ip address (checked with ifconfig). After approx. 30seconds, it get's self healed.

What I did after recovering from suspend:
ifconfig told me that there is no ip address for eth0 (there was no eth0).
iwconfig told me that there is eth0 with wireless extension - but not associated.

iwconfig (5seconds later) told me that it is associated with our wireless Net.

any hint on this?

---

### Post by stults on 2006-01-31
Okay, I've got one more possible solution for you up my sleeve.

After resume try to run sudo /etc/init.d/networking restart in terminal and see if it brings your network back up.  If so, you can add that command to the bottom of /etc/acpi/resume.sh scipt.

If this still does not work my only suggestion is to do a lot of searching on the forums for people with similar problems.  My suggestion on searching the forums is to use lots of different phrasing in your search.  I have found that the search tool is very specific, as in it only searchs for the exact words you type.  Try using variations such as plurals and alternate names, as well as running many different searches.  Good luck!

---

