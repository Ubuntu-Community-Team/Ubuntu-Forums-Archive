---
title: "??? outgoing mail port ???"
date: 2005-08-22
forum: Desktop Environments
---

### Post by sickdude on 2005-08-22
ok the problem is that i use the outgoing mail on my ubuntu box, well that is not a problem it works like hell. but the real problem is that my ISP blocks outgoing mail, so i thought the only thing that they will block is the outgoing port. 

well i dont know for sure but i want to change the port to check if im right, and so that i can mail again because im in a pickle about this.

if you have any other bright ideas please let me know

thnx in advance  ;-)

---

### Post by heimo on 2005-08-22
If your ISP is blocking mail to outside mail servers (others than their smtp servers), they're not blocking client side ports, they're blocking connections to port 25, which is default SMTP port on mail servers (the "port" that receives your e-mail messages).
 
Solution: Use ISPs smtp-servers for outgoing mail


EDIT: Oh, and i think this is on wrong forum. :-?

---

### Post by tonym on 2005-08-22
You can still use your own mail system (eg postfix or exim) but configure it to forward to your ISP's servers.

---

### Post by sickdude on 2005-08-22
[QUOTE=tonym]You can still use your own mail system (eg postfix or exim) but configure it to forward to your ISP's servers.[/QUOTE]

ok but which .conf file do i need to edit? maybe dumb question but postfix isnt my strongest point  :-?

---

### Post by sickdude on 2005-08-23
have been looking in the conf files but i cant seem to see the right conf file.

and if my ISP blocks outgoing mail how can i forward the mail from my ubuntu box to the external mailserver. this has to be the same port right? ](*,)

---

