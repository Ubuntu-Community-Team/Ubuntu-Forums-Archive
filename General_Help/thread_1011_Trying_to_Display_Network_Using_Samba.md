---
title: "Trying to Display Network Using Samba"
date: 2004-10-17
forum: General Help
---

### Post by wolos on 2004-10-17
I start Nautilus and click on Network to try to display the other computers on my LAN. I can see Workgroup, but when I click on Workgroup, I get an error saying that this folder does not exist. I should be looking at several other computers at this point. Any ideas?

Steve

---

### Post by viking777 on 2007-09-02
I'll resurrect this very old thread as it never got an answer and I have the identical problem.

3 boxes, 1 windows, 1pclinux 1kubuntu. All 3 see each other and ping each other. When I try to access the kubuntu box from either of the others, I see the workgroup, the computers within it and the shared folders within the computer, but when I try to access any of the shared folders I just get 'Folder does not exist' every time:confused::confused:

I even get this error if I try to look at the shared folders using the kubuntu box itself, as long as I am using samba it claims they don't exist. The folders are perfectly accessible without samba.

It sounds like a firewall problem but they are not running.

I am running Gibbon, on a 64bit laptop but nobody else on the Gibbon forum is reporting any such problem so I though I would try here.

---

### Post by viking777 on 2007-09-02
That is amazing, I have been working on this for days and about 60 seconds after I post the query I solved it.

My solution was:

1) Reconfigure PClinux to be a primary domain controller (dead easy in PCL just a couple of clicks in their control centre - Ubuntu devs please take note I would not have had a clue how to do this in Ubuntu)

2) Noted that this has changed sharing mode from 'share' to 'user'.

3) Changed Kubuntu sharing mode to 'user'.

4)Deleted both shares, recreated them and I have access!!

NB I have tried 'user' share mode before but without success, I think the other 2 steps were the most important here.

---

### Post by viking777 on 2007-09-02
1 reboot later and all that has undone itself back to a one way connection - although admittedly it is the other way round.

Life is too short for this kind of nonsense.

---

