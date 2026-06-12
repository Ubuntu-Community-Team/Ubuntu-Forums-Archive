---
title: "Pidgin Buddy List opens at startup"
date: 2009-05-15
forum: General Help
---

### Post by rock4christ on 2009-05-15
Im running 9.04, and I have tried the pidgin-extprefs trick and the pidgin-plugin-pack one. I cant get it to not popup on startup.

---

### Post by emacbri on 2009-05-15
Hi,

Try looking for an option in Pidgen's prefs.:)

---

### Post by rock4christ on 2009-05-15
nope. no option there.

---

### Post by rock4christ on 2009-05-15
anyone have any ideas?

---

### Post by trpnblies7 on 2009-05-15
Have you checked Startup Programs under Preferences to see if it happens to be in that list for some reason? If it is, uncheck it.

---

### Post by rock4christ on 2009-05-15
no, I want pidgin to start at startup, I just don't want the buddy list popping up every time I boot.

---

### Post by dazzler on 2009-05-15
> **rock4christ said:**
> no, I want pidgin to start at startup, I just don't want the buddy list popping up every time I boot.

Amen to that you ever get this sorted out?

---

### Post by rock4christ on 2009-05-15
> **dazzler said:**
> Amen to that you ever get this sorted out?

nope. hoping someone will have a sol'n

---

### Post by rock4christ on 2009-05-15
nobody has a solution? dang!

---

### Post by michy99 on 2009-05-15
According to this:

[http://sprayfly.com/2008/08/21/launch-pidgin-minimized-on-startup-in-ubuntu-hardy-804/](http://sprayfly.com/2008/08/21/launch-pidgin-minimized-on-startup-in-ubuntu-hardy-804/)

pidgin is trying to minimize before the system tray is initialized. Shows how to set up a script to fix it.

---

### Post by rock4christ on 2009-05-15
when I do that, pidgin doesn't start

---

### Post by michy99 on 2009-05-15
What happens if you try to run the script from the command line?

---

### Post by rock4christ on 2009-05-15
it starts, and terminal sits forever with a blank flashing line below where I entered the command.

---

### Post by michy99 on 2009-05-15
What is the command you put in sessions?

---

### Post by rock4christ on 2009-05-15
also, when I start the system, I see the sys tray twitch like it is trying to load it a few times

---

### Post by rock4christ on 2009-05-15
I have no 'Sessions'

I assumed it wanted 'Startup Applications'

the command was '~/pidgin.sh'

---

### Post by rock4christ on 2009-05-15
is the fact that it is in startup apps the prob?


just in case, here is the contents of the file:
#!/bin/bash
sleep 30
pidgin

---

### Post by rock4christ on 2009-05-16
anyone?

---

### Post by rock4christ on 2009-05-16
is everything right? if so, any other ideas?

---

