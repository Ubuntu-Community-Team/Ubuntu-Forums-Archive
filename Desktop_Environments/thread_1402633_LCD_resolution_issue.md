---
title: "LCD resolution issue"
date: 2010-02-09
forum: Desktop Environments
---

### Post by adellalin on 2010-02-09
I just wiped out everything on my pc and installed 9.10. My LCD monitor is hg216D HDMI ( native resolution is 1680 x 1050 ) and everything is so large now because I only have 800x600 resolution available in the system. 

I tried to add new resolution by editing /etc/gdm/Init/Default file using xchandr command. But it didn't work for me. Can someone send me the command to add new mode resolution ?

thanks in advance.

---

### Post by dE_logics on 2010-02-09
In one of my cases, after specifying the refresh rate, the problem went fine.

But fist you have to make a Xorg.conf file which can be generated thought the following procedures - 

sudo /etc/init.d/gdm stop

You'll be back in command line...log in.

As said in the previous thread - 

[QUOTE=dE]Xorg -configure

It places the new configuration file somewhere (it will tell, I forgot). copy that file to /etc/X11 with the name Xorg.conf and start/restart X.[/QUOTE]

But how to start X? Here is the magical command - 

/etc/init.d/gdm start

Problem's not fixed yet. I know. Figure the horizontal and vertial refresh rate of your monitor...it will be there in the specifications, then edit your xorg.conf as root (I've assumed you have copied the new xorg.conf file to /etc/X11 after renaming) and add the following sections to your 'monitor' section - 

```
HorizSync <whatever your monitor supports>
VertRefresh <"         "     "       "   >
```

That resolved the issue for me.

---

