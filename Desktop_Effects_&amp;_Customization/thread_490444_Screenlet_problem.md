---
title: "Screenlet problem"
date: 2007-07-02
forum: Desktop Effects &amp; Customization
---

### Post by andrewsomething on 2007-07-02
Does any one know where the file telling what screenlets will run on the daemon's start is located?

I've been running screenlets for months with no real problem, but recently I tried to change my setup a bit. Now when starting screenlets the program seems to run very slow. The first two screenlets show up right away. The next will slowly show up over a very long time. I can't right click on any of them, and ones like weather or rss don't connect to the network. 

I simply want to start all over. I can't remove screenlets since I can't right click on them. I completely removed through Synaptic, but when I reinstall and start the same thing happens. 

I want to try deleting the file which tells the daemon which screenlets to start, so I have a clean slate.

Any ideas?

---

### Post by andrewsomething on 2007-07-02
I'm really stumped. I've gone through every folder listed by Synaptic to make sure that screenlets are completely uninstalled. Then after reinstalling, the exact same thing happens. The desktop becomes poplulated with screenlets that I can't right click on, most of which are not funtioning....

Anyone?

---

### Post by Fireblend on 2007-07-02
No usr/local/share/screenlets folder?

---

### Post by andrewsomething on 2007-07-02
> **Fireblend said:**
> No usr/local/share/screenlets folder?

After a complete uninstall there are a couple files left in /usr/local/share/screenlets. I've tried deleting those before reinstalling, but the problem still remains after the reinstall. There's some sort of configuration file hiding some where that I need to get rid of. There might be a better solution, but I can't think of it... I think one of the screenlets that I hadn't use previously is broken and causing the problem. 

Can you remove individual screenlets from the command line?

Thanks for the try. Any other ideas?

---

### Post by Mr Greencastle on 2007-07-02
Try deleting the screenlets files in /usr/local/bin (If any)
Also try .config/screenlets (In your home directory, must be able to see hidden files).

I had this problem with the weather screenlet.

Good Luck

Mr Green

---

### Post by andrewsomething on 2007-07-02
.config/screenlets was it!

Thanks so much! Every things back to normal!

---

