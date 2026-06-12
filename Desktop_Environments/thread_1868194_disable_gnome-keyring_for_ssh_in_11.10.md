---
title: "disable gnome-keyring for ssh in 11.10"
date: 2011-10-23
forum: Desktop Environments
---

### Post by neoubu on 2011-10-23
Greetings,

Does anyone know how to remove the "unlock private key" message for ssh in 11.10?

In previous versions it could be removed from the "Startup Applications" menu and / or gnome configuration.

I find it annoying to have this message popup when trying to ssh from a terminal.  I don't mind that the gnome / graphical environment is hooked into ssh-agent, but I don't want ssh to be interfered by gnome with the keyring otherwise.

Any help is appreciated.  Also I'm using gnome-shell if it matters.

neoubu

---

### Post by CircleCode on 2011-10-26
Hi,

starting programs are now under /etc/xdg/autostart/, I think you could disable startup scripts from here.

On my side, I miss this feature that I was loving under 11.04 and disappeared when I installed 11.10... If somebody have an idea to enable it back...

Greetings.

---

### Post by neoubu on 2011-10-26
Thanks.  That solved it.  I renamed the gnome-keyring-ssh.desktop in that directory and now there's no interference from keyring.

I agree, it would be nice if there was a way to do it from a GUI as there was before, but at least it was simple and clean from the CLI as well.

nU

---

