---
title: "setting samba read/write permissions for seperate users"
date: 2006-10-02
forum: Desktop Environments
---

### Post by phildacey on 2006-10-02
Hello all, 

I'm having trouble finding out how to share folders with specific access permissions for each user so I thought I'd ask. I'm using samba and this is the set up:

[Ubuntu box] - should be able to read/write to all folders shared on [server box]

[Xp Box]     - should be able to read/write to all folders shared on [server box]

[xp Box2]    - should have read only access to all folders shared on [server box]

[xp Box3]    - should have read only access to all folders shared on [server box]

[xp Box4]    - should have read only access to all folders shared on [server box]

Eventually, I'll get round to sharing the home directories on all machines but at the moment I just want to achieve the above. Thanks in advance : )

---

### Post by phildacey on 2006-11-06
in case anybody else is wondering why they can't write to their samba shares: my problem was that the samba user trying to write to the directory didn't have access rights, so sudo chown <user> <file/directory> fixed this for me.

---

### Post by dannyboy79 on 2006-11-06
> **phildacey said:**
> in case anybody else is wondering why they can't write to their samba shares: my problem was that the samba user trying to write to the directory didn't have access rights, so sudo chown <user> <file/directory> fixed this for me.


wait, how is that a solution, if you have 4 different users than you obviously can't have the folder owned by all the users? You stated that you wanted ubuntu box to have read/write for all shared folders on the server as well as winxp box, if these 2 have different users, than chowning a folder or file with a username wouldn't allow the other to haev write access??? Can you better explain how you solved this as I have this issue as well. Thanks. I think you have to add all the users to the ubuntu box that you want to have write access to the share and then create a smb.conf line that states, writable users = danna daniel suzie

i don't think it writable users but something like that, I would have to do man smb.conf and read up on it I guess but I was hoping you could help to save me from reading the man

---

