---
title: "Dial Up Connection"
date: 2005-07-10
forum: Desktop Environments
---

### Post by Infatuated_iPod on 2005-07-10
How do i set up a dial up connection with ubuntu, I am currently using Netscape DIal Up Service. I have absolutely no idea how to get online. Linux Networking is the only problem that i have. If i could ever figure it out, i would never use Windows. Someone please help me figure out how to set up my Dial up Connection. 

Maybe i need to change ISP's?\

Thanks.

-Lev

---

### Post by adwait on 2005-07-10
Umm, first off System>Administration>Networking. Then check mark the the Configured for ppp in the properties dialog box. Then run pppconf and give all the necessary info....

You can then connect with pon and disconnect with poff.

---

### Post by Infatuated_iPod on 2005-07-10
My modem is not detected..

---

### Post by adwait on 2005-07-10
have you installed the drivers for your modem? what kind of modem do you have?

---

### Post by Infatuated_iPod on 2005-07-10
I have an ESS E556T - PI Date Fax Modem 

I do not think there are any drivers installed, and i do not know how to do it.

---

### Post by adwait on 2005-07-10
Visit the manufacturers site and download linux drivers. If

1) They are *.deb, then use
sudo dpkg -i <filename>

2)They are RPM. use
sudo alien <filename>
sudo dpkg -i <deb_created_by_alien>

3)They are a binary file, use
chmod +x <filename>
./<filename>

---

### Post by Infatuated_iPod on 2005-07-10
I have no idea who the manufacturer is.. :-\

EDIT.. actually i do , but where are the linux drivers?

---

### Post by adwait on 2005-07-13
Many manufacturers dont provide Linux drivers :(. Maybe you could try some generic drivers for the modem......

---

### Post by coolclassic on 2005-07-13
Who is the manufacture as a google search does not produce a result on ESS E556T - PI Date Fax Modem

---

### Post by autocrosser on 2005-07-13
what I did was--
1. searched Google for Linux modem issues
2. found out that my internal modem was not supported by Linux
3. searched for a USB modem that would work with Linux (Zoom Fax/Modem 29xx-older Supra Express 2670 (a couple model#s by Supra work)-depends if you are Windows box or Mac box)
4. Went to eBay & searched for a Zoom Modem 29xx--
5. Bought one for 12.50 + shipping
6. hooked it up
7. Setup my network connection via /dev/ttyACM0 (or /dev/USB/ttyACM0--depends on what distro you use)
8. dialed out at close to 48K

End of story----

This was over a two month time about a year & 1/2 ago--has worked with a few minor glitches since----

Cheers!!
Dean

---

### Post by coolclassic on 2005-07-13
Your modem is from ESS Technology and the model is ES56T Pci modem. Here is a link that may help you.

[http://www.devidal.tv/~chris/winmodems/ess/ess_es56pi.html](http://www.devidal.tv/~chris/winmodems/ess/ess_es56pi.html)

Generally as this is a Winmodem they don't work under linux.

---

