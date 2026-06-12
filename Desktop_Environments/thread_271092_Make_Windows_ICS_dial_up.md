---
title: "Make Windows ICS dial up?"
date: 2006-10-04
forum: Desktop Environments
---

### Post by nekr0z on 2006-10-04
Hello to all!

At my parent's home we have 3 laptops and a desktop sharing one dialup connection (yeah, it sucks, but no choice). WinXP desktop has a dialup connection that is shared by all laptops via LAN.

On WinXP laptops one has an option to make the server (aka desktop) dial or hang up on demand, without having to go downstairs and do this from desktop itself. Is the same possible for my Ubuntu-powered laptop?

---

### Post by mozetti on 2006-10-04
It should be -- the setting that allows the desktop to dial/hang-up is a setting on the desktop itself, and not the laptops. If I remember correctly, the setting on the Desktop machine is under ICS and says, "Allow other computers to control the connection state" or something along those lines. So, if you add a Ubuntu laptop to the network and it tries to go online, it should prompt the desktop to dial out.

---

### Post by nekr0z on 2006-10-04
You've mixed two options in server's setup. One is to allow connection when it is required, this is what you describe and is totally inacceptible: nobody wants the desktop to dial up ever time Windows wants to send regards to M$.

Another option is "allow other computers to control the connection state". This adds an option in WinXP connection's right-click menu on laptops to dial or hang up — by hand, not automatically! THIS is what's required.

---

### Post by mozetti on 2006-10-04
> **nekr0z said:**
> You've mixed two options in server's setup. One is to allow connection when it is required, this is what you describe and is totally inacceptible: nobody wants the desktop to dial up ever time Windows wants to send regards to M$.

Another option is "allow other computers to control the connection state". This adds an option in WinXP connection's right-click menu on laptops to dial or hang up — by hand, not automatically! THIS is what's required.

Well, I wasn't confusing the two things, as you seem to believe. But, after some further research (you're welcome, by the way), it seems that you won't be able to enable this feature in Ubuntu after all.  According to the article I found ([http://www.practicallynetworked.com/sharing/xp_ics/internetgateway.htm)](http://www.practicallynetworked.com/sharing/xp_ics/internetgateway.htm)), the only way to have this feature is to use the Windows Networking Wizard, which obviously won't work on Linux.

---

### Post by nekr0z on 2006-10-04
Well, anyway, I'm glad we finally are talking about the same thing: I need to be able to command my server to hang up or dial, that's it.

I'm absolutely sure Windows Networking Wizard is not the only way to do the trick, as I have several times set the whole thing up without any wizards, manually. The problem is a bit deeper:

Windows somehow becomes aware that the server has a dial-out ability, and uses some interface (provided by the Internet Gateway driver) to communicate with server on that subject.

Ubuntu, on the other hand, just sends a DHCP request, gets DHCP settings from WinXP server and uses it as a primary gateway, neverminding all this dial-up thing. In other words, Ubuntu can't tell whether this server is connected to the outer world via dialup, or some wire, or satellite, or whatever.

Surely there is some Windows protocol that provides this dialup-control functionality to client machines, and Ubuntu (or any Linux flavour) only needs the corresponding software/driver/whatever to use it. I'm actually positive that there is some port listening on the server, and one could terminal it and do the trick manually — the questions are what commands to give and what port to connect to.

What I wonder is if some Linux software exists, that could do the same thing this WinXP Internet Gateway driver does. I haven't found any, so I came here to ask.

---

