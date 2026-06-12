---
title: "Install Beryl using proprietary FGLRX drivers from ATI"
date: 2007-09-09
forum: Desktop Effects &amp; Customization
---

### Post by Imashinu on 2007-09-09
Right now I'm reading the wiki ([http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)) trying to complete this process but I am getting the following errors.

It tells me:
    * Add the correct repository key: 
```

gksudo wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```

So I did so, then it says:

    * Read #How to add extra repositories. Add this to your repository list (or directly to /etc/apt/sources.list using gedit): 

```
deb http://ubuntu.beryl-project.org/ feisty main
```

Now once I do so I get this error:

```
W: GPG error: http://ubuntu.beryl-project.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
```


Any ideas on how to fix this? 

Is this necessary to complete the process

---

### Post by DaH-RaT on 2007-09-13
same problem here also

---

