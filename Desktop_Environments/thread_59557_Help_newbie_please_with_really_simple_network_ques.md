---
title: "Help newbie please with really simple network questions"
date: 2005-08-24
forum: Desktop Environments
---

### Post by stig on 2005-08-24
Hi, please can someone help a newbie by answering some really simple, basic questions on networking in Linux (simple to Linux people but not to me and probably some other newbies)? I have done a lot of searching but I can&#8217;t find the answers to these basic things. :|  Sorry to put them in one post but, as they are related,  I think it&#8217;s better than scattering them among several posts. Perhaps it would help other people if these points were clarified in one place.

1. I know how to set the hostname on 2 networked computers, but what does domain name mean? Is it a name chosen by me or is it restricted to certain names? Does it mean the same as Windows NT domain in Win98? If I network a Linux box to a Win box do I use the same domain name?

2. I see there are two main ways of networking - NFS and Samba. I thought NFS was for linking Linux to Linux, and Samba for linking Linux to Win. But now I&#8217;m confused - can Samba do the lot?

3. In the Unofficial Ubuntu Guide, Samba section, under &#8220; How to add/edit/delete network users?&#8221; it says to insert

system_username = "network username"

I assume that I actually do insert the words system_username but that "network username" is to be replaced by something else. But what? Is this the same as user login name? If I have two computers with users &#8220;laurel&#8221; and &#8220;hardy&#8221; respectively, do I add them both to each computer, or only laurel to hardy&#8217;s PC and vice versa.

4. What is a samba password? Is it my Ubuntu login password? If not, do I simply make one up?

5. In many of the guides to networking there are instructions to use the IP address of the computer. But my router uses DHCP and, as I understand it, this allocates different IP numbers to the boxes at each boot-up. So what do I enter instead of the IP address?

I would be really pleased to find out the answers to these questions! :razz:

---

### Post by nad on 2005-08-24
The domain name is the name of the network a particular computer is connected to. The computer [www.example.com](www.example.com) is named 'www' and is part of the 'example' domain. Yes, it means the same as an NT domain name. but, in the instance of a Windows NT network the domain has a primary domain controller, the NT machine. In a peer-to-peer network (a network without a domain controller) the domain name is known as the workgroup name. Use the same workgroup name for all computers on your subnet.

Yes, samba can do the lot.

The system_username = "network username" is an alias configuration feature to associate you with a network account named you, the second name being required to be in quotes (only if it has a space? use the quotes to be certain). All computers on your network should have an identical field in the config file.

A samba password is the network password to be used by that user for the samba implementation. Samba users must be explicity added to the samba password file in order to be able to use the network. The command: smbpasswd -a  will prompt you for a new samba user and password. Once again, this must be done on each computer you wish to connect to.

As your network has no domain controller, the easist way to resolve hostnames to dotted quad addresses is to set up your /etc/hosts file. Give each computer on your network its own static address and add a line to the file in the form dotted_quad_address hostname .

Please see:

man smb.conf
man smbpasswd
man hosts
man interfaces

And the samba docs (to really make your head spin) at /usr/share/doc/samba and /usr/share/doc/samba-doc . You will need to gunzip the gz docs in order to be able to read them, or, just doubleclick them from nautilus. The archive manager should start up and allow to read them from there. The html docs you may of course open in your browser of choice. Just start with index.html .

---

### Post by KeplerNiko on 2005-08-24
[QUOTE=stig]Hi, please can someone help a newbie by answering some really simple, basic questions on networking in Linux (simple to Linux people but not to me and probably some other newbies)? I have done a lot of searching but I can&#8217;t find the answers to these basic things. :|  Sorry to put them in one post but, as they are related,  I think it&#8217;s better than scattering them among several posts. Perhaps it would help other people if these points were clarified in one place.

1. I know how to set the hostname on 2 networked computers, but what does domain name mean? Is it a name chosen by me or is it restricted to certain names? Does it mean the same as Windows NT domain in Win98? If I network a Linux box to a Win box do I use the same domain name?

2. I see there are two main ways of networking - NFS and Samba. I thought NFS was for linking Linux to Linux, and Samba for linking Linux to Win. But now I&#8217;m confused - can Samba do the lot?

3. In the Unofficial Ubuntu Guide, Samba section, under &#8220; How to add/edit/delete network users?&#8221; it says to insert

system_username = "network username"

I assume that I actually do insert the words system_username but that "network username" is to be replaced by something else. But what? Is this the same as user login name? If I have two computers with users &#8220;laurel&#8221; and &#8220;hardy&#8221; respectively, do I add them both to each computer, or only laurel to hardy&#8217;s PC and vice versa.

4. What is a samba password? Is it my Ubuntu login password? If not, do I simply make one up?

5. In many of the guides to networking there are instructions to use the IP address of the computer. But my router uses DHCP and, as I understand it, this allocates different IP numbers to the boxes at each boot-up. So what do I enter instead of the IP address?

