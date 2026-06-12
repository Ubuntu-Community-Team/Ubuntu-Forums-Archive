---
title: "Password Omelot"
date: 2005-08-17
forum: Desktop Environments
---

### Post by Chan on 2005-08-17
Somehow, my passwords are not working , where they were for a few weeks.  What is the path of least resistance - Can I do something as  ROOT that will straighten the mess out, or do I have to install a new copy of Kubuntu?  (I'm also having trouble getting into Superuser Mode, because that password is screwed up, also.)

Any kind words of advice would be appreciated.  I'll bet a few others have run into this situation, and could give me a way out of a major re-install.  Thanks, Chan ](*,)

---

### Post by Juergen on 2005-08-18
Boot into 'recovery-mode' or with the live-CD.

Then you can check if /etc/passwd, /etc/shadow and /etc/group are OK and maybe reset the passwords.

There might also be backups of these files, but don't just copy them back. You might lose users or groups.

---

