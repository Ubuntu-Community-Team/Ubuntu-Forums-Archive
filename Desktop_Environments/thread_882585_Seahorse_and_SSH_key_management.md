---
title: "Seahorse and SSH key management"
date: 2008-08-07
forum: Desktop Environments
---

### Post by txapelgorri on 2008-08-07
Hi there:

I was trying to manage some SSH public keys that I have from other users with Seahorse. Specifically, I was trying to import them. Seahorse refuses importing, prompting me that it's unable to load the file: "Invalid file format".
Looking up for any workaround, bug or info about this point I've found this: [https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/252288](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/252288)

Is really Seahorse not accepting SSH keys management anymore?. Any alternative to this software (if that is true)?.

Cheers, Ibon.

---

### Post by sayakb on 2008-08-07
See here if you have a solution: [http://www.funnestra.org/ubuntu/hardy/](http://www.funnestra.org/ubuntu/hardy/)

---

### Post by txapelgorri on 2008-08-07
Thanks for answering, but no luck at the site you mentioned. ssh-add filename ask me for a password on the public part of a certificate that I want to import, and of course, I haven't any pass for that shell certificate at all (it's the public part!).

Cheers, Ibon.

---

### Post by sayakb on 2008-08-07
Read here: [https://help.launchpad.net/YourAccount/CreatingAnSSHKeyPair](https://help.launchpad.net/YourAccount/CreatingAnSSHKeyPair)

---

### Post by txapelgorri on 2008-08-07
Hi:

Thanks for answering. I've read that, but I can't find any solution or any conclusion for my question (am I missing something?).

Cheers, Ibon.

---

### Post by pormogo on 2008-08-21
I have a somewhat related issue. I am assuming that seahorse-agent has either replaced or absorbed ssh-agent in ubuntu. I am able to import my ssh keys using the ssh-add command and everything works as I would expect ssh-agent to work. However Seahorse doesn't seem to actually store my keys in between reboots. Every time I reboot my laptop I have to re add my ssh keys using ssh-add. When I open the seahorse gui the ssh keys that I added using ssh-add aren't anywhere to be found. Is there a way to add my ssh-keys into seahorse permenantly so that I don't have to re add them each time that I boot?

---

