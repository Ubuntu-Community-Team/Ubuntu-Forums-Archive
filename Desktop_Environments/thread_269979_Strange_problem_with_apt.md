---
title: "Strange problem with apt"
date: 2006-10-02
forum: Desktop Environments
---

### Post by ojai on 2006-10-02
I just tried installing the gpsd package but it apparently had some issues installing.  Now any time I try using apt or dpkg, I get:

  "fgets gave an empty string from diversions [i]"

What's that all about?  My system is in a completely hosed state right now as I can't install or uninstall that package using apt or dpkg.

Does anyone know what might have happened?  I've been using Debian and Ubuntu for a few years now and have never seen that error.  Google doesn't come up with much either so I'm not sure what my options are :-(

Thanks,

-Charlie

---

### Post by Ramses de Norre on 2006-10-02
What are the outputs on these:```
sudo dpkg --configure -a
sudo apt-get install -f
sudo aptitude install -f
dpkg -l fgets
```

---

### Post by ojai on 2006-10-02
Thanks for the reply.  Here's the output:

---
root@omar [~]
# dpkg --configure -a
dpkg: fgets gave an empty string from diversions [i]

Mon 02 Oct 15:31:51
root@omar [~]
# apt-get install -f
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gpsd
Suggested packages:
  hotplug
Recommended packages:
  gpsd-clients
The following packages will be upgraded:
  gpsd
1 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B/207kB of archives.
After unpacking 618kB of additional disk space will be used.
Do you want to continue [Y/n]?
Preconfiguring packages ...
dpkg: fgets gave an empty string from diversions [i]
E: Sub-process /usr/bin/dpkg returned an error code (2)

Mon 02 Oct 15:32:04
root@omar [~]
# aptitude install -f
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages have been kept back:
  gdb gpsd openssh-client openssh-server ssh
0 packages upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the gpsd package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

Mon 02 Oct 15:32:20
root@omar [~]
# dpkg -l fgets
No packages found matching fgets.
---

---

### Post by ojai on 2006-10-04
Can anyone help me with this?  My system's in a completely foobared state right now and I have no clue as how to fix this apt/dpkg hell I'm in :(

Thanks

---

### Post by super7 on 2007-02-09
I have exactly the same problem and exactly the same output. i tried to google for the error message "fgets gave an empty string from diversions" but without usable links. only thing I found that another person had his pc crashed before, same happened with my pc.

before I had some problems with some other files of the package management.

* I had either to delete and rebuild (delete /var/lib/dpkg/available and rebuild via aptitude update) and 
* replace /var/lib/aptitude/pkgstates with /var/lib/aptitude/pkgstates.old

I'm running ubuntu 6.10, just installed yesterday ... currently my system is not updateable, I would really like to avoid a reinstall (yesterday partition magic mysterically removed the linux partition so not again ...)

any help would be greatly appreciated!
thanks,
super7

---

