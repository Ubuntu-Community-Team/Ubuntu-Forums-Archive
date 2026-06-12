---
title: "MUGEN, Apparmor &amp; Hardy"
date: 2008-02-05
forum: Gaming &amp; Leisure
---

### Post by osd_daedalus on 2008-02-05
Hi everybody,
Everyone knows that a good method to run mugen is to kill apparmor...

But now is the problem: guess what, in Hardy, Apparmor is compiled into the kernel! And so it is not possible to kill it...

So, I need help to create a profile in order to make mugen work... someone can help me?

Thanks in advance.

---

### Post by osd_daedalus on 2008-02-06
So, here is what I tried:

I have created an apparmor profile with aa-genprof: (my mugen is in /home/deda/mugen)
```
root@kubuntu:~/mugen# aa-genprof mugen
```

P.S. I became root with "sudo -s"

This is what appears:
```
Connecting to repository.....
Writing updated profile for /home/deda/mugen/mugen.
Setting /home/deda/mugen/mugen to complain mode.

Please start the application to be profiled in
another window and exercise its functionality now.

Once completed, select the "Scan" button below in
order to scan the system logs for AppArmor events.

For each AppArmor event, you will be given the
opportunity to choose whether the access should be
allowed or denied.

Profiling: /home/deda/mugen/mugen

[(S)can system log for SubDomain events] / (F)inish

```

Simple, isn't it? :)
And I have monitored syslog with "tail -f /var/log/syslog":

```
Feb  6 15:21:48 kubuntu logger: GenProf: 37e694b0ef8b6de6f9ec53ed9a8a01f6
```

It seems that all goes ok, so I start mugen, but nothing (*,)
Syslog tells me:
```
Feb  6 15:22:45 kubuntu kernel: [ 1725.519674] audit(1202307765.222:6): operation="inode_create" request_mask="w::" denied_mask="w::" name="/tmp/upxBOSMZWCAHVV" pid=7861 profile="/home/deda/mugen/mugen" namespace="default"
Feb  6 15:22:45 kubuntu kernel: [ 1725.519707] audit(1202307765.222:7): operation="setattr" request_mask="w::" denied_mask="w::" attribute="size,mtime,ctime," name="/tmp/upxBOSMZWCAHVV" pid=7861 profile="/home/deda/mugen/mugen" namespace="default"
Feb  6 15:22:45 kubuntu kernel: [ 1726.005895] audit(1202307765.710:8): operation="inode_permission" request_mask="r::" denied_mask="r::" name="/tmp/upxBOSMZWCAHVV" pid=7861 profile="/home/deda/mugen/mugen" namespace="default"
Feb  6 15:22:45 kubuntu kernel: [ 1726.005928] audit(1202307765.710:9): operation="inode_permission" request_mask="rUx::" denied_mask="rUx::" name="/tmp/upxBOSMZWCAHVV" pid=7861 profile="/home/deda/mugen/mugen" namespace="default"
Feb  6 15:22:45 kubuntu kernel: [ 1726.005940] audit(1202307765.710:10): operation="inode_unlink" request_mask="w::" denied_mask="w::" name="/tmp/upxBOSMZWCAHVV" pid=7861 profile="/home/deda/mugen/mugen" namespace="default"
Feb  6 15:22:45 kubuntu kernel: [ 1726.005962] audit(1202307765.710:11): operation="inode_permission" request_mask="Ux::" denied_mask="Ux::" pid=7861 profile="/home/deda/mugen/mugen" namespace="default"

```

And dmesg output is:
```
[ 1725.519674] audit(1202307765.222:6): operation="inode_create" request_mask="w::" denied_mask="w::" name="/tmp/upxBOSMZWCAHVV" pid=7861 profile="/home/deda/mugen/mugen" namespace="default"
[ 1725.519707] audit(1202307765.222:7): operation="setattr" request_mask="w::" denied_mask="w::" attribute="size,mtime,ctime," name="/tmp/upxBOSMZWCAHVV" pid=7861 profile="/home/deda/mugen/mugen" namespace="default"
[ 1726.005895] audit(1202307765.710:8): operation="inode_permission" request_mask="r::" denied_mask="r::" name="/tmp/upxBOSMZWCAHVV" pid=7861 profile="/home/deda/mugen/mugen" namespace="default"
[ 1726.005928] audit(1202307765.710:9): operation="inode_permission" request_mask="rUx::" denied_mask="rUx::" name="/tmp/upxBOSMZWCAHVV" pid=7861 profile="/home/deda/mugen/mugen" namespace="default"
[ 1726.005940] audit(1202307765.710:10): operation="inode_unlink" request_mask="w::" denied_mask="w::" name="/tmp/upxBOSMZWCAHVV" pid=7861 profile="/home/deda/mugen/mugen" namespace="default"
[ 1726.005962] audit(1202307765.710:11): operation="inode_permission" request_mask="Ux::" denied_mask="Ux::" pid=7861 profile="/home/deda/mugen/mugen" namespace="default"
[ 1726.005974] AppArmor: aa_register: Failed to get filename

```

