---
title: "Dolphin cannot browse workgroup smb shares"
date: 2011-05-16
forum: Desktop Environments
---

### Post by peabrane on 2011-05-16
I have read lots of web threads on this subject but have failed to find any
answers that solve my exact problem.

I have a network of an XP computer, an XP laptop, a Kubuntu computer and an
xubuntu laptop. The only one giving the problem is the kubuntu one. All
computers can access the other's shares. However, Dolphin on the
kubuntu computer cannot browse the "samba shares", none of the other computers
have any problems browsing these shares. Kubuntu's dolphin can access the
workgroup, it lists the computers in the workgroup but when I select any of the
computers in the workgroup (including kubuntu itself), it returns "The file or
folder smb://<servername> does not exist". If I enter the "add network folder" dialogue and
type in the name of the server and folder, there is no problem accessing a local
or remote share providing I get the name correct.

I tried smbtree in kconsole and this listed all shares on the network without
any problem. So what is it that smbtree can do that Dolphin cannot?

Thunar on the xubuntu laptop works OK so I tried installing that on kubuntu.
When I tried it out, it gives "Failed to open "<servername>" Failed to retrieve
share list from server."

I have tried all sorts of things from various threads....I have tried adding
wins to the /etc/nsswitch "hosts:" line - no change. In the smb.conf file, I
have tried playing about with the name resolve order line but this did not help.
I also added
client lanman auth = Yes
lanman auth = Yes
... this did not help either. Neither did enabling the "wins support" line or
putting "local master = yes".

What else can I say about the configuration? Wins is running and I have fixed ip
addresses. I do not have nfs running. The kubuntu version is 11.04 but I have
had this problem on earlier versions of kubuntu.

There cannot be anything fundamentally wrong with smb or the firewall as I can
access remote shares. If thunar is to be believed, it is the service that
retrieves the share list that is failing. However, some threads indicate that
smbtree can give the same "failed to retrieve share list from server"
message. I don't understand why smbtree does not give this error but thunar
does and yet Dolphin gives a "does not exist" message.

I've run out of things to try. Any ideas anyone please?

---

