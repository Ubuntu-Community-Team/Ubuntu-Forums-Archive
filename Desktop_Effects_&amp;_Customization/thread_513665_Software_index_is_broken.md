---
title: "Software index is broken"
date: 2007-07-30
forum: Desktop Effects &amp; Customization
---

### Post by karma_2burn on 2007-07-30
Enable compiz-fusion in Ubuntu Feisty

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

i was following the above tutorial (see link) and i am having problems with synaptic package manager. i cannot update my system now. i have tried rebooting-no help. i am pretty new to all this as well. many thanks for any suggestions or help.       here is the error i am seeing:

in synaptic :



Software index is broken
[I]
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
[/I]


in the termiinal: 

sudo apt-get install -f

After unpacking 1323kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 153960 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070728~3v1ubuntu1_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070728~3v1ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070728~3v1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by amadeus266 on 2007-07-30
Try this...
In Terminal type "dpkg --configure -a"
Then open Synaptec and look under "Custom Filters" then Broken.
Fix whatever it shows there and you should be good.

---

### Post by karma_2burn on 2007-07-30
thanks amadeus266 for the reply-i am still having issues, hopefully just due to my ignorance:

after running dpkg --configure -a:

dpkg: dependency problems prevent configuration of compiz:
 compiz depends on compiz-decorator; however:
  Package compiz-decorator is not installed.
dpkg: error processing compiz (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 compiz


i went into synaptic / followed your directions / found two entries that are broken and highlighted them / click edit-fix broken packages /  hit apply and get this error:

E: /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070728~3v1ubuntu1_i386.deb: trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins

then when i go back into synaptic these two are still marked as broken

am i not executing this correctly?

thanks

---

### Post by TekNullOG on 2007-08-03
I just had the same problem. I fallowed the advice given above. I found the broken packages with the package manager. I uninstalled them and them reinstalled them and it all worked fine after.

I wish you the best of luck.

---

