---
title: "Help with (bio)simulation cluster using 11.1 server (64bit)"
date: 2012-04-02
forum: Education &amp; Science
---

### Post by haadah on 2012-04-02
Hi,

I'm currently working on a project where some heavy simulations are to be run and therefore i though that i would gather my computers together in a cluster. Searched the web and found that Ubuntu was a good place to start (I have worked very little with linux, and it was Fedora and CentOS).

I found a very nice, although outdated, guide [here]("https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide") which i used (i also used the info found [here]("http://ubuntuforums.org/showpost.php?p=10986503&postcount=453")). I can get the cluster working with a switch but the problem is that i do not want to use a switch(i have completed part 1 of the guide, and using a switch gotten a working PXE boot), rather i want all the nodes connected directly to the main node which is equipped with 8 ethernet ports.

What i want:

1) eth0 is the outbound connection to the internet and is set to receive IP from an external DHCP server.

2) eth1 through 7 are to be connected with a node each, i want the IPs for these connections to be static (i have used inet static). The IP is of the format 10.1.1.x with subnet 255.0.0.0 (this can be changed but i prefer it to be this format). E.g. eth1=10.1.1.1 .. eth7=10.1.1.7

3) I want the nodes to have IPs 10.1.1.1x, and where each node is given a specific IP based on MAC address.

1) and 3) are easy to configure. However i can't get 2) to work no matter what i do. I have a suspicion that it is the group declaration in dhcpd.conf that i'm not configuring correctly (i'll post the file tomorrow as i'm not physically present at the cluster and have not yet setup SSH).
I have added eth1 through 7 to the isc-dhcp-server conf. so that the system knows to look for DHCP calls.

I would like your help with solving this issue, i have no idea what to do to make this work. I have search for days and found nothing on or no one that has made a cluster using direct connection between main node and compute nodes.

Edit:
I found the solution: I went with a different system ([http://www.perceus.org/site/html/debian_quickstart.html](http://www.perceus.org/site/html/debian_quickstart.html)) and followed the guide for Debian. It worked for a single NIC, i then used bonding ([http://wiki.debian.org/Bonding](http://wiki.debian.org/Bonding)) and bonded all the NICs (except eth0) together as a single interface. Viola, it now works :)

---

