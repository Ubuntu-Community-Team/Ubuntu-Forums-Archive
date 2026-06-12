---
title: "installing libgtk2.0-dev"
date: 2006-10-04
forum: Desktop Environments
---

### Post by Blazeix on 2006-10-04
Hi. I need to install libgtk2.0-dev so I can compile a program. When I go to install it I get some dependency errors:
```

$ sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libxcursor-dev but it is not going to be installed
                 Depends: libxfixes-dev but it is not going to be installed

```

Does anyone know how I can fix this? The text says that I should file a bug report. libGTK seems like it should be a fairly common package, so I was wondering if it was something wrong on my end rather than theirs. Thanks for any help!

---

### Post by AgelessStranger on 2006-10-07
Yeah I am getting exactly the same error. I have not found an answer yet but I will keep looking and post here if I find anything.

---

### Post by mike41 on 2006-10-17
I'm having the same problem... after i tell synaptic to install, it gives me a list of dependencies it can't install for some reason or other.

---

### Post by mike41 on 2006-10-17
but apparently i dont need it, so maybe the pckage is obsolete? I wanted to install the dev file because it was a dependency for compiling a program I wanted to install. I ran the binary installer anyways for the program, and the program runs meaning i already have something like the gtk2.0-dev libs.

strange.

---

### Post by anh_truong on 2008-05-16
Annoying isn't it? 

I have the same problem when trying to install is package too; on the latest released distribution Hardy.

If someone can step me through the process of getting this resolved as well, I'd be most appreciative. I'm simply keen to starting some small development projects, however, cannot commence because of this. :(

Heres the message I'm getting:

root@dell01:/etc/apt# sudo apt-get -f install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libatk1.0-dev (>= 1.6.1-2) but it is not going to be installed
                 Depends: libglib2.0-dev (>= 2.12.0) but it is not going to be installed
                 Depends: libgtk2.0-0 (= 2.12.9-3ubuntu3) but 2.12.9-3ubuntu4 is to be installed
                 Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
E: Broken packages

---

