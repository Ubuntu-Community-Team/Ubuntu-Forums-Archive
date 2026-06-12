---
title: "Truecrypt and &quot;Fuse: failed to....&quot; HELP PLEASE"
date: 2010-11-05
forum: Desktop Environments
---

### Post by steven.smith on 2010-11-05
Hey there. So I wanted to create a Truecrypt volume on my Openvz Ubuntu 10.04 VPS. The install of Truecrypt went fine, however creating the volume itself is frustrating the hell out of me. 

I start by creating the volume by entering the password, algorithm,etc... and it starts making the volume. It then begins the process and eventually goes to %100 percent. However, when it's finished, it comes up with a sudden error saying:

~ "fuse: failed to open /dev/fuse: Permission denied"
It then deletes the truecrypt volume leaving me at step one.

This is very frustrating for me because I can't figure out the problem. First I tried adding user "root" to group "fuse", I did it successfully, but it didn't make a difference.

I then tried to Chmod with full 777 access to the /dev/fuse directory (I know it's a security risk, but I wanted to see if it would work). It still didn't make a difference. It keeps up with the same "fuse; failed to open..." error.

After that, I decided to uninstall fuse by using the command:
~ apt-get remove fuse-utils

That STILL didn't make a difference, I was still getting the same error.

I'm at my wits end with this, I have no clue what to do and am seriously considering just reinstalling the OS.

Does anyone know what the problem is and how to fix it?:confused:

---

### Post by lible on 2011-09-01
bump!

---

### Post by WyoGuy on 2011-11-22
I am having the same problem.  I signed up for cheap VPS (virtual machine) hosting.  I get a server running Ubuntu 10.10 with kernel version 2.6.18-274.  I am running under an OpenVZ container.  

  I have tried everything I can think of to resolve the permissions issue.  I am thinking that the FUSE support in the kernel might not work for me.  

  My next step is to try and download and compile a tar-ball of the FUSE package without the kernel support option.  Anybody have experience with this kind of thing?

---

