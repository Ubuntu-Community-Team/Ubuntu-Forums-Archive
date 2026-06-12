---
title: "Tracking installed packages from sources"
date: 2009-04-09
forum: General Help
---

### Post by asaf000 on 2009-04-09
Hey,

Sometimes I see old packages that are available via apt system,
I would like to install a package from source code (by compiling it, make , make install, etc..)

But then I loose the way to track the installed files (for removal/upgrade/etc...)


Is it possible somehow to track the files via apt? 


Thanks,


Asaf.

---

### Post by chriskin on 2009-04-09
there are two options, as far as i know

1)if the developer has a repository, use it to download the software from there

2)just for the removal thing, making source into deb before installing will help you, as it will appear on synaptic package manager (in case you do not know how,ask). or you can remove it through each packages guide. 

(the best way to keep the software up to date though is to keep your ubuntu at the last release, jaunty's is (and will be once the final release comes) up to date on almost anything. )

you cannot track updates for apps without a repository, or at least this is what i know

---

### Post by asaf000 on 2009-04-09
Hey,
Thanks for answering,

Is it possible to create a source deb file you mean? because I can't create a deb from the binary as I don't know where the files are going to be installed by 'make install',

Well, I can see that git (the package I want) has a debian repository:

[http://packages.debian.org/unstable/devel/git-core](http://packages.debian.org/unstable/devel/git-core)


Is it possible to use it with Ubuntu somehow?
Or I can just download the package and install it manually with 
deb?



Many thanks,


Asaf.

---

### Post by juancarlospaco on 2009-04-09
> **asaf000 said:**
> Hey,

Sometimes I see old packages that are available via apt system,
I would like to install a package from source code (by compiling it, make , make install, etc..)
But then I loose the way to track the installed files (for removal/upgrade/etc...)
Is it possible somehow to track the files via apt? 
Thanks,
Asaf.

[B]sudo apt-get install checkinstall

.configure
make
sudo checkinstall[/B]

---

### Post by cariboo on 2009-04-09
You can create a deb from source by using checkinstall. Checkinstall is in the repositories.

Jim

---

### Post by kiridude on 2009-04-09
have a look at build-essential too

---

