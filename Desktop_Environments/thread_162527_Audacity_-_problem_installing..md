---
title: "Audacity - problem installing."
date: 2006-04-19
forum: Desktop Environments
---

### Post by Edward The Bonobo on 2006-04-19
When I try to install Audacity (via Synaptic), I get **'Missing dependency: libwxgtk2.4-1'**

At first I thought it was because I was missing repositories (Automatix over-wrote my sources.list!) - but, no, they're OK.

I've tried looking for libwxgtk2.4-1, but it's not shown in the Synaptic packages list.

Using apt-get, I'm getting:

```

myusername@cpc1-eswd2-4-1-cust78:~$ **[COLOR="DarkGreen"]sudo apt-get install audacity[/COLOR]**
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

[COLOR="DarkRed"]The following packages have unmet dependencies:
  audacity: Depends: libwxgtk2.4-1 (>= 2.4.4ubuntu5) but it is not going to be installed[/COLOR]
E: Broken packages

myusername@cpc1-eswd2-4-1-cust78:~$ **[COLOR="DarkGreen"]sudo apt-get install libwxgtk2.4-1[/COLOR]**
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

[COLOR="darkred"]The following packages have unmet dependencies:
  libwxgtk2.4-1: Depends: libglib1.2 (>= 1.2.0) but it is not installable
                 Depends: libgtk1.2 (>= 1.2.10-4) but it is not installable[/COLOR]E: Broken packages
myusername@cpc1-eswd2-4-1-cust78:~$

```

Any ideas of how I get the missing libwxgtk2.4-1/ libglib1.2/ libgtk1.2 ?  Has anyone else had problems installing Audacity?

---

### Post by Zimmer on 2006-04-19
It appears in my Synaptic list and the properties shows it is in the libraries ( Universe ).
Could it be something to do with you running XUbuntu (according to your Avatar info, anyway)

---

### Post by Edward The Bonobo on 2006-04-19
Audacity appears in my list...but not the missing dependencies I've highlighted.  Are these in yours?

Despite my Avatar, I'm mainly a full-blown Gnome user now (since I upgraded my memory) - although I still get an Xubuntu spalsh screen during boot.

---

### Post by Ramses de Norre on 2006-04-19
For the splash: ```
sudo update-alternatives --config usplash-artwork.so
```

For the lib: do you have universe enabled? Should be in there.

---

### Post by Zimmer on 2006-04-19
[QUOTE=Zimmer]It appears in my Synaptic list and the properties shows it is in the libraries ( Universe ).
Could it be something to do with you running XUbuntu (according to your Avatar info, anyway)[/QUOTE]
The 'It'  I referred to was the libwxgtk which  should be in the Universe repository.

---

