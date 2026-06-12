---
title: "Searching for packages"
date: 2011-02-24
forum: Desktop Environments
---

### Post by towheedm on 2011-02-24
If I don't know the exact name of a package, I can search for it using the search box in Synaptic.  Let's say for example, I wanted to install a package named package-1ubuntu5.  If I did not know the exact name, I could enter 'package' in the search box and get a list of all packages containing the phrase 'package'.

How can I do this from the command-line if I don't know the exact name of the package?  Now, I don't mean entering the package version as in:

```
apt-get install package=1ubuntu5
```

But instead list all packages containing the phrase 'package'.

---

### Post by Frogs Hair on 2011-02-24
Open the synaptic package manager and search for the package and mark for installation. I think that may be easier than guessing at package names in the terminal .

If there are many similar packages you will have to find the exact one you need.

---

### Post by towheedm on 2011-02-24
Yeah so I can do that.  But, I am trying to learn to do most everything from the CLI.

---

### Post by Krytarik on 2011-02-24
You can use "apt-cache" for that:
[http://manpages.ubuntu.com/manpages/natty/en/man8/apt-cache.8.html](http://manpages.ubuntu.com/manpages/natty/en/man8/apt-cache.8.html)

Greetings.

---

### Post by towheedm on 2011-02-24
Seems to be what I was looking for.  Will certainly have a closer look at it.  Thanks.

---

### Post by oldos2er on 2011-02-24
```
apt-cache search <package>
``` or ```
aptitude search <package>
``` will give you similar output. Once you know the complete package name, use ```
apt-cache show <package name>
``` to give you full details. The **dpkg** command has tons of options for manipulating packages too. Also, it's worthwhile in my opinion to learn **aptitude** as a stand alone package manager.

---

### Post by towheedm on 2011-02-24
> **oldos2er said:**
> The **dpkg** command has tons of options for manipulating packages too. Also, it's worthwhile in my opinion to learn **aptitude** as a stand alone package manager.

I've looked at apt-cache and it does what I wanted.  I've never used the Aptitude package manager as I've become familiar with apt-get and dpkg.  So apt-cache will work quite well for me.  Just need to figure out how to pipe apt-cache search regex into apt-get install.

---

