---
title: "I totally screwed myself...plz help, chmodded /usr"
date: 2005-12-03
forum: Desktop Environments
---

### Post by Dark_Link2135 on 2005-12-03
I did something completely stupid....I was messing around trying to get sound in q3 and i was getting pissed at screwing with all the folder permissions, so i ran

sudo chmod 770 /usr

Needless to say i totally screwed over my window manager, now all i can work from is the prompt....id just reinstall but i have vital files that I *MUST* have.....like a 10 page essay i just finished up tonight...:(

Is there anything I can do?

i tried running 
apt-get install gnome
but i couldnt connect to the server at all.

Right now im using my windows laptop *blegh*

---

### Post by doitashimashite on 2005-12-03
Permissions on /usr should be 0755 so try this:

sudo chmod 0755 /usr

---

### Post by xmastree on 2005-12-03
[QUOTE=doitashimashite]sudo chmod 0755 /usr[/QUOTE]Spoilsport! I was gonna tell him it's gone forever... :twisted:

No, all you've done is disallowed anyone other than root to read that directory. No big deal.

But why was your work in /usr in the first place rather than your home directory? if it's 755 you still don't have write permission there.

---

### Post by doitashimashite on 2005-12-03
[QUOTE=xmastree]
But why was your work in /usr in the first place rather than your home directory? if it's 755 you still don't have write permission there.[/QUOTE]

That's not what he said, he said that he screwed up his window manager, which is not unlikely when you disable read- and execute permissions on /usr for anyone other than user (or group) root..

---

### Post by xmastree on 2005-12-03
Ah, I understand now.

---

