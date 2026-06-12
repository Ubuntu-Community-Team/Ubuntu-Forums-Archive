---
title: "A question about Dapper vs. Breezy"
date: 2006-03-14
forum: Desktop Environments
---

### Post by ardchoille on 2006-03-14
When Dapper is released as stable, will the repos for Dapper be as full as the repos for Breezy are now? What I mean is, I have a lot of favourite apps that are in the Breezy repos and I install those apps on all the machines on which I install Breezy. Will I be able to use those Breezy apps on Dapper when Dapper released as stable? Or will Breezy and Dapper be using the exact same repos? The thing is, I am wondering if I should wait to install Dapper until its repos have the same apps as Breezy repos do now.

---

### Post by matthew on 2006-03-14
It probably already has all the apps you are using now, just newer versions of them (if they were available) and they may not yet be completely stable. Once the upgrade is made you will be using different repos that are the same in idea, but with different names (ie you change "Breezy" to "Dapper" in every place it occurs in your /etc/apt/sources.list file).

For further research on specific programs, whether they are present in Dapper and version numbers you take a look here
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

---

### Post by ardchoille on 2006-03-14
[QUOTE=matthew]It probably already has all the apps you are using now, just newer versions of them (if they were available) and they may not yet be completely stable. Once the upgrade is made you will be using different repos that are the same in idea, but with different names (ie you change "Breezy" to "Dapper" in every place it occurs in your /etc/apt/sources.list file).

For further research on specific programs, whether they are present in Dapper and version numbers you take a look here
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")[/QUOTE]
Thank you for the info and for the link. Seems I won't have to worry :)

---

### Post by az on 2006-03-14
[QUOTE=ardchoille]Seems I won't have to worry :)[/QUOTE]

That's the point.  That's why it is so difficult for a developer to make a proper debian package.  It's so that apt does the work for you (synaptic, adept, add/remove packages all use apt - Advanced Package Tool)

---

### Post by dpaint4 on 2006-03-14
I'm looking forward to the upgrade, but worry about the process. Will it be something that they system handles through the standard update system, or will we need to download and burn a new ISO and install from scratch? Surely not, but I'd love a definite answer about it, since this is my first Ubuntu (and my first time to use Linux exclusively and not just as a toy or rescue tool).

---

### Post by az on 2006-03-14
[QUOTE=dpaint4]I'm looking forward to the upgrade, but worry about the process. Will it be something that they system handles through the standard update system, or will we need to download and burn a new ISO and install from scratch? Surely not, but I'd love a definite answer about it, since this is my first Ubuntu (and my first time to use Linux exclusively and not just as a toy or rescue tool).[/QUOTE]
You can do either.  There may be a popup that says you have updates and there is a new version of Ubuntu, do you want to stick with breezy or upgrade to Dapper, instead of you haveing to change your sources.list by hand (or through synaptic)

You can also download the iso and make it into a disk and insert that into your breezy system.  It will say "hey, do you wanna install these packages?)

---

### Post by Zotova on 2006-03-14
I would have to warn about dist-upgrading as when I tried from Hoary > Breezy it did not work. I was unable to boot into Ubuntu and basically had to do a clean install of Breezy. So I'd warn anyone thinking of trusting Ubuntu to update everything to make a backup of any of there important files first.

---

### Post by justaguynpc on 2006-03-14
On the contrary, I, as well as alot of others, successfully upgraded our Hoary ---> Breezy without a hitch.

I have always ensured my system was up to date as possible before a dist upgrade. That in itself may reduce the potential of mishap.  

justaguy

---

### Post by ardchoille on 2006-03-14
Whenever a new release of my distro comes out, I always burn it to CD and then install from scratch, but that's just me :)

---

