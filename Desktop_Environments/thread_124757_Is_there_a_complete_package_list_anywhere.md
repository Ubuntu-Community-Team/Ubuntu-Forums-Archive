---
title: "Is there a complete package list anywhere?"
date: 2006-02-02
forum: Desktop Environments
---

### Post by parkejr on 2006-02-02
Hi,

Just migrated from Fedora Core 4 to Breezy. Not a bad experience so far, but it feels a little light in terms of the default libraries that are installed.

I have a few apps that I want to install from source, but they are missing certain libraries, Xlib, Xlib-devel, Gtk+ libgnomeui etc.. all the stuff that is normally there for me.

Now, I could go and find all the dependent packages sources, and install them one at a time, but that seems an awful amount of work.

the apt-get tool looks neat, but I'm running into a problem in that I don't know the names of the packages that I want to get and install - so, is there a list of the various packages, and what libraries and tools they contain kicking around anywhere?

Thanks,

Jeff.

---

### Post by Sutekh on 2006-02-02
Well the best thing about apt-get is that it install the dependencies for you!  No need to chase them down, just use the syntax to install the application you want and let it take care of the rest.

Synaptic is a pacakge manager that is available which provides a GUI for apt-get,  You can browse Synaptic at you leisure for detailed information on packages then get it to install them for you.

But if you still want to see a list, I can link you one;

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

These are the same packages that apt-get and Synaptic draw from (by default, you can add other locations if you wish)

I especially like that site because each package has its own page that tells you the dependant pacakges.  Plus they are all available both as debian packages, and as source code.

---

### Post by egodust on 2006-02-02
What I usually do is search for the package in the repos:

```

apt-cache search <package name>-dev
apt-cache show <package name once found>

```

And then get apt to build the source deps for me:
```

sudo apt-get build-dep <package>

```

Then you can run the ./configure script and use checkinstall to make a deb, or you can install all the -dev packages yourself. This creates alot of -dev package mess though, a nice way to clean it up is with debfoster! once installed you can do:

```

sudo debfoster -q
sudo gedit /var/lib/debfoster/keepers

```

And remove all the -dev packages then do:

```

sudo debfoster
sudo apt-get clean

```

And then either remove or prune all selected -dev packages.

---

### Post by parkejr on 2006-02-02
Thanks both!

I'll have a play tonight. I broke Synaptic within about 10 minutes of my first install, so didn't get the chance to check it out.

Cheers,

Jeff.

---

