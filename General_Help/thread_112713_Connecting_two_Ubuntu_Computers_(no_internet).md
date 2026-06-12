---
title: "Connecting two Ubuntu Computers (no internet)"
date: 2006-01-04
forum: General Help
---

### Post by 90Brougham350 on 2006-01-04
Hi, I'm new to these boards. Recently started using Linux, and I really enjoy it. I don't know much code yet, but I'm learning. So, with that, hi everyone!

Here's my problem:
I have Ubuntu on my desktop and Ubuntu on my laptop. On my desktop, I have all my music and video files on a NTFS hard drive, but I figured out how to mount it from the help files so I can use my files in Ubuntu. I was pretty proud of myself, having never played with the terminal before. So now I want to use an Ethernet cable and transfer my files from my desktop to my laptop, since I'm going to be doing a little traveling, and can't take the desktop along, obviously. 

My question:
How do I go about transfering data between two computers running Ubuntu, by way of an ethernet cable?

Am I completely nuts? I think this is called bridging, isn't it? Meh, I don't know much yet but I want to learn. I'd really appreciate it if somebody could walk me through this one. I don't have a router or anything like that, just two computers and a cable. Much appreciated!

Brian

---

### Post by srt4play on 2006-01-04
You're going to need a crossover cable to network computer straight to another computer.

There are many ways to do it, but IMO the easiest and what I would do is set up a ssh server on the computer you want to transfer files from.  Then log in through the nautilus file browser via the Go --> location menu entry.  Then in the address bar type  ssh://remoteusername@ip.address.of.ssh.server
Once you give the password you will be browsing the remote file system and you can copy and paste.

---

### Post by 90Brougham350 on 2006-01-04
Sorry for the newb questions, how much does a crossover cable cost? Can I get one at Circuit City or Best Buy? Could you elaborate a little more on the ssh server? I'm new to all of this. Sorry for the simple questions, but thanks for patience!

Brian

---

### Post by dcast on 2006-01-04
you can buy a straight ethernet cable adn turn it into a crossover cable like this: 

