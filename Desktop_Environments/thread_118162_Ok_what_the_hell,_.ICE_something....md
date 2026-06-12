---
title: "Ok what the hell, .ICE something..."
date: 2006-01-16
forum: Desktop Environments
---

### Post by curuxz on 2006-01-16
Ok so my laptop and main pc were working fine as per usal last night, main pc on gnome and lappy on xfc. So anyway I boot up this morning and neither will login! what the hell!? the error i get on both is that some .ICE file has permission errors a quick ctl+alt to a terminal and a chmod 777 command later and im back in X windows but what the hell was this file and why did it go down at the exact same time on 2 diffrent computers running diffrent window managers :S

Anyone else know whats going on please let me in on this odd error! 

Ta

---

### Post by GeneralZod on 2006-01-16
Yeah, this happens way more often than it should.  I've heard that it can be triggered by running KDE apps as root, but I've never really seen any decent explanation as to why.

---

### Post by curuxz on 2006-01-16
Odd neither system has KDE atm :S 

And they both happened at the same time, i mean that suggests something networked died on me :S

Oh the file is called .ICEauthority and its mostly giberish, with lots of refrences to MAGIC-COOKIE ok what is this stupid thing? lol

---

### Post by kassetra on 2006-01-16
.ICEauthority has issues when you run graphical applications with sudo.  Since you are technically running the application from a user account and not a root account, the .ICEauthority file is rewritten as sudo - which then locks the user out of using that file.

the .ICEauthority file stores X authorization records;  when you start an X session a new record is appended to it.

k3b is an app that commonly causes .ICEauthority lock-out issues on gnome systems.

---

### Post by kassetra on 2006-01-16
.ICEauthority has issues when you run graphical applications with sudo.  Since you are technically running the application from a user account and not a root account, the .ICEauthority file is rewritten as sudo - which then locks the user out of using that file.

the .ICEauthority file stores X authorization records;  when you start an X session a new record is appended to it.

k3b is an app that commonly causes .ICEauthority lock-out issues on gnome systems.

---

### Post by curuxz on 2006-01-16
Thanks kassetra, they do both have that application and both were used for burning disks yesterday, looks like i was the vitim of an unfortunate bug :(

Tend not to run apps as sudo so k3b must do it self :S

---

### Post by JimmyJazz on 2006-01-16
it happened to me when switch back and forth between KDE and Gnome

---

### Post by curuxz on 2006-01-16
Odd bug, anything the dap guys should know about, this could realy get in the newbies way, tho they probs already know :S

---

### Post by kassetra on 2006-01-16
[quote=curuxz]Thanks kassetra, they do both have that application and both were used for burning disks yesterday, looks like i was the vitim of an unfortunate bug :(

Tend not to run apps as sudo so k3b must do it self :S[/quote] 
I'm pretty sure this bug has been around since Warty - but I'm not certain if it's an Ubuntu bug or a Gnome bug - but here is a workaround for using k3b.

k3b requires root privileges in order to access your drives (and it is setup to use sudo) - so to stop your .ICEauthority file from being locked every time you use k3b, setup your root account and run k3b from the command line with:
```
$su
Passwd:
#k3b
```

---

### Post by kassetra on 2006-01-16
[quote=JimmyJazz]it happened to me when switch back and forth between KDE and Gnome[/quote]

similar issue there as well...

kde and gnome sometimes do not play very nicely together.

---

### Post by curuxz on 2006-01-16
Strange tho, on a clean install of ubuntu I cant find the file. (so it must come from something like k3b) but the laptop was running xfc only and main pc ubuntu only. Real pain in the ass, should I file a bug report?

---

### Post by ahave2005 on 2006-01-16
I've eperienced the same problems concerning .ICEauthority, but only a few times, when I just installed Ubuntu 5.10. I've never tried to install KDE, and never installed any KDE programs, except K3b. I've started K3b as root a good few times to troubleshoot, never turned out to an issue with K3b, but it didn't give me any problems with .ICEauthority to run K3b with root permissions.

I'm no help, I don't give a solution. But I'm baffeled, since the problem never arised since I installed 4 months ago.

The only thing I can come by, is that, at some point my screen started to go blank or dim, whenever I had to give the root password in GNOME. Which my laptop doesn't.

/ahave

---

### Post by curuxz on 2006-01-16
Admins have moved thread, probs a good call i did not realise this was a bigger issue than just me. 

Maybe some kind of patch to ubuntu that looks for the file and checks its permissions at boot? Would that be hard to add..?

---

### Post by morphodone on 2006-01-16
i've had this happen as well, i think on other distributions even

whenever you try to run a kde app under another desktop...

most solutions suggest deleting the .ICEauthority file and then
trying to login

---

### Post by qferret on 2006-01-16
Similar issues after opening k3b. Nautilus as root is my favorite offender.... sometimes I just don't feel like a prompt heh. :p 

Mine is always .Xauthority instead of .ICEAuthority though (but I believe it's the same basic concept.)

Anyone know the diff between the 2 files?

---

### Post by kassetra on 2006-01-16
What these files are and what they do are a little hard to understand - but let me see if I can make sense of it for you: 

When you get to your login screen, you have started up an X server.  This server is capable of allowing many users to login at the same time.

Now, when you login, the display manager (usually GDM on Ubuntu) gives you a token or a cookie so that you can connect and access the X server as a proper client.  (So that you can login and use the X server.)

This cookie is stored in .Xauthority or .ICEauthority.  It's automatically generated and passed to one of these files as soon as you login - so if you don't have write permissions to these files - you can't accept the cookie - and therefore, you can't get into your own personal session.

As for the difference between the two - the only difference is which X server / *DM are you running.

---

### Post by kassetra on 2006-01-16
[quote=curuxz]Admins have moved thread, probs a good call i did not realise this was a bigger issue than just me. 

Maybe some kind of patch to ubuntu that looks for the file and checks its permissions at boot? Would that be hard to add..?[/quote]

Since the files are on a per-user basis - boot time would have to check through every user's home directory on the system... I'm not sure that would be such a wise thing to do.

---

### Post by 5-HT on 2006-01-17
Hi, sometimes I get forgetfull and sudo graphical apps...thankfully I haven't had an issue yet with .ICE(X)authority, but in case I do in the future I'm just wondering that the best fix would be (after searching some threads on this topic and finding different responses):

I. Change owner of the file back to me (if it belongs to root)
II. Delete the file
III. Delete all the contents of the file but not the file itself (if it still belongs to me)
IV. Give w/r permissions to the file

Or are all/some of these ok?


Also, not sure if this fits in this thread (could always start a new one, but it's not a big issue by any means and seems relevant here)...
I just noticed that I've always used sudo to launch gedit when needed (and it seems that all posts I come across here about editing files outside one's own home folder indicate the same).

When I tried launching it with gksudo via the 'Run Program' dialogue, and from the CLI...there seems to be the problem in that the file that opens is blank (regardless of which file I open); however, while running with sudo the file is there as it should be.

So is it ok to run gedit with sudo when needed (guessing so...), and is there a reason why I'm having this problem when trying to launch it with gksudo?

Thanks for any suggestions.

---

### Post by curuxz on 2006-01-18
yea i got around it by going to a text terminal (btw I love that feature of opening new terminals from the f-keys) and just doing a chmod 777 to the offending file. Pain tho...

---

