---
title: "Ubuntu Software Center says an app is installed, but the Terminal says it isn't"
date: 2014-04-03
forum: Gaming &amp; Leisure
---

### Post by MelPhleg on 2014-04-03
Ubuntu Software Center says an app is installed, but the Terminal says it isn't installed.

This what I put in the terminal, & what it spit out: ~$ dpkg -l | grep -i personalitypremiumlite
ii  personalitypremiumlite                        1.0.0-0ubuntu1                               Luxury pack of personality tests & games. Both fun & serious packs.
ii  personalitypremiumlite-bin                    1.0.0-0ubuntu1                               Luxury pack of personality tests & games. Both fun & serious packs.
~$ cat $(dpkg -L personalitypreiumlite | grep '\.desktop$') | grep ^Exec 
Package `personalitypreiumlite' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.


Now what do I do?

Thanks

---

### Post by steeldriver on 2014-04-03
You have a typo ... personality[COLOR=#ff0000]**preium**[/COLOR]lite

---

### Post by MelPhleg on 2014-04-03
oops

---

### Post by MelPhleg on 2014-04-03
hmm...well, that didn't help either.
it says on the "[SIZE=1]I installed an app but I don't know how to run it. Help?[/SIZE]" FAQ, that the prompt should come up with an Exec= to put in a command. But the terminal only shows the blinking rectangle, no Exec= anywhere.

---

### Post by MikeCyber on 2014-04-04
In a term: whereis myapp
if it's in the binary path you could do:
which myapp
If it's not in the /usr/bin etc. you have to load it manually alike:
./path/to/myapp
with wildcards something alike:
./pa*/to/mya*
or cd to where the app is and do: ./myapp

---

