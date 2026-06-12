---
title: "I want to cry (firestarter, dhcp3)"
date: 2006-01-01
forum: General Help
---

### Post by chocolatetoothpaste on 2006-01-01
I am ready to cry, I have tried to work this out for so long.  I once had firestarter up and running smooth, and I had dhcp3 running to, handing ip's like candy on my LAN.  I had to reinstall due to my stupid mistake, and now I cannot get them to work.  I had this prob before, but some on sent me to this thread [http://www.ubuntuforums.org/showthread.php?t=74925&highlight=firestarter+work](http://www.ubuntuforums.org/showthread.php?t=74925&highlight=firestarter+work) and I got the problem solved.  Now, I have done exactly what this thread says, and I can't get it to work again.  I am desperate! Someone, anyone, please help!

---

### Post by readingboy on 2006-01-01
Please describe in more detail the troubles you are having. Details on the errors you see or the configuration you're trying to complete will help us diagnose your situation better. :)

---

### Post by chocolatetoothpaste on 2006-01-02
Okay, I will tell you everything I can.  I have tried for 2 weeks to get this setup to work, but alas to no avail.  I curse myself for doing this, but I am downloading fedora4 and I am going to try that if I can't get it to work in ubuntu, but I don't want to do it becaus I LOVE ubuntu.  Okay, here is the scoop.

I want to setup up a standalone computer to act as a router/firewall, mainly to protect 2 winxp machines form being force fed viruses (it has happened several times).  After doing a little searching I decided on using the Firestarter firewall.  After a little more research I determined I wanted also to enable DHCP to serve up any machine that would connect to my network.  I installed Firestarter and the dhcp3-server, and I ran the firewall wizard, but it would not let me enable dhcp services, it gave me some error saying I had no internet connection.  I did some searching and posting and someone sent me this link: [http://www.ubuntuforums.org/showthre...restarter+work](http://www.ubuntuforums.org/showthre...restarter+work)   This soved the problem!  Firestarter fired up with no errors, ip's were being assigned right when computers were connected to the LAN.  It was serious bliss!  I felt so accomplished!  It was so easy getting on the network and sharing internet.  It was awesome.  Well, I had a couple minor problems, mainly the server was giving a wrong DNS ip, so I opened the file /etc/resolv.conf, I added the correct information, then I did ```
sudo chattr +i /etc/resolv.conf
``` to lock the file. Again, bliss. I was so happy.  Well, I decided the network needed a little kick, make it a little more powerful, you know?  So I starter toying with samba.  I had 2xp machines, 1 ubuntu workstation, and obviously the firewall.  I had the 2 xp's and the ubuntu workstation sharing files like the cold.  It was very convenient.  I kept  making changes to the server.  I wanted it to be a file server, and act as like a domain login(like they have in schools) so all my other machines would authenticate through the server.  Well, I soon realized that the firewall was blocking all of these incoming connections, and there was really no way to add all of them the the "white list" without feeling I had compromised security.  Well, in the midst of trying to get things to work properly, I somehow toasted the os.  I set the computer to a static ip and then turned off dhcp on the DSL modem.  Then, without paying too much attention, I switched eth0 (the internet connection card) back to dhcp, but without the modem serving it up, the computer freaked.  Anyway, I couldn't get it to work again, so I started doing a fresh os install.  It all went fine.  It booted up first time perfect. So I started installing firestarter and dhcp again, getting ready to set up again.  Well, when I went through that article again to set it up, it didn't work quite right.  DHCP didn't start like it was supposed to, and i got the error again.  So, I restarted the computer, thinking this may help, but on boot up, up it says "configuring network interfaces" it freezes.  It won't even say fail, it just feezes.  Well, after a little trial and error, I determined that I think the DSL modem was freezing it up.  So when I booted again, after disconnecting the modem, I went in and gave the computer a static IP address, and turned off dhcp on the moded.  I now have internet shared between the xp machines.  However dhcp still is not working, and I am not satisfied with static ips, because tomorrow, I become the sys admin for a real estate company, with several computers, and more being added.  YOu can imagine my frustration.
  So, I just have no logical explanation for why things just won't work.  I have duplicated 100%, as far as I can tell, the steps I took before to make firestarter work perfectly, and dhcp also.  Please, anyone, anything, HELP.

PS- I have tried the other version of dhcp, and it does not work either.  Thanks.

---

### Post by ardchoille on 2006-01-02
When you "sudo chattr +i /etc/resolv.conf", the system will create a new file "resolv.conf.dhclient-new" because it can't write to /etc/resolv.conf anymore - at least that is what happened to me. So, I did "sudo chattr +i /etc/resolv.conf.dhclient-new" and all is well. It's possible that your system created this new file. Do you have a /etc/resolv.conf.dhclient-new file? If so, view its contents and see what's there.

---

### Post by chocolatetoothpaste on 2006-01-02
In the /etc/resolv.conf.dhclient-new it had the old, incorrect information.  So I changed it and locked it too.  But, not to sound ingorant, what exactly will this fix?  As I said above, me real problem I think is my network interfaces freezing on me.  And I need to get dhcp3-server working.  Thanks, for your input.

---

### Post by chocolatetoothpaste on 2006-01-02
My other ubuntu workstation used to get an ip via dhcp, and when I started it up this morning, it froze for a second, but then continued to boot.  Could it have been my DSL modem freezing the system when trying to use dhcp?  But I don't think that explains why I can't run dhcp3-server on my other ethernet interface.  And why would the one computer freeze and not the other?

---

### Post by socrazy143 on 2006-01-02
It seems to me that you would be better off using either a firewall router or a distro more suited for firewalls (I highly recommend m0n0wall [http://www.m0n0.ch](http://www.m0n0.ch) those are zeroes in the address).  I understand that you want the Ubuntu box to work as file server and that is a good job for it especially if you are new to Linux.  However running the firewall on the file server is a bit risky and lends to its own problems.  Back in the day (HA!  Like two years ago) I ran Red Hat 9 as a File Server/DHCP/DNS and that thing go hacked regularly.

I would seriously set up a m0n0wall between your file server and the Internet and put your XP machines on the same subnet.  Then feel free to give the File Server a static IP and issue DHCP to the XP boxes.

Internet -> m0n0wall -> Switch -> File Server, XP1, XP2

The switch is needed if your m0n0wall box only has 2 NIC ports.

I run m0n0wall now on an old Pentium box (note that is Pentium I) with 64 MB of RAM and a 2 GB hard drive.  You could put it on a flash drive if you wanted.

You could of course go buy a Firewall/Router on the cheap (Linksys, D-Link) and save a couple of bucks but you know the Geek in you wants to play with m0n0wall.  Come on, admit it!  :razz:

---

### Post by chocolatetoothpaste on 2006-01-02
I definitely realize now that I need to seperate the two boxes and their funcitons, but I want to stick with ubuntu for both servers.  I can't be assured that a box with m0n0wall won't freeze on boot up either.  That has been one of my main problems.  The other seems to be that, if I have a file server serving up IP's does that machine need 2 net cards.  Right now the way it works is, the firewall connects to the net, but it uses dhcp to assing all the other machines on the LAN, because their default gateway is the firewall box.  Well, if I moved dhcp to the file server, will the other machines still be able to get ip's?  How?  Would the file server just broadcast throughout the network?  If so, how does that keep the firewall from getting a little messed up with those broadcasts?

---

