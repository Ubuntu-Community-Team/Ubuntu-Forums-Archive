---
title: "Networking Ubutu-to-Ubuntu"
date: 2005-05-25
forum: Desktop Environments
---

### Post by orion_114 on 2005-05-25
I have managed in the past to get my Ubuntu machine and my XP machine to share files, but now I have ditched Windows and I am having some troubles sharing files between the two ubuntu boxes.
[list]
[*]Do I still need to use Samba for the shares ?
[*]Are there any additional user setup steps that I neet to go through?
[*]Can I browse the shares easily ?
[*]Are there any tutorials for this setup ?
[/list] 

I want to be able to have my one machine as my file server housing my music so I can stream it to the other machines in my place.

---

### Post by Amarack on 2005-05-25
You certainly don't "need" to use Samba, there are alternatives. Namely you can use NFS, which works well. But since you are already familiar with Samba setup and usage there is also no real downside (IMHO) to using samba for sharing files between two linux computers. 

Regardless of whether you use Samba or NFS you can browse shares easily. There also exist lots of tutorials online to help setting up both. 

Here is a forum post which has links to some useful tutorials:
[http://www.ubuntuforums.org/showthread.php?t=35368&highlight=nfs](http://www.ubuntuforums.org/showthread.php?t=35368&highlight=nfs)

And here is a good guide from ubuntuguide for samba:
[http://www.ubuntuguide.org/#sambaserver](http://www.ubuntuguide.org/#sambaserver)

---

### Post by orion_114 on 2005-05-26
Thanks Amarack.
Hopefully I can get it working now :D

---

