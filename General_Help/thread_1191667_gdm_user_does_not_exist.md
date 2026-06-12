---
title: "gdm user does not exist"
date: 2009-06-19
forum: General Help
---

### Post by lecoeus on 2009-06-19
Hi there. I installed virtual box on my Ubuntu Jaunty the other day and I set up Windows XP in it. I couldn't get USB support and I saw somewhere on the Internet that you should put yourself in the users group for USB to work. This is probably where I screwed myself. I went to admin-users and groups-manage groups and in the users group I checked beside my username. Now when I try to login I get an error saying "The GDM user gdm does not exist. Please correct GDM configuration and restart GDM."

I tried going into recovery mode and typing sudo dpkg-reconfigure -a, but it failed. It seems I should be able to correct this situation given that I know what the problem is. Can anyone think of a solution by manipulating /etc/group or /etc/gdm/gdm.conf or the live cd? I can post any files if necessary.

Thanks.

---

### Post by Antonio Tavares on 2009-08-10
Hi!
I'm having the same problem in Ubuntu 9.04. It apeared sudenly out of the blue!
I have no reason for the disapearance of the group. At least I'm sure it was not me. Another bug I think...

---

### Post by jonbjarna on 2009-08-24
I have the same problem, for some reason all but 2 users have been deleted, root and myself and I had to edit /etc/sudoers to sudo.

Can someone help me out with this problem ?

The last thing I did was:
[https://help.ubuntu.com/community/FixShowAllUsers](https://help.ubuntu.com/community/FixShowAllUsers)

---

