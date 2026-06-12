---
title: "Keeping /home directory clean?"
date: 2009-05-11
forum: General Help
---

### Post by MysticalRiotCandy on 2009-05-11
I want to keep visible files (random screenshots, .odt, etc.) from saving into my ~/ directory.  I still need the hidden files to be there, however.  Is there a way for me to disable visible (as in, web browser, nautilus, etc.) from placing files in my home directory, but for background processes (like configuration files of my web browser or nautilus) to still be able to save into it?

---

### Post by pro003 on 2009-05-11
if you press ctrl+H you'll hide/view your hidden files... am not sure am following you but suppose thats whats bothering you...

---

### Post by Triptol on 2009-05-11
I would not recommend this, but you can try the following: change the rights on your homedrive so nothing can write there:
```
chmod 500 /home/[your_username]
```
Now nothing can write on that level, but all your programs will still be able to access the existing subdirs.
This will cause a problem as soon as any new program will try to create a directoy or a file directly in your homedir. And I am not sure whether the X server does this on logon (.Xsession files and so on) so this might completely break your installation. (Nothing you won't be able to fix though)

AGAIN: I WOULD NOT RECOMMEND THIS.

---

### Post by MysticalRiotCandy on 2009-05-11
> **pro003 said:**
> if you press ctrl+H you'll hide/view your hidden files... am not sure am following you but suppose thats whats bothering you...
Okay.  By default, pretty much every program I have saves their files to /home/user (me).  I *could* go into every program and change their save locations, but I'd much rather be able to lock the home directory from the apps being able to save their.  So that all I can see is Documents, Pictures, Music, Videos, Public, etc.  However, if I just lock it out so that files and folders cannot write to /home/user, then all the hidden configuration files like .local, .gnome2, .bashrc, etc., wouldn't be able to save.  In other words, that would just create more problems, such as when I try to add a new theme, it won't be able to save.  So I want to know if it's possible to lock out my home directory from apps that I use like Epiphany and Open Office, but leave it open to their configuration files to save?

To post above: yeah, that's the problem I ran into before.

---

### Post by Triptol on 2009-05-11
As stated before: if you change the rights on your home directory, you will not be able to create any new files/folder directly in you home directory. However: the subdirectories will remain unchanged.

If you just don't want to see the hidden files, then ctrl+H will do.

---

