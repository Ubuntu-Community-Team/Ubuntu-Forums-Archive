---
title: "First time installer on Dell Latitute D400, WiFi not working"
date: 2009-08-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bob_young on 2009-08-22
Hi,
 
First time I've used Ubuntu on a laptop, in this case a Dell Latitude D400.  The PC had XP on it, which became corrupted.  I took the opportunity to install Ubuntu in is place, but cannot get the inbuilt WiFi card to work.  
 
The version of Ubuntu I have installed is version 9.04 and the inbuilt wiFi card is an[FONT=Univers-Condensed-Medium][SIZE=2][COLOR=#231f20][FONT=Univers-Condensed-Medium][SIZE=2][COLOR=#231f20][FONT=Univers-Condensed-Medium][SIZE=2][COLOR=#231f20]
Intel® Pro Wireless MiniPCI card.
 
The network symbol appears at the top of the screen but withy a cross on top.  I have tried to access a hidden WiFi network with the correct network name and WPA/WPA 2 PSK password, but all it tells me is that it has just disconnected from the internet.
 
Please can you advise?
 
Regards,
Bob
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by Old_Grey_Wolf on 2009-08-22
Use the menu System -> Administration -> Hardware Drivers to see if there is a driver for the card listed. If there is, activate it.

---

### Post by bob_young on 2009-08-22
Hi,
 
No proprietary drivers are installed, but have ndiswrapper installed.  Is it possible to use the windows drivers for the dell under ubuntu with this?

---

### Post by Old_Grey_Wolf on 2009-08-23
Taken from the Help and Support:

# Obtain the Windows Driver for your system and locate the file that ends with .inf.
# Install the ndisgtk package.
# Open ndisgtk (System &#9656; Administration &#9656; Windows Wireless Drivers).
# Select Install new driver.
# Choose the location of your Windows .inf file and click Install.
# Click OK.

---

