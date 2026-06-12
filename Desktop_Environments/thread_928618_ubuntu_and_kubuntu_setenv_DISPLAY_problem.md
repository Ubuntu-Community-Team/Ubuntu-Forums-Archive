---
title: "ubuntu and kubuntu setenv DISPLAY problem"
date: 2008-09-24
forum: Desktop Environments
---

### Post by crsmds on 2008-09-24
I have a ubuntu 7.10 desktop next to me, to which i would like to have a "xhost" ssh connection from my kubuntu PC. Here i am not able to "setenv DISPLAY my_pc_ip_address:0.0 and see the xsession of ubuntu in my machine.

Anybody can give me a solution for the above in a step by step manner, Thanks a lot in advance, i am totally new to this OS.

Rgds,
CRS.

---

### Post by bingoUV on 2008-09-24
Use "ssh -X", and you will not need to mess with xhost, and DISPLAY.

setenv is used in csh shell. Ubuntu has bash by default, in which you would do it this way:
```

export DISPLAY=my_pc_ip_address:0.0

```

If you use csh, it was fine. What is the error you got when you did setenv?

---

### Post by McNils on 2008-09-24
If you still want to go ahead make sure that the x-server is listening to tcp. The default is not to listen.

---

### Post by crsmds on 2008-09-25
> **bingoUV said:**
> Use "ssh -X", and you will not need to mess with xhost, and DISPLAY.

setenv is used in csh shell. Ubuntu has bash by default, in which you would do it this way:
```

export DISPLAY=my_pc_ip_address:0.0

```

If you use csh, it was fine. What is the error you got when you did setenv?
hi,

I am getting the following error, this is the error in both bash and tcsh shells.

Display 192.168.1.15:0.0 unavailable, simulating -nw

pl. let me know wht to do next?

rgds,
crs

---

### Post by crsmds on 2008-09-25
hi,

tcp has been made to listen.

but still i am not able get the display of ubuntu pc in to my kubuntu machine.

can you help me further.thanks.

rgds,

---

### Post by gaffar4all on 2008-09-25
HI,  I have a problem when i switch from ubuntu  to kubuntu n vice versa from logout options........  
1)  Pidgin  n kopete show me errors...............  
   pidgin shows  
          Purple's D-BUS server is not running for the reason listed below
                 failed to get connection: Failed to execute dbus-launch to auto launch Dbus -Sesion.

2)  I am unable to logout from Pidgin(yahoo) and kpote(yahoo)

3)  I use   xkill command in terminal and after all i get popups of sign ins and outs of my pals.

4) ihad downloaded conpiz-check thru terminal but there was an error thouhg it showed it can run propably on my hardware.....  so d i really need a ge force Nvidia to use desktop special effects.........?

---

