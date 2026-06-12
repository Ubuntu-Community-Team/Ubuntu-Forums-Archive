---
title: "VM Virtualbox Ubuntu 13.10 Desktop LAMP. i cannot access with remote ftp client"
date: 2013-11-10
forum: Desktop Environments
---

### Post by adamjedgar on 2013-11-10
Hi guys,

I have installed Ubuntu 13.10 on VM Virtualbox and set up LAMP server on my own test system here at home (I am self hosting it to the internet through static ip address assigned by my isp) 

I then installed a default test wordpress cms which is up and running except for ftp connection used to add new plugins and media...it simply will not work!

To try a different method i installed filezilla client on another system and attempted to use that to connect directly to my web server instead of going through wordpress...i keep getting a cannot connect error (i think from memory its a "500 child died" error code).

I tried uninstalling ftp server app in ubuntu and installing new ones (such as vsftpd, and ftpd) nothing seems to work! From the youtube videos i have watched, it seems as if the ftp server software should just install and work "straight out of the box". I should be able to ftp connect using filezilla remotely without any tweaks on the Ubuntu 13.10 desktop LAMP. Is this true?

Virtual system setup is as follows: [B]Windows 7x64 Host + VM Vritualbox 4.3.2 r904055 + Ubuntu 13.10 LAMP
[/B]
[I]Just another note... i also have ubuntu 12.04 LAMP setup on same VM Virtualbox machine and it is running nicely and i am able to ftp connect and tranfer files/folders/change server folder/file permissions etc using filezilla client via static ip address.
I tried posting this question is the ask.ubuntu site. However, i dont seem to be getting any response as of yet. Im wondering if that's because its a release issue that requires fixing? Or is it because Ubuntu13 desktop version is restricted such that ftp functionality in Virtual Machine LAMP server is disabled/or not working?[/I]

---

### Post by adamjedgar on 2013-11-15
i think i may have figured it out...as i mentioned, i am running a vm Virtual box virtual server(ubuntu) on a windows 7 host.

There are 3 versions of Ubuntu installed 12.04, 13.10x32bit and 13.10x64bit. Each is has the same static IP address because i only run one at a time!

Now what i didnt think about was... my technicolor gateway stores 3 things.
1.the mac address of the virtual machine
2. its device name and 
3. the port forward ip address.


In addition to that, it appears i may only be allowed to port forward each application listed on the router to a single device at any one time. (For example 1 x http server to ubuntu 13x32-virtual machine) I was trying to get each of these assigned to 3 different virtual machines simultaneously that, whilst not being run at the same time and contain different mac address and device names, have the same static ip address (10.0.0.60)!!!

Whenever i started up a different virtual machine with the same IP address, the router was automatically changing the device name, however the game and application sharing applications (eg http server) had already been assigned to a previous mac address which was not being automatically updated...even though the device name in port forwarding had changed. 

Now my guess is that this is a purposeful restriction on the router to prevent idiots such as myself from naively causing a problem by trying to run multiple virtual machines, all with the same static ip address, as web server on the same network with the same port forwarding details!!!:popcorn:

Hope this may be of help to someone else who more than on virtual server set up and is also having port ftp problems

What i now wonder is...can i add additional copies of the same application in the routers applications list????:rolleyes::-k

---

### Post by adamjedgar on 2013-11-15
Nope cant be done!!!](*,):-({|=

---

