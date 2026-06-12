---
title: "Broke Adept, Trying to Install Wine"
date: 2005-12-21
forum: Desktop Environments
---

### Post by ddesmarais58 on 2005-12-21
Dear Forum Members:

Would appreciate any help possible: Following instructions for Ubunto / Debian-based linux varieties on "Frank's Corner ... Wine - Windows on Linux" site to install Wine (a windows compatibility layer), I added a line to the default list of repositories given in Ubuntu's Adept package management utility.

The line was referring to an apt repository for on the Debian site, I think, where packages comprising WINE reside.

Since then, Adept crashes saying can't open the list of repositories.  I have tried running "apt" and "apt-get update" in terminal mode, but Adept still crashes -- actually "apt-get update" crashes in terminal mode also.

Tried installing Adept, I think, again from my 1 CD Ubuntu installation "set" and installation looks for a 2nd CD which I never had to download / produce before...

Arrgh!

Please help this hopeless NewB.

Thanks, Dennis   :confused:

---

### Post by MartinJ on 2005-12-21
This happened to me - The 'Manage Repositories' option in Adept seems to be messing things up sometimes.

You can add repositories using the terminal:

```
sudo nano /etc/apt/sources.list
```

then type or paste in the new repository at the bottom of the file.  Use ## to enter a comment if wanted.

I would also make sure that the old wine repository that broke Adept is removed.

---

### Post by tkjacobsen on 2005-12-21
[QUOTE=ddesmarais58]Dear Forum Members:
I added a line to the default list of repositories given in Ubuntu's Adept package management utility.
[/QUOTE]
Try to remove or comment out that line in /etc/apt/sources.list. 
Instead add mulitverse and universe repos and install wine from them.

---

### Post by ddesmarais58 on 2005-12-21
Thanks, All:

I followed your excellent suggestions and got Apt and Adept working fine again, by editing out the offending line as suggested and added lines making the "universe" packages available.

BUT, lacking common sense, I got entranced by the variety of packages now and "broke" Apt and Adept again when installing packages relating the Webmin Unix interface. (Sounded like a good idea...)

Apt downloaded all packages successfully and was unpacking and installing, when the installation process asked me for my local domain name, I gave it one, in my ignorance,  ("localdomain") and everything hung up when the process then tried to bind to the "YP server" and eventually went into background mode after the attempt to bind returned a result of " 1 ".

Probably made things worse by forcing an exit from Apt as nothing was happening for a looooong time and restarting my machine.

I noticed the same error during startup screen output as an attempt to bind to the "YP server" failed again then backgrounded as the startup continued normally, except for a problem with the DHCP service.

I know that I have un-applied package changes floating around in the machine, but Adept now insists I am not "Root" and just gives me read-only access. (Machine probably knows its safer from my blundering attacks that way...)

Which way back to sanity, please?   :confused:

---

### Post by ltmon on 2005-12-21
Woah, that sounds like a mess... it really shouldn't have happened that badly.

Do other "sudo" commands recognize you as root?

Try typing in a terminal:

> sudo apt-get install xvier

(this should install a silly little game, and if it works/doesn't work may help diagnose your problem).

L.

---

### Post by ddesmarais58 on 2005-12-22
Thanks, Ltmon:

That's a good start. It gave me a message re: how to finish the package installation process, which carried on with several messages in turn on how different programs need to be further configured.

Thanks again - but I will take whatever other ideas are out there. :smile:

---

### Post by ltmon on 2005-12-22
[QUOTE=ddesmarais58]Thanks, Ltmon:

That's a good start. It gave me a message re: how to finish the package installation process, which carried on with several messages in turn on how different programs need to be further configured.

Thanks again - but I will take whatever other ideas are out there. :smile:[/QUOTE]

I gather it didn't fix the problem though?  Can you post the output of the command?

L.

---

