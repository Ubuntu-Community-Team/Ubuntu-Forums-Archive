---
title: "How to report bug agains snap package?"
date: 2016-06-27
forum: Desktop Environments
---

### Post by abcuser on 2016-06-27
Hi,
on Ubuntu 16.04 I can report bug against official package by using:
ubuntu-bug <package_name>

How to report a bug against snap package?

1. Before installing any snap package, check default /snap directory:
```
$ ls -l /snap/
```
drwxr-xr-x 2 root root 4096 jun 27 19:38 bin
drwxr-xr-x 3 root root 4096 jun 26 08:48 ubuntu-core

```
$ ls -l /snap/bin/
```
total 0

2. Install hello-world snap:
```
sudo snap install hello-word
```

3. Repeat step 1:
```
$ ls -l /snap/
```
drwxr-xr-x 2 root root 4096 jun 27 19:44 bin
drwxr-xr-x 3 root root 4096 jun 27 19:44 hello-world
drwxr-xr-x 3 root root 4096 jun 26 08:48 ubuntu-core
```
$ ls -l /snap/bin/
```
-rwxr-xr-x 1 root root 601 jun 27 19:44 hello-world
-rwxr-xr-x 1 root root 580 jun 27 19:44 hello-world.echo
-rwxr-xr-x 1 root root 576 jun 27 19:44 hello-world.env
-rwxr-xr-x 1 root root 580 jun 27 19:44 hello-world.evil
-rwxr-xr-x 1 root root 572 jun 27 19:44 hello-world.sh
-rwxr-xr-x 1 root root 592 jun 27 19:44 hello-world.showdev
-rwxr-xr-x 1 root root 584 jun 27 19:44 hello-world.usehw

4. You can test the snap:
```
/snap/bin/hello-world
```
and 
Hello World!
is displayed in terminal.

5. Remote snap package:
```
sudo snap remove hello-world
```

6. Check if remove was successful:
```
$ ls -l /snap/bin/
```
total 0

```
$ ls -l /snap/
```
drwxr-xr-x 2 root root 4096 jun 27 19:46 bin
drwxr-xr-x 2 root root 4096 jun 27 19:46 hello-world
drwxr-xr-x 3 root root 4096 jun 26 08:48 ubuntu-core

Note: It is clear there was hello-world directory not removed.

```
$ ls -l /snap/hello-world/
```
total 0

Note: And directory is empty.

It looks like a bug.

How to report a bug against "hello-world" snap package?

Thanks

---

### Post by Frogs Hair on 2016-06-27
I've experimented with a couple of packages and installed and removed using the following.
```
snap find
``` ```
sudo snap install package-name
``` or```
 sudo snap remove package-name
``` To see a list of installed packages.
 ```
snap list
```

---

### Post by mc4man on 2016-06-27
Bugs against snapd behavior can be filed on [ubuntu-snappy]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-snappy") or ubuntu-core if applicable 
What you are reporting is likely not a bug, /snap/ is just representative of mounted squashfs's. Try unmounting the hello-world squashfs if still mounted or reboot, then check /snap/ again.

As far as actual snap packages it's likely bugs would have to be presented to whoever packaged it or the source owner/dev, Ubuntu/Canonical isn't going to be that responsible. That's part of the benefit of snaps to Canonical..

---

### Post by grahammechanical on 2016-06-27
It may be a bug but it may also be intentional.

 /snap/bin/appname is under root and contains the application. /snap/appname is under /home and contains user data for that app. Do we want that removed? I will give an example with the Notes snap app. Under root there is this

/snap/notes/1  with more files and folders in the 1 folder. And also

/snap/bin/notes which is the executable shell script for the Notes snap app. But under /home there is this

/snap/notes/1/.config/Awesomeness/Notes,ini. Which is a plain text file that contains the actual notes that I have made with the Notes snap. If I need to re-install the Notes snap app by removing it and re-installing it I would not want to lose my data.

Is it not common practice in Linux for the removal of an application not to remove user configuration files in /home?

On a real snappy Ubuntu core system the file system would be a snap and read only and there would be a partition called writable where user date would go and would not be lost if the OS snap was upgraded ( which means completely overwritten) or a snap app was removed.

Regards

---

