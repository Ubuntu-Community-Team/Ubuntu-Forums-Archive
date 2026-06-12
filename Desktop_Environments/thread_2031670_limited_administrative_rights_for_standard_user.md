---
title: "limited administrative rights for standard user?"
date: 2012-07-22
forum: Desktop Environments
---

### Post by goodbye-windows(tm) on 2012-07-22
Hi All,

My daughter isn't quite old enough to have administrative rights on her laptop (Dell 15R running 11.10 Unity). 

So, when she goes to a friends house, she can't connect to their wireless with her punchbox.

Is there anyway I can allow her to do specific tasks (such as add a wireless connection) without having to use the administrative password??

TY.

Art

---

### Post by Lars Noodén on 2012-07-22
That's what [sudo](https://help.ubuntu.com/community/Sudoers) would be for.  It's often misused as an all-or-nothing proposition for doling out admin privileges, but if you know the names of the programs you wish to run then you can add just those and only those.  Can you figure out which programs are needed to set the wireless?

---

### Post by steeldriver on 2012-07-22
It *should* be possible for non-administrator users to create and use wireless connections via the nm-applet - they are referred to as 'user-connections' and are different from the 'system-connections' that are created by sudo users - however it seems to have become mired in a spaghetti of policykit

I just tried it on an Xubuntu 11.10 laptop and it *did* work however imho the process is far from obvious:

With wireless connections enabled (which standard users appear to be able to do no problem)

1. Edit Connections --> select the 'Wireless' tab --> Add 

At this point, a window will pop up for the connection information - and** it has 'Available to all users' at the bottom checked but grayed out. **This is what makes the addition fail for non-administrator users (because it tries to save to /etc/NetworkManager/system-connections/)

2. fill in the SSID - **at this point the 'Available to all users' box will become active and you can uncheck it**

3. fill in the wireless security info and (if anything other than DHCP) the IPv4 info in their respective tabs

4. save the connection

IMHO it *should* be easier than this - the whole point of N-M is supposed to be that it simplifies this type of roaming connection. See here for how confusing it all is: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=642136](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=642136)

---

### Post by goodbye-windows(tm) on 2012-07-22
> **steeldriver said:**
> It *should* be possible for non-administrator users to create and use wireless connections via the nm-applet - they are referred to as 'user-connections' and are different from the 'system-connections' that are created by sudo users - however it seems to have become mired in a spaghetti of policykit

I just tried it on an Xubuntu 11.10 laptop and it *did* work however imho the process is far from obvious:

With wireless connections enabled (which standard users appear to be able to do no problem)

1. Edit Connections --> select the 'Wireless' tab --> Add 

At this point, a window will pop up for the connection information - and** it ****has 'Available to all users' at the bottom checked but grayed out. **This is what makes the addition fail for non-administrator users (because it tries to esave to /etc/NetworkManager/system-connections/)

2. fill in the SSID - **at this point the 'Available to all users' box will become active and you can uncheck it**

3. fill in the wireless security info and (if anything other than DHCP) the IPve4 info in their respective tabs


OK, I tried...but, no matter what I did,  I was always asked for the password efor the administrator.

In my case, the 'available to all users' was NOT grayed out (in step 1). I was logged into my daughters account (with her name and password), and I deleted our own wireless network from the list of available wireless networks so that I would build a new network connection from scratch.

My daughters laptop is running Unity, 11.10.

I think I can make a video of my attempt to change the wireless setup. I'm fairly new to Unity, all my experience is using Xubuntu and I'm not even good at running Xubuntu::>

We use DHCP, and the IPVE4 info was set to DHCP on the IPVE4 tab.

Regards,

Art

---

### Post by goodbye-windows(tm) on 2012-07-23
I had another go at the problem. This time, I deleted our household  wireless from the list of available nodes. Then I restarted the  computer. I did this to simulate the conditions that would exist if my  daughter fired up her computer in a new area that had wireless service.

This time when I went to create a new wireless entry, it acted just as  you described, the 'available to all users' was grayed out. As soon as I  entered our SSID for the router in our house, the checkbox became  active and I unchecked the box and proceeded.

So, it all worked.

TY for the help. 

Art

---

### Post by steeldriver on 2012-07-23
OK glad it worked - to my mind regular users shouldn't have to jump through hoops like that, it would be better if all wireless connections were user-connections by default and any hoop jumping was reserved for setting up system-connections. However I'm sure the maintainers have thought it all through and there are good reasons why it is the way it is.

---

### Post by goodbye-windows(tm) on 2012-07-23
Hey steeldriver,

> **steeldriver said:**
> OK glad it worked - to my mind regular users  shouldn't have to jump through hoops like that...........

I couldn't agree more. But, I used to be on the other end of similar situations before I retired, and there's no way to make everyone happy. 

The developers have to consider security as a more important issue than convenience is. And, they're much more aware of the security issues than most users are (I hope). 

Anyway, last night I tested the wireless after rebooting. It seems that the wireless connection I added without sudo (from my daughters account) had another new issue. 

It seems that every time the computer boots, it needs to have the password to the new wireless connection entered manually. But, it does work otherwise.

It will get the job done, as my daughter usually does not go away for weeks at a time.  And, most public wireless nodes don't require a password anyway. If no password is required, she can log on without the need to have any sudo or administrative rights.

I'm curious though, can a wireless node be added by logging into the computer via the internet (by remote control)?

I'm going to make this as solved, even though the solution is not quite a 100 percent fix. **Many thanks for your comments and assistance**. It makes a big difference and is a major factor regarding the viability of Linux).

Go Ubuntu!!

Art

---

### Post by asmoore82 on 2012-07-23
> **goodbye-windows(tm) said:**
> My daughter isn't quite old enough to have administrative rights on her laptop

That's a tough call... you do know that she/anyone can drop to a root prompt by passing 'init=/bin/bash' as a boot parameter? The equivalent can also be done on any Apple OSX device by holding Apple+S during startup: straight to a root prompt; no password needed.

Which is not to say that you shouldn't restrict her account to prevent accidental mischief, just wanted you to be aware.

---

