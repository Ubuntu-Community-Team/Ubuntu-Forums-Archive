---
title: "*delayed web page loading*  :( dont make me go back to XP"
date: 2005-12-19
forum: General Help
---

### Post by ova-microsoft-dude on 2005-12-19
I just love linux compaired to XP... it rocks

But i have one problem, when i use any internet browser in ubuntu 10, gnome or KDB there is a long delay between the time i type or link to a website and until there is any activity in my modem. The webpage usualy takes on av 5-10 secconds to appear. However, once it does reach the website it actualy sends and recives data as fast as XP. Also, once i am connected to a website, any part of that website loads like normal, its just the initial delay of contact. 

This gets verry anoying as i visit manywebsites.

Is there anyway to fix this problem. I am sure there must be somthing going on. I would hate to have to go back to XP :( but i only use my computer for the net.

I am using an ADSL speedstream 4200 modem. 

Thanks for anyone's help in advance.

---

### Post by Zonkle on 2005-12-19
Try to clean the History,Temp files,Cookies, and everything in the Browser .... it might help.

And if you use Firefox .. I saw a lot of tweaking for it here and there, but I've never tried them before ... look for them in the forum.

Sorry I don't have any other idea.

---

### Post by briancurtin on 2005-12-19
theres a thing or two in the "about:config" page in firefox you could mess with, but i cant think of them off the top of my head. they usually make things that take a second, take less than a second, not anything that takes 5-10 seconds come down. 

the problem is not ubuntu. the problem is either your modem, or firefox. try upgrading to anything above the default ubuntu install of firefox as the fresh mozilla versions tend to run quicker anyways for some reason. see if that helps maybe.

---

### Post by BathroomNinja on 2005-12-19
I agree with installing a newer version of firefox. Try this guide to installing Firefox 1.5:
[http://www.ubuntuforums.org/showthread.php?t=99004](http://www.ubuntuforums.org/showthread.php?t=99004)


Let us know if that made it faster.  It made pulling up pages a bit faster for me.

---

### Post by bionnaki on 2005-12-19
install the lastest firefox (1.5): [https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29](https://wiki.ubuntu.com/FirefoxNewVersion?highlight=%28firefox%29)

---

### Post by handy on 2005-12-19
There's a thing you can do in Firefox, which may or may not help you, It will do no harm:
Enter "about:config" in the address field, then enter "ipv6" in the filter field, a single line should come up:
double click on it to turn it's value into "true"
That will turn off "IPv6" which you don't need & can cause a lot of internet conection problems at this stage.

Without changing this setting I can not conect to the internet!

Another thing (most likely to solve your problem) that will slow you down when connecting to different sites is if you have "Static IP Address" set in (using Gnome desktop) menu item: System/Administration/Networking"  select your network card, probably "eth0"  then the "Properties" button & choose "DHCP" in the "Configuration" drop down.

Good Luck

handy

---

### Post by maglis on 2005-12-19
If it is Firefox you are using to browse the web, try an extension called "[fasterfox]("https://addons.mozilla.org/extensions/moreinfo.php?id=1269&application=firefox")".

---

### Post by briancurtin on 2005-12-19
open a new tab in firefox, type "about:config" and go down to network.http.pipelining. double click on this line to set it to true. this allows the browser to make multiple simultaneous requests for a page. it is complimented by the maxrequests line right below it, which you can set to some number to open the maximum amount of requests up to a higher number.

this may help with your problem as well. its one of the about:config hacks i was thinking of earlier


another is to right click on that about:config page and select new > integer. name is "nglayout.initialpaint.delay" and the value you want it set to is 0. by default it is something just above 0, meaning that it holds off for a little bit before painting the screen of the page you just downloaded. this will ensure a quicker page display. try it out.

i believe you have to close firefox and restart it for these two to take effect

---

### Post by ova-microsoft-dude on 2005-12-20
[QUOTE=handy]There's a thing you can do in Firefox, which may or may not help you, It will do no harm:
Enter "about:config" in the address field, then enter "ipv6" in the filter field, a single line should come up:
double click on it to turn it's value into "true"
That will turn off "IPv6" which you don't need & can cause a lot of internet conection problems at this stage.[/QUOTE]

Thanks handy!!!! IT WORKED!!! 

LINUX ROCKS>>>>> :p  :)  :smile: :razz: 

I think this should be a defult in firefox... as this is a really tricky question and it seems (on further researching) alot of poeple have been helped by the "ipv6" fix....

maybe this could be a sticky or something.... 

Thanks!!

---

