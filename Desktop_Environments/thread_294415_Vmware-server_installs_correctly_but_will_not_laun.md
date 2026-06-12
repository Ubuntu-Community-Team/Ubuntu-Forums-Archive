---
title: "Vmware-server installs correctly but will not launch in Edgy Eft"
date: 2006-11-06
forum: Desktop Environments
---

### Post by dwith on 2006-11-06
I have re-installed Edgy four times during the last five days for various different reasons. I have installed vmware-server and configured it properly. The configuration states that it is running properly and I can telnet to it, but the main console does not start. I click on the icon and the system attempts to load it for twenty-thirty seconds and then silently fails. I have been reading the forums vigorously, and have attempted all of the proposals mentioned there, but still cannot get the server console to come up.

vmware.com was mentioned in one post. The user described a script for a common installation bug. Where at vmware.com does one download this script?

Breezy previously ran vmware-server correctly on the same machine. I am not sure where to go with troubleshooting on this one.


](*,) 

Thanks

---

### Post by temcat on 2006-11-06
> **dwith said:**
> I have re-installed Edgy four times during the last five days for various different reasons. I have installed vmware-server and configured it properly. The configuration states that it is running properly and I can telnet to it, but the main console does not start. 

[...]



I have the same problem.

---

### Post by xodus1 on 2006-11-06
start vmware from terminal by typing "vmware" it may tell you the error

---

### Post by titanman128 on 2006-11-06
I also just did a clean install of vmware server on edgy with the same problem. I installed "xinetd" from the repositories and all is good, up and running.

---

### Post by dwith on 2006-11-10
I installed xinetd, but still can't get vmware to open. When I run vmware from the command line:

[FONT="Courier New"]son@Shechem:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.[/FONT]

This seems wrong, because I have gone through the configuration process and the install program says that vmware is installed and running correctly. What isn't configured properly?

---

### Post by hpne on 2006-11-11
> **titanman128 said:**
> I also just did a clean install of vmware server on edgy with the same problem. I installed "xinetd" from the repositories and all is good, up and running.

That worked for me. Thanks a lot!

---

### Post by igknighted on 2006-11-11
> **dwith said:**
> I installed xinetd, but still can't get vmware to open. When I run vmware from the command line:

[FONT="Courier New"]son@Shechem:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.[/FONT]

This seems wrong, because I have gone through the configuration process and the install program says that vmware is installed and running correctly. What isn't configured properly?

You cannot properly install and configure vmware server without the xinetd package installed.  Run the config it asked for (after installing xinetd) and it should work.

---

### Post by FrankVdb on 2006-11-11
Check whether you don't have library libdbus-1-2 and libdbus-1-3 installed.

If both happen to be installed, VMware Server won't start. Instead, it will keep your CPU busy until you kill the process. 

Check using Synaptic. If both libraries are installed, simply remove libdbus-1-2 en you should be fine.

---

### Post by dwith on 2006-11-11
I installed xinetd before I configured vmware. Sorry, my post was misleading on that point.

---

### Post by dwith on 2006-11-11
> **FrankVdb said:**
> Check whether you don't have library libdbus-1-2 and libdbus-1-3 installed.

If both happen to be installed, VMware Server won't start. Instead, it will keep your CPU busy until you kill the process. 

Check using Synaptic. If both libraries are installed, simply remove libdbus-1-2 en you should be fine.

I have a dbus package and libdbus-1-3. Any recommendations?

---

### Post by peterbakker on 2006-11-13
same problem here, 
first did a clean install, after installing OK, program doesn't start...](*,) 
invoked the /usr/bin/vmware-config.pl and after some system restarts got behind this list: 
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

and stop at tis point:
What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.17-10-generic/build/include] 

Extracting the sources of the vmmon module.

tar: /usr/lib/vmware-player/modules/source/vmmon.tar: Functie open() is mislukt: No such file or directory
tar: Fout is niet herstelbaar -- tar sluit nu af.
Unable to untar the "/usr/lib/vmware-player/modules/source/vmmon.tar" file in 
the "/tmp/vmware-config2" directory.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

now, i don't have all week so i stop and wait this time for i don't know a distro with vmware-server out of the box or something... (like openoffice):-k

---

