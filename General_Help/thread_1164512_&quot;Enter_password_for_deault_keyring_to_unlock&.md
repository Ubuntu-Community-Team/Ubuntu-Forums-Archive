---
title: "&quot;Enter password for deault keyring to unlock&quot;"
date: 2009-05-19
forum: General Help
---

### Post by cody7002002 on 2009-05-19
I just installed ubuntu netbook remix on my asus eee pc and everytime I start up I get this prompt

Enter password for default keyring to unlock:
The application "NetworkManager Applet" (/usr/bin/nm-applet)wants access to the default keyring, but it is locked

Then I put in my password and I continue to the desktop.

I'm wondering what this prompt means and how can I get it to stop popping up everytime I start my computer.

---

### Post by Benboom on 2009-05-19
Does this have to do with your wireless connection? I just went throught this, too. I saved the solution in my scrapbook, but alas, I don't have the author's name. Anyway, this worked for me, although perhaps your problem is something entirely different:

"Re: Howto: Get Network Manager to stop asking you for your keyring password 

I might have had another problem as the rest of you, but all i had to do is check one box to fix this problem. This is what i did. Also, i have 9.04. 

Menu > Preferences> Network Connections.

Then i clicked on my Wireless that i have connect automatically when i boot up. Clicked on Edit. And at the very bottom it has a box to make the connection available to all users. Check that box. 

That fixed it for me. No codes or terminal or anything."

---

### Post by cody7002002 on 2009-05-19
Thank you!!! That fixed the problem perfectly! =)

---

### Post by cody7002002 on 2009-05-19
hmmm the problem came up again. When I installed the program twhirl which requires access to the internet and everytime I run it I get the same "enter password..." prompt. X(

---

### Post by kazohnine on 2009-07-28
Hey!
This happened to me too, and it's strange because it happened just after when i got rid of the network manager keyring. 
Did you find the answer to solve this?
That would be great if you could give me a hand with this cause is getting rather annoying!

Thanks.

---

### Post by doas777 on 2009-07-28
I just stopped using network-manager for configing my nics, and havn't had the problem in some time.

---

### Post by kazohnine on 2009-07-28
And how do you stop network manager working? I'm quite new at Linux. And by the way, if I stop it, will it interfere in my wifi connection ?
Thank you.

---

### Post by sandydoull on 2009-07-28
One alternative workaround is to leave the password blank when the prompt comes up the first time, then it will not ask for a password in the future. You will get a warning that this is unsafe, but it depends on who has access to your computer! If you use the computer in a home setting then you probably don't need to password protect your internet connection or everything else that uses keyring.

If you want to reset previously entered passwords you can delete all entires by going to system>>accessories>>passwords and keyrings

---

### Post by speedwell68 on 2009-07-28
> **kazohnine said:**
> And how do you stop network manager working? I'm quite new at Linux. And by the way, if I stop it, will it interfere in my wifi connection ?
Thank you.

Yes it will effect your Wifi.  If you don't like it you change it to WiCD.  It is in the standard Jaunty repositories.

```
sudo apt-get install wicd
```

It'll uninstall the standard network manager and replace it with WiCD.  It will mean you'll have to enter you WEP/WPA key again.  It doesn't prompt you for the keyring at startup like the other one.

---

### Post by doas777 on 2009-07-28
well, network-manager is primarily there for wifi connectivity, so if you use wifi, then you will want it, or something like wicd or whatever. traditionally, the network is a fundemental part of a Unix style OS, so the network starts as root, and does so long before the user has a desktop. With mobile computing, the user needs the ability to connect to the network (or not) of his/her choosing, so the OS can;t start the network at boot like it used to. so, network manager is there to allow the configuration of the network to happen in the users space, not the systems. 

since you are using a netbook (somthing i should have noticed before now), disabling the network manager is not the right plan for you, unless you plan to replace it with another wifi connection manager. sorry.

anyway, from an academic standpoint, to disable the network-manager and manually configure your IP settings, just follow the instructions here:
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)
and then uncheck "Network Manager" in System -> Startup applications.

---

