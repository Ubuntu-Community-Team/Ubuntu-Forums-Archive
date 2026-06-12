---
title: "Boot Into Shell"
date: 2005-08-07
forum: Desktop Environments
---

### Post by Subfix on 2005-08-07
How do I go about booting directly to the shell instead X?
I accidently messed up my xorg.conf and I need to root shell and fix it ...
Thanks.

---

### Post by Subfix on 2005-08-07
Nevermind, I read [http://ubuntuguide.org/](http://ubuntuguide.org/)

Great documentation by the way... wow!  :)

---

### Post by Subfix on 2005-08-07
Ack... how do I chmod xorg.conf +rw for all users so I can mount it in Mandriva and edit it?

OR

Is there an editor in the shell provided by the 'rescue' command? I can't find one...

Help!

 ](*,)

---

### Post by Teren on 2005-08-07
[QUOTE=Subfix]Ack... how do I chmod xorg.conf +rw for all users so I can mount it in Mandriva and edit it?

OR

Is there an editor in the shell provided by the 'rescue' command? I can't find one...

Help!

 ](*,)[/QUOTE]
 +rw for all users: sudo chmod 666 xorg.conf  OR sudo chmod a+rw xorg.conf

editor: nano

---

### Post by Subfix on 2005-08-07
Ah ha! Thank you very much.

---

