---
title: "Need help removing VirtualBox"
date: 2009-04-27
forum: General Help
---

### Post by gui-tar on 2009-04-27
I installed virtualbox to emulate some of my windows software and now i want to remove it. But i cant seem to remove it. can anybody please provide me instructions on removing it?

---

### Post by kpkeerthi on 2009-04-27
If you installed using deb file, you should able to search and remove from Synaptic (System -> Admin -> Synaptic)

---

### Post by gui-tar on 2009-04-27
yes i tried that. but when i search for VirtualBox a lot of packages come but it does not have a tick on them. See the attachment for the picture...

---

### Post by Saghaulor on 2009-04-27
I would make sure to remove the virtual disk first before removing the program, because it might remain behind, and you don't want a large virtual parition eating up space when it's not doing anything.

Also, run this from the command line.

To figure out what you have installed.

```
aptitude search virtualbox
```

That of course will return all instances of virtualbox in the package manager. The ones that are listed with an 'i' preceding their name are the packages actually installed. 

To remove the packages that are installed, just run the following.

```
sudo apt-get remove 'thepackagename'
```

Obviously the quotes are for mention, so do not include them in the actual command. You can list all of the package with a space between them and it will remove them all. Or you could run this command.

```
sudo apt-get remove virtualbox*
```

And it will remove all instances of virtualbox.

---

### Post by gui-tar on 2009-04-27
Wow! thankyou a lot. it solved my problem! :)

---

### Post by Saghaulor on 2009-04-27
I'm glad that I could help.

---

