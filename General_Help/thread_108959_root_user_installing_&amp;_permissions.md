---
title: "root user/ installing &amp; permissions"
date: 2005-12-27
forum: General Help
---

### Post by nic-clark on 2005-12-27
Hi,

I've just installed Ubuntu, and so far so good - this is the first time I've really used linux.

I can't seem to work out how to install new things though- the permissions on the drive are set only to read and I can't change them as it says I don't own them. Thereofr I can't make new files etc. Is there a root user in Ubuntu that I can use or is there a way of changing the permissions? I am also trying to install a .rpm package using the dpkg command and it says I don't have the rights - I guess this is the same issue?

I've read the post earlier about drive permissions, but my setup is different to that in that I only have one disk - I dont want to go messing it up! Attached is a shot if the fstab file. My machine is a Dell pIIII 1.5ghz with 512mb and 60g hdd.

Hope someone can help!

Cheers,

Nic

---

### Post by kaamos on 2005-12-27
You should be able to create new files inside your home directory (like /home/nic-clark). Elsewhere you need permission, and this can be used with the "sudo" command. So if you wish to install or remove a program you must use sudo.

Additional info here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

For installing .rpm files you must use the "alien" program. So install alien with synaptic (instructions -> [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)) and then open a terminal, navigate to the folder where the rpm is and type
```
sudo alien -i **name_of_file.rpm**
```

---

### Post by stuporglue on 2005-12-27
> I am also trying to install a .rpm package using the dpkg command and it says I don't have the rights - I guess this is the same issue?


Check for the program you are trying to install in Synaptic first. If it's a common program, it probably exists already configured for Ubuntu. There are exceptions, but you can save yourself a lot of work if it is in there.

---

### Post by steve.horsley on 2005-12-27
[QUOTE=stuporglue]Check for the program you are trying to install in Synaptic first. If it's a common program, it probably exists already configured for Ubuntu. There are exceptions, but you can save yourself a lot of work if it is in there.[/QUOTE]

You may ned to enable the Multiverse and Universe binary repositories in Synaptic to be able to find it though:
Start->System->Administration->Synaptic Package Manager
Settings->Repositories
Click +Add, and then add the Multiverse and Universe, then OK
Now you can search for the package you want.

---

