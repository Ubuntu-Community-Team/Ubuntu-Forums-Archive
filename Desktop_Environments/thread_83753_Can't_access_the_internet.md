---
title: "Can't access the internet"
date: 2005-10-29
forum: Desktop Environments
---

### Post by otware on 2005-10-29
Well I can...in some ways.

I can ping my router, and webpages: 'ping -c4 192.168.1.1', 'ping -c4 www.google.com' etc. But I cannot actually load webpages in Firefox 1.0.7. However once today, when i did 'firefox www.weebls-stuff.com' in terminal, it actually started to load the webpage, and stuff came up on the screen. it told me I had to download a plugin, so i pressed to download and it just hung for ages, not downloading. 

I can download packages using synaptic, so there is not problem there. I doubt it is a problem with my connection, as it works perfectly well under Windows XP. 

Any ideas on what the solution might be? btw I had a similar problem with Kububtu, but I could access the internet with Konqueror - not with firefox though.

---

### Post by otware on 2005-10-29
...any ideas?

---

### Post by cwaldbieser on 2005-10-29
[QUOTE=otware]...any ideas?[/QUOTE]
Are you just having problems with pages that use Flash, or does every page give you a problem?

---

### Post by otware on 2005-10-29
lol sorry everything gives me a problem. firefox and GAIM do not work.

---

### Post by zekolas on 2005-10-29
well it seems like a firefox problem, can you browse the web with other browsers like nautilus or even opera? I might try to uninstall firefox, also remember to delete the firefox profile in your /home/username direcory, I think it is a hidden directory called ".mozilla-firefox" also delete the "/usr/lib/mozilla-firefox/" directory then try to re-install firefox with apt-get. 

Also what happens when you put an ip adress in firefox, for example type in "216.239.57.99"(google) and see if it brings google up.

---

### Post by otware on 2005-10-29
well i thought i tried the IP for news.bbc.co.uk. however i think i actually entered the wrong ip (because im an idiot), probably the ip of a random dns server. 

How would this effect gaim? I was not aware that nautilus was a browser...i thought it was a tool that enables you to graphically install programs...

##btw:
I just tried a few things. I can ping the news.bbc.co.uk url and IP. If i put the IP (212.58.226.44) into firefox, the transfer bar gows half-way, and the title comes up on the window saying 'bbc news'. still no luck with Gaim. and it wouldn't let me delete /usr/lib/mozilla-firefox, even though i used su. 

How can you use nautilus to go online?

---

### Post by cwaldbieser on 2005-10-29
[QUOTE=otware]well i thought i tried the IP for news.bbc.co.uk. however i think i actually entered the wrong ip (because im an idiot), probably the ip of a random dns server. 

How would this effect gaim? I was not aware that nautilus was a browser...i thought it was a tool that enables you to graphically install programs...

##btw:
I just tried a few things. I can ping the news.bbc.co.uk url and IP. If i put the IP (212.58.226.44) into firefox, the transfer bar gows half-way, and the title comes up on the window saying 'bbc news'. still no luck with Gaim. and it wouldn't let me delete /usr/lib/mozilla-firefox, even though i used su. 

How can you use nautilus to go online?[/QUOTE]

Did you try disabling ipv6 like in this thread: [URL="http://www.ubuntuforums.org/showthread.php?t=80374&highlight=IPV6"]
[/URL]  Lots of people seem to have problems with IPv6.

---

### Post by otware on 2005-10-30
is ipv6 one of the things under networking?

---

### Post by zekolas on 2005-10-30
Ok it seems a lot of people are haveing this issue and it related to firefox enabling ipv6 and going through routers that do not support it. Follow these directions

 To fix this issue follow these steps:
1. sudo nano /etc/modutils/aliases

Look for this line:
# alias net-pf-10 off # IPv6

Change the line to: (remove the #)
alias net-pf-10 off # IPv6

2. sudo update-modules

then in firefox
type "about:config" in the address bar
then type "network.dns" and you will see the options shrink to only a few.
double click on the "ipv6 enable" and this will disable the function.

---

### Post by otware on 2005-10-30
Ok /etc/modutils/aliases has no lines at all in it. it is completely blank. i tried adding 
> alias net-pf-10 off # IPv6
but I don't know how to save the file.

What should I do?

Basically the file is completely blank. Nano gave me some instructions which didn't work (^R for read file etc.). How are these supposed to work? you type them in and press enter and nothing happens.

---

### Post by cwaldbieser on 2005-10-30
[QUOTE=otware]Ok /etc/modutils/aliases has no lines at all in it. it is completely blank. i tried adding 

but I don't know how to save the file.

What should I do?

Basically the file is completely blank. Nano gave me some instructions which didn't work (^R for read file etc.). How are these supposed to work? you type them in and press enter and nothing happens.[/QUOTE]
Are you sure?  Mine has a boat load of lines in it.  Try navigating to the file in Nautilus and see how big it is.  If it doesn't have anything in it, it should have size 0.

---

### Post by otware on 2005-10-30
Well if I can't navigate in the command line really. pressing the down arrow doesn't do anything, so presumably none of the lower lines have been written on. Is there something you have to do to actually edit and/or read the file?

---

### Post by otware on 2005-10-31
anybody?

---

### Post by teaker1s on 2005-10-31
browser address bar type 'about:config' search ipv6 and change 
network.dns.disableIPv6 to true- note this affects the iso with firefox an update from repositories of firefox and the problem goes away.

Number two the person I submited a bugzilla report couldn't read as there is an issue where ubuntu and debian can't see auto discover dns an easy cure is to configure a static ip on both the router and ubuntu system-admin-networking and set router dns address manually and enter it into ubuntu networking manually.

this affected me as I had internet, but synaptic had no access to repositories until I manually set my isp dns address

---

### Post by otware on 2005-10-31
Yes! firefox now works! Thank you! Yer I did wot you said and changed 'network.dns.disableIPv6' to true. 

However I'm still having some trouble with Gaim. any ideas?

---

### Post by cwaldbieser on 2005-10-31
[QUOTE=otware]Well if I can't navigate in the command line really. pressing the down arrow doesn't do anything, so presumably none of the lower lines have been written on. Is there something you have to do to actually edit and/or read the file?[/QUOTE]
Sorry, I meant open Nautilus, and browse to the directory where the file is and look at how big it is.

---

### Post by skisky on 2007-07-31
you must login as root, before you can do that you need to enable the root account....you can only edit the file when logged in as root. After you edit that file by removing the # you have to click save, as if your saving a word processing document.

---