As you can see, codes in brackets (es. [1726.xxxxx]) flag entries both in dmesg and in syslog.

Ah, I have forgotten: the new profile (/etc/apparmor.d/home.deda.mugen.mugen) says:
```
# Last Modified: Wed Feb  6 15:21:48 2008
#include <tunables/global>
/home/deda/mugen/mugen {
  #include <abstractions/base>

  /home/deda/mugen/mugen mr,
}

```

MR? What does it mean? :confused:

Any ideas? I will keep trying ;)

-------------------------------------------
ADDED:

Now that I'm learning Apparmor (wow, now this thread sounds that a security one ;) ), I'm resolving permissions:

Apparmor, in syslog, warns that it wants permissions "r", "w" and "Ux". So I have modified my profile (/etc/apparmor.d/home.deda.mugen.mugen) in something like this:

```
# Last Modified: Wed Feb  6 15:21:48 2008
#include <tunables/global>
/home/deda/mugen/mugen {
  #include <abstractions/base>

  /home/deda/mugen/** rwUx,
  /tmp/** rwUx,
}

```

It is necessary to reboot Apparmor with "/etc/init.d apparmor restart" everytime profiles are changed.

Then this is the only error message in /var/log/syslog when I try to run mugen:

```
Feb  6 21:20:57 kubuntu kernel: [ 1606.641929] audit(1202329257.493:13): operation="inode_permission" request_mask="Ux::" denied_mask="Ux::" pid=11770 profile="/home/deda/mugen/mugen" namespace="default"
``` 

Just one message... but the matter is: there is no "name" entry :!:
It means: something wants "Ux" permission... but WHAT?????? ](*,)](*,)

Come on guys, I need just a little step to make things work!!!!

---

### Post by osd_daedalus on 2008-02-06
It's not possible!!!!!

I edited the profile as is:

```
# Last Modified: Wed Feb  6 15:21:48 2008
#include <tunables/global>
/home/deda/mugen/mugen {
#  #include <abstractions/base>

/** rwUx,
}

```

I commented the "#include" for making possible to set permissions in /lib/ and /opt/...

Why I have the same error message? I gave permissions to the entire filesystem!!!!

Hope someone helps me, or I will need a neurologist :lolflag:

---

### Post by CarpKing on 2008-02-07
Whether you figure it out or not, you should file a bug about how difficult (or hopefully not impossible) it is to run a program that is distributed in this manner.  There are a couple others that I've run into (some benchmarking program [Geekbench?] also didn't work until I turned off Apparmor).  I guess running stray executables is exactly what this program is supposed to prevent you from doing, though, so I guess we'll have to hope for the best.  It would be nice if they had some way to control this from the file properties dialog.

---

### Post by osd_daedalus on 2008-02-09
> Whether you figure it out or not, you should file a bug about how difficult (or hopefully not impossible) it is to run a program that is distributed in this manner. There are a couple others that I've run into (some benchmarking program [Geekbench?] also didn't work until I turned off Apparmor). I guess running stray executables is exactly what this program is supposed to prevent you from doing, though, so I guess we'll have to hope for the best
I tried Geekbench and it works here, even with Apparmor activated.
However, I accept your suggestion and I have just submitted this in Launchpad. 

[https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/190516](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/190516)
> It would be nice if they had some way to control this from the file properties dialog.
I know that are some distributions (if I remember well, Suse, Fedora and Mandriva) that integrates Apparmor settings with GUI in their system settings. Maybe Ubuntu will do this... but it's not so difficult to create profiles and set permissions via shell.

---

