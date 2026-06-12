---
title: "vmware-tools after update?"
date: 2005-12-21
forum: General Help
---

### Post by SundaY82 on 2005-12-21
Hi!

I'm new to linux but I managed to install ubuntu 5.10 without any problem, I then installed vmware-tools to be able to share with my win2k3 64bit host. This also worked well with no complications. I then ran the update that updated among other things the kernel to a new version, after this vmware-tools doesnt work anymore. If I try to run vmware-config-tools.pl or what its called I need to compile it myself this time. 

Now to the question, can someone please explaine in simple steps what needs to be downloaded and installed for me to compile this, If I run apt-get install gcc it will install the latest version I think, and this wont work. 

The kernel the update wants to install is 2.6.12.16.1

Thanks!

---

### Post by rcerreto on 2005-12-21
I'm not sure I understood exactly.
Yes, if you're going to compile a module to be inserted into the kernel, you need to use the same gcc version which has been used to compile the kernel.

**cat /proc/version**

will you tell which (likely 3.4)

**sudo apt-get install gcc-3.4**

will do the trick.
I guess you need also kernel headers and (not sure) make.

If you have installed some other release of gcc (4.0?):
**export CC=/usr/bin/gcc-3.4**

so the needed version will be used

---

### Post by SundaY82 on 2005-12-21
thx for the info, I managed to solve it by:

1. Running the update so that kernel 2.6.12-10-386 was installed
2. apt-get install gcc-3.4
3. apt-get install make
4. apt-get install linux-headers-2.6.12-10-386
5. export CC=/usr/bin/gcc-3.4
6. Reboot
7. vmware-config-tools.pl and just hitting enter all the way.
8. Reboot
9. Done!

Maybe someone else can benefit of this info. 

How do you now what gcc version was used for a kernel before ju install it?

Importat because my network gets disabled after install of kernel and reboot, so I need all to be installed before rebooting when the old kernel is still in use.

---

### Post by MartinG on 2005-12-22
[QUOTE=SundaY82]How do you now what gcc version was used for a kernel before ju install it?[/QUOTE]```
cat /proc/version
``` gives all the info you need.

BTW, you don't need to reboot all the time. It would still have worked if you left out steps 6 & 8.

---

