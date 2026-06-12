---
title: "Panel clock disappeared...?"
date: 2011-09-26
forum: Desktop Environments
---

### Post by decosting on 2011-09-26
It's gone. Not sure where it went.

I've gone into gconf-editor and then Apps > Panel > Applets > Clock_Screen> Prefs

Clock_Screen is not there, however, and seemingly nothing similar.

Any ideas? :(

---

### Post by Frogs Hair on 2011-09-26
Hello and Welcome

What Ubuntu version ?  If it is 11.04 are you using  the Ubuntu Classic desktop or Unity  ?

---

### Post by RussianSoup on 2011-09-26
If you're using Gnome, killall gnome-panel does the trick for me when I have panel problems (which I have ALL the bloody time)

---

### Post by decosting on 2011-09-26
> **Frogs Hair said:**
> Hello and Welcome

What Ubuntu version ?  If it is 11.04 are you using  the Ubuntu Classic desktop or Unity  ?

Yes, 11.04, and I am using Unity (on a netbook).

---

### Post by decosting on 2011-09-26
> **RussianSoup said:**
> If you're using Gnome, killall gnome-panel does the trick for me when I have panel problems (which I have ALL the bloody time)


I'm using unity, which means I'm not using Gnome, I think... (Sorry, linux n00b...)

At any rate, when I try the killall, i get 'gnome-panel no process found"

---

### Post by Frogs Hair on 2011-09-26
First try this command in the terminal . ```
unity --reset
```

If the clock does not appear open the Synaptic package manager and make sure indicator-datetime is installed . If the package is installed , right click on the line including that package , mark for reinstallation and select apply . Logout and back in .

---

### Post by cheesesesvouchers on 2013-01-18
Open a terminal (CTRL+ALT+T) and try this
 sudo apt-get install indicator-datetime
 may need to log out and back in again or reboot to see it


It worked for me.
originally posted by Warren Hill

---

