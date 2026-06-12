---
title: "Worhspace switcher, on 11.04"
date: 2011-06-08
forum: Desktop Environments
---

### Post by Snody on 2011-06-08
I notice that by default there is only 4 workspaces available on Natty Narwhal. Can I get more as I could with 10.10?

---

### Post by Copper Bezel on 2011-06-09
So far as I know, it's still in General Options -> Desktop Size.

---

### Post by linuxnewuser2011 on 2011-06-09
how to use Workspace switcher ???

---

### Post by cybrsaylr on 2011-06-09
> **Copper Bezel said:**
> So far as I know, it's still in General Options -> Desktop Size.

How do you get to: General Options -> Desktop Size?

I can't find it?

---

### Post by Copper Bezel on 2011-06-09
In CompizConfig. If you don't have it installed, run 

```
sudo apt-get install compizconfig-settings-manager
```

and choose CompizConfig from Preferences or, in Unity, type Compiz in the Dash or run ccsm from the Run Dialog.

---

### Post by cybrsaylr on 2011-06-09
> **Copper Bezel said:**
> In CompizConfig. If you don't have it installed, run 

```
sudo apt-get install compizconfig-settings-manager
```


Help needed!

Ok I installed CompizConfig with the above code in terminal.
It went throught OK.

Then changed my destop settings to 6 from 4.
That went OK.

Then tried setting up the compiz desktop cube and rotate cube like I had on Karmic and completely messed up Natty!

All I get now is a purple Natty screen with NO icons and nothing else on restart!
I can't do anything else!

What did I do wrong? And how can I get back to running Natty normal again like before putting Compiz in?

Can someone please HELP?....:(
How do I reverse what I did?

I created a 'new folder' on the blank purple screen and was able to get into my Home folders so all seems well inside but with no desktop icons I can't do anything or even get on the Internet with this PC. I am using another PC to post this.

---

### Post by Copper Bezel on 2011-06-09
The cube's a mess in the present version of Compiz. See [this guide]("http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html") to get your desktop back.

---

### Post by cybrsaylr on 2011-06-10
> **Copper Bezel said:**
> See [this guide]("http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html") to get your desktop back.

Got that guide in another thread.
Played around with it for a couple hours and got nowhere.

Ended up doing a reinstall of Natty, which took 16 minutes and desktop is back and all looks normal again.

Too bad the cube is a mess.
The cube worked great on Karmic.

---

### Post by stinkeye on 2011-06-10
You can enable the cube in Natty by following a set order when enabling/disabling plugins.
[**_[COLOR="DarkRed"]Enable Desktop Cube in Unity, Ubuntu Natty[/COLOR]_**]("http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html")
alt+F2 and running ```
compiz --replace
``` and/or ```
unity --replace
```
usually fixes most corruption issues when you have the right plugins enabled.
Creating a couple of desktop launchers using those commands can help if you no longer have access to alt+F2 or the terminal.
Once I got it setup right I've had no problem with the cube.

---

