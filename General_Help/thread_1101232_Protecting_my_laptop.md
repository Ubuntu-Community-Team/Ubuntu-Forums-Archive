---
title: "Protecting my laptop"
date: 2009-03-20
forum: General Help
---

### Post by bapy on 2009-03-20
Hi pretty new to ubuntu and i was wondering what type of protection could i add to it to make it more secure. On windows i know that you can use things such as ad-aware. i was wondering are there any types of programs like that, that i could put on my ubuntu to make it safer. also is there anything i could add such as firewalls that could help keep unfriendly things out. and i'm looking for something free if possible. thank you. also i know updating might be a good option but last time i updated my wireless didnt work afterward, so if possible something that wouldnt interfere with my wireless. so if anyone could help me that would be great ill post where i got my wireless solution so you folks can see what method i used and if your advice for my problem would conflict with the wireless or not [http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_25.html]("http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_25.html")

lastly i would like something similar to ad adware, so i could sweep my laptop every so often if possible, or if ad adware works with ubuntu that would be great. thank you.

---

### Post by Kevbert on 2009-03-20
You are obviously thinking with Windows in mind and haven't got rid of that mindset. Don't worry, a lot of us, including me couldn't understand why the need for antispam, antivirus, malware and firewalls aren't all that of a problem in Ubuntu. This is due to the built in and proactive (unlike Windows which is reactive) security features. I'm using [COLOR="Red"][UFW]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw")[/COLOR] firewall, along with Spam Avert, NoScript and Adblock Plus for Firefox (which you can get via Tools-Add-ons in Firefox). If you are emulating or sharing files with Windows/DOS it is worth having some antivirus software such as [[COLOR="Red"]ClamAV[/COLOR]]("http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html"), but this will only look for Windows viruses. Nearly all viruses for Linux/Ubuntu are theoretical.
Please also take a look at [[COLOR="Red"]this[/COLOR].]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by mb_webguy on 2009-03-20
Well, your first step is to... um... keep running Ubuntu.  Read the link about security in my signature for a more in-depth answer, but in short:

No Linux viruses are known to exist in the wild.  Only a few dozen have ever been known to exist, most of those were proofs of concept developed in a computer lab, and none affect the current version of the Linux kernel.  So you don't need antivirus software unless you're dual-booting with Windows and want to avoid infecting your Windows installation.

Because of the system Linux uses for file ownership and permissions, any malicious software you install (which you have do knowingly) and run (which you have to do knowingly) is limited in scope.  As long as you don't run untrusted programs using sudo, any potential damage is limited to your user's home directory.  And as long as you don't run untrusted programs, you don't even have to worry about that.  Most applications you'd ever want to run can be found in the official repositories and available through Add/Remove Applications and Synaptic Package Manager, anyway.  So you don't need anti-spyware software, either.

All ports are closed in Ubuntu by default.  Unless you install a server application to listen at a port, nothing can get into your system.  And if you *do* install such an application, you generally *want* the port for that application open.  So you don't need a firewall application.  (Technically there's more to it than this, but that's all you need to know at this point.  Read the link for more.)

So all that's basically left is your web browser.  While you can't get infected by viruses or spyware, you're still susceptible to malicious scripts in your web browser.  The best way to avoid this (and a lot of annoying ads and flash animations) is to install the Adblock Plus extension in Firefox.  You could also install the NoScript extension, but it's not absolutely necessary.

If you're worried about privacy, you could install a program called IPBlock, which blocks your computer from connecting to IP addresses that could be monitoring your internet activity or otherwise have less that good intentions for you.

But otherwise, you're safer than you've ever been, just because of your choice of operating systems.  Sit back and relax.

EDIT:  Kevbert's link is quite a bit more thorough (and thus longer) than the one I posted, but they both tell you the same things.  You might want to try mine first, and if you're still not quite convinced move on to his.

---

