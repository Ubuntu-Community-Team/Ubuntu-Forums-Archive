---
title: "terminal doesn't display ssh login splash correctly"
date: 2009-02-08
forum: Desktop Environments
---

### Post by davygravy on 2009-02-08
My Hardy installation handled this w/ no problem... when logging into a headless Debian box, I always got this splash image: [IMG]http://buffalo.nas-central.org/images/thumb/4/4a/Debian-armelv2.png/450px-Debian-armelv2.png[/IMG] ... and it worked nicely...

Since I upgraded to Intrepid, it hasn't looked right... in fact it is a mess (see below).   I'm guessing some encoding var has been changed in Intrepid, or needs to be set, but I'm at a loss as to what exactly to change...  

I am 100% sure that there was no change in the Debian box... only on the Ubuntu side...  also 100% sure it happened at upgrade time...

Ideas??  

Thanks in advance,

 davy

```
\033[2J\033[0;0H
\033[40m\033[40m
\033[0m\033[37m\033[40m                               \033[0;37;40m
\033[0;1;31;40m         \033[31m_sudZUZ#Z#XZo=_\033[40m         \033[0;37;40m\033[1;47mDDDD\033[3CEEEEEE\033[1CBBBB\033[3CIIIIII\033[2CAAAA\033[3CNN\033[3CNN\033[40m
\033[0;1;31;40m      \033[31m_jmZZ2!!~---~!!X##wa\033[40m       \033[0;37;40m\033[1;47mDD\033[1CDD\033[2CEE\033[5CBB\033[1CBB\033[4CII\033[3CAA\033[2CAA\033[2CNNN\033[2CNN\033[40m
\033[0;1;31;40m   \033[31m.<wdP~~\033[40m            \033[31m-!YZL,\033[40m     \033[0;37;40m\033[1;47mDD\033[2CDD\033[1CEEEEE\033[2CBBBBB\033[4CII\033[3CAAAAAA\033[2CNNNN\033[1CNN\033[40m
\033[0;1;31;40m  \033[31m.mX2'\033[40m       \033[31m_%aaa__\033[40m     \033[31mXZ[.\033[40m   \033[0;37;40m\033[1;47mDD\033[1CDD\033[2CEE\033[5CBB\033[2CBB\033[3CII\033[3CAA\033[2CAA\033[2CNN\033[1CNNNN\033[40m
\033[0;1;31;40m  \033[31moZ[\033[40m      \033[31m_jdXY!~?S#wa\033[40m   \033[31m]Xb;\033[40m   \033[0;37;40m\033[1;47mDDDD\033[3CEEEEEE\033[1CBBBBB\033[2CIIIIII\033[1CAA\033[2CAA\033[2CNN\033[3CNN\033[40m
\033[0;1;31;40m \033[31m_#e'\033[40m     \033[31m.]X2(\033[40m     \033[31m~Xw|\033[40m  \033[31m)XXc\033[40m \033[0;37;40m
\033[0;1;31;40m\033[31m.2Z`\033[40m      \033[31m]X[.\033[40m       \033[31mxY|\033[40m  \033[31m]oZ(\033[40m \033[0;37;40m\033[2C\033[1;37;40mLinux Version 2.6.27.4\033[0m
\033[0;1;31;40m\033[31m.2#;\033[40m      \033[31m)3k;\033[40m     \033[31m_s!~\033[40m   \033[31mjXf`\033[40m \033[0;37;40m\033[2C\033[1;37;40mCompiled #1 PREEMPT Thu Oct 30 23:59:42 CDT 2008\033[0m
\033[0;1;31;40m \033[31m1Z>\033[40m      \033[31m-]Xb/\033[40m    \033[31m~\033[40m    \033[31m__#2(\033[40m  \033[0;37;40m\033[2C\033[1;37;40mOne ARM Feroceon rev 0 (v5l) Processor, 128M RAM\033[0m
\033[0;1;31;40m \033[31m-Zo;\033[40m       \033[31m+!4ZwaaaauZZXY'\033[40m    \033[0;37;40m\033[2C\033[1;37;40m266.24 Bogomips Total\033[0m
\033[0;1;31;40m  \033[31m*#[,\033[40m        \033[31m~-?!!!!!!-~\033[40m      \033[0;37;40m\033[2C\033[1;37;40marmel.lenny.local\033[0m
\033[0;1;31;40m   \033[31mXUb;.\033[40m                       \033[0;37;40m\033[2C
\033[0;1;31;40m    \033[31m)YXL,,\033[40m                     \033[0;37;40m\033[2C
\033[0;1;31;40m      \033[31m+3#bc,\033[40m                   \033[0;37;40m\033[2C
\033[0;1;31;40m        \033[31m-)SSL,,\033[40m                \033[0;37;40m\033[2C
\033[0;1;31;40m           \033[31m~~~~~\033[40m               \033[0;37;40m\033[2C
\033[0m\033[255D

Debian GNU/Linux lenny/sid
root@192.168.1.50's password: 

```

---

### Post by Yashiro on 2009-02-10
Is this the *issue.net* file it's failing to parse or something else?

---

### Post by tahitibub on 2009-07-10
Hi DavyGravy,

I don't know if you remember me but you helped me a few months ago to install Debian Lenny on my kurobox pro (and I thank you again a lot for this greatfull help).

Now, I have the same problem with this kurobox than you have with ubuntu. Here is the splash screen when I connect with ssh to the KB :

```
\033[2J\033[0;0H
\033[40m\033[40m
\033[0m\033[37m\033[40m                               \033[0;37;40m
\033[0;1;31;40m         \033[31m_sudZUZ#Z#XZo=_\033[40m         \033[0;37;40m\033[1;47mDDDD\033[3CEEEEEE\033[1CBBBB\033[3CIIIIII\033[2CAAAA\033[3CNN\033[3CNN\033[40m
\033[0;1;31;40m      \033[31m_jmZZ2!!~---~!!X##wa\033[40m       \033[0;37;40m\033[1;47mDD\033[1CDD\033[2CEE\033[5CBB\033[1CBB\033[4CII\033[3CAA\033[2CAA\033[2CNNN\033[2CNN\033[40m
\033[0;1;31;40m   \033[31m.<wdP~~\033[40m            \033[31m-!YZL,\033[40m     \033[0;37;40m\033[1;47mDD\033[2CDD\033[1CEEEEE\033[2CBBBBB\033[4CII\033[3CAAAAAA\033[2CNNNN\033[1CNN\033[40m
\033[0;1;31;40m  \033[31m.mX2'\033[40m       \033[31m_%aaa__\033[40m     \033[31mXZ[.\033[40m   \033[0;37;40m\033[1;47mDD\033[1CDD\033[2CEE\033[5CBB\033[2CBB\033[3CII\033[3CAA\033[2CAA\033[2CNN\033[1CNNNN\033[40m
\033[0;1;31;40m  \033[31moZ[\033[40m      \033[31m_jdXY!~?S#wa\033[40m   \033[31m]Xb;\033[40m   \033[0;37;40m\033[1;47mDDDD\033[3CEEEEEE\033[1CBBBBB\033[2CIIIIII\033[1CAA\033[2CAA\033[2CNN\033[3CNN\033[40m
\033[0;1;31;40m \033[31m_#e'\033[40m     \033[31m.]X2(\033[40m     \033[31m~Xw|\033[40m  \033[31m)XXc\033[40m \033[0;37;40m
\033[0;1;31;40m\033[31m.2Z`\033[40m      \033[31m]X[.\033[40m       \033[31mxY|\033[40m  \033[31m]oZ(\033[40m \033[0;37;40m\033[2C\033[1;37;40mLinux Version 2.6.25.6\033[0m
\033[0;1;31;40m\033[31m.2#;\033[40m      \033[31m)3k;\033[40m     \033[31m_s!~\033[40m   \033[31mjXf`\033[40m \033[0;37;40m\033[2C\033[1;37;40mCompiled #1 PREEMPT Sat Jun 14 09:47:31 CDT 2008\033[0m
\033[0;1;31;40m \033[31m1Z>\033[40m      \033[31m-]Xb/\033[40m    \033[31m~\033[40m    \033[31m__#2(\033[40m  \033[0;37;40m\033[2C\033[1;37;40mOne ARM Feroceon rev 0 (v5l) Processor, 128M RAM\033[0m
\033[0;1;31;40m \033[31m-Zo;\033[40m       \033[31m+!4ZwaaaauZZXY'\033[40m    \033[0;37;40m\033[2C\033[1;37;40m266.24 Bogomips Total\033[0m
\033[0;1;31;40m  \033[31m*#[,\033[40m        \033[31m~-?!!!!!!-~\033[40m      \033[0;37;40m\033[2C\033[1;37;40mKuroBox-Pro\033[0m
\033[0;1;31;40m   \033[31mXUb;.\033[40m                       \033[0;37;40m\033[2C
\033[0;1;31;40m    \033[31m)YXL,,\033[40m                     \033[0;37;40m\033[2C
\033[0;1;31;40m      \033[31m+3#bc,\033[40m                   \033[0;37;40m\033[2C
\033[0;1;31;40m        \033[31m-)SSL,,\033[40m                \033[0;37;40m\033[2C
\033[0;1;31;40m           \033[31m~~~~~\033[40m               \033[0;37;40m\033[2C
\033[0m\033[255D

Debian GNU/Linux 5.0 \\n \\l

root@192.168.0.4's password: 

```

Before this happens, I made a few apt-get update and apt-get upgrade.

Have you any idea of the source of this problem ?

Regards

---

