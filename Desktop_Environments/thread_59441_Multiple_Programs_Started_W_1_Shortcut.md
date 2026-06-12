---
title: "Multiple Programs Started W/ 1 Shortcut?"
date: 2005-08-24
forum: Desktop Environments
---

### Post by randomjester on 2005-08-24
Is it possible to launch 2 programs with one shortcut or .bat? Specifically, Tor and Privoxy. I wanted to see if it would be possible to do so. Have one shortcut "Tor-Priv" to launch Tor and then Privoxy. Possible?

Thanks

---

### Post by tvelocity on 2005-08-24
[QUOTE=randomjester]Is it possible to launch 2 programs with one shortcut or .bat? Specifically, Tor and Privoxy. I wanted to see if it would be possible to do so. Have one shortcut "Tor-Priv" to launch Tor and then Privoxy. Possible?

Thanks[/QUOTE]
 You can create a shell script: create a new file "tor-priv.sh", edit it with gedit (or your favourite text editor), and put the commands you want it to run one after the other, for example, if i wanted to run gedit and the calculator, i would type in:

> 
gedit &
gcalctool


Note the &, if you don't use it, the second program will only launch AFTER the first one has exited.

Don't forget to mark the file executable from it's properties. Then you can either click the shell script directly, or even better, hide it somewhere in your /home, create a launcher, and point to it.

---

### Post by randomjester on 2005-08-24
tvelocity,

Thank you for the helpful reply. Would you be able to help me set the file up? I'm not exactly sure what to put in... These are the programs I want to start.

"C:\Program Files\Tor\tor.exe"
&
"C:\Program Files\Privoxy\privoxy.exe"

What exactly would I put into the "tor-priv.sh" file to start those programs up by clicking on it?

Thanks again.

---

### Post by manuska on 2005-08-24
If you are using wine (as it somewhat seems)
```

wine "C:\Program Files\Tor\tor.exe" &
wine "C:\Program Files\Privoxy\privoxy.exe"

```

---

### Post by randomjester on 2005-08-24
*EDIT*

Fixed my problems. The solution was to have the .bat file in the Privoxy folder and create a shorcut to my desktop to use. Privoxy now loads without an error. This is the final working code.

```

@Echo Off

START /min "" "C:\Program Files\Tor\tor.exe"
START /min "" "C:\Program Files\Privoxy\privoxy.exe"

```

Thank you for the help.

---

### Post by randomjester on 2005-08-25
Does anyone have any ideas at all on how to 'fix' this?

---

### Post by matthew on 2005-08-25
I'm still unclear. Are you trying to do this on Ubuntu or on Windows?

---

### Post by KingBahamut on 2005-08-25
[QUOTE=matthew]I'm still unclear. Are you trying to do this on Ubuntu or on Windows?[/QUOTE]
 Gah...thats windows....what the heck is that crap doing in here.

---

### Post by Whatsisname on 2005-08-25
I hate to be a jackass but that error tells you exactly what is wrong, and how to fix it. Read it a bit closer.

---

