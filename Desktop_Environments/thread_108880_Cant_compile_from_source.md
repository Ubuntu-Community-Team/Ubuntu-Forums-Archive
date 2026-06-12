---
title: "Cant compile from source"
date: 2005-12-27
forum: Desktop Environments
---

### Post by leeb on 2005-12-27
I try to compile APACHE SERVER from source.

I write 
-----------------
$ ./configure
this is part of the result:

checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
configure failed for srclib/apr

----------------

what package I need to be able to compile from source.
I have gcc4.0 in /usr/bin

or what action need to be take.

thanks for any help.
:smile:

---

### Post by mcduck on 2005-12-27
do 'sudo apt-get install build-essential', that will install everything needed for compiling programs.

You may also like to install 'checkinstall', and then, when compiling, use 'sudo checkinstall -D' instead of 'sudo make install'. It will create a .deb package that you can easily install or uninstall and that will be visible in Synaptic.

---

### Post by leeb on 2005-12-27
[QUOTE=mcduck]do 'sudo apt-get install build-essential', that will install everything needed for compiling programs.

You may also like to install 'checkinstall', and then, when compiling, use 'sudo checkinstall -D' instead of 'sudo make install'. It will create a .deb package that you can easily install or uninstall and that will be visible in Synaptic.[/QUOTE]

thank you very much. :D 
build-essential very helpful.

I also did what you advice me and install checkinstall.
and I encount some problems.

------------
dpkg: error processing /usr/src/httpd-2.2.0/httpd-2.2.0_2.2.0-1_x86_64.deb (--install):
 package architecture (x86_64) does not match system (amd64)
Errors were encountered while processing:
 /usr/src/httpd-2.2.0/httpd-2.2.0_2.2.0-1_x86_64.deb
------------
what is the problem?

---

### Post by mcduck on 2005-12-27
I don't know about that problem, I only have a 32 bit CPU, and I actually get every program I need from repositories. But 'man checkinstall' says that switch '-A' would let you set the architecture, so perhaps something like 'sudo checkinstall -D -A amd64' would work?

---

### Post by leeb on 2005-12-27
[QUOTE=mcduck]I don't know about that problem, I only have a 32 bit CPU, and I actually get every program I need from repositories. But 'man checkinstall' says that switch '-A' would let you set the architecture, so perhaps something like 'sudo checkinstall -D -A amd64' would work?[/QUOTE]
thank you.
I install both apache and php thx to your help.

I am sure this is not the last time I am compiling this app's, and when I do I will use the -A arg.

becouse right now, I dont want to break some thing that work - yet.

thank you again.

---

