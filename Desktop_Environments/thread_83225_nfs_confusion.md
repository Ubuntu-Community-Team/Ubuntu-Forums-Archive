---
title: "nfs confusion"
date: 2005-10-28
forum: Desktop Environments
---

### Post by CharlieC on 2005-10-28
I followed the directions in the NFS Client how to and all seemed to go well. The nfs server machine on my network is called linuxthree and the IP is 192.168.1.3  the OS is SUSE 10.0. The client machine is this one which is called linuxfour and the IP is 192.168.1.1. 
    From the SUSE machine I can see this one (linuxfour) but there are not shared folder, I think I must have to do something there but don't know what. From this machine linuxfour I can not see linuxthree which is the SUSE10.0. I would like to be able to trade files on the two machines.
    BTW, I have linuxthree set up as a SAMBA server and when I go to the Network choice in Places I can see my SUSE machine as well as my XP Pro machine. I hope that is clear it seems a little confusing to me. I feel like I am missing one easy step but cant figure it out.
    I am pretty now to linux so complicated responses unfortunately will probably go right over my head.

TIA
Charlie

---

### Post by fdimmling on 2005-10-28
I'm not quite shure if I understand your posting correctly but I have the impression you are mixing up NFS and Samba a bit. If you have installed the nfs server on a machine you can export directories on that machine for other linux machines. In SuSE this can be done quite easily using YaST. On the client side you have to install nfs-common to get the client working. You have to write a line into /etc/fstab to mount it. On my system it looks like

desktop:/home	/desktop	nfs	user,exec,bg	0	0

which mounts  /desktop on the client computer to  /home on the server machine called desktop which is 192.168.0.2, which means I have an entry

192.168.0.2 desktop.mydomain desktop

in /etc/hosts

Friedrich

---

