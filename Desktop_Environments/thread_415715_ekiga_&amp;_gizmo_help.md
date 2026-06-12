---
title: "ekiga &amp; gizmo help"
date: 2007-04-20
forum: Desktop Environments
---

### Post by s_p_a_r_k_y on 2007-04-20
I have a gizmo account which can dial out to land lines, but would also like to do video chat, so I would use ekiga for all the calling.

from some other threads I gathered that I need 

account name: gizmo
registrar: proxy01.sipphone.com:5060
user: 17476137xx
password: my password

More options
Authentication login: 174761337xx
realm/domain: proxy01.sipphone.com
timeout:3600

However I get Registration failed: Forbidden.

when I enable the account. Any ideas? I can log in via the gizmo site with the same user info.

---

### Post by s_p_a_r_k_y on 2007-04-21
bumperuni

---

### Post by moschops on 2007-06-22
I have had the same problem - except my error is "Registration Failed".  My Gizmo account works fine with WengoPhone.

---

### Post by moschops on 2007-06-22
Not sure what I was doing wrong last night - could have been my router configuration at home, at work I tried it and I got it working with the following settings (note no port on the regsitrar...)


account name: <whatever you want>
registrar: proxy01.sipphone.com
user: <your 17476137xx sip number>
password: <your password>

More options
Authentication login: <your 174761337xx sip number>
realm/domain: proxy01.sipphone.com
timeout:3600

You do not need to click on the advanced tab - ekiga fills that in with defaults from the top part after you save.

---

