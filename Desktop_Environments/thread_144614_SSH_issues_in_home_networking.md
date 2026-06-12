---
title: "SSH issues in home networking"
date: 2006-03-14
forum: Desktop Environments
---

### Post by omarian on 2006-03-14
Hi. 
I was wondering if someone could help me figure out this issue I am having with SSH. When i installed Ubuntu 5.10 the first time, both ssh and ssh server were not installed so I apt-get installed them. I am on DSL and behind a Westell modem and Linksys BEFSR41 router. Have two machines: one running windows xp, one running Ubuntu 5.10. I made sure that SSH service is forwarded from the DSL modem to the router and from the router to the Ubuntu box.

I couldn't connect to Ubuntu at first so uninstalled both ssh and the server and then reinstalled them. It seemed like everything started working all of a sudden and I could access my Ubuntu from my windows and from outside provided I know the changing IP of my provider.

Then all of a sudden it stopped working. I removed the known_hosts file under /home/(username)/.ssh and then reinstalled the two components. Nothing. I cannot connect from with ubuntu or windows or outside. I get the “connection refused on port 22” message.
   
  I don’t have a firewall running yet on ubuntu and I made sure that the /etc/hosts.allow included the static IP I was going to access ubuntu from. I also included the line ALL:ALL in it. “Connection refused” again.
   
  I am wondering what is wrong. Should I manually remove every trace of ssh and then reinstall it again? I didn’t have any luck removing the .ssh folder with rm –r. It’s still there.
   
  Any suggestions again would be greatly appreciated. I am pretty psyched about Ubuntu and really want to learn it. I will post the contents of files if any of you guys needs more info.

---

### Post by munga_bill on 2006-03-14
Hey wow! That's interesting! I didn't think of connecting between Windows and Ubuntu with SSH, but I guess there's no reason why not. 
Was it easy to install install SSH in WIndows first? I read they make SSH for Windows, but I haven't tried it yet.
I only know about using SSH between Ubuntu boxes. I didn't have to do anything to /etc/hosts allow for that or do any port forwarding or know the outside IP address. I don't know how to do those things yet.
My home network only goes from one computer to another via my router, the ADSL modem is there but only for connecting to the internet in my set-up, and has nothing to do with my LAN. I only needed the internal IP addresses. As long as I set 'static' IP addresses for my inside my LAN, SSH works fine. 
 Regarding deleting your .ssh directory, when I do that it is usually sufficient for me to just delete it to the .trash the regular way (with my mouse), and then empty the trash. You aren't supposed to have to re-start your computer in Linux for anything, but I do anyway just to make sure.
That seems to get SSH working again if I had changed anything on my other computers on my LAN. There will be no .ssh folder, then after you make a new connection it will automatically make one.
Well that's how it works for me anyway, I don't know if that will help you, it sounds like you are way more advanced than me, but there's my two cents. Regards, munga_bill

---

### Post by markymarknz on 2006-03-14
Just a thought, what is the setup of your SSH? Have you set it up for using password only or a public key. I know for me I have disabled the password option and just use a public key (safer). If you are using a public key you need to put the info into the authorized_key file.

---

### Post by omarian on 2006-03-14
munga_bill: installing ssh in windows is pretty easy. All you have to do is find a client like Copssh, puTTy etc. Just do a google for "ssh client". There is tons of them. With puTTy you don't have to install it at all actually. It's only an executable file. It's pretty self-explanatory. I haven't tried really deleting the .ssh folder through Nautilus (mouse based, explorer like style). Perhaps I got ahead of myself and was looking for a more complicated cause for these issues. I will give that a try though. Sounds like a good suggestion.

markymarknz: Are you asking for the setup of the ssh client on the remote side or the ssh server on the ubuntu side. As far as the remote one, I am using a password based connection. I don't know how to disable public key authentication for Ubuntu. For now I think I am just going to remove all the references to SSH and then reinstall it. Perhaps I missed some config file somewhere.

Thanks for your reply guys.

---

### Post by omarian on 2006-03-15
Hello.

Still no luck connecting remotely to Ubuntu. I reinstalled ssh and the server this time through Ubuntu's synaptic package manager. The uninstallation of the server failed through synaptic though. Reason: "No file found"

It reinstalled without prompting any errors though. A lot of installations seems to go like that with Ubuntu which is great. After reinstalling, I could successfully perform from the terminal:

ssh username@127.0.0.1   
ssh username@192.168.x.x

I switched over to my XP machine and tried connecting to Ubuntu locally through Copssh but the terminal prompts for username and password and then hangs. This remains to be solved.

Turned just Ubuntu on this morning and wondered if I could connect to it remotely. No luck. Then I did some more searching on google and the forums and found [this]("http://www.users.bigpond.net.au/hermanzone/p11.htm") which gave me an idea:

**Possible problem:** 
The router is assigning IPs to my two machines through DHCP. The router rule that forwards ssh requests only sends them to the one specified IP that Ubuntu seems to have most of the time. Now booting sequence is important here because it means that if Ubuntu starts before XP (not the norm), then it will take the XP's IP and the router will not forward the traffic to Ubuntu. This is precisely what happened this morning.

**Possible solution: **
Assign a local static IP to Ubuntu and make sure that that is the destination IP for the SSH requests in the forwarding rule of your router. This way the booting sequence won't interfere with SSH forwarding.

I will post any updates and appreciate any comments.

Thank you.

---

### Post by munga_bill on 2006-03-15
That's a good link, setting a static IP for the Ubuntu computer should help some. I was just wondering if you have a Windows Network set up in your WIndows box, and can the Ubuntu computer connect to it easily? (Places, Network Servers). (Just as a test for trouble-shooting purposes). Ubuntu can easliy access shared files on any Windows Network without any configuring at all if the IP address is permitted in whatever firewall you have running in Windows. Another test maybe to help pin-point where any problems might be would be to use the 'Breezy' Live CD, or Knoppix, in either computer and try to make the SSH connection with the Live CD as the client and whether or not both hosts are able to accept the connections. (Try in one computer first, then in the other one). Both of those Live CDs come with SSH client capabilities, as long as you have a host to connect to you should easily be able to make a connection. I am able to connect with SSH in my LAN without using port forwarding at all, ( I don't even know how to set that up). I think that's only needed if you are away travelling and want to connect to your home network from your motel room somewhere with a laptop for example. Or if you want friends, family or work collegues to be able to access directories you make for them. They can access their shares from wherever they are (from their home or office). I haven't tried that yet, I've only read about it, but port forwarding shouldn't be part of your problem, that's the main thing I'm trying to say. (Well at least for my hardware and in my experience it doesn't seem like it would be needed anyway, not just for a LAN). 
I hope I'm being helpful, Regards, munga_bill.

---

### Post by omarian on 2006-03-16
Hi munga_bill.

I confirmed my suspicion in the previous posting that DHCP and the boot sequence would be the cause for the swapping of IP addresses. The XP had obtained Ubuntus IP and Ubuntu had grabbed that of XP. I didn't have time yesterday so I quickly changed (in the router forwarding table that is) the former IP of Ubuntu to match the former IP of XP and everything worked fine. As soon as I get a chance, I will give Ubuntu the static up and the confusion shouldn't happen again.

Thank you for all your efforts!

---

