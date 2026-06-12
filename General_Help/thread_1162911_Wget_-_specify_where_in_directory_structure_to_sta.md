---
title: "Wget - specify where in directory structure to start"
date: 2009-05-18
forum: General Help
---

### Post by visserman on 2009-05-18
Hi All

I've been trying to wget to automate some patch downloading from redhat.

I enter the url for the directory where I'd like it to get files from, but it always starts at the root. If I use the recursive option, it will get the whole site. If I use the nd (no directory) option, it only gets the file(s) in the root.

How do I specify where to start?

Here's what I've tried and my results:

wget -r [http://ftp.redhat.com/pub/redhat/metamatrix/connector_patch552/](http://ftp.redhat.com/pub/redhat/metamatrix/connector_patch552/) 

Gets me everything starting from ftp.redhat.com

wget -nd [http://ftp.redhat.com/pub/redhat/metamatrix/connector_patch552/](http://ftp.redhat.com/pub/redhat/metamatrix/connector_patch552/) 

Gets me index.html, the only file in the root at ftp.redhat.com

Why doesn't it start downloading from connector_patches552?

---

### Post by visserman on 2009-05-18
bump

---

### Post by unutbu on 2009-05-18
Is this what you are looking for?
```
wget --no-parent -r   http://ftp.redhat.com/pub/redhat/metamatrix/connector_patch552/
```

---

### Post by visserman on 2009-05-19
Many thanks, that does get me a lot closer.

It does get only the file, but it's still creating the full directory structure from the root.

Perhaps I'm going about this the wrong way. I simply want to copy all files in the specific directory (ie if i click on this link 
[http://ftp.redhat.com/pub/redhat/metamatrix/connector_patch552/](http://ftp.redhat.com/pub/redhat/metamatrix/connector_patch552/) 
my browser will offer to download whatever file is in that location, in this case a *.jar file)

How can I get the same behaviour from the shell? Is wget the right option?

---

### Post by unutbu on 2009-05-19
```
wget --no-parent -nd -r http://ftp.redhat.com/pub/redhat/metamatrix/connector_patch552/
```

The -nd flag tells wget not to create the entire directory structure.

The --no-parent flag tells wget not to grab files above the current location.

The -r flag tells wget to download recursively (i.e. all files linked on that page, and all files linked to links, etc.)

---

### Post by visserman on 2009-05-19
Whoohoo!


Thanks man. Much appreciated. Wget is one of those apps with a bewildering amount of options.

---

