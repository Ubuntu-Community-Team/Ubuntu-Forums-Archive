---
title: "Mistakenly changed permissions for /usr/ recursively - fix?"
date: 2009-04-01
forum: General Help
---

### Post by slockton on 2009-04-01
Hi,

I have Ubuntu Intrepid. I was trying to configure some perl modules today that required me to temporarily change permissions in a folder in /usr/.

Rather stupidly, I changed the permissions (chmod -R 755 /usr/, I presume) for all of the /usr directory. This caused the dreaded "greeter application appears to have crashed" error on reboot, stopping GDM from starting. I could only fix it by giving 777 permissions to all of /usr. Obviously, this is not ideal.

EDIT: I've just realised I cannot currently sudo. I get the error "sudo: must be setuid root".
EDIT2: sudo error fixed with "chmod 4755 /usr/bin/sudo" after becoming root. Everything else still 777.

Searching these forums, I can only find suggestions that I reinstall the OS (not good - hence this post). Since I don't have such time to spare right now, is there a way I can restore/repair permissions in this folder? Do the subdirectories within /usr that are common to all Ubuntu installations have a standard set of permissions that I can reapply?

Any help would be much appreciated.

Cheers,
Steve

---

### Post by Sinkingships7 on 2009-04-01
I've done this before, and the only way I've found (or heard of) is to reinstall. 

Sorry. :/

---

### Post by TyrantWave on 2009-04-01
Change the permissions of /usr to 644. (Do it recursively if needed):

sudo chmod -R 644 /usr

---

### Post by Tim Sharitt on 2009-04-01
I don't know that there is an ideal solution to your problem. Most files in /usr and it's sub-directories are set to 755 (for executables) or 644 (non-executable) permissions. 

Setting everything to 644 wouldn't work because you would not be able to run any programs filed under /usr and most of your applications are likely located in /usr/bin.

Setting everything to 755 may work, but I am not sure what risk may be associated with allowing everything to be executable. However, It would still be better than your current situation since your important files would not be globally writable. Having the executable flag set on all the files may have unknown consequences, but should not matter for the most part since most of the files which are not normally executable are images, header files, documentation, libraries, etc.

Sorry I can't give a more concrete suggestion, but I hope this information will help you decide what course of action to take.

---

### Post by slockton on 2009-04-03
Thanks for the responses everyone.

I chmod'ed /usr to 755 (recursively), apart from sudo, which needed fixing again with "chmod 4755 /usr/bin/sudo".

I've been using the computer for a couple of days now, mostly command line over ssh, and not noticed any weird behaviour. It may be fixed, but I'll keep a sharp eye on it and report any nonsense.

Cheers,
S

---

### Post by JKyleOKC on 2009-04-03
> **slockton said:**
> 
I chmod'ed /usr to 755 (recursively), apart from sudo, which needed fixing again with "chmod 4755 /usr/bin/sudo".

You may need to do the same for mount and umount, if you have any devices set up to allow mounting by the users. They are not setuid by default, but several of the network browsing programs require them to be changed...

---

### Post by eldragon on 2009-04-03
reinstall and learn the lesson.

---

### Post by slockton on 2009-04-04
Thanks for the helpful reply, JKyleOKC.

S

---

### Post by slockton on 2009-04-05
Another thing that needed fixing after the recursive chmod 755 in all of /usr...

Couldn't edit crontabs. Fixed with > sudo chmod 4755 /usr/bin/crontab

Cheers,
S

---

