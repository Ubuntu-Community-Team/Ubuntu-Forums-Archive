---
title: "unable to login - just kicks me out"
date: 2009-01-30
forum: General Help
---

### Post by scotty32 on 2009-01-30
Hi,

I've tried doing a search but cant find any answers.


This morning I logged in printed some files off for my brother, but half way through the Printer Server disconnected and I was unable to reconnect.

Decided to restart, login screen appeared and the printer set off printing but when I tried to login it just took me back to the login screen.

Even when I press Ctrl + Alt + F1 and try to login to the terminal it, it tries to load then just returns asking me to login.

I also tried Recovery Mode, Im able to start as Root and view GUI as Root but I cant get into my account.



What can I do?

---

### Post by scotty32 on 2009-01-31
Can anyone help?


I really dont want to have to Reinstall

---

### Post by Iowan on 2009-01-31
If you can login as root via recovery mode, try resetting your password. Check **man passwd** for details.

---

### Post by geirha on 2009-01-31
I have no idea what might be wrong. But try booting into recovery mode, and in a root shell, run ```
sudo -u *yourusername* -i
```
Does that work? Does it give any warnings or error messages?

Also, from the root shell, create a new user with ```
sudo adduser *newusername*
```
Reboot and try to log in with that new user. Does that work?

---

### Post by scotty32 on 2009-01-31
Thanks for the help but tried adding a new user (under root) thinking my user account was currupt but that does the same. When ever i Login via GUI im just taken to the Login page again with no errors. if i type the wrong password it does give an error.

Even under the terminal (Ctrl + Alt + F1) it just keeps asking me to login - no errors.


Can I ask what does that first command does? (sudo -u username -i)

---

### Post by geirha on 2009-01-31
It changes user to *username*. Somewhat like logging in, but without requiring a password (since root has full access)

Have you checked how much disk space you have?
```
df -h
```

---

### Post by scotty32 on 2009-01-31
I have my system and home in different partitions.

the home partition is around 8gb free - the root system im not sure but it should be a fair bit so i dont think its hard drive full.

---

### Post by scotty32 on 2009-02-01
the "sudo -u yourusername -i" thing worked and I was able to do "startx" and get to my desktop.

But alot of things are disabled (switch user applet / admin menu items) and the keyboard layout is US instead of UK - I assume this is because im still under Root?

Since alot of things are disabled I also assume it isnt safe to my desktop as normal?

---

### Post by geirha on 2009-02-01
Really odd. Have you uninstalled any packages lately? Might be you've accidentally uninstalled a package that depends on some important package. Try installing the ubuntu-desktop package. It should reinstall any important packages if that is the case. In the root shell in recovery mode: ```
aptitude install ubuntu-desktop
```

Also, does group membership of your user look ok? ```
groups *yourusername*
``` You should at least be a member of the admin group.

---

### Post by scotty32 on 2009-02-01
The only thing I did on friday was poke around the CUPS web admin page when it seemed to crash.

I restarted so it would reload CUPS but then once it had restarted I had these issues.


I might of done some updates on Thursday night but I cant really remember, and if I did i cant remember what they was for.


these are my groups: "*username* adm dialout cdrom plugdev lpadmin admin sambashare"

---

### Post by geirha on 2009-02-01
Have you tried booting an older kernel? It might be those updates installed a new kernel, so try booting the previous kernel.

---

### Post by scotty32 on 2009-02-01
Already tried that, no luck. 

Though my Grub menu hasnt changed so I dont think i got a new kernal.

---

