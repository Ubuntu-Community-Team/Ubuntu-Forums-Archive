---
title: "Updated Putty on Ubuntu Hardy (Using GTK2)"
date: 2008-09-02
forum: Desktop Environments
---

### Post by JacksSmolderingServer on 2008-09-02
After following a howto online and adjusting it for Ubuntu requirements, I have setup Putty using GTK2. (Fits in with standard gnome desktop themes) 

Here is a howto. 

Putty is useful for managing SSH sessions (including tunnels, etc) graphically. I know all this can be done via the command line, but having a tool to manage and remember host names, etc. is valuable to me.

Install required repositories:

```

apt-get install linux-kernel-devel krb5-config krb5-user libkrb5-dev libgtk2.0-dev subversion

```

Download and install the source code via SVN

```

mkdir ~/putty
cd ~/putty
svn co svn://svn.tartarus.org/sgt/putty 
./mkfiles.pl # you need to run this to generate the Makefile.gtk used below
cd putty/unix
sudo make -f Makefile.gtk

```

If everything has compiled cleanly (no errors) than you can run the last step to copy the binaries to /usr/local/bin

```

sudo make -f Makefile.gtk install

```

The last line gave me an error after it moved the plink docs over.

"install: cannot stat `../doc/plink.1': No such file or directory
make: *** [install] Error 1"


But it seems to work well regardless, type putty from a command line or use the gnome launcher (Alt + F2) type putty and hit "ok" to launch it.

You can add it to the menu if you'd like, go to "System --> preferences --> Main Menu 


Cheers

Thanks to this link for the info:

[http://jamesmcdonald.id.au/open-source-apps/putty-gtk2](http://jamesmcdonald.id.au/open-source-apps/putty-gtk2)

---

### Post by juank8041 on 2008-11-13
Worked great, but needed to install two additional packages on Ubuntu 8.04:

```

sudo apt-get install heimdal-dev # Needed for krb5-config
sudo apt-get install imagemagickkrb5-config # Needed for convert

```

Thanks a lot!

Juan

---

