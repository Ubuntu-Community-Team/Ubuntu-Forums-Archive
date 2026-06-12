---
title: "GDM Display Resolution"
date: 2005-08-14
forum: Desktop Environments
---

### Post by pablito on 2005-08-14
Hi,

What is the "proper" way to change the display resolution of the login desktop (gdm)?  Using the dialog in System|Admin doesn't provide the option. From some posts, I worked out that I could change it indirectly by re-ordering the supported resolutions listed in my xorg.conf file. Is that the only way?

Cheers,
Paul

---

### Post by moises on 2005-08-14
[QUOTE=pablito]Hi,

What is the "proper" way to change the display resolution of the login desktop (gdm)?  Using the dialog in System|Admin doesn't provide the option. From some posts, I worked out that I could change it indirectly by re-ordering the supported resolutions listed in my xorg.conf file. Is that the only way?

Cheers,
Paul[/QUOTE]
 Well, that is the only way I've found
What I ignore is if future upgrades could revoke these changes in the xorg.conf file

---

### Post by zetor on 2005-08-14
dpkg-reconfigure-gdm maybe?

---

