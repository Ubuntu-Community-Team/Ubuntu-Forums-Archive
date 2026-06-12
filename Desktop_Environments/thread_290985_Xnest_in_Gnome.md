---
title: "Xnest in Gnome"
date: 2006-11-01
forum: Desktop Environments
---

### Post by gerowen on 2006-11-01
Ok, I would like to know how to use Xnest.  I like to play with login screens, I've made a few and I like to be able to test them without actually having to log out and back in.  However, I'm having a problem, the same one I had in Fedora Core 5 before I came to Ubuntu.  When I run Xnest -query mastermachine :20 I get a nested X server with a gray background, but no gdm screen.  If I run gdmXnest it starts one with a solid black background and no login screen.  If I use gdmXnest I can send apps to the nested X server.  For example gedit --display :20 will make gedit open in the nested server, but if I start it with Xnest -query mastermachine :20, I cannot send applications to it.  If I try I get:
```

Xlib: connection to ":20.0" refused by server
Xlib: No protocol specified

cannot open display: :20

```
I've never used Xnest before, so any help is appreciated.

---

### Post by jpkotta on 2006-11-01
```
gdmflexiserver --xnest
```

---

### Post by gerowen on 2006-11-01
Thank you, that got it.

---

### Post by Leed on 2006-11-20
Been using this for a while, mainly for login on with different users into the Gui... 

However since the last upgrade, login doesn't work anymore, after writing login and password it just jumps back to the login screen. On false login I get an error, but with the proper password it just goes back to the login screen as if nothing ever happened. Changing session to KDE or Failsafe Gnome doesn't help. 

Anyone know what could be wrong?

Best regards
Dave

---

