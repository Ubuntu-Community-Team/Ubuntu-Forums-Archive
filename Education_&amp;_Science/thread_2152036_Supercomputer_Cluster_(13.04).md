---
title: "Supercomputer Cluster (13.04)"
date: 2013-06-06
forum: Education &amp; Science
---

### Post by Jinmarkus on 2013-06-06
Hello all,

I'm sure you've all heard this far too much, but I'm new to Ubuntu and I would like to set up a supercomputer cluster.  For my research I am to get this cluster up and running using 9 nodes (and perhaps additional), 1 master and 8 slaves.  I would prefer to run Ubuntu 13.04 and as I've noticed not a lot of information out there is on this version.  I've been working with and using old guides such as:

[https://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+cluster+guide&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=ubuntu+cluster+guide&ie=utf-8&oe=utf-8)

[URL="http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CDAQFjAA&url=http%3A%2F%2Fwww.stevekelly.eu%2Fcluster.shtml&ei=JsSwUdH3DYHaqwGanoCYDw&usg=AFQjCNHv1VRL2zuFJofSg9SXQkNNhH01Ug&sig2=9wXjzelGDhjnk1noqTL9Jg&bvm=bv.47534661,d.aWM"]http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CDAQFjAA&url=http%3A%2F%2Fwww.stevekelly.eu%2Fcluster.shtml&ei=JsSwUdH3DYHaqwGanoCYDw&usg=AFQjCNHv1VRL2zuFJofSg9SXQkNNhH01Ug&sig2=9wXjzelGDhjnk1noqTL9Jg&bvm=bv.47534661,d.aWM
[/URL]
and have recently looked into this guide as well but only briefly:
[URL="http://http://byobu.info/article/Building_a_simple_Beowulf_cluster_with_Ubuntu/#fn:ubuntu-wiki"]
[/URL][SIZE=2][http://byobu.info/article/Building_a_simple_Beowulf_cluster_with_Ubuntu/#fn:ubuntu-wiki]("https://email.uiowa.edu/owa/redir.aspx?C=E4SGm5SvVEGNEKGEsNTZm9p_CBRiNtAI9HahvxZ_Yh3go5yAy_gmfEcehyXMc8LYJXQ9iWpcysc.&URL=http%3a%2f%2fbyobu.info%2farticle%2fBuilding_a_simple_Beowulf_cluster_with_Ubuntu%2f%23fn%3aubuntu-wiki")[/SIZE]

I am familiar with maneuvering through the terminal and I have an understanding of computer hardware.

I have installed many of the required packages with regards to the first link, i.e.

# apt-get install dhcp3-server tftpd-hpa syslinux nfs-kernel-server nfs-common

and since this guide uses Kerrighed I also installed:

# apt-get install automake autoconf libtool pkg-config gawk rsync bzip2 gcc libncurses5 libncurses5-dev wget lsb-release xmlto patchutils xutils-dev build-essential openssh-server ntp

This guide deals with Ubuntu 8.04 and therefore some of the files/directories don't exactly line up.  For example the file: /etc/default/dhcp3-server was actually in the dhcp folder instead of the dhcp3 folder.  Seeing as I'm quite unfamiliar with this type of stuff it is easy for me to get tripped up.

My first real question is when editing the file /etc/dhcp3/dhcpd.conf they have a huge paragraph to write to the file under section 1.1.  Do I just copy that directly into the file? Do I append it?

Ideally if anyone finds the time to help me in this I would formulate my exact specific steps to achieving this goal and put up a nice guide somewhere.  It would be for individuals like me who are not really familiar with the specifics of Ubuntu and config file locations to set up something like this.

Thank you for your help and time!  Sorry for the long message

---

### Post by gabrielaca on 2013-06-23
try this [HTML]http://ubuntuforums.org/showthread.php?t=1030849[/HTML] its not for 13.04 and very quiet lately but very informative.

---

