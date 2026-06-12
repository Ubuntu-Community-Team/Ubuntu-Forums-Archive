---
title: "login cron task and delaying an app startup"
date: 2009-05-18
forum: General Help
---

### Post by rock4christ on 2009-05-18
1. how would I create a cron task that runs at every login(but waits about 25 sec) to automount a drive
2. how would i delay deluge's sartup by about 60 sec

---

### Post by rock4christ on 2009-05-18
I have received a suggestion to create a .bash_profile  in my home folder containing code to do the above. would that work in this case? if so, what would the bash script be? also, i was told .bash_profile runs at logon. is that true?

---

### Post by rock4christ on 2009-05-19
bump

---

### Post by rock4christ on 2009-05-19
anyone?

---

### Post by niokei on 2009-05-25
Hi!
Make a new text file save it as startme.sh and copy this in it:
```
#!/bin/bash
sleep 5  && deluge &
sleep 6  && checkgmail

```Basically the number after the "sleep" should mean the delay in seconds (but in my experience its a little bit off), however the higher the number is it's delayed more.
After the "&&" you have to write the command of your choosen app etc. 
And finally the "&" at the end means that the program will start in the background. (In this case deluge would start without the "&" symbol with popping up in my face at login, and I dont want that.

If you're ready with this script you have to allow executing it in the properties.
Than go to System-Preferences-Startup Applications Preferences, click on add, and browse for the file you've just made (mine is in home/username/.scripts/), name it and add it.

Now on login the system executes this script wich should start the applications as you set it up.

Hope it helps!

---

