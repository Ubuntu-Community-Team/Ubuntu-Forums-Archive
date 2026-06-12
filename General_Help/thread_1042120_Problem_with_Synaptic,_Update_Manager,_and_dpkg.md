---
title: "Problem with Synaptic, Update Manager, and dpkg"
date: 2009-01-17
forum: General Help
---

### Post by sumpm1 on 2009-01-17
Hey guys. On a fresh install of 8.10 - i386. I tried running synaptic and/or update manager and get the following error:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

So I ran 

```
sudo dpkg --configure -a
```

and got

```
dave@dave-desktop:~$ sudo dpkg --configure -a
Setting up doc-base (0.8.16) ...
Number found where operator expected at /usr/share/perl/5.10/Pod/Simple.pm line 1155, near ")
0"
	(Missing semicolon on previous line?)
syntax error at /usr/share/perl/5.10/Pod/Simple.pm line 1155, near ")
0"
Global symbol "@section_name" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1167.
Global symbol "@section_name" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1170.
Global symbol "$section_name" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1176.
Global symbol "@ell_content" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1177.
Global symbol "@ell_content" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1177.
Global symbol "@ell_content" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1177.
Global symbol "@ell_content" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1178.
Global symbol "@ell_content" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1179.
Global symbol "@ell_content" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1181.
Global symbol "@ell_content" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1181.
Global symbol "$section_name" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1184.
Global symbol "@ell_content" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1184.
Global symbol "$section_name" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1185.
Global symbol "$section_name" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1186.
Global symbol "$section_name" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1190.
Global symbol "$link_text" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1190.
Global symbol "@ell_content" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1191.
Global symbol "@ell_content" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1192.
Global symbol "$section_name" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1193.
Global symbol "@ell_content" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1193.
Global symbol "$link_text" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1204.
Global symbol "$ell" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1205.
Global symbol "$link_text" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1206.
Global symbol "$link_text" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1207.
Global symbol "$section_name" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1207.
Global symbol "$section_name" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1207.
Global symbol "@ell_content" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1209.
Global symbol "$link_text" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1210.
Global symbol "$section_name" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1210.
Global symbol "$link_text" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1211.
Global symbol "@ell_content" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1211.
Global symbol "@ell_content" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1218.
Global symbol "@ell_content" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1218.
Global symbol "@ell_content" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1219.
Global symbol "$ell" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1221.
Global symbol "@ell_content" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1222.
Global symbol "$ell" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1224.
Global symbol "$section_name" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1228.
Global symbol "$ell" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1229.
Global symbol "$section_name" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1230.
Global symbol "$ell" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1232.
Global symbol "@ell_content" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1235.
Global symbol "$ell" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1236.
Global symbol "@ell_content" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1237.
Global symbol "$ell" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1239.
Global symbol "$ell" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1243.
Global symbol "$ell" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1243.
Global symbol "$link_text" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1243.
Global symbol "$link_text" requires explicit package name at /usr/share/perl/5.10/Pod/Simple.pm line 1243.
syntax error at /usr/share/perl/5.10/Pod/Simple.pm line 1252, near "}"
/usr/share/perl/5.10/Pod/Simple.pm has too many errors.
Compilation failed in require at /usr/share/perl/5.10/Pod/Text.pm line 34.
BEGIN failed--compilation aborted at /usr/share/perl/5.10/Pod/Text.pm line 34.
Compilation failed in require at /usr/share/perl/5.10/Pod/Usage.pm line 436.
BEGIN failed--compilation aborted at /usr/share/perl/5.10/Pod/Usage.pm line 443.
Compilation failed in require at /usr/sbin/install-docs line 26.
Global symbol "$opt_rootdir" requires explicit package name at /usr/sbin/install-docs line 157.
Execution of /usr/sbin/install-docs aborted due to compilation errors.
dpkg: error processing doc-base (--configure):
 subprocess post-installation script returned error exit status 9
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
```

Can anyone tell me what the problem can be?

Thanks

---

### Post by taurus on 2009-01-17
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by ellen.marie on 2009-01-17
I'm new to Ubuntu and got the same error message when trying to install updates:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

Would someone please point me in the right direction to fix this problem?  I don't know how to manually run anything!

Thanks,

Ellen

---

### Post by taurus on 2009-01-17
> **ellen.marie said:**
> I'm new to Ubuntu and got the same error message when trying to install updates:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

Would someone please point me in the right direction to fix this problem?  I don't know how to manually run anything!

Thanks,

Ellen

Close update manager.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

