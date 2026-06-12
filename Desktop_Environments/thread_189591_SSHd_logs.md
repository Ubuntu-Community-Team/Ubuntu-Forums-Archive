---
title: "SSHd logs"
date: 2006-06-05
forum: Desktop Environments
---

### Post by xpmaniac4ever on 2006-06-05
Where does Dapper save the successfull/failed logins for sshd ?

---

### Post by Whitman on 2006-06-05
I believe it's /var/log/auth.log

---

### Post by xpmaniac4ever on 2006-06-05
It`s not there. I can`t see any accepted/failed logins there. Does anyone know where they really are ?

---

### Post by mat1t on 2006-06-05
it's in /var/log somewhere. There can't be that many files in there. Easiest way to find it is going to be to try and log in with a username you know will fail, then go into the directory, and type

"grep username *"

and see what files it brings back. (obviously replace username with the username you tried)

I'd try and be more helpful, but I'm on a windows box at work! :)

---

### Post by xpmaniac4ever on 2006-06-05
Thanks mat1t, but I tried your suggestions using grep and they didn`t work. May it be that the sshd keeps its logs in another directory or maybe something should be changed to allow it to log logins ?

---

### Post by mat1t on 2006-06-05
hmm. One issue could be that the command I gave you there for grep doesn't search sub-directories.

I'll be home in about an hour, so I should be able to check it around then and get back to you if no-one else has done so before then.

---

### Post by xpmaniac4ever on 2006-06-05
Ok ;)

---

### Post by carlosqueso on 2006-06-05
it lives in /var/log/auth.log  along with all the other login and logout attempts.  ```
cat /var/log/auth.log | grep sshd | less
``` will let you look at just the ssh logins -and outs.

---

### Post by mat1t on 2006-06-05
yep, I've got it in /var/log/auth.log as well

Bear in mind that you will need to sudo or su (be root basically) to view these files.

---

### Post by xpmaniac4ever on 2006-06-05
OK but for some reason the login events weren`t logged for me, dunno why. I`m now reinstalling Dapper :D Hope it`ll work. Thanks everyone. ;)

---

