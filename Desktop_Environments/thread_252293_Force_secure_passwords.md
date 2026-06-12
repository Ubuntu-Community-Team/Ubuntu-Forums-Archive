---
title: "Force secure passwords?"
date: 2006-09-06
forum: Desktop Environments
---

### Post by devnulljp on 2006-09-06
Looking for a way to force my users to choose secure passwords. 
At setup I give them random passwords like G^s%i1s_*7FsT but as soon as they log in they change to simple passwords like 1234 or cat or their username...so it's a cracker's dream.
I've seen systems where your password is checked for quality in the past (old RedHat used to force secure passwords).
I'd like to enforce a minimum length of 8 chars, must include at least 1 digit and one of !@#$%^&*()_+
Anyone know howto in (k)ubuntu?

---

### Post by devnulljp on 2006-09-06
Answering my own question:
Install libpam-cracklib
edit /etc/pam.d/common-password

comment out the line 
password   required   pam_unix.so nullok obscure min=4 max=8 md5

Remove comment from the line
password required         pam_cracklib.so retry=3 minlen=6 difok=3

---

### Post by mssever on 2006-09-06
I did a bit of looking around. It appears that pam is what you're looking for. Look at /etc/pam.d/common-password where password rules are stored. You'll probably want to read whatever man pages you can find about pam. You could also Google pam howto.

EDIT: you beat me to it :)

---

### Post by devnulljp on 2006-09-07
Thanks,
Google is my friend ;-)

---

