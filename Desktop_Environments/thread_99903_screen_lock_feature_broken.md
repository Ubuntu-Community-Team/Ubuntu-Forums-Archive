---
title: "screen lock feature broken??"
date: 2005-12-06
forum: Desktop Environments
---

### Post by eitan on 2005-12-06
hello,

  if i lock my gnome screen, i cannot unlock it (system->lock screen).
  i enter the correct password and each time get a "DENIED" 
  response from the system.

  this used to work.  not sure why this is now broken.  i did switch
  to kubuntu for a while and am back on gnome for the moment.

  what could be causing this???

thanks, eitan

---

### Post by sethmahoney on 2005-12-06
[QUOTE=eitan]hello,

  if i lock my gnome screen, i cannot unlock it (system->lock screen).
  i enter the correct password and each time get a "DENIED" 
  response from the system.

  this used to work.  not sure why this is now broken.  i did switch
  to kubuntu for a while and am back on gnome for the moment.

  what could be causing this???

thanks, eitan[/QUOTE]

Do you by any chance have multiple keyboard layouts installed?  I know if I leave mine in cyrillic and the screen locks I can't get back in unless I change back to English.

---

### Post by eitan on 2005-12-06
thanks for the tip.

just checked the contents of the 'layout' tab for my keyboard preferences. 
i have only one layout installed:  u.s. english

i will be sure to post another entry if/when i figure out what's going on.

---

### Post by Ryence on 2005-12-14
bump!  

I'm having the same issue.  I have not installed Kubuntu, but I was playing around with Kerberos and Samba.  Locked my screen and now the correct password gives me a big 'DENIED'

Anyone have any suggestions? 

Thanks in advance!

---

### Post by eitan on 2005-12-20
i got this resolved.  sorry i forgot to post a reply.

resetting the password by using the commandline passwd command resolves this issue.  don't know why but it does.

---

