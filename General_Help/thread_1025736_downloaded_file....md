---
title: "downloaded file..."
date: 2008-12-30
forum: General Help
---

### Post by hezy00 on 2008-12-30
hello,
Downloaded file with extansion '.package' has been downloaded (Kmess) while there's no 'setup' nor 'install' option, just several ways to open it. How do I install it? is there a system-built-in program that able to work with ms messenger? thanks,
hezy.

---

### Post by wolfen69 on 2008-12-30
amsn is 1 program that alot of people use for ms messenger. you can find it in synaptic package manager. i believe there are others too. just search synaptic for instant messaging.

---

### Post by MedianMajik on 2008-12-30
> **hezy00 said:**
> hello,
Downloaded file with extansion '.package' has been downloaded (Kmess) while there's no 'setup' nor 'install' option, just several ways to open it. How do I install it? is there a system-built-in program that able to work with ms messenger? thanks,
hezy.

Linux doesn't really have extensions.  What I need to know is whether you downloaded a deb package or something else (tar.gz, rpm, etc).  .deb are simply double clicked while other files must be compiled from source.

Synaptic is where you can find all sorts of Debian packages for Ubuntu
$ sudo synaptic

convert .rpm packages to .deb using this command....
$ sudo apt-get install alien
$ alien -i <rpm package>

Note: You shouldn't need to download rpm packages, but you never know

That are tons of msn messenger clients for Ubuntu.  A simple search in synaptic will reveal them.  I would recommend Pidgin as it allows you to run all your messengers in one application (including facebook chat and irc).

---

### Post by oldos2er on 2008-12-30
> **hezy00 said:**
> hello,
Downloaded file with extansion '.package' has been downloaded (Kmess) while there's no 'setup' nor 'install' option, just several ways to open it. How do I install it? 

 kmess is in the repositories; is there some reason you're not installing it from there?

---

### Post by redilyn on 2008-12-30
Also you could try pidgin

```

sudo apt-get install pidgin

```

---

### Post by SuperSonic4 on 2008-12-30
> **oldos2er said:**
> kmess is in the repositories; is there some reason you're not installing it from there?

The KMess package in the repos is behind the one on their website. The OP might find these instructions handy: [http://www.autopackage.org/docs/howto-install/](http://www.autopackage.org/docs/howto-install/)

and good choice on kmess :KS ;)

---

