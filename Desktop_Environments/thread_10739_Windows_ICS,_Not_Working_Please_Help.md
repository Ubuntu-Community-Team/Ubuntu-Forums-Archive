---
title: "Windows ICS, Not Working Please Help"
date: 2005-01-10
forum: Desktop Environments
---

### Post by andrewflanery on 2005-01-10
I have an internet connection that is shared through a windows xp pc.  I set up the computer running Ubuntu with a static IP address and typed in the window's ip as the gateway.  I know that they can see each other because samba is running fine and they can ping each other.  Just the internet connection will not share, does anyone have any ideas. 

BTW:  I did a search for this in the forums and none of the solutions provided for the others worked for me.

---

### Post by cabu on 2005-01-10
Did you also set the windows box IP as your DNS server?

---

### Post by twisted_steel on 2005-01-10
In my personal experience, all I needed to do to get connection sharing to work is enable DHCP on the client computer.  That way it will look up all the configuration information from the Windows computer.  Can you post the configuration you tried?

---

### Post by cabu on 2005-01-10
Yes, going via DHCP will work. I personally prefer to go with a static IP, since there is a lag at boot when the windows computer is not on to assign an address.

---

### Post by andrewflanery on 2005-01-11
I do have a static assigned, and no I don't have the windows machine set as my DNS server.  I will try DHCP again and see if it works.  I only had the windows machine set as the gateway.  Thanks for all the help.

---

### Post by andrewflanery on 2005-01-11
Okay, I tried DHCP and it didn't work still.  And I did check, the windows computer was set as a DNS server.  I don't know what else to do!  And ideas?

---

### Post by cabu on 2005-01-11
Do you have any kind of firewall software on the Windows machine that may be blocking you?

---

### Post by andrewflanery on 2005-01-11
I have a firewall, but isn't causing the problem.  i can use samba to share network resources and they can ping each other.  I just can't figure out why it isn't working.

---

### Post by andrewflanery on 2005-01-11
I am reinstalling now to see if it will make a difference.  This time I will leave it on DHCP.  Let you know how it goes.

---

### Post by andrewflanery on 2005-01-11
It made no difference at all, same as before.  I am starting to become depressed.  Anyone have any suggestions not tried?

---

### Post by Rancoras on 2005-01-11
You have ruled out a problem with the windows machine, right?

---

### Post by cabu on 2005-01-11
You may be able to use samba and ping the windows machine and still be blocked from the internet. Also, try accessing a website by it's ip address.

---

### Post by andrewflanery on 2005-01-12
I have tried accessing a website by it's IP, it still doesn't work.  And yes I am pretty sure that I have ruled out the windows machine.  I run Zonealarm on the windows machine, and I put the linux box into the trusted zone and turned off the firewall for trusted zone.  Any more ideas?

---

### Post by richbayliss on 2005-01-12
I'd personally try removing the firewall completely, and Set Ubuntu to use DHCP. start both machines, and when both are started, try accessing the net.

IF it doesnt work, restart the ICS machine - NOT THE UBUNTU ONE

There is a post about DHCP issuses i read earlier.

Worth a try?!!


NOTE - Samba and DHCP/DNS requests use different ports  :D

---

### Post by ulrich on 2005-01-12
when you search the rgistry of the winbox for "IPForward"
is there 0 or 1 to find?

this always was a problem when using W2K, dont know if its enabled in XP.

---

### Post by andrewflanery on 2005-01-12
It works now, thank you all.  It must have been the zonealarm firewall after all.  I disabled zone alarm and used windows firewall, and it works.  Thanks for all the help.

---

