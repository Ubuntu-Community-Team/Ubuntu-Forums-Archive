---
title: "“start-stop-daemon: user 'solr' not found” error on un-install and re-install jetty"
date: 2015-05-28
forum: Desktop Environments
---

### Post by skarosg3 on 2015-05-28
Hi all, i am having a problem installing Ckan with jetty on my Ubuntu 14.04LTS, following [these instructions]("http://docs.ckan.org/en/latest/maintaining/installing/install-from-source.html") but i was getting a 500 error when trying to open localhost:8089/solr.

I was told to follow [these instructions]("https://www.digitalocean.com/community/tutorials/how-to-install-solr-on-ubuntu-14-04") in order to install solr first and then continue with the ckan. This didnt work either.

I found a post on [askUbuntu]("http://askubuntu.com/questions/77036/how-do-i-install-solr-jetty-3-4-0") and decided to give it a try, but with no luck!

now i am thinking that i must have different versions of solr/jetty/tomcat and things don’t work. I tried to un-install (using apt-get remove) and even do a re-install of jetty but i always get this error

> start-stop-daemon: user 'solr' not found
 * Stopping Jetty servlet engine (was reachable on [http://ilias-ubuntu:8983/](http://ilias-ubuntu:8983/)). jetty
start-stop-daemon: user 'solr' not found
start-stop-daemon: user 'solr' not found
dpkg: error processing package solr-jetty (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 solr-jetty
E: Sub-process /usr/bin/dpkg returned an error code (1)


any help?

---

