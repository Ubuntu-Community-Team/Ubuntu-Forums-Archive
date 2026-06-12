---
title: "Problem Installing the Samba package in Ubuntu 8.10"
date: 2009-03-15
forum: General Help
---

### Post by mikho928 on 2009-03-15
Hi,

I'm fairly new to linux (learning curve of about 3 days now) and I've been trying to install the Samba package to Ubuntu.

Samba isn't registered as installed under Add & Remove programs, it tells me "Cannot install 'system-config-samba'" and it conficts with other software. When i try to remove samba under synaptic package manager it says i'd also have to remove ubuntu-desktop.

When i run apt-get install samba i get this error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.26a-1ubuntu2.5)
         Depends: libcupsys2 (>= 1.3.0)
         Depends: libldap2 (>= 2.1.17-1) but it is not going to be installed
         Recommends: smbldap-tools but it is not going to be installed
E: Broken packages

I dont know where to start in terms of a soloution, ive been looking around some forums and have yet to find a resoloution. Is there any way to get Samba installed properly, i really need this program in order to connect to my university to do my assigments. Thanks

btw ive already tried 
sudo get-apt install -f
and from dpkg: error processing samba (--configure):
dpkg: error processing samba (--configure):
 no package named `samba' is installed, cannot configure
Errors were encountered while processing:
 samba

---

