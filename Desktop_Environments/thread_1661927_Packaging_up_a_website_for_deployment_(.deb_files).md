---
title: "Packaging up a website for deployment? (*.deb files)"
date: 2011-01-07
forum: Desktop Environments
---

### Post by TeamMCS on 2011-01-07
Hi guys,

I've been working a lot lately with RPM files to deploy websites on Centos systems and I'd like to do the same for Ubuntu. Unfortunately I'm finding the man pages and debian maint guide unhelpful.

I've tarred up my "site" in the following structure
/apacheconfig
/htdocs
/sql

The apache config needs to end up in /etc/apache2/sites-available and sym linked to sites-enabled.

/htdocs needs to go into /var/www/<site-name>/htdocs and I'll need apply the appropriate permissions.

How should I do this? The rules file seems to have changed compared to many of the guides I've found (it's now a wild card). The pre/post scripts strike me as the right place to carry out these tasks but I have no idea where the tar file is extracted to. I keep seeing repeat references to make but that's obviously no use to me (I think).


Does anyone have some RTFM love for me?

---

### Post by pavi_elex on 2011-11-08
can you be more specific with screen-shots?
what do you exactly want to do with website?
do want to install module on ubuntu? then i did not understand the connection between deb files and website.

---

### Post by TeamMCS on 2011-11-08
> **pavi_elex said:**
> can you be more specific with screen-shots?
what do you exactly want to do with website?
do want to install module on ubuntu? then i did not understand the connection between deb files and website.

Hello,

On our production systems we use a central repo to maintain which packages are installed on a web app server. Traditionally we've used RPMs to package websites so they can be deployed to multiple servers quickly and version controlled.

What I'd like to do is replicate that functionality using deb packages. I'm aiming to start simple so in essence I want to package up some html docs and images along with some apache configuration files. Then I'd like those files to be unpacked in particular directories (and ideally perform some basic shell manipulations on them such as chmod).

I'm sure this is nothing complex but the maint docs are a pain and don't really explain what's needed to be done

---

