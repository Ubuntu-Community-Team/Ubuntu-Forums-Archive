---
title: "GNOME remote desktop - black screen problem"
date: 2005-09-23
forum: Desktop Environments
---

### Post by SimenT on 2005-09-23
Hi all!

First of all I'd like to thank all forum administrators and participators for creating an absurdely useful community and ubuntu resource. This forum has helped me countless times already and I am hoping that my first post will get noticed by a bright soul or two.

**My problem:**
I am trying to remotely connect to GNOME libvncserver running a no-ip client from a Windows XP PC. Connection is OK, but all I get is a black screen with a square, white cursor. I am using RealVNC, but similar errors appear when using TightVNC.

**My settings:**
[list]
[*]I have defined a password for desktop sharing in the GNOME configuration tool, but neither VNC clients prompt me for one.
[*]The remote desktop is set never to lock or prompt for password.
[*]Remote desktop color depth is 16.
[/list]

**A peculiar thing:**
If I restart the local VNC client, nothing happens; no black screen, no prompt. The client just dissappears but lies dormant in the Windows task manager. This happens with both clients.

Any help would be greatly appreciated!

Thanks

---

### Post by SimenT on 2005-09-23
[QUOTE=SimenT]Hi all!

First of all I'd like to thank all forum administrators and participators for creating an absurdely useful community and ubuntu resource. This forum has helped me countless times already and I am hoping that my first post will get noticed by a bright soul or two.

**My problem:**
I am trying to remotely connect to GNOME libvncserver running a no-ip client from a Windows XP PC. Connection is OK, but all I get is a black screen with a square, white cursor. I am using RealVNC, but similar errors appear when using TightVNC.

**My settings:**
[list]
[*]I have defined a password for desktop sharing in the GNOME configuration tool, but neither VNC clients prompt me for one.
[*]The remote desktop is set never to lock or prompt for password.
[*]Remote desktop color depth is 16.
[/list]

**A peculiar thing:**
If I restart the local VNC client, nothing happens; no black screen, no prompt. The client just dissappears but lies dormant in the Windows task manager. This happens with both clients.

Any help would be greatly appreciated!

Thanks[/QUOTE]
 I think I figured it out. It was as easy as using the configuration tool on the host ubuntu machine. I found the key "/desktop/gnome/remote_access/prompt_enabled" and turned it off. I will confirm this later when I have a chance to test it.

---

