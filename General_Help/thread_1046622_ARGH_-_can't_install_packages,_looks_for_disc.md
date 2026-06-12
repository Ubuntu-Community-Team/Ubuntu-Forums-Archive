---
title: "ARGH - can't install packages, looks for disc"
date: 2009-01-21
forum: General Help
---

### Post by floatingpoint on 2009-01-21
>  W: Failed to fetch cdrom:[Ubuntu-Studio 8.10 _Intrepid Ibex_ - Release amd64 (20081028)]/pool/main/p/pyopenssl/python-openssl_0.7-2_amd64.deb

I get this error when trying to install packages or applications in regular Ubuntu 8.10. I don't have Ubuntu Studio installed at all, I did/do have a Live CD (on a dvd, the .iso is 1.1gb)fur UbuStu8.10, but didn't really do anything with it.

I think I was downloading a couple of codecs or something like that, when the disk was in the drive. It said something about the disk, then gave a message like 
> 
"Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?"

If you hit no, you ge the above error. If you hit yes, it tells you some of the packages couldn't be installed iirc. 

Whenever I try to install a package now (for example I just tried to download Deluge from Synaptic) I get the following:
  
> "Please insert the disc labelled:
Ubuntu-Studio 8.10 _Intrepid Ibex_ - Release amd64 (20081028)
in drive /cdrom/"


Cancel takes you down one of the above routes, OK (inserting the disk) just throws the message up again almost immediately.

PLEASE PLEASE PLEASE, if anyone has any ideas, give me a hand. This is coming at the end of the worst series of problems I've had since switching to Ubuntu!

Thanks in advance!

---

### Post by Titan8990 on 2009-01-21
System -> Administration -> Software Sources


Disable the CD option.

---

### Post by floatingpoint on 2009-01-21
Titan, you're a hero.

Let this be a lesson to new ubu users. The most annoying problems you will encounter probably have the simplest solutions! :D

---

