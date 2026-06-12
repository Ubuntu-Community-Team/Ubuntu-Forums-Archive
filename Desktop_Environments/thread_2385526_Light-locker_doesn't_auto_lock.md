---
title: "Light-locker doesn't auto lock"
date: 2018-02-21
forum: Desktop Environments
---

### Post by jtodd.fr on 2018-02-21
I switched to lightDM with light-locker a while ago. I find that light-locker (started with `light-locker&`) doesn't auto lock once my system going inactivity, though I can manually lock by `light-locker-command -l` without a problem. 

My setting looks like [https://imgur.com/a/ZiA9v](https://imgur.com/a/ZiA9v)

What specific configuration may be needed so to let light-locker lock my screen automatically?

---

### Post by speartip on 2018-02-23
In your image, click the Security tab & check if "automatically lock the session" is set to "never". If so change it to "when the screensaver is activated".
I find it strange that you say you switched to LightDM & light-locker, when they're already default in xfce??

---

### Post by jtodd.fr on 2018-02-23
> **speartip said:**
> In your image, click the Security tab & check if "automatically lock the session" is set to "never". If so change it to "when the screensaver is activated".
I find it strange that you say you switched to LightDM & light-locker, when they're already default in xfce??

That seems to be because searching on the internet, some recommend to use xfce power manager to manage light locker (Sorry can't remember exactly now). So I install xfce4-power-manager for such purpose. Then when configure with light-locker-settings it will have a button (with name 'open') asking me to configure with xfce4-power-manager.

I actually remove gdm and run lightdm 
```

#apt-get install gdm 
The following NEW packages will be installed:
  caribou chrome-gnome-shell dleyna-server folks-common gdm gdm3 ...

# ps -ef | grep lightdm 
...      1376     1  0 14:18 ?        00:00:00 /usr/sbin/lightdm




```

But basically I fixed this now. The way is configuring with xfce4-power-manager, there exists a tab named 'security'. At the **automatically lock session** section choose **when the screensaver is deactivated** instead. The reason is because checking light-locker state (by `light-locker-command -q`) actually shows that light-locker state is inactive. That means when light-locker is running (not locking), it's in inactive state, which is opposite my original thought. So switching auto lock timing from activated to deactivated fixes the problem.

---

