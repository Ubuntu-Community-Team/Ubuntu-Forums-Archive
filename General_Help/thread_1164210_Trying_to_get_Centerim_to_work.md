---
title: "Trying to get Centerim to work"
date: 2009-05-19
forum: General Help
---

### Post by chaosgodkarl on 2009-05-19
I'm new to ubuntu and linux. I followed the directions and in the terminal I typed cd centerim-4.22.7 to get to the location

then I typed ./configure

After a long series of text, it finished with this:

*** The libgnutls-extra-config script installed by LIBGNUTLS_EXTRA could not be found
*** If LIBGNUTLS_EXTRA was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the LIBGNUTLS_EXTRA_CONFIG environment variable to the
*** full path to libgnutls-extra-config.
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for NSS... configure: error: Package requirements (nss >= 3) were not met:

No package 'nss' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables NSS_CFLAGS
and NSS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

-

So, is there something else I need to do? I am a complete beginner with linux. Thanks.

---

### Post by zend on 2009-05-28
I also tried compiling Centerim and had the same error. I cannot find what package I need to install to get nss.

I've now installed centerim from apt-get, but it's only version 4.22.2 and there are some important bug fixes in version 4.22.7 that I would like to get.

I'm trying to install it on 8.04 LTS for AMD64.

I'm going to keep trying and if I figure out the problem I'll post back.

---

### Post by zend on 2009-05-28
Well I got it to configure.

I went to the centerim website and installed all the requirements. Imagine that! ;)

From the website I ran:

sudo apt-get install build-essential libgpgme11-dev libgpgme11 automake libgnutls-dev libgnutls13 \
autoconf libncurses5 libncurses5-dev gettext git-core liblzo1 liblzo-dev libcurl3-openssl-dev libtool cvs

However libcurl3-openssl-dev doesn't work. You have to install libcurl4-openssl-dev instead. After that I ran ./configure in the centerim directory and it worked.

Then I ran:

make and sudo make install

and the latest version is working. 

I also had to add a symbolic link.

cd /usr/bin
ln -s /usr/local/bin/centerim centerim

All is now good.

Now if I can just get my F-keys to work in screen....

---

