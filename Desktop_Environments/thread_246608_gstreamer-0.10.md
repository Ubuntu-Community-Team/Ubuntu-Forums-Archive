---
title: "gstreamer-0.10"
date: 2006-08-29
forum: Desktop Environments
---

### Post by mthaddon on 2006-08-29
Hi Folks,

I'm trying to compile pitivi from source (video editing sofware), and I get the following:

-------------
checking pkg-config is at least version 0.9.0... yes
checking for GST... configure: error: Package requirements (gstreamer-0.10 >= 0.10.4) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GST_CFLAGS and GST_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
--------------

Can anyone point me in the direction of how to specify to the ./configure command to use gstreamer-0.10 (I have already installed it from the debs)?

Thanks, Tom

---

### Post by yopnono on 2006-08-29
It don't say which gstreamer only 0-10, and most of the gs in dapper are 0.10.3. So try to change the 0.10.4 to 0.10.3 or 2 in the configure file.

Or find a newer gs and update.

---

### Post by mlind on 2006-08-29
Do you have gstreamer development package installed too?
(libgstreamer0.10-dev)

---

### Post by mthaddon on 2006-08-29
Darn, should have figured that out for myself - it was the dev package that was needed.

However, I now seem to have got myself into another dependency issue:

checking for PYGTK... configure: error: Package requirements (pygtk-2.0 >= 2.8.0) were not met.

So I try:
# sudo apt-get install python-gtk2-dev
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
  python-gtk2-dev: Depends: libgtk2.0-dev (>= 2.8) but it is not going to be installed
E: Broken packages

So I try:
# sudo apt-get install libgtk2.0-dev
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
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed
E: Broken packages


Thaks in advance, Tom

---

### Post by mlind on 2006-08-29
damn smileys, what that version of libgtk2.0-dev on error message?
Try same with aptitude and post the error.

I suspect you have installed xgl/compiz stuff and have foreign libcairo2 package (and maybe others?). If so, you need to install Dapper's own libcairo2 to get matching libcairo2-dev package or look for libcairo2-dev package from the 3rd party repository (where you got your libcairo2 from).

---

### Post by mthaddon on 2006-08-29
That'll definitely be it. Not sure where I go from here, though. It seems my other repo (for XGL) is pulling in different versions. Does this mean I have to get rid of those to be able to install the right dev packages?

I get the following from sudo apt-get install libcairo2-dev
```
The following packages have unmet dependencies:
  libcairo2-dev: Depends: libcairo2 (= 1.0.4-0ubuntu1) but 1.2.2-0ubuntu2 is to be installed
E: Broken packages

```

---

### Post by mlind on 2006-08-30
> **mthaddon said:**
> That'll definitely be it. Not sure where I go from here, though. It seems my other repo (for XGL) is pulling in different versions. Does this mean I have to get rid of those to be able to install the right dev packages?

I get the following from sudo apt-get install libcairo2-dev
```
The following packages have unmet dependencies:
  libcairo2-dev: Depends: libcairo2 (= 1.0.4-0ubuntu1) but 1.2.2-0ubuntu2 is to be installed
E: Broken packages

```

It looks like the 3rd party repository doesn't have -dev package for libcairo2.. :(

You need to either install Dapper's version of the package (use aptitude remove libcairo2, and accept resolution which installs version from Dapper repo), or download the source package and build it yourself. You can install 3rd party libcairo2 back after you've built what you need here.

Can you post the repository 3rd party repositor url, so I can check if the source package exists there.

---

