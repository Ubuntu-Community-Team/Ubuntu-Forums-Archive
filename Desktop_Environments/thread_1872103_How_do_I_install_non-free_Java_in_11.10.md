---
title: "How do I install non-free Java in 11.10?"
date: 2011-10-30
forum: Desktop Environments
---

### Post by tdn on 2011-10-30
How do I install non-free Java in 11.10?

I have read [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java), however, it seems rather outdated. For example, it mentions adding lucid partner sources. Is that really correct to do in 11.10? 

From the Java help page:
``The Sun Java 6 packages are available from the partner repository. You can configure your system to use this repository via command-line: 
sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"''

Should I really do that in 11.10? I already have 
 deb [http://archive.canonical.com](http://archive.canonical.com) oneiric partner
But sun-java packages are not available for  install.

---

### Post by mtron on 2011-10-30
yes the ubuntu help is outdated. Java is now owned by Orace and distributions are not allowed to carry newer releases in their repositories.

Though it is still provided for natty, so i added the natty canonical partner repo to the sources.list

```
sudo gedit /etc/apt/sources.list
```

Add this at the bottom:

> ## Canonical Partner for natty
deb [http://archive.canonical.com](http://archive.canonical.com) natty partner

now save the file & close the text editor. Back in the terminal:
```

sudo apt-get update
sudo apt-get install sun-java6-jre
```

now you can disable the natty partner repository again. (just place a # at the beginning of the  deb line

> ## Canonical Partner for natty
#deb [http://archive.canonical.com](http://archive.canonical.com) natty partner

---

