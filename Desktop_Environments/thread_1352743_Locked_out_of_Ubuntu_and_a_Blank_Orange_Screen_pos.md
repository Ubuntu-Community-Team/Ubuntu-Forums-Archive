---
title: "Locked out of Ubuntu and a Blank Orange Screen post bootup"
date: 2009-12-12
forum: Desktop Environments
---

### Post by sgx100 on 2009-12-12
Hi,

All of a sudden my Ubuntu x64 stopped working with only a blank orange screen to see post bootup and nothing else.

Before that I get the following error ( As per sequence )

1. Could not update the ICEauthority file /home/user_name/.ICEauthority

2. There is a problem with the configuration server. 
( /usr/lib/libgconf2-4/gconf-sanity check - 2 exited with status 256 )

2. Nautilus could not locate the following folders : /home/user_name/desktop/home/user_name/ . nautilus

Please advice :(

Regards
sgx100

---

### Post by jacobs444 on 2009-12-12
[http://ubuntuforums.org/showthread.php?t=949750](http://ubuntuforums.org/showthread.php?t=949750) this should solve your problem.

---

### Post by sgx100 on 2009-12-13
> **jacobs444 said:**
> [http://ubuntuforums.org/showthread.php?t=949750](http://ubuntuforums.org/showthread.php?t=949750) this should solve your problem.

Hi Jacobs,

I tried that stuff but it didnt help.

Is there any way like a windows repair option..where all the system files are recopied leaving intact all the installed programs as the way are.

What happens if I reinstall Ubuntu over the same partition again...Will I loose all my settings and home folder.

Please reply ... Im gravely concerned abt my Ubuntu Installation :(

---

### Post by sgx100 on 2009-12-13
Hi Jacob,

The thing got back to normal...with a pinch of salt...like compiz disabled...cairo-dock disabled..anyways..who cares...its working :D

sudo chmod 755 /home/'username'

and...reboot

it worked...eureka !!!!

Thanks for ur support :) :popcorn:

---

