---
title: "Unable to join domain"
date: 2009-04-13
forum: General Help
---

### Post by eddie999 on 2009-04-13
Stuff that takes in Windows 2 min takes in this Penguin -**** 2 day's
As soon you try to do something you have to google and test for Day's
Is there someone that have solved this:
and yes i can do nslookup *domain*
and yes i can ping the Server and i have the right account for joinig the domain.

have installed likewise, samba, winbind

Could not connect to server *server.domain.com*
Connection failed: NT_STATUS_NOLOGON_WORKSTATION_TRUST_ACCOUNT
Failed to verify membership in domain: NT_STATUS_NOLOGON_WORKSTATION_TRUST_ACCOUNT!

Error: Unable to join domain [code 0x0008000e]

Domain join operation failed to create the computer account in Active Directory. Common causes are a bad administrator password, a bad OU name, or an existing
computer account without modification permissions.

--Eddie--

---

### Post by marks_linux on 2009-04-13
I expect theres a question hidden in there somewhere?

---

### Post by ibuclaw on 2009-04-13
> **eddie999 said:**
> Stuff that takes in Windows 2 min takes in this Penguin -**** 2 day's
As soon you try to do something you have to google and test for Day's
Is there someone that have solved this:
and yes i can do nslookup *domain*
and yes i can ping the Server and i have the right account for joinig the domain.

have installed likewise, samba, winbind

Could not connect to server *server.domain.com*
Connection failed: NT_STATUS_NOLOGON_WORKSTATION_TRUST_ACCOUNT
Failed to verify membership in domain: NT_STATUS_NOLOGON_WORKSTATION_TRUST_ACCOUNT!

Error: Unable to join domain [code 0x0008000e]

Domain join operation failed to create the computer account in Active Directory. Common causes are a bad administrator password, a bad OU name, or an existing
computer account without modification permissions.

--Eddie--

Hello and welcome to the UbuntuForums.

Firstly, may you please acquaint yourself with the forum [Code of Conduct]("http://ubuntuforums.org/index.php?page=policy").
Secondly, it is advised to use a **descriptive** topic title when starting help and support threads.


I have never tried to join a an AD myself from Linux, so I have no direct questions or answers to your problem at hand. But please feel free to read the available documentation on the Ubuntu helpdocs about authenticating on an Active Directory, as hosted here: [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

Regards
Iain

---

