---
title: "Problem with Ubuntu repositories"
date: 2009-04-30
forum: General Help
---

### Post by SandyM on 2009-04-30
I wanted to to have latest version of compiz, but there seem to be some problem with Ubuntu Compiz repositories as they are showing error messages like following

[B]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89[/B]

I have added the following compiz repositories:-

[B]deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) jaunty main 
#deb-src [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) jaunty main [/B]

I think there are some problems relating to public key which I don't have, please help

---

### Post by zvacet on 2009-04-30
```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2ED6BB6042C24D89
gpg --export --armor 2ED6BB6042C24D89 | sudo apt-key add -
```

---

