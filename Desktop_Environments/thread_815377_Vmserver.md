---
title: "Vmserver"
date: 2008-06-01
forum: Desktop Environments
---

### Post by coubury on 2008-06-01
I installed this but haveing problems starting it.

> Type XXXXX-XXXXX-XXXXX-XXXXX or 'Enter' to cancel:  929P4-YFVDE-2G785-4U6LT

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done

The configuration of VMware Server 1.0.6 build-91891 for Linux for this running
kernel completed successfully.

when i type sh /etc/init.d/vmware start i get this

> root@coubury-desktop:/home/coubury# sh /etc/init.d/vmware start
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
root@coubury-desktop:/home/coubury# sudo /etc/init.d/vmware restart
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   Virtual ethernet                                                    done
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
root@coubury-desktop:/home/coubury# 


but if i try to start it by going to APPLICATIONS--->SYSTEM TOOLS---> VMWARE SERVER CONSOLE

I get this error > COULD NOT LAUNCH MENU ITEM
Failed to execute child process "vmware" (No such file or directory) 

Also iv i type vmware in the terminal i get root@coubury-desktop:/home/coubury# vmware
bash: vmware: command not found


what going? am i doing somthing wrong?

---

