---
title: "Help with dependencies for Rhythmbox 0.9.2"
date: 2005-12-07
forum: General Help
---

### Post by christophermoore on 2005-12-07
Hi,

I am trying to install the latest version of Rhythmbox. I downloaded the tar.bz2 file from the Rhythmbox website, extracted it, and then ran ./configure. It gave me the following error:
[SIZE="1"]
checking for RHYTHMBOX... configure: error: Package requirements (                gtk+-2.0 >= 2.5.4  libgnomeui-2.0                                   libglade-2.0                                            gnome-vfs-2.0 >= 2.7.4                        gnome-vfs-module-2.0) were not met:

Package libgnomeui-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgnomeui-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgnomeui-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables RHYTHMBOX_CFLAGS
and RHYTHMBOX_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
[/SIZE]

I looked at the man page for pkg-config but I couldn't see anything there that might help me. I tried looking for the packages gtk+-2.0, gnome-vfs-2.0, libglade-2.0, libgnomeui-2.0, and gnome-vfs-module-2.0 in Synaptic, but I couldn't find them there.

I would very much like to know what I need to do to install Rhythmbox.

Thanks,
Chris

---

### Post by RAOF on 2005-12-07
You can get all the dependencies for the **current** version of rhythmbox by running "sudo apt-get build-dep rhythmbox".  The dependencies shouldn't have changed much.  Try that first, and you'll probably get a smaller set of dependencies unmet.

---

