---
title: "Dell Studio 1535 - Continuous operation of laptop's fan"
date: 2011-02-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by iokara08 on 2011-02-07
Hi everyone,

I am experiencing an issue using Ubuntu 10.10 on my Dell Studio 1535.
Eventhough my CPU and RAM exhibit a very light operation, the fan is running continuously in relatively high speed.
Is it possible to get rid of this issue?:confused:

Thank you in advance.

---

### Post by janderpola on 2011-02-08
have you installed the privative drivers? In my case (a Studio 1558 with ATI) this happened to me with the open-source drivers.

---

### Post by gordintoronto on 2011-02-08
You might install lm-sensors and the "hardware sensors monitor" applet.

---

### Post by iokara08 on 2011-02-18
Thank you all for your replies.

"Janderpola" you were right since the problem was associated with the graphic ddriver. After doing the following:

1) Disabling the visual effects
2) Restart
3) then straight after a more silent operation was observed
4) Then I uninstalled the default driver and I installed the additional driver offered by the system.
5)Restart
6) Enabling the Visual effects again
7) Silent operation was obtained

Thank you all.:cool:

---

### Post by zardosht_h on 2011-05-22
Hi, 

i am a newbie. Can you please explain how did you do these steps in more detail? I am using Ubuntu 11.04 on Dell studio 1558. 

thanks.

---

### Post by dmijgs on 2011-07-08
I have the same problem with a dell 1558 with a HD4570 graphic card and Ubuntu 10.10. Now, after installing the additional ATI drivers, the fan don't work so fast but it never stops, it keeps working all the time. If I use windows the system goes fine, the fan stops without any problem. Do yo know how to fix the problem?. 

Thank you.

---

