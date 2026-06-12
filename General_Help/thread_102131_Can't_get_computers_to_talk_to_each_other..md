---
title: "Can't get computers to talk to each other."
date: 2005-12-11
forum: General Help
---

### Post by rx7haze on 2005-12-11
I'm relatively new to linux and completely new to networking. I've spent about 8 hours over the past 2 days reading posts on networking. I can't even get past the first step. How to ping from each computer. I have a laptop running win xp. I have a desktop running XP and Ubuntu. I am connected by a crossover cable. I tested networking between the 2 running XP and everything worked fine, so I know the hardware is ok. 
From what I've read, it sounds like all i have to do to be able to ping is connect the 2 computers and assign an ip address to each. Can someone tell me where to do this in both XP and Ubuntu? In Ubuntu, I thought I could simply go to Networking and assign the computer name to be 192.168.0.1. I went to the hosts tab and for the entry with alias localhost.localdomain I changed the ip address to 192.168.0.1. I'm about to give up, but I'd hate to over something that sounds like it should be so easy.

---

### Post by soulestream on 2005-12-11
you need to assign them both ips

like 

xp ip 192.168.1.100, subnet mask 255.255.255.0

ubuntu ip 192.168.1.101 subnet mask 255.255.255.0

you can use the networking tool in ubuntu.

make sure it is "active"

then you should be able to ping

soule

---

### Post by rx7haze on 2005-12-11
Thanks for the reply. I was so frustrated I wasn't thinking clearly. Went and had some lunch and came back with a clear head and figured out how to assign the ip address to both computers.

---

### Post by rx7haze on 2005-12-11
I have everything set up for file sharing between xp and Ubuntu and am able to open and edit ubuntu files in xp and see xp files in Ubuntu. Is there a way to edit xp files in Ubuntu? 
And most importantly, I can't get internet connection sharing to work. I installed firestarter and configured it to share. I set the default gateway on xp = Ubuntu address (192.168.0.1). From all I've read, this should do it. Can't figure out what I'm missing.
Thanks, Bill

---

### Post by soulestream on 2005-12-11
using samba you can add fmask=0777, dmask=0777 to your mount line is /etc/fstab to get rwx access to the share.

my line is this

//windowsmachine/share /mnt/share smbfs credentials=/etc/samba/cred,rw,fmask=0777,dmask=0777 0 0   

the credentials part is a file that has username, password, domain. so i dont have to enter it manually and its masked so a regular user cant read my password. Not really neccessary, but works well.

soule

---

