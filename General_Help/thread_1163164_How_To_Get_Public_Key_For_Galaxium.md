---
title: "How To Get Public Key For Galaxium"
date: 2009-05-18
forum: General Help
---

### Post by ram2008 on 2009-05-18
**I tried to install Galaxium for 9.04 this morning but I got an error message complaining about no public key.  Evidently as a result of that Synaptic did not download the program.  The package is not available.  How do I get the public key?  The Google page where I obtained the info. about the repository made no mention of the public key.**

---

### Post by michy99 on 2009-05-18
Here's the key I found at launchpad. Do you know how to add it?

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXbLPgEEAL97Jb+t/J6uDSSWOd6npZhUERIjKpWr0qfge5QGYu7iPYLdoOc+p2Ohg2xj
N8DhJazsvI/mLrK5C2cc7jg+VwvLtq+DRkUYVrfC3srXTxWtHY7MnGsn48TRUbDZ5KFj2IsK
wj0LGS5DevC2YYqQPJ9YMlxogHq+gQ/ZJHVrrBhPABEBAAG0H0xhdW5jaHBhZCBQUEEgZm9y
IFRlYW0gR2FsYXhpdW2ItgQTAQIAIAUCSXbLPgIbAwYLCQgHAwIEFQIIAwQWAgMBAh4BAheA
AAoJED4CGRZ4VKOpW3UD/iP2txVgmxrhtyGkt6oZJ218Lq5goAvxCKQMW7JkuACFqWkxjTvm
veNFPwJMX5t23TP/rsDH4e6OCj3eO9wdog4L2iW2wMtjXUKNd45p9HbVkuoAcSbRJJA1JAaK
EGvExOz5HuiMLlm8JsvPAt6VzzszHymJ3B05Ii07+CqrOPRV
=gAZV
-----END PGP PUBLIC KEY BLOCK-----

```

---

### Post by VCoolio on 2009-05-18
That should solve your problem, but [here is a link]("https://help.launchpad.net/Packaging/PPA#keys?action=show&redirect=PPAKeys") to an explanation of adding ppa keys, so next time you know what to do.

---

### Post by ram2008 on 2009-05-18
OK guys, thanks for your posts.  I installed the key with no problem but I'm still getting a message that galaxium is not available.  Not sure what the problem is.  I'm sure I put in the correct repository information which is: deb [http://ppa.launchpad.net/galaxium/ubuntu](http://ppa.launchpad.net/galaxium/ubuntu) jaunty main.  That's the information that's in /etc/apt/sources.list. Not sure what to do next.

---

### Post by michy99 on 2009-05-18
After adding the sources, be sure to```
sudo apt-get update
```

---

### Post by ram2008 on 2009-05-18
Hi Michy99,

Yeah, I ran sudo apt-get update already but still no luck in getting Galaxium.  I think this is the first time I've had a problem getting any software.  I ran update again just now and checked the list of sources and the repository for Galaxium is there but the package still isn't available.  Very puzzling.

---

### Post by coniglia on 2009-05-20
i got the same problem, n after searching i found that u have to enter ths command: 

sudo apt-get install galaxium-svn

n it's installed right now :)

---

### Post by ram2008 on 2009-05-20
Hi Coniglia,

Thanks for you post.  I followed your suggestion and everything worked just fine.  Galaxium is up and running now.  I'm surprised that the backintime web site from which I obtained the repository details didn't include the necessary information.  Any idea what "svn" stands for?  Anyway, thanks a lot for your help.

---

### Post by shihkster1015 on 2009-08-04
but when i installed galaxium by typing "sudo apt-get install galaxium-svn", the galaxium is messed up itself. like I cant open a conversation windows, but i can see my contact lists. Also, i can't see my name or anything on the first three rows

Using Jaunty

---

