---
title: "Broken sudo - error 6"
date: 2009-06-01
forum: General Help
---

### Post by Irihapeti on 2009-06-01
I'm running Ubuntu 8.04.1 on an old Toshiba Satellite A10. It's been behaving fine until today.

I hadn't used it for several days. When I started it this afternoon, I found I couldn't open Synaptic. On entering the command in a terminal, I found that I was getting segmentation faults with error 6.

I noticed from the system log that pulseaudio has also been doing a segfault on logon.

I found this in the auth.log:

```
Jun  1 17:38:42 user-laptop2 polkit-grant-helper-pam[6530]: pam_unix(polkit:auth): conversation failed
Jun  1 17:38:42 user-laptop2 polkit-grant-helper-pam[6530]: pam_unix(polkit:auth): auth could not identify password for [user]
```

I haven't tried to add or remove users, or change permissions on any files.

Does anyone know if this can be fixed, or am I just up for a reinstall?

Edit:
I've since realised that there's a good deal else wrong with the installation - taking forever to login, open files and so on. So I've reinstalled.

---

