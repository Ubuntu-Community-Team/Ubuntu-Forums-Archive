---
title: "Windows XP machine no longer showing in findsmb"
date: 2009-03-02
forum: General Help
---

### Post by dannyboy79 on 2009-03-02
Hello all,
I don't know what's is going on but I had samba all setup with 1 ubuntu Feisty machine, 1 Mythbuntu Gutsy machine and 1 Windows XP Pro machine. THe windows machine has a couple shares on it. Samba is setup with security = user and it was all working at one time. Now all of sudden it doesn't. I use the command:
```
findsmb
```
and the windows machine doesn't even show up in the list? Windows XP  has simple file sharing disabled. The usernames and passwords for all 3 machines are the same. The smb passwords for the 2 ubuntu machines are the same. I don't know how to trouble shoot this. Can anyone help?
When I do:
```
smbclient -L WINXP
```
I get this in return:
Error connecting to 192.168.0.4 (No route to host)
Connection to WINXP failed
Any help would appreciated.

---

