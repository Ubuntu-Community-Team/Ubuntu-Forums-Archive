---
title: "what directory do I place self-made Key files for source updates?"
date: 2009-02-27
forum: General Help
---

### Post by rapachooie on 2009-02-27
Hi guys,

As per this site 

[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

I added the repository to install Open Office 3.  I followed the instructions and generated the authorisation keyfile and saved it to my /home/me/Documents/Linux/ directory.

I then updated apt-get etc and did the update, and everything went swimmingly, until I realised that the Documents directory is now owned by Root and I could not copy any of my documents in it.

I have since removed the authorisation file and am trying to figure out where to put it because I am working on my c.v. and want my Documents directory back (which I have already done by removing and mkdir again as I do not know how to change permissions for now).

In any case, I added the medibuntu repository and I followed the instructions for that, which told me to simply use a sudo apt-get command to get the keyfile.  This would obviously be desirable as it placed the keyfile inthe correct directory, whereas with the open office packages, I had to paste the authorisation code into a text document and direct the software updater to it.

so I would like to know 2 things...
1) what directory should I place this keyfile
and/or
2) how could I use the command line and apt-get to get the keyfile for me and place it in its correct home?

Thanks in advance.

Chewy

---

### Post by rapachooie on 2009-02-27
*bumb* (because I currently do not have any authorisation for one of my repo sources and the warning is irritating! :)

---

### Post by heindsight on 2009-02-27
Just use apt-key. That will grab the key from the keyserver and put it in the right place.

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 247D1CFF
```
(247D1CFF is the key identifier shown on the PPA page, you can use this method to add keys for any PPA, just change the key id)

---

### Post by rapachooie on 2009-02-27
brilliant! EXACTLY what I was looking for!!

Thanks :)

---

