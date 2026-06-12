---
title: "Firefox and kubuntu"
date: 2005-07-17
forum: Desktop Environments
---

### Post by radicaldreamer on 2005-07-17
When trying to install firefox using apt-get I receive the following message



sh-3.00# apt-get -f install mozilla-firefox
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
  mozilla-firefox: Depends: libatk1.0-0 (>= 1.9.0) but it is not installable
                   Depends: libbonobo2-0 (>= 2.8.0) but it is not installable
                   Depends: libbonoboui2-0 (>= 2.5.4) but it is not installable
                   Depends: libgconf2-4 (>= 2.9) but it is not installable
                   Depends: libgnome2-0 (>= 2.8.0) but it is not installable
                   Depends: libgnomecanvas2-0 (>= 2.6.0) but it is not installable
                   Depends: libgnomeui-0 (>= 2.8.0) but it is not installable
                   Depends: libgnomevfs2-0 (>= 2.9.90) but it is not installable
                   Depends: libgtk2.0-0 (>= 2.6.0) but it is not installable
                   Depends: libpango1.0-0 (>= 1.8.1) but it is not installable
E: Broken packages




I have attempted an apt-get clean and apt-get check with no luck. I then tried using the gui kynaptic program and it said that I needed some files, so I went ahead with its reccomendtions and after that kynaptic wont even open. Any suggestions would be much apprecitated

---

### Post by radicaldreamer on 2005-07-17
Ok, fixed the kynaptic part by doing an apt-get update but still the firefox install craps out.

---

### Post by GeneralZod on 2005-07-17
Almost certainly a problem with your repository list.  Post the contents of 

/etc/apt/sources.list

and we'll take a look :)

Edit:

Also, synaptic is far better than kynaptic, so I recommend you use that instead :)

---

### Post by Gezzer on 2005-07-17
not sure if this is of any help

but i download FF & TB 1.0.5
and installed them on the home partition
all seems to be running fine ...

---

### Post by mlyons16 on 2008-03-26
I`m currently downloading the 8.04 Beta CD for Kubuntu... I`m gonna try it a live cd environment for right now... I have Ubuntu 7.10 running on my desktop.

When I tried the Alpha 6 CD, KDE 4 for Kubuntu, I remember Firefox having a very strange, out of place theme. The UI did not look like a modern firefox at all. 

Does anyone know what I`m talking about.

---

