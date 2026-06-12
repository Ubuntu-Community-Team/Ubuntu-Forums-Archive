---
title: "New to KUBUNTU! problems.."
date: 2005-04-19
forum: Desktop Environments
---

### Post by marcocandini on 2005-04-19
I'm new to linux, and for now I've installed only Suse9.2
But  I wanted to try kubuntu, and I've some beginning problems..
*The bigger is this.. During the installation of latest kubuntu, I was asked for an user name and password.. But I wasn't asked for the root password! And so.. How to login as root???
*During the installation I made the network setup (using the paramethers that worked in suse), but in suse after setting up the network, I needed to setup my adsl (my username, password for my ISP...) and to connect with kinternet. Where I can do this in Kubuntu?

Thanks
Marco

---

### Post by weeguy on 2005-04-19
This has been mentioned quite a few times in the forums before. Ubuntu disables root login by default for security reasons. Usually a sudo command would be sufficient to get the job done. However if you really need to login as root,

[quote=bin]
In the meantime:-
1. sudo root passwd
- your own password
- new password for root

2. edit /etc/kde3/kdm/kdmrc and change the line AllowRootLogin to =true

You can then login as root.....
[/quote]

---

### Post by marcocandini on 2005-04-19
If I write sudo root password, I read unknown command or something similar.
If I try to edit, as at point 2, I not have write permissions!

And I've the adsl setup problem...

---

### Post by heimo on 2005-04-19
It's passwd not password. And to the second question, you must use root privileges to edit that file (*su* to become root, or sudo kedit [filename]).

---

