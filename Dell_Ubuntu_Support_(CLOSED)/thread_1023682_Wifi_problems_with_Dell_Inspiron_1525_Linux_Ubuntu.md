---
title: "Wifi problems with Dell Inspiron 1525 Linux Ubuntu 8.04 Hardy"
date: 2008-12-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by niled on 2008-12-28
Hi!

I got a Dell inspiron 1525 Laptop with Linux Ubuntu 8.04 Hardy

The Wifi modem I got is a: 0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

I have problems with my Wireless connection:(. I recently tried to insert a sim-card into the modem to get wireless internet. But I didn't get a wireless icon anywhere and it didn't work, I tried just to find some wireless networks in my neighbourhood(I know that least one got it cuz I found it with my brothers computer) but I still can't find the icon or anything.  I've been looking around on the different forums to find a solution, tried some of them i.e. this one:

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

Which didn't work for me. I don't have this icon which is shown here: [http://www.debianadmin.com/images/wpa/1.png](http://www.debianadmin.com/images/wpa/1.png)

And in the System-->Administration-->Hardware drivers  |Nothing is shown, it's empty, which makes me wonder if the computer even knows that there's a Wifi-modem. 

Please help me with this. I've spent a lot of time trying to sort it out by myself because that's what I hoped I would do, but now I'm stuck. And don't know what to do:confused:.

//Johan

---

### Post by IsraeliHawk on 2008-12-28
I've got the exact same laptop (and i truly enjoy it..!) and the simplest and easiest way to solve this is (i know you'll probably find this annoying..) simply by connecting the computer to a wired connection. 

Ubuntu will recognize it automatically, and install the updates. pay attention to press the yes button once or twice during the installation of the updates - it'll be for the specific driver. 

reboot

and enjoy.. :P

update if you can..

---

### Post by niled on 2008-12-28
I've been connected to a wired connection for a long while. I've updated everything as soon as possible, my last update was just a few days ago and I'm connected right now as well. So that is not the problem.
Ubuntu has to recognize my wireless modem, and find updates for it, which it hasn't done. And I've checked all the updates I got since the first day I got the laptop. And I think there has been none concerning Wireless connection. So I hope this clarify my problem little bit more than my original post
And my problem still exits:(

---

### Post by AmyRose on 2009-01-03
You don't need a SIM card for Wi-Fi.

Did you try installing the backported modules? Did this laptop come preinstalled with Ubuntu or did you install it over/alongside Windows?

Instructions for installing the backported modules are here: [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/WiFi_LED_does_not_work](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/WiFi_LED_does_not_work)

---

### Post by niled on 2009-01-04
My wireless does now work. Because of a failure in my computer, the button on the side was broken, that's why I didn't start the wireless. But it now works fine!

---

