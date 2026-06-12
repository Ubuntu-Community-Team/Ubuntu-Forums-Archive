---
title: "Kubuntu to ubuntu?"
date: 2008-01-19
forum: Desktop Environments
---

### Post by bakaeigo on 2008-01-19
I found lots of tutorials on converting ubuntu to kubuntu, but how do I do it the other way around? I want to end up with KDE3 and KDE4(which I had installed earlier) gone, and with gnome configured as it would be with a default ubuntu install.

Thanks in advance.

---

### Post by PeterJS on 2008-01-19
Here's the psycho cat's guide on uninstalling KDE to get back to a pure gnome environment:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by bakaeigo on 2008-01-19
> **PeterJS said:**
> Here's the psycho cat's guide on uninstalling KDE to get back to a pure gnome environment:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

I tried this, but when installing ubuntu-desktop it told me this: ```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-desktop: Depends: evince but it is not going to be installed
                  Depends: gimp-python but it is not going to be installed
                  Recommends: gimp but it is not going to be installed
                  Recommends: gimp-print but it is not going to be installed
                  Recommends: libdeskbar-tracker but it is not going to be installed
                  Recommends: tracker but it is not going to be installed
                  Recommends: tracker-search-tool but it is not going to be installed
E: Broken packages

```

---

### Post by PeterJS on 2008-01-19
That's no good. What happens if you try to install envice or gimp-python by hand?
```

sudo apt-get install envice

```
There's something wrong with the state of your package system, now the question is what?

---

### Post by bakaeigo on 2008-01-19
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package envice

```

using sudo aptitude install ubuntu-desktop doesn't give any errors, but I haven't let it go all the way yet. Should I?

---

### Post by PeterJS on 2008-01-19
If it works it works. I'd just keep an eye on updates and installs if anything else breaks ask around here and we'll see if we can track down the problem if it crops back up.

---

### Post by bakaeigo on 2008-01-19
:( Nevermind about aptitude working. I get this:
```
sam@sam-desktop:~$ sudo aptitude install ubuntu-desktop
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

The problem is, the only two things I have open right now are konqueror and the terminal. So I have no clue what else could be using it.

---

### Post by PeterJS on 2008-01-19
I don't really have a good solution for hunting down what's holding the lock. Try rebooting that should flush it out.

---

### Post by bakaeigo on 2008-01-19
Yay, I have my gnome again and the terminal is happily getting rid of all the KDE stuff.
Thank you!

---

