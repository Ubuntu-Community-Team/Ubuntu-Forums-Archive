---
title: "clean up desktop"
date: 2016-05-09
forum: Desktop Environments
---

### Post by Pinkie_B on 2016-05-09
Hi Ubuntu-ers,

I know this question has been asked at least twice before, but the solutions posted don't work for me, or are otherwise not complete.

I have "links" to [home] and [computer] and [trash] on my desktop and I can't make them go away. someone said to type alt+f2 then gconfig then nautilus and i did that, but nothing happens. a menu shows up with stuff that I can click on, but it does nothing. 

In the terminal, the Desktop appears to be empty.

Can someone help?

---

### Post by jim_deadlock on 2016-05-09
It should really be possible to do this out of the box, but it's not. You need to install/run Tweak Tool > Desktop

---

### Post by grahammechanical on 2016-05-09
What version of Ubuntu are you using? I have not seen icons for home, computer & trash on the Ubuntu desktop for years. But I have seen such things on distributions built on Ubuntu such as Xubuntu & Lubuntu, 

Unity Tweak tool is only useful when using Ubuntu with the Unity user interface.

Regards

---

### Post by jim_deadlock on 2016-05-09
There's Tweak Tool and Unity Tweak Tool, they're 2 different things.

---

### Post by PaulW2U on 2016-05-09
> **Pinkie_B said:**
> Can someone help?
According to other posts that you've made recently you're using Ubuntu 14.04.3 LTS
> **grahammechanical said:**
> I have not seen icons for home, computer & trash on the Ubuntu desktop for years.
That's because you've chosen not to put them there. :)

Pinkie_B, I've just checked with Unity Tweak Tool on Ubuntu 16.04 and your're just a couple of mouse clicks away from adding or removing such icons from the Unity desktop.

You shouldn't have to resort to using gconf-editor or dconf-editor to make such changes. Installing Unity Tweak Tool from the official repositories allows you "tweak" your Unity desktop quickly and easily.

---

### Post by RobGoss on 2016-05-10
In Ubuntu 16.04 with _Unity Tweak Tool_ installed Just open up [COLOR=#000000]**Unity Tweak Tool **and click on **Desktop icons** and you should be able to **add **them or **remove** them from that screen[/COLOR]

---

### Post by Pinkie_B on 2016-05-11
Hi Paul!

Thanks! You have my utmost respect for figuring out my system when I don't remember how to.
So, could you let me know what those mouse clicks are?

Best

Pink

---

### Post by Pinkie_B on 2016-05-11
Hi All,

So it seems that "Unity Tweak Tool" is the thing I need to hide these icons. 

Thank you.

Next step: can anyone tell me what that is and how I get and use it?

Best

Pink

---

### Post by vasa1 on 2016-05-12
See [http://www.omgubuntu.co.uk/2013/02/introducing-unity-tweak-tool](http://www.omgubuntu.co.uk/2013/02/introducing-unity-tweak-tool). I know it's an oldish link but you're on 14.04. So there's not much point linking to articles about the application version for 15.10 or 16.04.

Please disregard "*Unity Tweak Tool can be easily installed by adding the daily build PPA to your software sources, simply by pasting the following in your favourite terminal application: ...*". The application is now in the standard repository and you can install it as described below.


If you decide to install it, just run *sudo apt-get install unity-tweak-tool* _**after**_ you've run *sudo apt-get update* and *sudo apt-get upgrade* without any errors appearing. If you're not sure, post the output of these two commands here for people to look at and guide you further.

---

