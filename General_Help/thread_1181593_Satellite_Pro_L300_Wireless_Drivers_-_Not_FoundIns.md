---
title: "Satellite Pro L300 Wireless Drivers - Not Found/Installled"
date: 2009-06-08
forum: General Help
---

### Post by Vision1337 on 2009-06-08
Hey all. this is my second time using ubuntu, i reformatted my computer, as the first try with ubuntu i couldnt get wireless up and running. Aparently ubuntu doesnt reconize my drivers. So i will post as much information as i can.

About my experience with ubuntu:

I am still a very newb to ubuntu, i know how to install stuff via terminal, i wouldnt mind a step by step guide, or if anyone can email me help: [email]Vision@id.ru[/email]

Info:

Ubuntu 8.04
Comp: Toshiba Statellite Pro L300 
Model Number: PSLB1A-02D008
Wireless Card: I Am Not Sure On This.

I go into terminal and type: lspci .... I get:

Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00:0 Ethernet Controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet Controller (rev 02)

I am sure thats it.
I really need to get wireless working, otherwise im going to HAVE to go back to windows, i really like ubuntu, its alot more complicated, witch is what i like.

I have looked everywhere, i can never find the right drivers, please email me, i will check this thread every1-2hours. Tysm for any help. I really need this :)

---

### Post by kiridude on 2009-06-08
I would recommend as a first step to install Ubuntu 9.04 (latest edition). It is very possible that your wireless issue has been resolved in the newer version. If not, post back.

---

### Post by Vision1337 on 2009-06-08
How would i achieve that? since im ubuntu how would i burn the latest version, and i cant really do that as internet has been slowed, otherwise i would, any chance i can update ubnutu to the latest version like thru a program? since new versions always come out? :)

---

### Post by kiridude on 2009-06-08
Since you are using 8.04, you would have to go to 8.10, then 9.04.

I would suggest a fresh install. Download iso from ubuntu.com then burn to a cd, then boot with the cd and follow instructions. Instructions for how to burn the ISO to a cd are on the ubuntu site. You can download the ISO and burn it to cd in Windows if you're having problems with your present Ubuntu system.

I didn't really understand what you mean by, "i cant really do that as internet has been slowed."  How slow is "slow internet?"

---

### Post by Vision1337 on 2009-06-08
My internet downloads at a firm rate of 10kb/s at an australian dl link.

And im not sure what you mean by go to 8.10 then 9.04, would i not be able to download 9.04, reformat the whole comp and boot from disk? or would that not work?

---

### Post by kiridude on 2009-06-08
By upgrade, I mean simply clicking on upgrade in your update manager and everything is done automatically. You cannot upgrade from 8.04 to 9.04. You can only upgrade to the next version; therefore, you would have to upgrade first to version 8.10, then from 8.10 to 9.04. As this is a pain in the *** and leaves more room for errors, I recommend a fresh install:
- download 9.04 from Ubuntu.com
- burn downloaded image to a cd.
- put the cd in your cd drive and restart the computer.
- follow instructions to install new operating system.

Your internet speed is slow, so just leave it to download for a few hours and you'll be fine.

---

### Post by Kevbert on 2009-06-08
I believe that your wireless is possibly Realtek based. Do you have Windows XP drivers for wireless ? If so, you could go the ndiswrapper/ndisgtk route.
You may be able to use the drivers [[COLOR="Red"]here[/COLOR]]("http://forums.msiwind.net/debian/rtl8187se-drivers-for-ubuntu-and-deb-packages-t4954.html").
Ubuntu 9.04 supports this wireless chipset by default, so if you perform a clean install of 9.04 you may be able to get wireless to run straight away.

---

### Post by Vision1337 on 2009-06-08
Thanks for your help, i am downloading it, i do however have a few last questions.

I am really interested in ubuntu for the main fact of the complicity, windows is just so easy to use.
I am looking to become of some people might call a "hacker" however in my terms i prefer "learning systems of the web" but however i do have some questions.

1. I see that you use Ubuntu 9.04 Jaunty, does this mean there is different types of 9.04?
2. Is ubuntu really worth it for what i wish to do, i just found out i can get java to play the games i play. such as runescape, no i dont like it, i make money from it.
3. I have alot of windows programs that i wish to use, such as ZoneAlarm, and AVG. for secruity purposes. How would i go about finding the most secure/best anti-virus/firewall software (free/cracked) for ubuntu?

I do reliase that i am very new to ubuntu, i have had it on VPS using VMware before on XP. would i be able to grab your msn? might be easyier.

---

### Post by Vision1337 on 2009-06-08
OH that sounds great Kevbert. i'll reply as soon as i get 9.04 up in about 2days :O going to take 22hours-2days to download ubuntu, my internet speeds up in 6days but i dont wanna start blowing 700mb of my 12gb plan right of the bat.

---

### Post by Kevbert on 2009-06-08
The term hack refers to a quick and dirt solution to a problem or a clever way to get something done and so hacker refers to someone who's creative.
There are several versions of 9.04 Jaunty Jackalope - 32 bit or 64 bit, desktop or server, Ubuntu (gnome interface), Kubuntu (KDE) and Xubuntu (XFCE) as well as several other variants.
For games and other Windows applications you could try Wine (it's in the repositories), but not everything will work. Sun Java is also there.
Security generally isn't a problem. [[COLOR="Red"]UFW[/COLOR]]("https://help.ubuntu.com/8.04/serverguide/C/firewall.html") is the recommended [COLOR="Red"][firewall]("https://wiki.ubuntu.com/UbuntuFirewall")[/COLOR]. Antivirus software is generally not required as Linux viruses are currently only theoretical and don't exist in the wild. If you are emulating Windows or DOS you may need one for protecting shared Windows/DOS data such as [[COLOR="Red"]BitDefender[/COLOR]]("http://www.bitdefender.com/media/html/en/unicesportal/"), but in most cases any AV software will only scan for Windows/DOS viruses (which won't effect your linux system).
The good things about Linux are it's free, secure and very customisable.

---

