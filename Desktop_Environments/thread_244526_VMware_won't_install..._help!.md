---
title: "VMware won't install... help!"
date: 2006-08-26
forum: Desktop Environments
---

### Post by titancomputing on 2006-08-26
I've been trying to install VMware to install XP in Dapper Drake Kubuntu, but everytime I finish the part where I tell it where to put the icons (I've been accepting the default values for everything) I get the following error messages:

Do you accept? (yes/no) y

Thank you.

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]


** (process:12868): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_d esktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:12868): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_d esktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:12871): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_d esktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:12871): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_d esktop_entries_lookup_group (entries, group_name) == NULL' failed
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes] y

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]


I've got a regular kernel here... so I really don't know what it's problem is. Here's the results of a uname -r on m system.


2.6.15-26-686

Can someone please help me as I REALLY need this program. Thanks.

---

### Post by Dubbayoo on 2006-08-26
it continued to install so it must be a non critical error. what happens when you run it?

---

### Post by gruffy-06 on 2006-08-26
You should install the Linux kernel headers for your running kernel or get the latest source code from [www.kernel.org](www.kernel.org) and compile a new kernel.

Compiling is difficult, so let us get the headers instead.

In a terminal, type:
*sudo apt-get install linux-headers-686*

After the kernel headers are installed, run vmware-config.pl again and follow instructions. Can't do anything about the "egg" errors, though.

---

### Post by titancomputing on 2006-08-26
I can't run it because when I tell it to use the compiler, it doesn't find it and keeps looking.

---

### Post by gruffy-06 on 2006-08-26
A very difficult situation. You might want to read the VMware Server documentation. If that won't help, VMware might know something.

---

### Post by Dubbayoo on 2006-08-26
it's asking you for the header files; have you installed them? if you haven't then you know what you need to do.

---

### Post by titancomputing on 2006-08-26
Header files are installed and up to date.

---

### Post by -deadcats on 2006-08-26
Here's how to do it:
1. Start Synaptic, search for "linux" and sort by installed. 
2. Take a good look at your installed linux kernel. Find the packages linux-kernel-headers, linux-headers-686, linux-image-686 to match your installed kernel. Install them.
3. Also search for and install gcc and g++, make, and probably binutils.
4. Reboot after install.
5. Now rerun vmware-config.pl. It should be hunky-dory.

regards,
-dc

P.S. This routine's worked for me with all VMWorkstation 5 versions.

---

### Post by thingy on 2006-08-26
apt-get install build-essentials flex bison [I]linux-headers-686

After the above is installed, retry the vmware installation
[/I]

---

### Post by Dubbayoo on 2006-08-26
then there has to be more to your error that you havent' shown us.

---

### Post by titancomputing on 2006-08-26
Tried both suggesions, neither worked. :(

---

### Post by jnoreiko on 2006-08-27
> **-deadcats said:**
> Here's how to do it:
1. Start Synaptic, search for "linux" and sort by installed. 
2. Take a good look at your installed linux kernel. Find the packages linux-kernel-headers, linux-headers-686, linux-image-686 to match your installed kernel. Install 

Done that. I've got 'linux-386', version 2.6.15.22 and I've installed 'linux-headers-386', same version.
I don't know what answer to give to the VMware setup's question
> What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]


The dependency that has been installed is version 2.6.15.23, so I get an error message:
> The directory of kernel headers (version 2.6.15-23) does not match your running
kernel (version 2.6.15-23-386).  Even if the module were to compile
successfully, it would not load into the running kernel.


EDIT: panic over for now at least... there was another package installed.

The answer at least for me is: /usr/src/linux-headers-2.6.15-23-386/include

---

