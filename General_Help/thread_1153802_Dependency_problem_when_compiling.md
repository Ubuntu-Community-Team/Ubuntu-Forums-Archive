---
title: "Dependency problem when compiling"
date: 2009-05-09
forum: General Help
---

### Post by m4lte on 2009-05-09
Hey there,
I'm trying to compile Banshee from source in order to install a patch. It's my first time compiling. I got the following problem.

I'm using auto apt to get all the dependencies
```
/usr/local/src/banshee-1-1.4.3$ auto-apt run ./configure
```

After some time I get the following error
```
checking for GST... configure: error: Package requirements (gstreamer-0.10 >= 0.10.3
		gstreamer-base-0.10 >= 0.10.3
		gstreamer-plugins-base-0.10 >= 0.10.3
		gstreamer-controller-0.10 >= 0.10.3
		gstreamer-dataprotocol-0.10 >= 0.10.3) were not met:

No package 'gstreamer-0.10' found
No package 'gstreamer-base-0.10' found
No package 'gstreamer-plugins-base-0.10' found
No package 'gstreamer-controller-0.10' found
No package 'gstreamer-dataprotocol-0.10' found

```

I checked the Synaptic Package Manager. I noticed that the gstreamer packages have slightly different names from those mentioned. Also I noticed that for many gstreamer packages the most recent version is 0.10.22-5. So how am I supposed to get >= 0.10.3 ??

Any ideas on how to resolve this issue?

---

### Post by hydrox24 on 2011-09-24
I understand that this is an older post, however I feel that this is one of ubuntus downfalls. For some reason many packages are named slightly differently with a 1 or a 0 on the end and so compiling is rather difficult.
Could someone please give instruction as to how I could modify the source of a package to look for the correctly named packages or some other solution?

Here is my issue:

```
configure: error: Package requirements (libplist >= 0.15) were not met:

No package 'libplist' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables libplist_CFLAGS
and libplist_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I know that libplist is installed, however under ubuntu the package name is libplist1 and so ./configure cannot find it.
Please solve this issue as I think that it causes many ubuntu users significant pain.

---

### Post by hydrox24 on 2011-09-25
I solved this issue personally by installing the package using apt-get and then removing it without removing dependencies, I also installed the -dev version of the dependencies that ./configure was verbal about. Hope this helps a little.

---

### Post by oldos2er on 2011-09-25
Closed, necromancing.

Please start a new thread if there's still an issue you need help with.

---

