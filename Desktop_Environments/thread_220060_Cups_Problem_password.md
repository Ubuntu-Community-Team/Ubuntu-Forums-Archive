---
title: "Cups Problem password?"
date: 2006-07-20
forum: Desktop Environments
---

### Post by russoje on 2006-07-20
I am using CUPS web server to set up a Laser Jet network printer.

Cups wants a password but it wants root.  Well there is not a root on this lol.

So I set a root password and CUPS still won't take root and the password.  So I tried to log into root to do this printer.

But no your not allowed to log into root as system admin so who can>

In the mean time I got to commandline and I can log in as root but now I can't startx because root can't run x lol

Help

Also I was setting the task bar trying to make it smaller and it poofed is there anyway to get it back?

Thanks

Jeanette

---

### Post by goobers on 2006-07-20
if you put **sudo** before anything on the command line, it will run it as root

---

### Post by Hi-Teck on 2006-07-20
I had the same prob. with cups. I never got access into it. To get my printer to share I used to following guide.
[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

If you have anymore questions feel free to ask.

Hi-Teck

---

### Post by russoje on 2006-07-20
I can't use sudo because CUPS is a web page.  How do I sudo a box that has user and password on it?

---

### Post by russoje on 2006-07-20
As far as that shared computer thing I have a HP jet direct card printer so I don't really share it.  Its just on the network and i print directly to it

---

### Post by goobers on 2006-07-20
> **russoje said:**
> I can't use sudo because CUPS is a web page.  How do I sudo a box that has user and password on it?
Sorry about that, i was having a mad moment :p I found a webpage on the subject, does it help at all? [http://www.cups.org/doc-1.1/sam.html#13_2](http://www.cups.org/doc-1.1/sam.html#13_2)

---

### Post by Hi-Teck on 2006-07-20
I have not worked with a hp jetdirect printer yet under linux. I am a linux newbie/novice....So I am talking from what I have learned...I am guessing you may have to edit /etc/cups/printers.conf yourself. There is a line in the file called "DeviceURI" this is the path to where ur printer is located.

I set up my system to printer to a networked printer on a WinXP machine once and the line looked like this 
"DeviceURI smb://login:pass@SERVERNAME/printername"
login = login to pc
Pass = password
and so on.....
smb = samba (is how linux and windows talks on a network)

*I know this in not the correct line you need but it may lead you in the right direction.*

Also here is my printers.conf file I used.
----------------------
# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Sun Oct  9 22:15:44 2005
<DefaultPrinter LaserJet-4>
Info LaserJet-4
DeviceURI smb://login:pass@SERVERNAME/printername
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>
--------------------------------

GOOD LUCK

Hi-Teck

---

### Post by Anduu on 2006-07-21
[http://www.ubuntuforums.org/showthread.php?t=10761&highlight=cups+password+shadow](http://www.ubuntuforums.org/showthread.php?t=10761&highlight=cups+password+shadow)

---

### Post by russoje on 2006-07-21
You guys are all great thanks for the help.  None of it worked but this is a great and helpful forum.

I decided to just reinstall what I had on the laptop because I was hoping that this would get my atheros wifi card working which it did not. 

Also the whole not having a root account left a bad taste in my mouth.  I really did not like anyone telling me I can't log into my own root account.

But this is a great community and maybe I will try Ubuntu again some day.

Thanks

Jeanette

---

