---
title: "Permanently log in as root?"
date: 2005-06-04
forum: Desktop Environments
---

### Post by Curlydave on 2005-06-04
Is there a way to make it so you always actually log in as the root user? This would greatly simplify things.

---

### Post by foxy123 on 2005-06-04
[QUOTE=Curlydave]Is there a way to make it so you always actually log in as the root user? This would greatly simplify things.[/QUOTE]
yeah, it would, especially to ruin your system...

---

### Post by Curlydave on 2005-06-04
[QUOTE=foxy123]yeah, it would, especially to ruin your system...[/QUOTE]

To what? To "run" my system?

---

### Post by angkor on 2005-06-04
:-) I think foxy did mean '*ruin*'

I think you can, but I do not think it's very sensible. You always seem to talk about 'having authority' over you HD. Well I almost never log in as root and still have complete control and power over my system. I can wipe it out with one single command logged in with my user account.

Well you asked for it:

Go to System->Administration->login screen setup-> and allow root to login using GDM. Next enable automatic login. Dunno if this works though. And don't come crying to me when you fsck up your system...I'm just the messenger....Btw this is not that difficult...you could have found this out yourself. ;-)

---

### Post by Curlydave on 2005-06-04
Nice!!! I love you angkor. Have my babies. :) Now, I know, I've been warned. I don't have anything super-valuable on my Linux HD, so I'm not tooo worried if something happens. Now, what would happen, and why is this so taboo? It's not like I'm going to start rummaging through my hard-drive and delting files for the fun of it. I've heard outside security threats cited, but are there actually any viruses for Linux? (I'm thinking chances of somethign bad happenign from a hacker=slim-none.)

And yea, I probably should have been able to figure that out myself. I've glanced over those login settings several times, but nothing jumped out at me. I guess I missed that one.

---

### Post by jcooper on 2005-06-04
[QUOTE=Curlydave]Now, what would happen, and why is this so taboo? It's not like I'm going to start rummaging through my hard-drive and delting files for the fun of it. I've heard outside security threats cited, but are there actually any viruses for Linux? (I'm thinking chances of somethign bad happenign from a hacker=slim-none.)[/QUOTE]

Think of it this way. You're a beginner to linux. You could, in theory, request help from someone on the internet (either via a forum or IRC etc), who then instructs you to either run a command that could be malicious, or gives you a malicious script and says "run this by doing ./runme.sh in a terminal" to fix your Xorg/sound/icons/other problem. Of course, with a limited understanding of linux, and trusting of individuals on the internet, you could hose your system.

Learn to work the *nix way, rather than take the run-as-admin route of windows and try applying it to your linux desktop. Typing sudo before the important commands really isnt that much of a big deal.

---

### Post by Curlydave on 2005-06-04
But... If they wanted me to run a malicious command, they'd just have it start with sudo.

---

### Post by Xerampelinae on 2005-06-04
People don't like to run as root since that makes all the programs you use run as root... which means an exploit in any of these apps (gaim, firefox, for example) would have root privs.

---

### Post by lovebug356 on 2005-06-04
For terminal users:
$ sudo passwd root
...
$ su root
( you are now in the terminal with the root account )

It is not a Taboo, It is just non-sense to always log in as root.
What can happen?
Tell us in a week ;-)

---

### Post by Xerampelinae on 2005-06-04
[QUOTE=lovebug356]For terminal users:
$ sudo passwd root
...
$ su root
( you are now in the terminal with the root account )

It is not a Taboo, It is just non-sense to always log in as root.
What can happen?
Tell us in a week ;-)[/QUOTE]
 sudo -s -H

also gives you a root prompt.

---

### Post by angkor on 2005-06-05
[QUOTE=Xerampelinae]sudo -s -H

also gives you a root prompt.[/QUOTE]

or just su [enter]
[enter root passwd]

---

### Post by Firetech on 2005-06-05
sudo su
or 
sudo -i
gives you a "real" root prompt, easier.

---

### Post by enquiry on 2005-06-05
[QUOTE=angkor]or just su [enter]
[enter root passwd][/QUOTE]
That doesn't work under Ubuntu unless you have created a root user. sudo su, does however work.

---

### Post by angkor on 2005-06-05
[QUOTE=enquiry]That doesn't work under Ubuntu unless you have created a root user. sudo su, does however work.[/QUOTE]

I have. :)

---

### Post by jeremy on 2005-06-06
[http://ubuntuguide.org/#allowrootlogingnome](http://ubuntuguide.org/#allowrootlogingnome) tells you how to do it. That said, I dn't recommend it.

---

### Post by nocturn on 2005-06-06
[QUOTE=Curlydave]I don't have anything super-valuable on my Linux HD, so I'm not tooo worried if something happens. Now, what would happen, and why is this so taboo? I[/QUOTE]

This isn't a Taboo.  In the early Linux days, lots of people ran desktops as root, during install, the setup created the root pw and no user. 
The reason why this is no longer the case, and each distro now at least offers to create a user during install is that some people got burned. 

Running as root has many disadvantages, security being one.  Being to careless being the second ("rm -rf *", ... oops, I wasn't in /tmp).
Processes started as root have more privileges, so them crashing can have worse consequences.

I can think off 100 good reasons not to run as root, but I fail to find 1 to do it.

---

### Post by tread on 2005-06-06
The biggest one, as someone already noted, is that any exploits in say firefox, would be able to compromise the whole system. You could with care manage to not do 'rm -rf /' :) but the security issue remains.

Besides, its a matter of developing good habits. A lot of people run Windows as administrator, and look how messy that can get. Even if Linux is more secure, running as root can get you messed up .. I know because I have done 'rm -rf /' .. a shell script ran amok when I was learning :)

---

### Post by Takis on 2005-06-06
[QUOTE=tread]Besides, its a matter of developing good habits. A lot of people run Windows as administrator, and look how messy that can get. Even if Linux is more secure, running as root can get you messed up.[/QUOTE]
I would say that this is one of the reasons Linux is more secure. In fact, CurlyDave, Microsoft is going to emulate the whole "password to do anything" action in [Longhorn](http://www.microsoft.com/windows/longhorn/security.mspx) . Specifically:
"For tasks that do require elevated privileges, such as installing an application, Longhorn allows the user to enter administrative credentials in place without requiring a logoff."

---

