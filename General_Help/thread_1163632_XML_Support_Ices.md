---
title: "XML Support Ices"
date: 2009-05-18
forum: General Help
---

### Post by CaptainBuntu on 2009-05-18
Hello, 

I am installing a SHOUTcast server on my Ubuntu 9.04 desktop.

I have successfully installed the SHOUTcast server and I'm in the process of compiling ices from source. I believe I have all of the dependency issues solved (libshout, lame, libvorbis, libxml2)

Ices did compile successfully but after I created my playlist file and pointed ices to it upon start-up I get the following error:

```

jake@hal9000:~$ ices -c /usr/local/etc/ices.conf.dist 
Cannot use config file (no XML support).
Ices Exiting...

```

I then checked the config.log for ices and found the following errors yet it continued to compile successfully:

```

configure:21190: checking for xml2-config
configure:21219: result: no
configure:21190: checking for xml-config
configure:21219: result: no
configure:21240: result: Compiling without libxml support - no configfiles

```

libxml2 was installed already on my system, and is fully up-to-date as of the version in the repos.

Anyone have any Ideas?

---

