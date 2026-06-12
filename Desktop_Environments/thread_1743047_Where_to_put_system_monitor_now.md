---
title: "Where to put system monitor now ?"
date: 2011-04-29
forum: Desktop Environments
---

### Post by Ghost_Mazal on 2011-04-29
Lo guys , I always used to add system monitor with monitors for cpu , network and HDD on the top panel.

Now in 11.04 there is no top panel anymore.
Where can I put my system monitor now ? any suggestions ?

Thanx

---

### Post by ivanovnegro on 2011-04-29
To the left side bar if its only the launcher for the program, but if you refer to the applet, you cant do it anymore on Unity but I think there are some how-tos to do it anyway.

---

### Post by Ghost_Mazal on 2011-04-29
ag no man :( This Unity is turning out to be way more trouble than it's worth

---

### Post by sikander3786 on 2011-04-29
For CPU and RAM, you can use the AppIndicator for System Monitor. See here.

[http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html](http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html)

---

### Post by tomski on 2011-04-29
> **Ghost_Mazal said:**
> ag no man :( This Unity is turning out to be way more trouble than it's worth

exactly
not everyone wants their pc/laptop to look & feel like a netbook with a monolithic desktop environment

---

### Post by -=pug=- on 2011-04-29
> **sikander3786 said:**
> For CPU and RAM, you can use the AppIndicator for System Monitor. See here.

[http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html](http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html)
Many thanks that is exactly what I needed. I'd actually considered changing distro for a while thinking I couldn't even monitor basic system usage from my taskbar anymore.

I'm still not convinced it seems like a lot is being hidden from the user which I don't like, but I'll give it another week to see if I can be converted.

---

### Post by collisionystm on 2011-04-29
> **Ghost_Mazal said:**
> Lo guys , I always used to add system monitor with monitors for cpu , network and HDD on the top panel.

Now in 11.04 there is no top panel anymore.
Where can I put my system monitor now ? any suggestions ?

Thanx


[http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/](http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/)

There is a system monitor Indicator applet. I use it

---

### Post by ivanovnegro on 2011-04-29
> **-=pug=- said:**
> Many thanks that is exactly what I needed. I'd actually considered changing distro for a while thinking I couldn't even monitor basic system usage from my taskbar anymore.

I'm still not convinced it seems like a lot is being hidden from the user which I don't like, but I'll give it another week to see if I can be converted.

You can also use the normal system monitor from applications or from the terminal.

---

### Post by Ghost_Mazal on 2011-04-29
> **collisionystm said:**
> [http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/](http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/)

There is a system monitor Indicator applet. I use it

That one works nice. Now I just need one for network activity.

---

### Post by collisionystm on 2011-04-29
> **Ghost_Mazal said:**
> That one works nice. Now I just need one for network activity.

All of those indicators on there are pretty cool.... just remember to set them to start with your computer!

---

### Post by Ghost_Mazal on 2011-04-29
> **collisionystm said:**
> All of those indicators on there are pretty cool.... just remember to set them to start with your computer!

I can't find the application's command so I can do that ???

---

### Post by sikander3786 on 2011-04-29
The name by which you install one is its command ;-)

e.g, sudo apt-get install <this>, <this> will be the command mostly.

---

### Post by collisionystm on 2011-04-29
> **Ghost_Mazal said:**
> I can't find the application's command so I can do that ???


Bring up the Eyeglass menu ( press the windows key) type startup 

click on startup applications

Add an entry

---

### Post by Ghost_Mazal on 2011-04-29
> **sikander3786 said:**
> The name by which you install one is its command ;-)

e.g, sudo apt-get install <this>, <this> will be the command mostly.

It was installed with a deb file

> **collisionystm said:**
> Bring up the Eyeglass menu ( press the windows key) type startup 

click on startup applications

Add an entry

I know that , but I don't know the command to add there for the applet

---

### Post by collisionystm on 2011-04-29
```
indicator-sysmonitor
```

I found this by hitting

```

ALT+F2

```
and typing indicator

---

### Post by Ghost_Mazal on 2011-04-29
> **collisionystm said:**
> ```
indicator-sysmonitor
```

I found this by hitting

```

ALT+F2

```
and typing indicator

Thanx , when I type that in ALT+F2 I only get "indicator" though

---

### Post by petex on 2011-05-01
I must say that i really like unity so far (just my 2nd day of testing) even though i miss things like sys mon overally i like the change. And finally!! system search is here !

---

### Post by lisandro79 on 2011-07-08
See this thread for the solution. Ubuntu 11.04 has really nice GUIs for changing compiz configuration properties

[http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html](http://ubuntu4beginners.blogspot.com/2011/04/tweak-unity-to-better-suit-your-needs.html)

---

### Post by Blasphemist on 2011-07-08
You could also use screenlets or conky to monitor the state of the system in much detail. 
[http://screenlets.org/index.php/Home](http://screenlets.org/index.php/Home)
[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

