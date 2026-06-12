---
title: "Kernel 6"
date: 2024-03-14
forum: Desktop Environments
---

### Post by DigiAngel on 2024-03-14
Well....I've had to do this twice now, on two different systems (one an HP Omen laptop, the other a Tuf Gaming MB desktop).  After letting dist-upgrade upgrade to kernel 6, both of these devices started to sporadically stop powering off or suspending properly.  Sometimes, sudo poweroff would exit from X...but stay stuck at reboot: powering off...without actually shutting of the system (this is issue one).

So, I went back to kernel 5 and no issue.  The problem now though is...I don't believe I'm getting any new kernel updates in the kernel 5 train anymore.  Is there a way I can validate this and find out if I'm missing the latest kernel 5 updates?  Thank you.

---

### Post by TheFu on 2024-03-14
The 5.15 update I received was Mar 9.  vmlinuz-5.15.0-100-generic  That's on a 20.04 server system.  Decided to check all my systems. Ansible makes that easy:
```
hadar | CHANGED | rc=0 >>                                                                   
5.15.0-100-generic                                                                          
pi4 | CHANGED | rc=0 >>                                                                     
5.15.92-1-osmc                                                                              
vpn | CHANGED | rc=0 >>                                                                     
5.4.0-173-generic                                                                           
blog44 | CHANGED | rc=0 >>                                                                  
5.4.0-173-generic                                                                           
wallabag | CHANGED | rc=0 >>                                                                
5.15.0-100-generic                                                                          
pihole1 | CHANGED | rc=0 >>                                                                 
5.15.0-100-generic                                                              
pihole2 | CHANGED | rc=0 >>                                                                 
5.15.0-100-generic                                                              
nextcloud-lxd | CHANGED | rc=0 >>
5.15.0-100-generic
istar | CHANGED | rc=0 >>
5.15.0-100-generic
deneb | CHANGED | rc=0 >>                                                                 
5.15.0-100-generic                                              
```                

These are a mix of Debian, 20.04 and 22.04 systems.  For the 5.4.x kernels, the last update was Feb 2.  They are older and more stable, as should be expected.  Perhaps I should switch them to HWE kernels?  Way bother. They are doing the job I need and are stable.  No worries.

I don't have any 6.x kernels here.  Too new for me.

---

