---
title: "my brother has broken package manager...."
date: 2007-02-28
forum: Desktop Environments
---

### Post by JasonRivers on 2007-02-28
Hi all...

My brother decided it would be funny to install a package called "hot-babe" on my system. i didn't find this funny, so i tried to remove it, and it fell over and died (though i can't remember the exact error, as it was a while ago.

Anyway, now it is half installed, and package manager is giving me "The package hot-babe needs to be reinstalled, but I can't find an archive for it"

I have tried the solutions at [http://www.ubuntuforums.org/showthread.php?t=252922&highlight=package+needs+to+be+reinstalled+can%27t+find]("http://www.ubuntuforums.org/showthread.php?t=252922&highlight=package+needs+to+be+reinstalled+can%27t+find")

and also at
[http://www.ubuntuforums.org/showthread.php?t=372066&page=2&highlight=package+needs+to+be+reinstalled+can%27t+find]("http://www.ubuntuforums.org/showthread.php?t=372066&page=2&highlight=package+needs+to+be+reinstalled+can%27t+find")

with no joy, here's the output:

```
jason@ubuntu:~$ sudo dpkg --remove --force-remove-reinstreq hotbabe
Password:
dpkg: status database area is locked by another process
jason@ubuntu:~$ sudo dpkg --remove --force-remove-reinstreq hotbabe
dpkg - warning: ignoring request to remove hotbabe which isn't installed.
jason@ubuntu:~$ sudo dpkg --remove --force-remove-reinstreq hot-babe
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 132083 files and directories currently installed.)
Removing hot-babe ...
dpkg: error processing hot-babe (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 hot-babe

```

```
jason@ubuntu:~$ sudo dpkg --purge --force-remove-reinstreq hot-babe
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 132083 files and directories currently installed.)
Removing hot-babe ...
dpkg: error processing hot-babe (--purge):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 hot-babe

```


if anyone could help me on this it would be great, because i'm now unable to install or uninstall anything, including update my system.

thanks.

Jay

---

### Post by zanglang on 2007-03-01
Not sure what messed up the archives, but you can try reinstalling and then properly purging the package immediately after that. So:
```
sudo apt-get install --reinstall hot-babe
sudo apt-get remove --purge hot-babe
```

If it says it can't find the package you might need to manually add a source for it to use. Try this one:
[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

---

### Post by JasonRivers on 2007-03-01
Hi Zanglang,

its not a package from package manager, its something he downloaded, I still have the downloaded package in my waste bin, I haven't cleared it out incase I need it....

so these 2 commands still give me the same error of it needs to be re-installed

---

### Post by zanglang on 2007-03-01
Oh, ok. Try installing the deb manually first then. Type:
```
sudo dpkg -i <path to deb file>
sudo apt-get remove --purge hot-babe
```

---

### Post by fakie_flip on 2007-03-24
I am having the same problem. I tried removing a deb package called hot-babe, and it broke my package manager. Now when I try installing any other package, I can't.

```
chris@ubuntu:~$ sudo apt-get install gtetrinet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package hot-babe needs to be reinstalled, but I can't find an archive for it.
chris@ubuntu:~$ sudo dpkg --remove --force-remove-reinstreq hot-babe
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 171221 files and directories currently installed.)
Removing hot-babe ...
dpkg: error processing hot-babe (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 hot-babe
chris@ubuntu:~$ cd .Trash/
chris@ubuntu:~/.Trash$ sudo dpkg -i hot-babe_0.2.2-2_i386.deb 
Selecting previously deselected package hot-babe.
(Reading database ... 171222 files and directories currently installed.)
Preparing to replace hot-babe 0.2.2-2plf6.10 (using hot-babe_0.2.2-2_i386.deb) ...
Unpacking replacement hot-babe ...
dpkg: warning - old post-removal script returned error exit status 10
dpkg - trying script from the new package instead ...
dpkg: error processing hot-babe_0.2.2-2_i386.deb (--install):
 subprocess new post-removal script returned error exit status 10
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 hot-babe_0.2.2-2_i386.deb
chris@ubuntu:~/.Trash$ sudo apt-get remove --purge hot-babe
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package hot-babe needs to be reinstalled, but I can't find an archive for it.
chris@ubuntu:~/.Trash$ sudo dpkg --purge hot-babe
dpkg: error processing hot-babe (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 hot-babe
chris@ubuntu:~/.Trash$ sudo apt-get install --reinstall hot-babe
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package hot-babe needs to be reinstalled, but I can't find an archive for it.
chris@ubuntu:~/.Trash$ 

```

---

### Post by zanglang on 2007-03-24
Have you tried. adding Medibuntu to your repository first so you can reinstall the offending package using apt, and _then_ purging it?

---

