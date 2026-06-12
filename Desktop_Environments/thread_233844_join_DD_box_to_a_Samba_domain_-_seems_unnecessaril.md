---
title: "join DD box to a Samba domain - seems unnecessarily hard to do !"
date: 2006-08-10
forum: Desktop Environments
---

### Post by neill on 2006-08-10
hi

i have a SUSE PDC which acts as a fileserver for my home LAN

the XP clients i (have to) use log onto the domain and My Documents is mapped to /home/user on the PDC

so the XP client uses My Documents in the usual way, and all the files are actually held on the PDC, and from there i centralize backups, share printers and the like

now i want the kids to get online/on the LAN and i **desperately **want to avoid them using XP - for all sorts of reasons (security, point of principle, ease, cost .. the list goes on) - so i'm experimenting with ubuntu

however, i also want to set up a system like i have for the XP clients - ideally i would have /home on the ubuntu client mapped to /home/user on the SUSe PDC. that way if the kids break the client i've got a backup of their data on the PDC and if they trash the data on the PDC i've got a backup from last night on the external HDDs plugged into the PDC

i know i can mount a share from the PDC onto the ubuntu client at logon but i can't guarantee the kids will store data there rather than in /home (of course they can store the data anywhere they like, but a least if i can map /home i've taken a big step, rather than asking them to always use something in /mount)

i've read some stuff about linux clients joining windows domains - and there's very little out there ! i'm not using an AD or LDAP setup for which i can find some info, but that's not relevant. it's actually extremely simple to join a domain in XP - it's seems strange it's so hard with linux :-({|= 

can anyone help me with this problem ?????

thanks

neill

---

