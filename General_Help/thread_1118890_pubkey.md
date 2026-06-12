---
title: "pubkey"
date: 2009-04-07
forum: General Help
---

### Post by djallalnamri on 2009-04-07
* hello
* i frequently have this error message these last days (i am using french as system language but i guess the meaning should be obvious for everyone who use ubuntu):PG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: Les signatures suivantes n'ont pas pu être vérifiées car la clé publique n'est pas disponible*: NO_PUBKEY EFD9A0E0EC6B3CADImpossible de récupérer [http://ppa.launchpad.net/ubuntume.team/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubuntume.team/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found
*well i can still update the system but i really would like to find a solution to this problem
*i am going to google around in between
*thanks in advance

---

### Post by schmidtbag on 2009-04-07
I don't understand French but as far as I can tell, whatever is trying to happen can't connect to a server, meaning, dead link.  Unless this is important to you, I would just ignore it, otherwise, try finding and updated version.  I'm almost positive I get a similar issue and everything works fine for me.



By the way, there are french forums, I forget what its called but it might just be ubuntuforums.fr

---

### Post by chriskin on 2009-04-07
follow this : 

> **taavikko said:**
> This is for the first key,

```
gpg --keyserver keyserver.ubuntu.com --recv 0c713da6
``````
gpg --export --armor 0c713da6 | sudo apt-key add -
```Do the same for the other key...
Last 8 digits...

Probably good idea to tell the problem to owner of ppa?

as said , use the 8 last digits instead of the ones in the example above

---

### Post by djallalnamri on 2009-04-11
*hello
*i think  have fixed the problem:being on ubuntu muslim edition,i did not know that the ubuntuME team changed their repos untill 2 days so all i have was to modify repos links and all is ok now...
*so it is SOLVED

---

