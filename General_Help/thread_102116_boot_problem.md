---
title: "boot problem"
date: 2005-12-11
forum: General Help
---

### Post by yamca on 2005-12-11
Hi,
  Im using linux for 6 mounts. I have a winXP+ubuntu 5.1 system. Today i was using ubuntu. Then i had to switch winxp. after i restarted the computer. It tried to boot the ststem from the network. Normally it directly boots from hdd0. &#304; couldnt find a solution and then reinstalled grub.

  Ubuntu and winxp dont boot. (ubuntu freezes at "waiting for network interface to come up", at winxp i get only a black screen).
When i was using ubuntu i tried to change the permission to the winxp NTFS partiton. I used :
chmod 777 /media/hdc1 and chown 777 /media/hdc1
i dont know if these command caused a problem.

my system: XP2400+, ati 9700pro+1024MB RAM,Asus A7N8X-E mobo

---

### Post by lysis on 2005-12-11
booting from the network SHOULD be a bios feature.  if not, then i unfortunately don't have any good solutions for you.

---

