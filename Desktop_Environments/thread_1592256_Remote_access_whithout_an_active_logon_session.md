---
title: "Remote access whithout an active logon session"
date: 2010-10-10
forum: Desktop Environments
---

### Post by vbSteve on 2010-10-10
Hi,

I'm in the process of converting my Windows NT server to an ubuntu server box. I've been testing the server edition in a virtual machine and I only have one problem.

My server computer doesn't have a screen and i was wondering if i can logon to the computer using remote desktop without an active logon session already in progress.

At the moment, I need to be logged on in the desktop environment before i can connect to the remote desktop service in Ubuntu.  In Windows, you don't need to have an active logon session to connect remotely (so you can startup a session without needing a screen). I would like to have the same, so i don't need to run to server just to logon after restarting it.

It is probably some service i need to start on system boot, but well, i'm not that familiar yet with linux servers, at least not to do that kind of stuff.

My users would also like to have a visual interface (which is why i installed the ubuntu-desktop from the repository).


Anyone here has a solution for this?

---

### Post by cinohpa on 2010-10-10
You need to be more specific about your use case. 

First, you say that you have to log in to be able to remote into your ubuntu server. Is there ANYTHING you are doing after logging in before it works? 

Are you logging directly into the ubuntu server? What protocol are you using? If you are just using ssh then it already starts up at boot. 

If you are using something that relies on ssh it probably doesn't start up at boot. 

If you are using something else you need to look around in /etc/init.d to see if there is a script pertaining to what ever service you are using to remote into your server and read your documentation about how to start it properly. 

Also what sort of internet connection is your server connecting over? If it is wireless you need to initialize your wireless connection at boot. Which means uninstalling the network-manager package and configuring your wireless in something like wicd (and make sure that the server will connect automatically to the wireless network!).

---

### Post by vbSteve on 2010-10-12
I think i was pretty clear about my case, was I not?

What I meant was the desktop login, using vnc or whatever. Not via the ssh. I would like to have my clients to logon to their desktop, in a visual environment (not in a terminal environment), somewhat the same result like i would've connected to a windows server using the the remote desktop tool in windows. 
And at the moment it's a virtual machine, on my developer pc (Windows 7 Ult); so no wifi or whatever.

But I think I managed it. I abandoned that fancy desktop because of the added server load.
Thanks anyway :)

---

