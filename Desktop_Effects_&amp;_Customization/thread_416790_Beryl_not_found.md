---
title: "Beryl not found?"
date: 2007-04-21
forum: Desktop Effects &amp; Customization
---

### Post by Duckk on 2007-04-21
I'm a semi-new user of Ubuntu, so please bear with me.

I've upgraded from 6.10 to 7.04. I figured I'd give Beryl a whirl, so I'm trying to install it. I can't find it in the package manager, and the command line steps to add it to the repository hangs when I try the 

wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

step. It says that it "cannot write to 'root@blah' (Broken Pipe)". I'm probably missing something simple, but, again, I haven't had much time to tinker with Ubuntu. Thanks for the help.

---

### Post by chakkaradeep on 2007-04-21
Enable the Universe repos from your Synaptic Package Manager and do,

**sudo apt-get install beryl beryl-manager emerald-themes emerald**

That should make Beryl work in Feisty ! :)

---

### Post by antonferdinand on 2007-06-20
Work in Ubuntu Edgy tooo..

I try to write :

# sudo apt-get install beryl beryl-manager emerald-themes emerald

Then

# wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
--10:45:36--  [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg)
           => `-'
Resolving ubuntu.beryl-project.org... 195.114.19.35, 208.113.193.9, 80.77.247.17, ...
Connecting to ubuntu.beryl-project.org|195.114.19.35|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,415 (2.4K) [application/octet-stream]

100%[===========================================================================================================================>] 2,415         --.--K/s             

10:45:38 (1.06 MB/s) - `-' saved [2415/2415]

OK

---

### Post by antonferdinand on 2007-06-21
its work in my laptop and amazing, thx for ubuntu and beryl, i post my installation progress in my blog


--
regards,
Anton Ferdinand
Site on [http://capsule.web.id/blog/](http://capsule.web.id/blog/)
Email [email]anton@capsule.web.id[/email]

---

