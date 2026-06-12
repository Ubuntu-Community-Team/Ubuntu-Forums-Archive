---
title: "Problems with installing programs using Synoptic"
date: 2009-05-24
forum: General Help
---

### Post by KRDouglas on 2009-05-24
I accidentally posted this in another area and this might be the best one.  I am new to Ubuntu 8.04 and I'm having problems with the Synaptic system.  Heads-up!!  I am extremely new to Linux and will need directions on where to post command lines.

[SIZE=3]Synoptic Error Message:  Administration-Synaptic Program Manager[/SIZE]

Error ocurred
E:  Malformed line 52 in source list /etc/apt/sources.list (dist parse)
E: The list of sources cannot be read.
Go to the repository dialog to correct problem
E;_cache->open () failed, please report


[SIZE=3]Ubuntu Software:  System-Administration-Software-Source[/SIZE]

Canonical-supported open source software (main)
Community-maintained open source software (universal)
Proprietary drivers for devices (restricted)
Software restricted by copyright or legal issues.


[SIZE=3]Add/Removal  [/SIZE]

Failed to check for installed and available applications.
"This is a mjor failure of your software management system.  Please check for broken package Synoptic . check the file permissions and correctness  of the file.  '/etc/apt/sources.list' and reload the software information with 'sudo apt-get update' and 'sudo apt-get install-f"


I have know idea where I'm supposed to enter the new commands.  Could someone please give me detailed directions?  It would be greatly appreciated.


Kevin

---

### Post by cariboo on 2009-05-24
I would check line 53 in /etc/apt/sources.list. Press Alt-F2 and type:

```
gksu gedit /etc/apt/sources.list
```

You can enable line numbering in the test editor by going to Edit-->Preferences-->Display Line Numbers.

---

### Post by KRDouglas on 2009-05-25
Thanks for the help!!  I tried your suggestion and I got the code list which I do not understand.  I tried loading the commands '/sudo apt-get update' and '/sudo apt-get install-f' and got nowhere.  Tomorrow I will call tech support at Free Geek in Portland, Oregon and see if they can help me out.

Thanks for your help.

Kevin

---

