---
title: "Cant install alien"
date: 2009-05-25
forum: General Help
---

### Post by nikhilbhardwaj on 2009-05-25
Here's what happens when i try to install alien
--------------------------------------------------------------------------------------
elnino@ubuntu:~/Sources/listen-0.6.2$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alien is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libbeecrypt6 (4.1.2-7) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libbeecrypt6 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of librpm4.4:
 librpm4.4 depends on libbeecrypt6; however:
  Package libbeecrypt6 is not configured yet.
dpkg: error processing librpm4.4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of rpm:
 rpm depends on libbeecrypt6; however:
  Package libbeecrypt6 is not configured yet.
 rpm depends on librpm4.4 (>= 4.4); however:
  Package librpm4.4 is not configured yet.
 rpm depends on librpm4.4 (<< 4.5); however:
  Package librpm4.4 is not configured yet.
dpkg: error processing rpm (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of alien:
 alien depends on rpm (>= 2.4.4-2); however:
  Package rpm is not configured yet.
dpkg: error processing alien (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libbeecrypt6
 librpm4.4
 rpm
 alien
E: Sub-process /usr/bin/dpkg returned an error code (1)
-----------------------------------------------------------------------------------------------------

when i use it 
elnino@ubuntu:~/Sources$ sudo alien -k pygtk-devel-0.6.8-3.ppc.rpm 
rpm: error while loading shared libraries: /usr/lib/libbeecrypt.so.6: file too short
Error executing "LANG=C rpm -qp --queryformat %{NAME} pygtk-devel-0.6.8-3.ppc.rpm":  at /usr/share/perl5/Alien/Package.pm line 482.

I was trying to compile a program named listen
elnino@ubuntu:~/Sources/listen-0.6.2$ make
Checking for Python... /usr/bin/python
Checking Python version: 2.6
Checking for PyGTK >= 2.6: found
Checking for pyGTK-devel >= 2.6:
not found
Listen requires pyGTK-devel
make: *** [check] Error 1

so i found the rpm and then tried to convert it using alien
but as you can see no success

please help me out

---

### Post by oldos2er on 2009-05-25
'listen' is in the repositories. Is there some particular reason you want to compile it?

---

### Post by nikhilbhardwaj on 2009-05-26
I didn't know that it was in the repositories.
the version in the repos is 0.5 whereas the source is for 0.6
but i can do without compiling.
thanks for that

BUT
HOW do i fix alien
it still doesnt work
this is what i get from synaptic

E: libbeecrypt6: subprocess post-installation script returned error exit status 2
E: librpm4.4: dependency problems - leaving unconfigured
E: rpm: dependency problems - leaving unconfigured
E: alien: dependency problems - leaving unconfigured

---

### Post by cariboo on 2009-05-26
Run

```
sudo apt-get -f install
```

in a terminal. The above command will download and install any missing dependencies.

---

### Post by Soul-Sing on 2009-05-26
What programm are you trying to install? Maybe it has a native Ubuntu version or alternative...

---

### Post by nikhilbhardwaj on 2009-05-27
heres what happens when i do 
sudo apt-get -f install

elnino@ubuntu:~$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libbeecrypt6 (4.1.2-7) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libbeecrypt6 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of librpm4.4:
 librpm4.4 depends on libbeecrypt6; however:
  Package libbeecrypt6 is not configured yet.
dpkg: error processing librpm4.4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of rpm:
 rpm depends on libbeecrypt6; however:
  Package libbeecrypt6 is not configured yet.
 rpm depends on librpm4.4 (>= 4.4); however:
  Package librpm4.4 is not configured yet.
 rpm depends on librpm4.4 (<< 4.5); however:
  Package librpm4.4 is not configured yet.
dpkg: error processing rpm (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of alien:
 alien depends on rpm (>= 2.4.4-2); however:
  Package rpm is not configured yet.
dpkg: error processing alien (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libbeecrypt6
 librpm4.4
 rpm
 alien
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by nikhilbhardwaj on 2009-05-27
i was trying to compile listen a music player similar to amarok for gnome.
yes i was able to find it later in the repos but there seems to be a configuration problem with apt-get the alien package more specifically

---

### Post by nikhilbhardwaj on 2009-05-28
fixed it

i did the following
sudo apt-get purge alien
sudo apt-get purge rpm librpm4.4
sudo apt-get purge libbeecrypt6

followed by
sudo apt-get update
and
sudo apt-get install alien

looks like it was a problem with the packages installation the first time.
thanks for your time guys.

---

