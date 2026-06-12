---
title: "Konsole won't start"
date: 2016-08-09
forum: Desktop Environments
---

### Post by milosb793 on 2016-08-09
Hello everybody there! :)

I'm pretty new Linux user. Now i'm using Kubuntu 16.04 and before last two days i have checking Konsole appearance and also looking how to autorun some code by  starting Konsole. I don't remember what exactly i done there in settings. :) 
But i've added this to therse files:
- [http://i.prntscr.com/9e01de61e3e647398834feaac45eadb4.png](http://i.prntscr.com/9e01de61e3e647398834feaac45eadb4.png)
- [http://i.prntscr.com/2c29b6a948f54c10b90d438515d3319f.png](http://i.prntscr.com/2c29b6a948f54c10b90d438515d3319f.png)
And after restarting system, Konsole won't start...
Just appear for few seconds and disappear again.

There is error code:
- After running from xterm: [http://i.prntscr.com/7c5fe070f6d9408fbfadf9979ca05455.png](http://i.prntscr.com/7c5fe070f6d9408fbfadf9979ca05455.png)

Notice: 
- I tried to remove it, with: 
```
     sudo apt-get purge --auto-remove konsole &&     sudo apt-get clean
```
and install it again. But still the same.

---

### Post by ajgreeny on 2016-08-09
I don't know where the KDE or konsole configurations are in your home as I don't use KDE but have a search for folders and files, perhaps in ~/.config, that might be related to this problem and rename them for now to see if you can get konsole to start again.

---