[http://www.littlewhitedog.com/content-8.html](http://www.littlewhitedog.com/content-8.html)    that is if you can't buy one.

---

### Post by srt4play on 2006-01-04
Hey, there is nothing wrong with asking questions and no need to apologize. That's what these forums are for.  

I found this at Circuit City's website:
[http://www.circuitcity.com/ssm/Belkin-CAT5e-Crossover-Patch-Cable-A3X126A-10-YLW-M-/sem/rpsm/oid/98124/catOid/-13011/rpem/ccd/productDetail.do](http://www.circuitcity.com/ssm/Belkin-CAT5e-Crossover-Patch-Cable-A3X126A-10-YLW-M-/sem/rpsm/oid/98124/catOid/-13011/rpem/ccd/productDetail.do)

and this at Best Buy's website:
[http://www.bestbuy.com/site/olspage.jsp?skuId=6991963&type=product&id=1099390830926](http://www.bestbuy.com/site/olspage.jsp?skuId=6991963&type=product&id=1099390830926)

SSH stands for secure shell, and is a way of remotely accessing a pc. Typically used only for command line access, but through nautilus you can browse files of remote ssh servers much like you would in windows network neighborhood or whatever they call it now.

---

### Post by 90Brougham350 on 2006-01-05
[QUOTE=srt4play]ssh://remoteusername@ip.address.of.ssh.server
Once you give the password you will be browsing the remote file system and you can copy and paste.[/QUOTE]

OK, so the remote user name I type in, is that the name of the account on the server computer I'm trying to access? So for instance, if the account on the server computer was John_Doe_123, I just type that in? How do I find the ip address of the server computer?

So when I plug the crossover cable in and turn both computers on, I just go into Nautilus on the laptop and type in the info and password and i can view the desktop?

Brian

---

### Post by srt4play on 2006-01-05
Ok one step at a time.

First you need to verify that the computers can talk to each other.  What ip address did you give the desktop? What ip did you give the laptop?

To find out the ip address of an Ubuntu computer, type this in a terminal:

ifconfig

And you will see probably two entries, one for eth0 and one for lo.  eth0 is your ethernet device, and it's ip address is given in the "inet addr:x.x.x.x" part of the output.  For example, one of my boxes has this as output:

eth0      Link encap:Ethernet  HWaddr 00:10:B5:5D:58:4C
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::210:b5ff:fe5d:584c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1488 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:510668 (498.6 KiB)  TX bytes:493630 (482.0 KiB)
          Interrupt:10 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3717522 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3717522 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4010384439 (3.7 GiB)  TX bytes:4010384439 (3.7 GiB)

where the machines ip address is 192.168.0.3

Once you know the ip address of the desktop, type this in a terminal on the laptop:

ping x.x.x.x

where x.x.x.x is the ip address of the desktop that you found using the ifconfig command.  If you get replies, good you're communicating. If it just sits there with no replies, then there is a problem with the networking configuration.

Post back and we'll continue.

---

### Post by 90Brougham350 on 2006-01-06
Alright, I bought a cable, but when I type 

ifconfig

in the terminal, I don't get an IP address. I'm not connected to the internet because the two computers are connected to eachother. The little network logo in the upper right of the screen changed and showed I was plugged in when I plugged the crossover cable in. I'm assuming this is the problem. I'm also assuming that since the little network logo changed when I plugged it in to both computers, the connection is good. Alright, where to from here?

Brian

---

### Post by professor_chaos on 2006-01-06
First off, I'm not so sure you need a crossover cable if your network cards are realitively new.

Second, since neither computer is connected to the internet, then just assign each one a unique IP
On the menu bar at the bottom of screen click Applications -> System -> Admin -> Networking. Click on Ethernet Connections -> properties. Change Configuration to Static IP. Make sure connection is enabled.

Then, after doing this verify IP by "ifconfig" command. When both machines have a unique IP address, then try to ping the other computer from the terminal.
If ping works, then you are free to set up a number of methods to transfer data. NFS, FTP, SSH, etc.

---

### Post by 90Brougham350 on 2006-01-06
Alright, I'm getting somewhere now. Unfortunately I ran into some problems. My laptop has Ubuntu on it and I was able to quickly set a static IP address. However, my desktop has Ubuntu and Suse on it. I first installed Suse when I was interested and then switched to Ubuntu. When I started the desktop tonight, I discovered my C drive is corrupt, so Ubuntu won't load, but Suse will. However, when I get to the Network Address Setup in Suse, I can't set a static IP address that seems to work. I type in a number (I'm using 187.65.43.21), and it looks like that's the network card's number, but ping from the laptop doesn't work.

Brian

---

### Post by markovuc on 2006-01-06
To setup ip addresses from console is not very hard. Here is what I would do:

You can set ip address with ifconfig command. That kind of setting will not be remembered after you reboot, but will be enough to set up local network between two computers for transfering files (that is what I do when I need to transfer files from my laptop to my home computer). On your laptop you should type (in console):

ifconfig eth0 10.0.1.1 netmask 255.255.255.0 broadcast 10.0.1.255

And on your home computer:

ifconfig eth0 10.0.1.2 netmask 255.255.255.0 broadcast 10.0.1.255

Two computers are now on the same network and can talk to each other. At this point I usually start ssh daemon on one of the computers. On suse you can start it from yast, and on ubuntu you may type (as root):

/etc/init.d/ssh start  (or sudo /etc/init.d/ssh start)

Now you can connect to that machine via ssh, by typing:

ssh 10.0.1.1 (or 10.0.1.2)

or copy files with scp command, for example:

scp [email]username@10.0.1.1:/home/username/Desktop/*.mp[/email]3 .

will copy all mp3 files from your Desktop folder on 10.0.1.1 machine to 10.0.1.2

Or you can start sshd on Suse, and connect to it from gnome on ubuntu box (as suggested in 2nd post).

Also, remember to stop firewall on the computer that has ssh daemon running (if you have firewall running at all).

I hope this will work for you ;)

---

### Post by 90Brougham350 on 2006-01-07
Alright, I'm good to go. Thanks for all your help. I was still having no luck connecting even after I had done all the steps, turns out the crossover cable I bought; the ends were messed up. Bought a new cable, and it works like a charm! Thanks everyone!

Brian

---

