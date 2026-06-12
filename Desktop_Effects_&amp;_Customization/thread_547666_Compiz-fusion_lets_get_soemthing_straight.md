---
title: "Compiz-fusion lets get soemthing straight"
date: 2007-09-10
forum: Desktop Effects &amp; Customization
---

### Post by uposer111 on 2007-09-10
Ok, Ive followed like 10 guides on how to install compiz fusion and i am baffled that none of them are working.

Here is my Video Card [Ati 1950 Pro]("http://ati.amd.com/products/RadeonX1950/x1950pro.html") The driver is fglrx

I followed a couple guides as i said before setting up a xgl server and what not, and i ended up getting the wobbly windows working on the gnome interface, but I am trying to get it to work on my KDE interface because thats what i use. The wobbly windows only work, not the 3d cube or any other of the plugins. Im thinking that the problems may all be linked to my ATI video card, could this be a possibility? If it is i still have the generic video card that came with my computer, but it dosnt allow my dual monitors.

Following this guide [Forlong]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty")

I get a couple errors, and i want to know if they matter. First off, when im adding the Repository's I get this error.
```
W: GPG error: http://kubuntu.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: http://mirror3.ubuntulinux.nl dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
```
He said don't worry about authentication, but im going to supply all my errors just in case.

I follow the guide without flaws up until he tells us to open compizconfig. I locate it, i click on it, it opens for a split second and then closes. I dragged the link to my desktop and tried again, same conclusion.

I can do Alt-F2 compiz --replace without any errors, but when i do ccsm, it opens for a split second and closes. Im not sure what exactly im doing wrong here.Ive been going at this for days with no luck no progression and no answers. I am even will to setup a remote connection for someone to look at what may be wrong. My computer is up-to-date.

Thanks in advance. My msn is [email]uposer111@hotmail.com[/email] to speak with me directly.

Jeff

---

### Post by Vadi on 2007-09-10
Strange that the CCSM doesn't open. Open your terminal (applications - accessories - terminal), and type **ccsm** in there. What does it say?

Have you tried posting on the official Compiz forums? If no, please post at forum.compiz.org, someone there definitely will be able to help you.

---

### Post by uposer111 on 2007-09-10
This is what i get:
```
File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 197, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 196, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 193, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

```

I will go post on those forums now.

Thanks, 
Jeff

---

### Post by uposer111 on 2007-09-10
bump

---

### Post by Forlong on 2007-09-10
Hi,

first of all, why didn't you post on "my" thread - this way I would've noticed your problem right away.
> **uposer111 said:**
> I get a couple errors, and i want to know if they matter. First off, when im adding the Repository's I get this error.
```
W: GPG error: http://kubuntu.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: http://mirror3.ubuntulinux.nl dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
```
He said don't worry about authentication, but im going to supply all my errors just in case.
Those are error messages for _other_ repositories!

I said specifically in the how-to to remove them, if they have something to do with Compiz. And that's pretty obvious, since you have broken dependencies.

Please remove all repositories regarding Compiz/Beryl (in fact remove _every_ repo that you don't know about).
Then remove Compiz completely and try again.


Regards,
Nick

---

