---
title: "Modems and ISP's"
date: 2006-02-28
forum: Desktop Environments
---

### Post by eightbit on 2006-02-28
Just wondering what types of dialup modems and isp's work with kubuntu.  I have 3, 1 pctel, 1 smartlink and 1 external motorola 33.6, and the 2 winmodems don't detect on kubuntu 5.10 and the external doesn't authenticate w/ my isp.  I use the smartlink with Linspire 5.0 and it works fine.  But linspire is too bloated for me , besides kubuntu is way faster and better.  I use 650dialup.com for my isp, but I would be willing to change isp's for one that works with kubuntu,  and I'd be willing to purchase a new modem if needs be.  Anyone have any winning modem/isp combinations with kubuntu 5.10?

Thanks in advance,
Scott :-k :-k :-k

---

### Post by gingermark on 2006-02-28
Maybe say which country you live in. Might help folks recommend an ISP.

I'm guessing you're a Yank. I'll leave others to guess why :D

---

### Post by Taino on 2006-02-28
Kubuntu is just Ubuntu with a Kde (front end), so the setup for the modems would be the same.. (driver wise etc..)

Modem setup info here from the Wiki:
[https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems](https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems)

What are you running? a PC or laptop?
Prefer to use an internal or external modem?
And what brand, model, speed, etc.. is the modem (you want) to use?

Post some of that info and we can help look into it further in a more specifc way. :cool:

---

### Post by eightbit on 2006-02-28
Yeah sorry ,USA.  Is it that obvious?

---

### Post by eightbit on 2006-02-28
I seem to have the most luck with the motorola 33.6 external.  I just plug it into the serial and set kppp to ttys0(com1).  But it failes to authenticate the password "no suitable passwords" Believe me I've checked the password and username plenty of times, they're correct.

---

### Post by Taino on 2006-03-01
[QUOTE=eightbit]But it failes to authenticate the password "no suitable passwords" Believe me I've checked the password and username plenty of times, they're correct.[/QUOTE]

Have any odd ascii characters in your password? anything other than letters and numbers would be a problem even spaces would be a problem in linux.

---

### Post by GeneralZod on 2006-03-01
[QUOTE=eightbit]I seem to have the most luck with the motorola 33.6 external.  I just plug it into the serial and set kppp to ttys0(com1).  But it failes to authenticate the password "no suitable passwords" Believe me I've checked the password and username plenty of times, they're correct.[/QUOTE]

Give this "noauth" tweak a try and see if it works then:

[http://ubuntuforums.org/showpost.php?p=593966&postcount=7](http://ubuntuforums.org/showpost.php?p=593966&postcount=7)

---

### Post by Matchless on 2006-03-03
Hi,
       Most external modems work without any driver installing and Ihave just managed to get an internal Smartlink working on kubuntu breezy, latest kernel update. have a look at the wiki dialupmodemhowto and then look at this Additional Smartlink internal modem howto:

I have found that in the latest Kubuntu Breezy update with Linux-headers 2.6.12-10-386 version 2.6.12-10-28 the Smartlink drivers in the Universe does not work.
All the steps in the wiki dialupmodemhow to, using the sl-modem-source file found on the universe repositories, compiles very successfully without any errors and the modem is detected nicely in KPPP and can be properly queried there as well. Then when connecting it runs and then fails to dial. The command ATDT also fails on a terminal and then locks the modem up, which can only be released by rebooting or using sudo ungrab-winmodem and sudo /etc/init.d/sl-modem-daemon restart. I have experienced this on various different PC's with Breezy and can recall that it did work with the first initial CD distribution of Breezy, but have not proven that again.

The problem can be overcome by using the  file slmodem-2.9.11-20051101.tar.gz that can be downloaded from the [http://phep2.technion.ac.il/linmodems/packages/smartlink/](http://phep2.technion.ac.il/linmodems/packages/smartlink/) site. You can then use the sl-modem daemon that can be downloaded from the universe repositories and your modem will be working again. Assuming you have successfully compiled and installed the driver from the repositories, but the dialing does not work. If not you have to install all the pre requisites up to that stage before continuing, gcc3.4, correct version linux headers etc (see dialupmodemhowto in wiki)
 These steps can be followed:
Use Synaptic to uninstall the sl-modem-modules, sl-modem-source and sl-modem-daemon files completely after determining that they do not work with your modem.
Now extract the file slmodem-2.9.11-20051101.tar.gz to the Desktop (use right click, extract here)
Rename this extracted folder to an easier name i.e. slmodem
CD in to this folder slmodem
sudo make
sudo make install
modprobe slamr
dmesg | grep slamr
  Check that no error messages were given during the last 2
Use Synaptic to install sl-modem-daemon from the repositories, or from your cache if still there
Use KPPP to test your modem, select /dev/modem and enter modem details and under Device do a Query Modem, if this works you are 99% there.
Now edit the /etc/default/sl-modem-daemon and change the line SLMODEMD_COUNTRY=SOUTHAFRICA                     (replace the USA default)
Do a reboot and check if your KPPP Modem Query shows South Africa
Now try and connect and the dialling should work

Note:  If the modem freezes due to interupting it or whatever you can save rebooting if you install ungrab-winmodem, also from the above site. You can then set up a Desktop icon, by right clicking with the following two commands sudo modprobe-ungrab-winmodem and sudo /etc/init.d/sl-modem-daemon restart and this icon can then just be clicked to properly reset your modem without rebooting.
Smartlink modems using Netodragon chip ND92XPA works well with this, but chip MDV92XP does not work in Breezy at all, but I recall using it in Hoary successfully. This again has not been proven again.

---

