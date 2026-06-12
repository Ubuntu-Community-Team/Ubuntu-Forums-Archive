---
title: "Login with SSSD not working with GDM"
date: 2024-01-29
forum: Desktop Environments
---

### Post by simonjcarr on 2024-01-29
I have installed GDM and ubuntu-desktop on Ubuntu 22.04. The server is added to an Active Directory Domain. 

When I try to login to desktop using the AD, I get taken back to the login screen but don't see any errors on the screen. When I view the logs, I see that there were permission errors creating local folders for the AD User.

It looks like a home folder is not being created when a AD user tries to login. What settings do I need to change to create a new home folder when an AD user logs in.

---

### Post by simonjcarr on 2024-01-29
I solved this by a bit more googling. :P

I added the following to /etc/pam.d/common-session
session required    pam_mkhomedir.so skel=/etc/skel umask=0022

---

