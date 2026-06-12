---
title: "Edited pekwm menu file, doesn't work, now it's gone"
date: 2010-02-26
forum: Desktop Environments
---

### Post by jwmollman on 2010-02-26
I installed pekwm on my netbook last night with Ubuntu 9.10 minimal, and I'm now trying to edit the menu file.

I typed:
```

cd ~/.pekwm

```to get into the directory of the config files for pekwm, and then I did:
```

sudo nano menu

```and nothing appears to be in the file anymore. All I tried to do was add "scite" to the menu, and I followed the correct syntax (I'm pretty sure). I can type "startx" at the prompt and it displays my cursor, but when I right click, the menu doesn't show up. So I'm guessing I screwed up that menu file. It says the defaults are stored in /usr/local/etc/pekwm, but when I go to /usr/local/etc/, there is no "pekwm" folder.

Is there anything I can do to start back at square one?

---

### Post by urukrama on 2010-02-28
Did the pekwm menu work normally before you edited it? If so, you most likely made a small error when you tried to add scite to it.

The default pekwm configuration files are found in /etc/pekwm (I believe older versions used the directory you were looking in). Try copying those back to your own pekwm directory, but make sure you don't use sudo, as this means you won't have access to them as a normal user. Use the following command:

> cp -r /etc/pekwm/* ~/.pekwm/ 

(You also don't need sudo to edit a file that is in your home directory (~), by the way. You should have permission to edit it as a normal user.)

---

