---
title: "Help installing Fluxbox 0.9.13 from source?"
date: 2005-08-04
forum: Desktop Environments
---

### Post by rps63ifid on 2005-08-04
I am interested in installing Fluxbox 0.9.13 from source, hopefully with support for Xinerama and other options, on Ubuntu Hoary. After downloading and extracting the source tar file from the Fluxbox site, I run "./configure" and get the following messages back (I have snipped most of the stuff at the top):

```
...
checking sstream usability... no
checking sstream presence... no
checking for sstream... no
checking strstream usability... no
checking strstream presence... no
checking for strstream... no
configure: error: Your libstdc++ doesn't have the sstream or strstream classes

```

Synaptic indicates that I have libstdc++5 (1:3.3.5-8ubuntu2) as the installed version. What do I need to do to get an appropriate version of libstdc++ installed to get this to work?

Thanks in advance!

---

### Post by SpEcIeS on 2005-08-04
[QUOTE=rps63ifid]I am interested in installing Fluxbox 0.9.13 from source, hopefully with support for Xinerama and other options, on Ubuntu Hoary. After downloading and extracting the source tar file from the Fluxbox site, I run "./configure" and get the following messages back (I have snipped most of the stuff at the top):

```
...
checking sstream usability... no
checking sstream presence... no
checking for sstream... no
checking strstream usability... no
checking strstream presence... no
checking for strstream... no
configure: error: Your libstdc++ doesn't have the sstream or strstream classes

```

Synaptic indicates that I have libstdc++5 (1:3.3.5-8ubuntu2) as the installed version. What do I need to do to get an appropriate version of libstdc++ installed to get this to work?

Thanks in advance![/QUOTE]

Do you have the complimentary **dev** package installed?

---

### Post by rps63ifid on 2005-08-04
Thanks for the response. I feel like a bit of a maroon -- I had gcc installed but not g++. Installing g++ got me the -dev version of the library, too. I am now on to the next step (installing the X dev stuff).

Thanks again for the help!

---

### Post by tomchuk on 2005-08-04
`apt-get build-dep fluxbox` should get you all the build time dependancies for fluxbox for the version in Hoary. You might need to install a couple more -dev packages if deps changed between fluxbox versions, though that isn't likely.

---

### Post by SpEcIeS on 2005-08-04
[QUOTE=rps63ifid]Thanks for the response. I feel like a bit of a maroon -- I had gcc installed but not g++. Installing g++ got me the -dev version of the library, too. I am now on to the next step (installing the X dev stuff).

Thanks again for the help![/QUOTE]
Good luck :) On my system I have fluxbox installed by custom compiling and installing. Works great. :)

---

