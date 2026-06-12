---
title: "Authomatic log in problem!"
date: 2010-06-24
forum: Desktop Environments
---

### Post by philmar on 2010-06-24
Im using Ubuntu 9.10[COLOR=Black](Karmic Koala) installed in VMware
I set my login as authomatic from the last time i opened my OS. and the next time i open it did'nt required password but the desktop did not comes out insted [/COLOR][COLOR=Black]an error command comes out.
please see attachments!
I'm using "philmar" as my login name and there is 2 users from my OS
[/COLOR] [B][URL="http://releases.ubuntu.com/karmic/"] 
[/URL][/B]

---

### Post by VH-BIL on 2010-06-24
This is solved on this thread:
[http://ubuntuforums.org/showthread.php?t=949750](http://ubuntuforums.org/showthread.php?t=949750)

---

### Post by philmar on 2010-06-25
Thanks! already solved but in a different way!

[http://ubuntuforums.org/showthread.php?t=1505264&highlight=log+in+problem](http://ubuntuforums.org/showthread.php?t=1505264&highlight=log+in+problem)

i used  [COLOR=Red]startx[/COLOR] after rebooting just to show my desktop and typed in terminal:


 
ls -la /home/your_id | grep Private
  
then restart!

---

### Post by VH-BIL on 2010-06-25
Good to hear!

---

### Post by VH-BIL on 2010-06-25
Good to hear!

---

### Post by philmar on 2010-06-25
> **VH-BIL said:**
> Good to hear!
Thanks a lot!

---

