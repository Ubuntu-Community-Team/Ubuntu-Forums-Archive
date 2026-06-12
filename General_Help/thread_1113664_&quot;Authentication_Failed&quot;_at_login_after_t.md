---
title: "&quot;Authentication Failed&quot; at login after trying LDAP"
date: 2009-04-01
forum: General Help
---

### Post by tproberts on 2009-04-01
Hello,

I tried setting up my laptop as an LDAP client and failed. I believe I was able to get the computer to join the domain, but when logging in to the computer afterwards, gnome launched very slowly, and reported errors (only one I remember was a Nautilus error suggesting I kill bonobo). I tried reversing the client config by removing libnss_ldap with synaptic.

Now I can't even log in. I get an "Authentication Failed" message at the login window right as soon as I enter my name - I don't get promted to enter a password. If I CTRL-ALT-F1 I get the login prompt in shell, but again can only enter the username and get a failure message instead of being prompted for a password.

Can somebody PLEASE help me get this back to the way it was before? I'm giving up on LDAP and just want to be able to log into my computer again.

I've tried searching and find many references to comment out the line:
@include common-pamkeyring

but it isn't in my pam.d/gdm file. Further, pam_ldap.so does not return when I try to 'locate pam_ldap'.

By the way, 4 of my files in /etc/pam.d/ show recent modification dates: common-account, common-auth, common-password, and common-session. Their contents are:
[common-account]
account sufficient pam_ldap.so
account required pam_unix.so

[common-auth]
auth sufficient pam_ldap.so
auth required pam_unis.so nullok_secure use_first_pass

[common-password]
password sufficient pam_ldap.so
password required pam_unix.so nullok obscure min=4 max=8 md5

[common-session]
session required pam_unix.so
session required pam_mkhomedir.so skel=/etc/skel/
session optional pam_ldap.so
session optional pam_foreground.so

Thanks in advance for your assistance!
Tom

---

### Post by tproberts on 2009-04-02
I'm wondering if it would be easier at this point to reinstall. However, I would really like to backup my home directory first. Is there a way to reinstall Ubuntu without reformatting or overwriting my home directory?

---

### Post by Augsburg on 2009-05-05
Hit
<ctrl> + <alt> + <F2>

Then log in locally and un-edit the files.  You can even kill gdm or delete the required file to start gnome again (type startx).

---

