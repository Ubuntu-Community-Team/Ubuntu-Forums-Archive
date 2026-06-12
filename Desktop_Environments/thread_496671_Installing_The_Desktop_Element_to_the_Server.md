---
title: "Installing The Desktop Element to the Server"
date: 2007-07-09
forum: Desktop Environments
---

### Post by Dan221081 on 2007-07-09
Ok I am currently working for a company that are in the process of setting up their own (internally) hosted website. They have hired a company to create a website for them that will allow them to access and edit the site using a content management system. However when the server was delivered we found that they had put Ubuntu server 6.06 Dapper Drake on it. 

So the first thing I tried to do was to try and install the desktop element onto the server. So I did the following :-

Apt get Update
Apt get Install ubuntu-desktop
Apt-get Install GDM

This took a fair while to download as we are only on a 2mb connection here. However when it finished we rebooted the server thinking we would be presented with the desktop interface once the server booted back up. 

However when the server restarted this was not the case and the server was still presenting us with the text based console. So we looked into ways of starting the desktop using the command 'Startx' but this just presents us with an error message.

The error message is as follows :-

[B]Hostname : Unknown Host 
XAuth: Creating New Authority File /root/.Serverauth.15723
X: Cannot Start /etc/x11/x (No Such file or Directory), Aborting.

Giving Up

Xinit: Connectiong refused (error111): Unable to connect to Xserver
Xinit: No Such Process (Errno 3) : Server Error[/B]

I wondering if someone can help im not massively experienced with linux however over the last couple of months I  have been experimenting with various distros so any input would be great 

Many Thanks

Dan

---

### Post by bclark on 2007-07-09
try:

sudo /etc/init.d/gdm start

---

### Post by Dan221081 on 2007-07-09
Ok I had a crack at that and got the following :-

Sudo Unable to lookup (computername).(domainname).com via gethostname()
Sudo /etc/init.d/gdm command not found

:(

---

### Post by bclark on 2007-07-09
> **Dan221081 said:**
> 
Sudo Unable to lookup (computername).(domainname).com via gethostname()
Sudo /etc/init.d/gdm command not found

:(

just to make sure type 'sudo' in all lower case

---

### Post by az on 2007-07-09
Don't log in as root.  That's your problem.

As well, make sure all the packages were properly installed (probably not neccessary, since GDM was already installed and you would have been told of broken packages when you tried to install that.)

sudo apt-get -f install


As well, if you have trouble with any dektop hardware, install the desktop kernel.  The server kernel does not play well with all dektop hardware (like some mice, for example)

sudo apt-get install linux-image-generic

---

### Post by Dan221081 on 2007-07-10
Ahhh Great I will have a go at logging in with a different user I dont know if these guys have setup any standard accounts on the server yet. 

I ran Grep (companyname) /etc/passwd to see if there was any users similar to that

and I got back the name of another user which was (companyname)admin

but when I 

su (companynameadmin)

I got a prompt back which looked like this :-

(companyname)@(domainname)

so I ran the 'startx' again but got the same error message :-

[B]Hostname : Unknown Host 
XAuth: Creating New Authority File /root/.Serverauth.15723
X: Cannot Start /etc/x11/x (No Such file or Directory), Aborting.

Giving Up

Xinit: Connectiong refused (error111): Unable to connect to Xserver
Xinit: No Such Process (Errno 3) : Server Error[/B]

Im guessing that either the user that I switched to was also at root level ?? Or that the problem lies with the networking side of things (going on the failure to connect error messages)

I created a pleb user switched to him using su and then tried to run startx but got the same error message :(

Oh I tried the two commands above 

the **apt-get -f install **returned that it didnt need to do anything 
and the **apt-get install image-generic** came back saying it couldnt find the package 
I tried another **apt-get update** and then tried it again but no joy.

---

### Post by az on 2007-07-10
> **Dan221081 said:**
> Ahhh Great I will have a go at logging in with a different user I dont know if these guys have setup any standard accounts on the server yet. 

I ran Grep (companyname) /etc/passwd to see if there was any users similar to that

and I got back the name of another user which was (companyname)admin

but when I 

su (companynameadmin)

I got a prompt back which looked like this :-

(companyname)@(domainname)

so I ran the 'startx' again but got the same error message :-

[B]Hostname : Unknown Host 
XAuth: Creating New Authority File /root/.Serverauth.15723
X: Cannot Start /etc/x11/x (No Such file or Directory), Aborting.

Giving Up

Xinit: Connectiong refused (error111): Unable to connect to Xserver
Xinit: No Such Process (Errno 3) : Server Error[/B]

Im guessing that either the user that I switched to was also at root level ?? Or that the problem lies with the networking side of things (going on the failure to connect error messages)

I created a pleb user switched to him using su and then tried to run startx but got the same error message :(

Oh I tried the two commands above 

the **apt-get -f install **returned that it didnt need to do anything 
and the **apt-get install image-generic** came back saying it couldnt find the package 
I tried another **apt-get update** and then tried it again but no joy.

Don't run startx as root!

and it's 
sudo apt-get install linux-image-generic

---

### Post by Dan221081 on 2007-07-10
"Don't run startx as root!"

I didnt :-

"I created a pleb user switched to him using su and then tried to run startx "

unless thats still classed as root ???

when I created bob I used the following :-

**useradd -gusers -s/bin/bash -ptest -d/home/bob -m bob**

because I only added him to the users group I'm guessing he shouldnt have any admin privilages.

sorry was a typo in my last post I did try 

**sudo apt-get install linux-image-generic **

and it couldnt find it.

The output was

[B]Reading Package list...Done
Reading Dependancy Tree...Done
E: Unable to locate package linux-image-generic[/B]

The problem Im encountering has got to be network related im going to download a copy of ubuntu server and run it in a vmware enviroment and see what happens. Im guessing that I wont have half as many problems as I am at the mo.

---

### Post by linuxpimp on 2007-10-27
Hi all

Similkar issues but with Gutsy.

WHen i try sudo apt-get install ubuntu-desktop or sudo apt-get install gdm i get "package not found" for each of them?
Please assist.

Thank

LP

---

### Post by linuxpimp on 2007-10-27
> **linuxpimp said:**
> Hi all

Similkar issues but with Gutsy.

WHen i try sudo apt-get install ubuntu-desktop or sudo apt-get install gdm i get "package not found" for each of them?
Please assist.

Thank

LP

Looks like my problem was DNS and ipv6 related as in [http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)

Packages downloading now, so looks ok.

LP

---

### Post by Soarer on 2007-10-27
If you are going to use this as a server, you might want to look at [Webmin]("http://www.webmin.com") which is a web based graphical-ish interface for servers. You can then adminster your server from any browser.

---

### Post by socceroos on 2007-10-27
> **Soarer said:**
> If you are going to use this as a server, you might want to look at [Webmin]("http://www.webmin.com") which is a web based graphical-ish interface for servers. You can then adminster your server from any browser.

Another possible option is Ebox. Great server configuration tool. It should be officially supported in the next Ubuntu release (Long Term Support), and from the sound of it, it will be the official tool for administering Ubuntu Server edition.

You can install this package via synaptic with: sudo apt-get install ebox-all ebox

---

### Post by Soarer on 2007-10-27
Ebox looks interesting. It is not as comprehensive (yet?) as Webmin (no Apache, MySQL for example) but I'd rather use a tools from the repos any day.

Thanks socceroos :)

---

