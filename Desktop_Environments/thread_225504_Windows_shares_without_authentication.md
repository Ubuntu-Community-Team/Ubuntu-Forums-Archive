---
title: "Windows shares without authentication"
date: 2006-07-29
forum: Desktop Environments
---

### Post by Gentist on 2006-07-29
I have a basic question about Windows shares and Ubuntu.

I've been trying to mount Windows shares via "Places->Connect to Server...", with some success. I can see the shared folders, but I can't browse them. Every time I try to browse anything, it asks for a username and password. Now, when accessing this using a Windows OS, I don't need any authorization, so I'm guessing this has something to do with the Windows permissions. Why is Gnome (samba) asking me for a username and password, and how do I make it not ask me for it? To my knowledge, there is no username and password for any of the shared folders, so I can't really provide one.

---

### Post by themoebius on 2006-07-30
I'm not sure I've ever had to use a username and password, but I use the network browser in Gnome and not the connect to server. You might try 'guest' with no password.

---

### Post by Gentist on 2006-07-30
I've already tried guest without a password. I think that's the default behaviour actually.

The reason as to why I don't browse for the network is that it doesn't actually show up (IIRC it's not configured to do so). I connect to it via the IP address when I use Windows too, and that's not a problem.

Does Windows use some weird authentication method, like only allowing those in the same group to access the shared folders, or is it the Linux implementation that's buggy?

---

