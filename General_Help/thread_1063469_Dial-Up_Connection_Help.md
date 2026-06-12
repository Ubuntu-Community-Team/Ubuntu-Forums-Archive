---
title: "Dial-Up Connection Help"
date: 2009-02-07
forum: General Help
---

### Post by Tramx on 2009-02-07
I recently switched to a dial-up connection in Ubuntu. I'm using CSloxinfo service provider and I'm provided 3 pieces of information. 1.) Username 2.) Telephone Connection No. 3.) Password. How can I set up my internet connection settings so it runs on dial-up? Help appreciated.

---

### Post by Shazaam on 2009-02-07
Do you have an internal or external dialup modem? Is the modem detected? Open terminal (Applications>Accessories>Terminal) and type this in and hit enter...
```
wvdial
```
If it is not detected go here...
[https://help.ubuntu.com/8.10/internet/C/modem-identify.html](https://help.ubuntu.com/8.10/internet/C/modem-identify.html)

Once you get the modem detected/configured open terminal again and type this in...
```
gksudo gedit /etc/wvdial.conf
```
This opens the wvdial configuration file for editing. Terminal will ask you for your user (login) password. You will not see anything as you type your password, don't worry type it in and hit enter.  When gedit opens you will see this...
```
[Dialer Defaults]
Phone = 
Username = 
Password = 
New PPPD = yes
```
Enter your ISP info and then go to File>Save and save it. To connect, open terminal and enter wvdial again and it should connect. Don't close terminal once it connects; hit CTRL+C to disconnect. Once it connects it is a good idea to run Synaptic and update Ubuntu. At this time install gnome-ppp through Synaptic. It is a gui dialer app for wvdial and will appear in Applications>Internet. After installing gnome-ppp go back and remove the info from wvdial.conf then open gnome-ppp and re-enter your connection info again. You should be good to go.

Note: if you are running Kubuntu the dialer app is called kppp.

---

### Post by deckeeper on 2009-02-07
There is more than one way to setup your dial up.   I thought I was the last guy to still have dial up :(   Try going to terminal and type...

sudo pppconfig 


BTW  winmodems generally don't work.. most exterior dial up modems do.

---

### Post by editrix on 2009-02-08
There's lots of us still on dialup. I wish the Ubuntu folks realized that. KPPP is a very good app and easy to understand, I recommend it even if you're using Gnome.

You'll also want to check out:
Dialup modem HowTo [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
Linmodems.org [http://www.linmodems.org/](http://www.linmodems.org/)

---

### Post by gfulton on 2009-02-08
I am dialup as well, but since I have an unsupported winmodem (well, it is supported but drivers are 20 dollars...) I am currently running under vmware. 

Hopefully I will be getting an external hardware modem soon!

-gf

---

### Post by ieee488 on 2009-02-08
plenty of 3Com PCI modems with TI chipset that work with Linux on eBay if you know what to look for
[http://xmodem.org/chipsets/ti/ti_700.html](http://xmodem.org/chipsets/ti/ti_700.html)

---

### Post by Tramx on 2009-02-21
Sorry for the late reply, I was on a short vacation trip :D. Thanks for all your comments. The dial-up configuration seems to work and now I am running dial-up. Until then, I hope I can find another ADSL service provider.

---

### Post by Sudofreak on 2009-02-23
I too do not have access to broadband (either DSL or cable)
and must rely on dialup for internet connectivity.
I got wvdial to work by following the instructions at the following site:
[http://dyenibib.wordpress.com/opensource-linux/wvdial-ubuntu-huawei-and-globe-visibility/](http://dyenibib.wordpress.com/opensource-linux/wvdial-ubuntu-huawei-and-globe-visibility/)
It works ok, but I have to connect as root (sudo wvdial)
which I am not really to wild about.  I was able to download
gnome-ppp, but haven't been able to get that to work because
of permission issues (probably have to run as root to get it to work.
I am very disappointed that all distributions of Linux treat dialup as if it were the scourge of the earth. I wonder how many people who are considering trying Linux, but don’t have access to broadband, would take the time to configure a modem. I would venture to say that unless a user is really committed to Linux, they aren’t going to take the time. I doubt that linux will ever make it out of the ‘not ready for prime time’ category if they continue to ignore a good portion of their target audience.

---

