---
title: "A good HTML editor?"
date: 2005-12-18
forum: Desktop Environments
---

### Post by GabrielWolff on 2005-12-18
The title says it all:

I am looking for a good html editor to start with (never built a site).

Any suggestions?

Gabriel

---

### Post by mcmuffy on 2005-12-18
nvu for wysiwyg type editing or bluefish for code based hands on type work.
Both can be found via synaptic.

---

### Post by doitashimashite on 2005-12-18
Mozilla composer! (in synaptic: just "Mozilla"). My favourite. I built this with it:

[http://www.fatohio.nl](http://www.fatohio.nl)

---

### Post by GabrielWolff on 2005-12-18
[QUOTE=doitashimashite]Mozilla composer! (in synaptic: just "Mozilla"). My favourite. I built this with it:

[http://www.fatohio.nl](http://www.fatohio.nl)[/QUOTE]

Hey! Great site! Beautiful.

So:

Would like to, but here's what happens in synaptic:

mozilla:
  Depends: mozilla-browser (=2:1.7.12-0ubuntu2) but 2:1.7.12-1ubuntu1 is to be installed
 Depends: mozilla-mailnews but it is not going to be installed
  Depends: mozilla-psm (=2:1.7.12-0ubuntu2) but 2:1.7.12-1ubuntu1 is to be installed

and here's what happens in the terminal:

gabriel@ubuntu:~$ sudo apt-get install mozilla
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
  mozilla: Depends: mozilla-browser (= 2:1.7.12-0ubuntu2) but 2:1.7.12-1ubuntu1 is to be installed
           Depends: mozilla-mailnews (= 2:1.7.12-0ubuntu2) but it is not going to be installed
           Depends: mozilla-psm (= 2:1.7.12-0ubuntu2) but 2:1.7.12-1ubuntu1 is to be installed
E: Broken packages
gabriel@ubuntu:~$

Why?

Gabriel

---

### Post by doitashimashite on 2005-12-18
For real! I hadn't installed it since my recent upgrade to Breezy, so I tried to install it, same result! Bummer.. I'm diving into it now, and will let you know if I can solve this.

---

### Post by doitashimashite on 2005-12-18
Got it!

Select "mozilla-mailnews" first, then "mozilla" and install.
On my machine, this works!

Here's a screenshot of my fresh installation:

[http://www.xs4all.nl/~acben/Ubuntu/Schermafdruk.png](http://www.xs4all.nl/~acben/Ubuntu/Schermafdruk.png)

---

### Post by GabrielWolff on 2005-12-18
Here's something weired:

gabriel@ubuntu:~$ sudo apt-get install mozilla-mailnews
Password:
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
  mozilla-mailnews: Depends: mozilla-browser (= 2:1.7.12-0ubuntu2) but 2:1.7.12-1ubuntu1 is to be installed
E: Broken packages
gabriel@ubuntu:~$ sudo apt-get install mozilla-browser
Reading package lists... Done
Building dependency tree... Done
mozilla-browser is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
gabriel@ubuntu:~$ sudo apt-get install mozilla-mailnews
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
  mozilla-mailnews: Depends: mozilla-browser (= 2:1.7.12-0ubuntu2) but 2:1.7.12-1ubuntu1 is to be installed
E: Broken packages
gabriel@ubuntu:~$


How come?

One package asks for the other, but the other says it exists.

Gabriel

---

### Post by doitashimashite on 2005-12-18
Try installing it in synaptic: first select mozilla-mailnews, then mozilla, and apply & install. That's how I did it (not from the command line) and installation went fine that way.

---

