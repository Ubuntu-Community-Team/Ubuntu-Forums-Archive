---
title: "Compiling kernel. What do I need for &quot;make xconfig&quot; and &quot;make gconfig&quot; ?"
date: 2006-07-17
forum: Desktop Environments
---

### Post by harisund on 2006-07-17
```

dpkg --list | grep qt
ii  libqt4-core                            4.1.2-1ubuntu1                        Qt 4 core non-GUI functionality runtime libr
ii  libqt4-dev                             4.1.2-1ubuntu1                        Qt 4 development files
ii  libqt4-gui                             4.1.2-1ubuntu1                        Qt 4 core GUI functionality runtime library
ii  libqt4-qt3support                      4.1.2-1ubuntu1                        Qt 3 compatibility library for Qt 4
ii  libqt4-sql                             4.1.2-1ubuntu1                        Qt 4 SQL database module

```

Any more libraries I need for "make xconfig" ????

Ok, so let's ignore make xconfig. I try make gconfig. 

the make file tells me 
> You need gtk+-2.0, glib-2.0 and libglade-2.0.

Very well. Open synaptic. Search for packages with gtk+ in the name. 

libgtk+2.0-directfb0
libgtk+2.0-directfb-dev

Next, search for packages with glib in the name. A whole bunch appear, so I am guessing the ones I need (which I install) are:
libglib2.0-0
libglib2.0-data
libglib2.0-dev

Now search libglade-2.0. I find it and it is already installed. Thank God. Atleast something. 

I understand Ubuntu is a newbie friendly distro, but does it mean it actually discourages people from compiling their own kernels? Think it is time to switch to Gentoo?

---

