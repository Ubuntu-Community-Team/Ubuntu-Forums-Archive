---
title: "Command prompt logon, no UI"
date: 2009-06-10
forum: General Help
---

### Post by fumblejack on 2009-06-10
I just installed Ubuntu server on an old computer of mine, amd all seemed to go fine.  When it starts up, it doesn't get to the login screen that I am used to.  It stays in the terminal view with a prompt for user, and then password.  It accepts the user and pass that I set up, but I don' know how to get it to start.  I experienced this with a Mint install that I had set up on a different laptop, but can't remember how to get it to start.  I thought that I had to type 'video', then manually choose the driver, but it isn't accepting this command.

---

### Post by synapsys on 2009-06-10
By default, Ubuntu server has no gui installed for security reasons. There will only be a gui if you specifically chose this option during install. If you have it installed you can login and type:

```
startx
```

---

### Post by michy99 on 2009-06-10
The server version does not come with a graphical interface. You can install one, but then you might as well install the desktop version instead.

---

### Post by balloooza on 2009-06-10
Try
```
sudo gdm
```
after text logon

---

### Post by balloooza on 2009-06-10
Oh wait, I forgot the server part :)
 type
```
sudo apt-get install ubuntu-desktop
```
then wait, then type the other command

---

### Post by balloooza on 2009-06-10
Ok, wait, do you want to use this old machine as a server, if so, do not install a gui, I can help you get a server running with a sick web interface

---

### Post by synapsys on 2009-06-10
Yeah.... usually don't want a server to have a gui..... it opens up unecessary security holes....

---

### Post by fumblejack on 2009-06-10
I am considering setting up a home network.  I got the old PC from  a family member and wanted to play.  I don't have a need for it, just a morbid curiosity.  I have only one windows xp computer at home.  My wife has a ton of music on it, and my two kids have their own users on it.  They aren't old enough for me to worry about parental controls yet.  Does anyone see a benefit for me to set up a server?  I would like to be able to have the knowledge of setting up web server and/or mail server, but again it is not necessary.

---

### Post by balloooza on 2009-06-10
Yes, A server is good for a home network, because it can be used as a firewall, a web server, A vpn server, and dhcp server, and DNS.

It is a great experiance setting up one, all you need is:

Network (computer to connect to it, it is pointless to make a server with no clients.
X2 Network cars,I picked up an extera at office max for 15 bucks (USD)
Server

Tada, You have two for sure, you might need a second card. It is great for me to have a server, and I benifit from the security, and vpn.

Some other features:
DHCP is much faster than standered router
DNS is a dns cache, this speeds up the internet, if you want to know the details, just ask
My server has been up for 60 days (as of today) And that is only because I had to relocate the server.

I would love to help you decide what you want with the server.

Mark

---

### Post by fumblejack on 2009-06-10
Well, both computers have on board network ports.  At present, I have digital cable and internet through the same provider.  Network hardware I am using include modem to switch to router.  The router has a firewall in it, which I know how to disable.  I guess I was hoping that I could set things up through a few commands, or 'wizard' of some type.  I installed server at work without any network or internet connection, with the intention of plugging it in at home, turning it on, and following a few prompts for initial setup.  Then getting into more depth later on.  I guess at this point, I should take it home and configure it from there.  I am not scared of trying things.  There really isn't much that I see could go seriously wrong.

I use the PC at home for streaming baseball games from MLB.com, which is quite secure, and streaming some tv shows from p2p site( i have yet to receive anything malicious).  My ISP provides an antivirus/spyware program, which probably won't be needed.  I would like to use the server as web server, mail server, but have a lot to learn about that kind of stuff.  I have dabbled with some web hosting software, but have no knowledge of html code.  I appreciate that you are willing to help, but this could be quite the undertaking for both of us.

---

### Post by balloooza on 2009-06-10
OK, so at home I use somthing called ebox, it is a server platform, based of of ubuntu, they also make there own disk, you can download the iso from:
[http://ebox-platform.com/download/latest](http://ebox-platform.com/download/latest)
This link will give you the latest ebox, it is verry stable for me, and it is based of of hardy LTS, so you have 2 more years of support, and a more mature system. (usualy servers are not upgraded after every release every 6 months)
So the first thing you will need is a computer (the one you install the ebox cd on) with two network cards, if you are fermiliar with the eternet naming system on linux, you will end up with eth0 and eth1, next you will need an ethernet cord, then you you should print out this:
[http://forum.ebox-platform.com/index.php?topic=896.0](http://forum.ebox-platform.com/index.php?topic=896.0)
So now comes the part when the network has to go down, alert your house (if you are like us) Then go to the router page (linksys router=192.168.1.1, but you already said you know how to disable it) and disable:
-Firewall
-dhcp
-NAT
And connect the setup like this

MODEM -----ethernet
                       |
SERVER ----one of the ethernets (it will end up being eth0, so you might half to swap)
                       |
ROUTER ----(NOT THE INTERNET PORT, USE ONE OF THE 4 LOCAL PORTS)
                       |    
                Other Computers, connected on the remaining 3 ports

Then the guide will take you through the basic setup, and get the internet running again, if you run into any problems during the install, (you probobly won't) then reset the router (little buton on the back) and connect it back how you had the setup, and post back here.

---

### Post by fumblejack on 2009-06-10
Awesome.  This actually excites me.  Being able to take control of my system.  I will give this a shot and see what happens.

---

### Post by cdsJerry on 2009-06-12
Ok. I'm a total newbie to Linux. I'm trying to install dotProject and need to build a Linux box to run it (it runs as a website).   I choose ubuntu because it looked like the easiest to learn and the server version included the PHP and MYSQL I needed.

So I did an installation of ubuntu server on a box I had already. Used the entire drive with plans to dedicate the machine to this task.  Figure it's high time I learn something about Linux as it sounds pretty interesting to me and I'm not a huge Windows fan, just experienced in Windows (I maintain a few Windows servers).

I'm a bit distressed however because I was expecting a GUI.  I see from this thread that it's not suggested to use a GUI but how does a newbie have any clue what commands are available?

This is my second time to experiment with Linux and both times I've finished the installation and been left with a system wanting commands with no way to know what commands are available.   I go from knowledgeable, to dumb-as-a-rock in 2.3 seconds.

---

### Post by michy99 on 2009-06-12
This might be a good place to start:

[https://help.ubuntu.com/9.04/serverguide/C/index.html](https://help.ubuntu.com/9.04/serverguide/C/index.html)

---

