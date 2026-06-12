---
title: "Help with X Server"
date: 2006-01-30
forum: Desktop Environments
---

### Post by Mundofr on 2006-01-30
hello, im really a newbie to all of this, waht ive done is tried to install a new video driver in my Dell Inspiron 2650.. and now my real problem, after a few tries to run the installer ive got an error that said that the Xserv was actually being used, and then some guy told me to press Ctrl + Alt + BackSpace.. after that i dont know what ive done.. i think i reconfigured my comp i dunno.. and now when i start my computer i only get the terminal, then i type in X and the Xserv seems to start up but it doesnt, it says 'Xerv is disabled now.  Restar GDM when it is configured'

Does anybody knows how to fix this problem?? i think i should run the configuration setup again but i dont know how, i cannot remeber the command =( plx help 

/Mundofr

---

### Post by dcstar on 2006-01-30
[QUOTE=Mundofr]hello, im really a newbie to all of this, waht ive done is tried to install a new video driver in my Dell Inspiron 2650.. and now my real problem, after a few tries to run the installer ive got an error that said that the Xserv was actually being used, and then some guy told me to press Ctrl + Alt + BackSpace.. after that i dont know what ive done.. i think i reconfigured my comp i dunno.. and now when i start my computer i only get the terminal, then i type in X and the Xserv seems to start up but it doesnt, it says 'Xerv is disabled now.  Restar GDM when it is configured'

Does anybody knows how to fix this problem?? i think i should run the configuration setup again but i dont know how, i cannot remeber the command =( plx help 

/Mundofr[/QUOTE]
sudo dpkg-reconfigure xserver-xorg

Next time, do a forum search and you will probably get the answer straight away.

---

### Post by Mundofr on 2006-01-30
thanks, now im reconfiguring everythign but im getting this error:

xserv-xorg postinst warning: overwriting possibly-customised configuration file; 
backup in /etc/X11/worg.config.200601301843

can you plx help me?? =S

---

### Post by dcstar on 2006-01-30
[QUOTE=Mundofr]thanks, now im reconfiguring everythign but im getting this error:

xserv-xorg postinst warning: overwriting possibly-customised configuration file; 
backup in /etc/X11/worg.config.200601301843

can you plx help me?? =S[/QUOTE]
It's a warning, it has told you the original file has been saved under a different name.

---

### Post by RAOF on 2006-01-30
[QUOTE=Mundofr]thanks, now im reconfiguring everythign but im getting this error:

xserv-xorg postinst warning: overwriting possibly-customised configuration file; 
backup in /etc/X11/worg.config.200601301843

can you plx help me?? =S[/QUOTE]
That's not an error, that's a warning.  It's saying "I'm now writing the configuration file.  It looks like it's been modified since I last wrote to it.  If you wanted to keep that customization, you can find it in this other file."

---

### Post by Mundofr on 2006-01-30
yeah but after this message the config program unloads, and then after that i tried running X and ive got the same thing, but i runeed it twice and i got a yellowish screen with an X mouse pointer =S is this good or bad?

---

### Post by Mundofr on 2006-01-30
NVM! cant belive it! after that i restarted teh computer and it appears to be working again =D.. ps im never gonna try to do something idont know again =P

---

