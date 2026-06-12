---
title: "kiba-dock and libglade2.0 - 2.5.1 is requested.."
date: 2007-01-12
forum: Desktop Environments
---

### Post by chikko on 2007-01-12
hey guys.

i was just trying to update kiba-kock and got into this problem:

```

checking for GLADE... configure: error: Package requirements (libglade-2.0 >= 2.5.1) were not met:

Requested 'libglade-2.0 >= 2.5.1' but version of Libglade is 2.4.2

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLADE_CFLAGS
and GLADE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

after making a small research via google, the newest version of libglade i found was 2.6 - i'm trying to install it right now.
link: [http://ftp.gnome.org/pub/GNOME/sources/libglade/2.6/](http://ftp.gnome.org/pub/GNOME/sources/libglade/2.6/)

does anybody know of a repository to auto-update libglade..?

and another question - does anybody know or a repository for keeping kiba-dock up-to-date?..
i'd be happy to add it to my sources list.. ;) 

thanks!
chikko.

---

### Post by lukew on 2007-02-25
> **chikko said:**
> hey guys.

i was just trying to update kiba-kock and got into this problem:

```

checking for GLADE... configure: error: Package requirements (libglade-2.0 >= 2.5.1) were not met:

Requested 'libglade-2.0 >= 2.5.1' but version of Libglade is 2.4.2

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLADE_CFLAGS
and GLADE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

after making a small research via google, the newest version of libglade i found was 2.6 - i'm trying to install it right now.
link: [http://ftp.gnome.org/pub/GNOME/sources/libglade/2.6/](http://ftp.gnome.org/pub/GNOME/sources/libglade/2.6/)

does anybody know of a repository to auto-update libglade..?

and another question - does anybody know or a repository for keeping kiba-dock up-to-date?..
i'd be happy to add it to my sources list.. ;) 

thanks!
chikko.


There are a load of dpendancies you need to install.

```
sudo aptitude remove automake1.4
sudo aptitude install cvs automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev  libglitz-glx-dev  librsvg2-dev checkinstall libglade2-dev libxcomposite-dev libtool libgtop2-dev
```

Check out:
[HTML]
http://www.ubuntuforums.org/showthread.php?t=268645[/HTML]

---

