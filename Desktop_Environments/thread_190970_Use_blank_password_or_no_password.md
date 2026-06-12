---
title: "Use blank password or no password?"
date: 2006-06-06
forum: Desktop Environments
---

### Post by daniel_bergamini on 2006-06-06
How do I configure ubuntu 6.06 allow and use blank passwords or no password for users? I believe it has something to do with the PAM configuration but haven't thus far been able to figure it out. I can passwd -d the user or manually delete the password field in /etc/shadow, but that user can not authenticate.

I understand it's not particularly secure, but it's something I would like to do. If you must know it's on an old tablet which needs to be docked to use a keyboard, and I would like to run sudo applets without typing on the on-screen keyboard. There is a known bug so the GOK doesn't work which means that it doesn't autostart at the password screen when enabled in the accessability page.

Oh yeah, even if I configure it to not lock the screen, after a hibernate, it still requires a password. Please advise. Thanks in advance.

---

### Post by tonyr on 2006-06-07
Here is an interesting duscussion on the subject.
[http://www.ubuntuforums.org/showthread.php?t=176180]("http://www.ubuntuforums.org/showthread.php?t=176180")

---

### Post by daniel_bergamini on 2006-06-07
Exactly what I was looking for, thank you. I couldn't find it from a search, and honestly still can't but at least I have a link. Too bad nobody can reply to that post. Hopefully other's can find this post and follow the link. I'll attempt to provide the solution here:

[quote=mlind]
okay, this seems to work, but feels like a hack.. 


```

sudo touch /etc/gdmnopassusers
echo $USER | sudo tee -a /etc/gdmnopassusers
sudo cp /etc/pam.d/gdm /etc/pam.d/gdm.orig
sudo sed '/common-auth/i\auth    sufficient      pam_listfile.so file=/etc/gdmnopassusers   sense=allow     item=user' /etc/pam.d/gdm > /etc/pam.d/gdm

```
basically just 
*create /etc/gdmnopassusers file and insert your daughters username there
*add directive auth sufficient pam_listfile.so file=/etc/gdmnopassusers sense=allow item=user to /etc/pam.d/gdm file, before @include common-auth directive

logout, and try to login. No password should be prompted.
[/quote]

I'll test it as soon as I get the chance and provide feed back. Thanks again.

---

