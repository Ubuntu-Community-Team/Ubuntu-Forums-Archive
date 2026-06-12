---
title: "Firestarter need some matches?"
date: 2006-04-22
forum: Desktop Environments
---

### Post by linuxa on 2006-04-22
Hi there

I recently installed Firestarter (firewall) from apt-get. And was surprised to find that I was unable to add or delete any policies in the program (see screenshot).

I start it by running a shortcut to "kdesu firestarter".

Does anyone what I'm doing wrong?

Or maybe it just needs the help of matches? :-D 

Regards

---

### Post by louis_nichols on 2006-04-22
[QUOTE=linuxa]Hi there

I recently installed Firestarter (firewall) from apt-get. And was surprised to find that I was unable to add or delete any policies in the program (see screenshot).

I start it by running a shortcut to "kdesu firestarter".

Does anyone what I'm doing wrong?

Or maybe it just needs the help of matches? :-D 

Regards[/QUOTE]

What exactly happens? Do you add a rule and then, on next restart, it's gone?

Do you click "apply" after adding rules?

---

### Post by Q4U on 2006-04-22
Have you tried the Edit menu?

Generally, I recommend Guarddog with Kubuntu. 

Both Guarddog and Firestarter are front-ends of IPTables, so what you have under the hood is the same. However, Guarddog is built on QT, while Firestarter is GTK. This means that the former loads far less dependencies and generally plays nicer with the rest of the desktop.

---

### Post by louis_nichols on 2006-04-22
[QUOTE=Q4U]Have you tried the Edit menu?

Generally, I recommend Guarddog with Kubuntu. 

Both Guarddog and Firestarter are front-ends of IPTables, so what you have under the hood is the same. However, Guarddog is built on QT, while Firestarter is GTK. This means that the former loads far less dependencies and generally plays nicer with the rest of the desktop.[/QUOTE]

It's worth mentioning, though, that their usage is fundamentally different. Guarddog might be better suited for beginners.

---

### Post by linuxa on 2006-04-27
Thanks for the reply guys.

I did end up switching to Guarddog, only because I got too tired of trying to configure FireStarter. Guess my paranoia for not having a firewall up won after all :P

Did a bit of configuring in order to get the new "pet" up and running (pun intended!) very different indeed to all the other Windows Firewalls that I've used.

If anyone is still reading this thread. Can someone answer this question for me please:

I'm sitting behind a wireless router here. Which would make my "zoning" for the firewall

Internet --- Wireless Network (I created this) --- Local

Why then do I need to give access to HTTP from Internet to Local Zone? One would've thought that access only needs to be granted in the way that it's illustrated above. As in Internet gives access to Wireless Network, which in turn gives access to Local...

But by stiffing the HTTP access from Internet to Local I ain't got no net. 

Just to satisfy my curiosity, maybe someone with a better understanding of the Zoning model in Guarddog can offer some insights.

Thanks all.

---

### Post by eeried on 2006-04-28
[QUOTE=linuxa]

I recently installed Firestarter (firewall) from apt-get. And was surprised to find that I was unable to add or delete any policies in the program (see screenshot).
...
Or maybe it just needs the help of matches? :-D 
[/QUOTE]

My problem too: the bar below the menu bar is greyed out.:-| 

As for installing guarddog: it requires 11 packages to be installed (22MB)! Good gracious! ;-)

cheers

---

### Post by louis_nichols on 2006-04-28
[QUOTE=eeried]My problem too: the bar below the menu bar is greyed out.:-| [/QUOTE]

did you go through the first run wizard and make all the correct settings there (like choosing the right connection device etc.)?

[QUOTE=eeried]As for installing guarddog: it requires 11 packages to be installed (22MB)! Good gracious! ;-)

cheers[/QUOTE]

That's probably because you've never installed KDE apps before, so those are the needed libraries to run. No big deal. You'll probably end up installing them sooner or later, anyways.

---

### Post by eeried on 2006-04-28
> did you go through the first run wizard and make all the correct settings there (like choosing the right connection device etc.)?

I ran the wizard but I can't remember the settings, I'm afraid. I'll try reconfiguring then.

---

### Post by linuxa on 2006-04-28
I personally do recall the act of going through the setting and configuring according to my own setup here. But the program started with the toolbar grayed out.

Could it be that we are actually running multiple instances of the program which is causing the second instance to be "read-only"?

I read somewhere that the Firestarter service has already started itself by the time we got to the desktop...

Basically I assumed that inorder to view my Firestarter setting + network traffic stats, I needed to start the program up (ala "kdesu firestarter). Was this wrong?

How do you guys access firestarter once you are at the Desktop?

---

