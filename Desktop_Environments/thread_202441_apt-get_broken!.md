---
title: "apt-get broken!"
date: 2006-06-23
forum: Desktop Environments
---

### Post by truenemesis on 2006-06-23
when I try to any apt-get command, I get this.

apt-get: error while loading shared libraries: libapt-pkg-libc6.3-6.so.3.11: cannot open shared object file: Input/output error

My gnome and linux kernel are now broken..

someone help me.

---

### Post by Ramses de Norre on 2006-06-23
That library is a virtual package, and the file should be in the apt package, so I'd download the .deb [here]("http://packages.ubuntu.com/dapper/base/apt") and install it with sudo dpkg -i package_name.

---

### Post by truenemesis on 2006-06-23
now i get this 

```

ldconfig: Input file /usr/lib/libXxf86dga.so.1.0.0 not found.

ldconfig: Input file /usr/lib/libXxf86misc.so.1.1.0 not found.

ldconfig: Input file /usr/lib/libXxf86vm.so.1.0.0 not found.

ldconfig: Input file /usr/lib/libaa.so.1.0.4 not found.

ldconfig: Input file /usr/lib/libadns.so.1.0 not found.

ldconfig: Input file /usr/lib/libapm.so.1.0.0 not found.

ldconfig: Input file /usr/lib/libapt-inst-libc6.3-6.so.1.1.0 not found.

ldconfig: Input file /usr/lib/libapt-pkg-libc6.3-6.so.3.11.0 not found.

ldconfig: Input file /usr/lib/libasprintf.so.0.0.0 not found.

ldconfig: Input file /usr/lib/libcamel-provider-1.2.so.8.0.1 not found.

ldconfig: Input file /usr/lib/libcdda_interface.so.0.9.8 not found.

ldconfig: Input file /usr/lib/libcdda_paranoia.so.0.9.8 not found.

ldconfig: Input file /usr/lib/libcdio.so.6.0.1 not found.

ldconfig: Input file /usr/lib/libcompface.so.1.0.0 not found.

ldconfig: Input file /usr/lib/libcrypto.so.0.9.8 not found.

ldconfig: Input file /usr/lib/libcspi.so.0.10.7 not found.

ldconfig: Input file /usr/lib/libcups.so.2 not found.

ldconfig: Input file /usr/lib/libcupsimage.so.2 not found.

ldconfig: Input file /usr/lib/libcurl-gnutls.so.3.0.0 not found.

ldconfig: Input file /usr/lib/libcurl.so.3.0.0 not found.

```

---

### Post by ifokkema on 2006-06-23
These are libraries from lots of different packages. Is your /usr/lib directory OK?

---

### Post by [Nirvana] on 2006-06-23
what does apt-get install -f tell you?

---

### Post by truenemesis on 2006-06-23
apt-get install -f gives me that no matter what. even with -f

apt-get: error while loading shared libraries: libapt-pkg-libc6.3-6.so.3.11: cannot open shared object file: Input/output error

---

### Post by ifokkema on 2006-06-23
[QUOTE=truenemesis]apt-get install -f gives me that no matter what. even with -f

apt-get: error while loading shared libraries: libapt-pkg-libc6.3-6.so.3.11: cannot open shared object file: Input/output error[/QUOTE]

What does
```
ls -lah /usr/lib/libapt-*
```

output? If the files are there, they seem damaged. Try an fsck on your system, files may be damaged or suddenly missing?

---

### Post by truenemesis on 2006-06-23
how can I do a fsck? 

when I do that ls command, i get
ls: /usr/lib/libapt-inst-libc6.3-6.so.1.1.0: Input/output error
ls: /usr/lib/libapt-pkg-libc6.3-6.so.3.11.0: Input/output error

could it be some error with chmod?

---

### Post by ifokkema on 2006-06-23
[QUOTE=truenemesis]how can I do a fsck? 

when I do that ls command, i get
ls: /usr/lib/libapt-inst-libc6.3-6.so.1.1.0: Input/output error
ls: /usr/lib/libapt-pkg-libc6.3-6.so.3.11.0: Input/output error

could it be some error with chmod?[/QUOTE]
This is not a problem with the file permissions, that would be a different error. I assume
```
ls /usr/lib/
```
will throw out a lot of error messages. I really suggest doing a fsck on your drive. Since it's your root partition (provided you don't have /usr/ on a different partition), you will need to use the live CD, because you're adviced to umount your partition before running fsck on it.

- Run 'mount', to see which partition your root partition is.
- Boot from the Live CD.
- Make sure the partition is not mounted.
- Run:
```
sudo fsck -f /dev/hda1
```
(replace /dev/hda1 with your root partition)
- If it throws error messages at you, carefully read what it says and fix your drive.

---

### Post by truenemesis on 2006-06-23
how do I make sure that my root partition is not mounted? whats the command?

---

### Post by ifokkema on 2006-06-23
[QUOTE=truenemesis]how do I make sure that my root partition is not mounted? whats the command?[/QUOTE]
Run
```
mount
```
and take a look at the output. If it contains a line like:
```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
```
then it's mounted. Note the " on / " which means the partition is mounted on the root directory.

---

### Post by truenemesis on 2006-06-23
okay, I did the fsck. Back on ubuntu.
when I run apt-get install -f
I get this
apt-get: error while loading shared libraries: libapt-pkg-libc6.3-6.so.3.11: cannot open shared object file: No such file or directory

now I installed that debian package. and i still get the error.
Im running i386 and installed this  libc6_2.3.6-0ubuntu20_i386.deb

---

### Post by ifokkema on 2006-06-23
[QUOTE=truenemesis]okay, I did the fsck. Back on ubuntu.
when I run apt-get install -f
I get this
apt-get: error while loading shared libraries: libapt-pkg-libc6.3-6.so.3.11: cannot open shared object file: No such file or directory

now I installed that debian package. and i still get the error.
Im running i386 and installed this  libc6_2.3.6-0ubuntu20_i386.deb[/QUOTE]
What was the output of fsck? Did it find anything? Repair your drive? Does the command
```
ls /usr/lib/
```
still return error messages?

"No such file or directory" sounds better than "Input/Output error". I guess that fsck repaired your drive. Now you're missing files in /usr/lib. If these are just a few, you can replace them by re-installing the packages containing these libraries. An other possibility is to run the Live CD again, and copy the contents of the /usr/lib directory to your /usr/lib. Make sure you don't overwrite files, but just copy files there, that you are missing. Read
```
man cp
```
on how to do that in the console.

I'm off now, will read any reply tomorrow.

Good luck!

---

