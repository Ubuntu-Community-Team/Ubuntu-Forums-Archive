---
title: "Help installing Java:"
date: 2005-06-15
forum: Desktop Environments
---

### Post by escobar on 2005-06-15
I was following the below instructions when try to install Java:

[http://ubuntuforums.org/showthread.php?t=3713:](http://ubuntuforums.org/showthread.php?t=3713:)

It didn't quite work so I went into /usr/local and deleted the Java file and, then deleted the Mozilla plugins directory, figuring I could try the instructions from scratch. When doing so, I get the following:

bsanks@TREADSTONE:~$ chmod a+x /home/bsanks/Desktop/j2re-1_4_2_08-linux-i586.bin
bsanks@TREADSTONE:~$ sudo mv /home/bsanks/Desktop/j2re-1_4_2_08-linux-i586.bin /usr/local
bsanks@TREADSTONE:~$ sudo ln -sf /usr/local/j2re-1.4.2_08/bin/java /usr/bin/javabsanks@TREADSTONE:~$ sudo ln -sf /usr/local/j2re-1.4.2_08/bin/java_vm /usr/bin/java_vm
bsanks@TREADSTONE:~$ cd /home/bsanks/.mozilla/plugins
bash: cd: /home/bsanks/.mozilla/plugins: No such file or directory
bsanks@TREADSTONE:~$ mkdir -p /home/username/.mozilla/plugins
mkdir: cannot create directory `/home/username': Permission denied
bsanks@TREADSTONE:~$ mkdir -p /home/bsanks/.mozilla/plugins
bsanks@TREADSTONE:~$ ln -s /usr/local/j2re-1.4.2_08/plugin/i386/ns610-gcc32/libjavaplugin_oji.so libjavaplugin_oji.so
ln: `libjavaplugin_oji.so': File exists
bsanks@TREADSTONE:~$ sudo ln -s /usr/local/j2re-1.4.2_08/plugin/i386/ns610-gcc32/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/
ln: `/usr/lib/mozilla-firefox/plugins//libjavaplugin_oji.so': File exists
bsanks@TREADSTONE:~$

The only difference between the instructions and what I was doing was I'm using Java version 1.4.2_8, so I just substituted the number 8, where 5 was in the tutorial. I had it working before I reinstalled Ubuntu, and now can't figure out where I'm going wrong. Any help would be much appreciated.

---

### Post by bored2k on 2005-06-15
1. OLD java. Bad for you.
2. OLD method. Hard for you.

A) [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
B) sudo apt-get update
C) sudo apt-get install sun-j2re1.5

D) java -version

That is it.

---

### Post by escobar on 2005-06-15
[QUOTE=bored2k]1. OLD java. Bad for you.
2. OLD method. Hard for you.

A) [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
B) sudo apt-get update
C) sudo apt-get install sun-j2re1.5

D) java -version

That is it.[/QUOTE]


Man, I'm working way too hard. Anyways, thanks that did it. Only thing now is Limewire takes a long time to bootup, but I'll live. Thanks.

Also, though java works now, I didn't get step "D" Is that a package I install or something I type into terminal? Thought I'd ask before I tried anything.

---

