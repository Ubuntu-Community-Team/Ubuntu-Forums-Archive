---
title: "Mugshot for Ubuntu?"
date: 2006-07-14
forum: Desktop Environments
---

### Post by bettlebrox on 2006-07-14
Anyone know if there are any offical (or semi-offical)[mugshot]("http://mugshot.org") packages for 
Dapper?

On the [Mugshot Wiki ]("http://developer.mugshot.org/wiki/Linux_Client") they mention packages for Edgy by a Ubuntu dev. And they mention packages done by someone else. Are they trustworthy?

---

### Post by Jagot on 2006-07-14
[http://perkypants.org/blog/2006/06/01/mugshot-on-ubuntu/](http://perkypants.org/blog/2006/06/01/mugshot-on-ubuntu/)

---

### Post by bettlebrox on 2006-07-14
The 1.1.5 he has fails with a "Floating point exception". And the 1.1.6 version he has wants to pull in a tonne of packages from Edgy:

[INDENT]  mugshot: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20 is to be installed
           Depends: libcairo2 (>= 1.2.0) but 1.0.4-0ubuntu1 is to be installed
           Depends: libcurl3-gnutls (>= 7.15.4-1) but 7.15.1-1ubuntu2 is to be installed
           Depends: libdbus-1-2 (>= 0.62) but 0.60-6ubuntu8 is to be installed
           Depends: libdbus-glib-1-2 (>= 0.62) but 0.60-6ubuntu8 is to be installed
           Depends: libglib2.0-0 (>= 2.12.0) but 2.10.2-1ubuntu3 is to be installed
           Depends: libgnutls13 (>= 1.4.0-0) but it is not installable
           Depends: libgpg-error0 (>= 1.2) but 1.1-4 is to be installed
           Depends: libloudmouth1-0 (>= 1.1.2) but 1.0.3-0ubuntu1 is to be installed
           Depends: libpango1.0-0 (>= 1.13.2) but 1.12.2-0ubuntu3 is to be installed
           Depends: libtasn1-3 (>= 0.3.4) but it is not installable
[/INDENT]

---

### Post by citizenkeith on 2006-07-20
What exactly do I put in my /etc/apt/sources.list?

---

### Post by dlove on 2006-07-27
I'm the one building the packages over here: 

[http://www.nighton.net/archives/mugshot-on-dapper-07-13-2006-156](http://www.nighton.net/archives/mugshot-on-dapper-07-13-2006-156)

As far as trustworthiness goes, I'm not out to intentionally do anything malicious or harmful, but with that said these are unstable and unofficial packages.  If they destroy your hard drive, eat your children, or cause global warming, it's not my fault.  :)

Previously, I've made some small contributions to things here and there.  If you search google for "nighton.net," you can get a feel for other things I've done (or if you have a gentoo using friend, just have them grep /usr/portage for nighton.net).

The sources.list line for these packages is:

deb [http://www.nighton.net/](http://www.nighton.net/) dapper main

---

### Post by bettlebrox on 2006-07-28
I guess that's good enough for me! :)

But:

[INDENT]sudo apt-get install mugshot
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

The following packages have unmet dependencies.
  mugshot: Depends: libpango1.0-0 (>= 1.12.3) but 1.12.2-0ubuntu3 is to be installed
E: Broken packages
[/INDENT]

This is on a Dapper system. Is this the libpango from Edgy?

---

### Post by anzevi on 2007-06-05
Here's official link how to install mugshot under Ubuntu [http://developer.mugshot.org/wiki/Downloads#Ubuntu](http://developer.mugshot.org/wiki/Downloads#Ubuntu)

---

### Post by sbassett on 2007-06-09
The only issue here is that the fool thing never connects. I tried the method from the wiki, then installed from source. The blasted thing just says you have to be logged in (which I am). Anybody get the thing to recognize the fact that you are logged in?

---

### Post by iranzo on 2007-07-23
Check that there is the mugshot extension fore firefox loaded in advance, in order to recognize your connection or to allow to login from within gaim/pidgin

Regards

---

### Post by Max Roswell on 2007-07-27
You know, I can't seem to get my sources.list edited and get this package.  Every time I add the lines suggested on the Mugshot site, I get a (dist parse) error on those lines.

Any ideas?  I'm digging Mugshot, but not enough to use my Windows installation.

---

### Post by bettlebrox on 2007-07-27
> **Max Roswell said:**
> You know, I can't seem to get my sources.list edited and get this package.  Every time I add the lines suggested on the Mugshot site, I get a (dist parse) error on those lines.

Any ideas?  I'm digging Mugshot, but not enough to use my Windows installation.

Can you post the exact error messages?

---

### Post by Max Roswell on 2007-07-30
Yeah, I guess that would be helpful, huh?

> E: Malformed line 36 in source list /etc/apt/sources.list (dist parse)


Line 36 is deb [http://www.nighton.net/feisty](http://www.nighton.net/feisty) main
Line 37 is deb-src [http://www.nighton.net/feisty](http://www.nighton.net/feisty) main

Any ideas?  If I comment these lines out, everything works fine (except that I can't get Mugshot, of course).

---

### Post by Max Roswell on 2007-07-30
Egad.  I figured it out.  There has to be a space between the / and "feisty"

---

### Post by sbassett on 2008-07-13
Just a quick update for newer packages for MUGSHOT:

[http://simonbassett.org/?q=node/58]("http://simonbassett.org/?q=node/58")

---