I would be really pleased to find out the answers to these questions! :razz:[/QUOTE]
 Keeping reading online--I've found that man pages aren't that friendly to read in order to understand what something is doing.  Rather, the things that are posted online are generally pretty easy to understand (and they're presented in an easier-to-read format).

My advice for setting up a network that will include Windows computers is to start with the Windows computers first.  They tend to take over and change arbitrary settings without warning--Ubuntu, for me, has done a really good job of just adapting when connecting to the network.

Also, I think the Windows computers will utilize Samba or a Samba-compatible protocol automatically-- that's what you want to use.

I initially set up my home network just between Windows computers.  Then, when it came time to get my Linux computers online, they detected pretty much all of the settings to connect.  I installed linneighborhood, and after entering a few passwords and domain names, my laptop was online wireleslly, sharing files without problems.  The latest release of Ubuntu does a really good job of configuring things automatically.

---

### Post by stig on 2005-08-25
Thanks nad. Thanks KeplerNiko!

I guess I'm still being a bit stupid on this but perhaps nad could further clarify a couple of points below?

[QUOTE=nad]The domain name is the name of the network a particular computer is connected to. The computer [www.example.com](www.example.com) is named 'www' and is part of the 'example' domain....[/QUOTE]
In the tldp NFS HowTo on " Getting NFS File Systems to Be Mounted at Boot Time" it uses the example of server master.foo.com and says to add to /etc/fstab
master.foo.com:/home  /mnt    nfs          rw            0    0

If I have given my computer the host name "ubuntu", and say I used the Windows default domain MSHOME, then I guess I would use ubuntu.MSHOME in this line instead of master.foo.com - but what about the extension? Do I have to use .com? Or can it be anything I like as long as my other PCs use the same extension?

[QUOTE=nad]The system_username = "network username" is an alias configuration feature to associate you with a network account named you, the second name being required to be in quotes (only if it has a space? use the quotes to be certain). All computers on your network should have an identical field in the config file.[/QUOTE]
Dumb question time again - if I am user stig, then does this mean I put
system_username = "stig"
or 
stig = "network username"

[QUOTE=nad]As your network has no domain controller, the easiest way to resolve hostnames to dotted quad addresses is to set up your /etc/hosts file. Give each computer on your network its own static address and add a line to the file in the form dotted_quad_address hostname .[/QUOTE]
Does this not contradict the use of DHCP? Can the router allocate one IP address to the computer while I allocate a different one?

Thanks for all your patience - at least I am learning more about Linux even if it is only slowly! :smile:

---

### Post by nad on 2005-08-25
In your instance, you do not need to use a top level domain designation. ubuntu.MSHOME  is correct.

I have never found it necessary to hand edit the /etc/samba/smbusers file. I would ignore the suggestion to add the line: system_username = "network username"  and just use the smbpasswd utility to manage samba users.

If you implement my advice to set up static IP addresses and your /etc/hosts file, you will not be using the DHCP service on this computer (dhclient). Your DHCP server (your router) will not get a request for address or routing information.

---

### Post by stig on 2005-08-25
Thanks nad for all the clarification. The domain and  the system_username = "network username" seem cleared up now.

I'm a bit cautious about the DHCP though. It is used because when I went onto broadband my ISP's (NAT) package included a router and all the instructions from the ISP were about using DHCP. That was when I had only two Windows PCs linked.

Now I have three PCs - a Linux-only, a Windows-only and one with two hard disks (a Linux and a Windows) (yes, it does sound masochistic!). Would I now need to set up static IP addresses on all three PCs and give up DHCP altogether?
(Then I wonder, why am I using DHCP now? Is it just because the ISP told me to do so or is there an advantage to DHCP?)

---

### Post by nad on 2005-08-25
You can usually throw away any software that comes from your ISP. It is not necessary to set up most broadband connections.

The advantage of using DHCP and your ISP's software is ease of setup and a more unified client environment for their support department.

Setting up static addresses and your hosts file will result in a more stable and easily addressable network. You will be able to use the hostname of the computer you wish to connect to rather than have to find its' dotted quad address to use.

---

### Post by prawn on 2005-09-28
I have a similar problem and would *really* like to get around it without using static IP addresses. I find using the router DHCP handy and would like to stick with it. I have an Ubuntu linux box (hostname foo) a couple of WinXP boxes (one with hostname bar) and an OSX. What I have found is I can 'ping foo' from the Windows box but I cannot 'ping bar' from the Ubuntu box. If the Windows box can do it, surely there must be a way for the Ubuntu box to do it without having to revert to static IPs.

---

### Post by EACeaser on 2005-09-28
[QUOTE=prawn]I have a similar problem and would *really* like to get around it without using static IP addresses. I find using the router DHCP handy and would like to stick with it. I have an Ubuntu linux box (hostname foo) a couple of WinXP boxes (one with hostname bar) and an OSX. What I have found is I can 'ping foo' from the Windows box but I cannot 'ping bar' from the Ubuntu box. If the Windows box can do it, surely there must be a way for the Ubuntu box to do it without having to revert to static IPs.[/QUOTE]

What your windows machines are doing is resolving IP addresses through WINS / NetBIOS broadcast discovery. To do that in linux, you need the libnss_wins.so.2 library (which is part of the winbind package), and then you need to add 'wins' to your /etc/nsswitch.conf under the "hosts:" section.

---

### Post by prawn on 2005-09-29
[QUOTE=EACeaser]What your windows machines are doing is resolving IP addresses through WINS / NetBIOS broadcast discovery. To do that in linux, you need the libnss_wins.so.2 library (which is part of the winbind package), and then you need to add 'wins' to your /etc/nsswitch.conf under the "hosts:" section.[/QUOTE]
Great feedback, thanks! I installed winbind, added wins and everything works like a charm. It was particularly helpful in allowing me to remotely administer a mysql server running on the ubuntu box using a windows machine. I was having to grant access to 192.168.1.% and now I can specify the host name. Thanks again. :p

---

