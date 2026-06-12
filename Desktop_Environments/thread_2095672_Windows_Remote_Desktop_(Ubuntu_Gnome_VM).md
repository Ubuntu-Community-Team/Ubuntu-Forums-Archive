---
title: "Windows Remote Desktop (Ubuntu Gnome VM)"
date: 2012-12-17
forum: Desktop Environments
---

### Post by Triton46 on 2012-12-17
Hi All, 

I have several VMs (Virtualbox) running Ubuntu under a Windows Server 2008 R2 host.  The VMs all start via an open source service called VBoxVMService.  Here is the wrinkle:

If I restart the host (Windows) all the services shutdown and the restart as they should, however, if I remote into the server it connects Windows Remote Desktop to one VM.  It is the same VM each time I restart Windows that has the issue.  If I remove the VM from the service (VBoxVMService) I do not have this issue.  

So, I combed through the list of packages on the VM to see if something was causing this such as Vinagre, RDesktop, etc.  I removed those packages but the problem persists.  I compared the packages in the problematic VM with another working VM and these are the only diffs:

libdbd-mysql-perl                               install
libdbi-perl                                     install
libelf1                                         install
libhtml-template-perl                           install
libmysqlclient16                                install
libnet-daemon-perl                              install
libplrpc-perl                                   install
libsysfs2                                       install
mysql-client-5.1                                install
mysql-client-core-5.1                           install
mysql-common                                    install
mysql-server-5.1                                install
mysql-server-core-5.1                           install
tsclient                                        deinstall
vinagre                                         deinstall


What could be causing this issue?

---

