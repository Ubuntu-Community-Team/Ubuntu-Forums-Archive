---
title: "Compiz Fusion on Gutsy"
date: 2008-02-02
forum: Desktop Effects &amp; Customization
---

### Post by colecampbell666 on 2008-02-02
[IMG]http://i26.tinypic.com/2ci9u80.png[/IMG]

I've heard something about needing XGL.

---

### Post by Elnahir on 2008-02-02
Same problem here. I've read some threads and googled trough many different pages but still haven't been able to fix this.

I'd appreciate some help. :)

---

### Post by deepclutch on 2008-02-02
do ya guys have below lines in /etc/X11/xorg.conf?
 ```
Section "Extensions"
    Option "Composite" "Enable"
EndSection 
```

---

### Post by FuturePilot on 2008-02-03
Depending on your graphics card you may need XGL. What card do you have?

---

### Post by Elnahir on 2008-02-03
Mine is ATI Radeon 9550; I know that ATI isn't the best choice for VGA's when you run an Ubuntu, but I saw a few comments from people who have Radeons - I just don't know what to do turn the effects on. : \

@deepclutch
Under lines is says: Option "Composite "0"; no "Enable" here. What do I write to enable it?

p.s. Excuse my lameness. :|

---

### Post by GooblyWoobly on 2008-02-03
Not sure, but I think compiz is not available for the restricted driver. So, try going back to the regular "free" driver and check.

---

### Post by FuturePilot on 2008-02-03
Yes, if you have an ATI card and are using the driver from the Restricted Driver Manager then you will need to install XGL.

---

### Post by ipatec on 2008-02-03
I'm having ATI X1400 and I have the same problem... how can I install XGL?

---

### Post by FuturePilot on 2008-02-03
```
sudo apt-get install xserver-xgl
```
should do it :)
Log out then log back in.

---

### Post by Elnahir on 2008-02-03
It works : ))) Thank you very much, guys. :)

---

