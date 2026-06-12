---
title: "Wireless not work"
date: 2010-10-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by michy88 on 2010-10-06
hi i got a Dell 1564 and i install Ubuntu as a application and after i get in i try to connect to a wireless and it doesn't pick up nothing

---

### Post by Dex73 on 2010-10-07
Go to System/Administration/Hardware Drivers to see if you have any. If not they'll have to be downloaded. I was able to get them just by system update using a ethernet cable.

Also, do you have a keyboard that allow you to turn off your wireless at the touch of a button? Some people have been know to bump them without knowing it.

---

### Post by michy88 on 2011-02-19
going to try that, were do i get the driver, no but im sure that i haven't switch anything of

---

### Post by am256 on 2011-02-20
In order for the following steps to work, you must be connected to the internet through your ethernet port on the laptop - if you are not, than you will not be able to search/download any additional drivers for your wireless.

On the top panel, Click on System --> Administration --> Hardware Drivers

You should get a popup that prompts you for the administrator password (you will need elevated privileges in order to search for proprietary drivers).  I have had to do this on most of the laptops which I have installed Ubuntu onto, using a proprietary driver for my wireless.

There should be some driver(s) that appear in the window. Basically, choose one and select "Activate."  If it installs correctly, you should have wireless functionality -- however I have found that sometimes if I have more than 1 wireless option, one of those options will install but then completely freeze my machine...when I go back to the desktop after rebooting I simply activate the other driver.

Hopefully this solves your issue.

---

