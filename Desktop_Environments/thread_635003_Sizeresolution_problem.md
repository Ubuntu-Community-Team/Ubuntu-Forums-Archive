---
title: "Size/resolution problem"
date: 2007-12-08
forum: Desktop Environments
---

### Post by Bnei on 2007-12-08
I have tried both Ubuntu and Kubuntu since the version 7.10 came out and I'm really impressed. Still, there is an issue that no one has been able to help me with and if not, I have to stick to other options Sad

The problem is that I have a Latitude X1, a laptop with a 12,1" screen running in 1280x768. When using this resolution in gnome or kde (ubuntu or kubuntu 7.10) everything looks so big that it is not possible to use.

I had the same problems using ubuntu so it looked the same using gnome but the screens are from kde.

Here are two examples of how it looks using kubuntu..
**[kde1]("http://user.it.uu.se/~hajo7895/screens/snapshot1.png")**
**[kde2]("http://user.it.uu.se/~hajo7895/screens/snapshot2.png")**

And this is XP, using the same resolution on the same computer..
**[xp]("http://user.it.uu.se/~hajo7895/screens/snapshot3.png")**

I don't know if you get the feeling that I get when using the different systems, but I don't enjoy working in either kde or gnome on my laptop unfortunately. I can change the size of the bottom menu of course, but that isn't nearly enough. Is there any way to "zoom out" or changing the display to make it more pleasent?

As mentioned, I'm very impressed with the latest ubuntu release and I want to support it, on both my laptop and my desktop computer. But the way it looks now, that's not gonna happen. Are there any solutions to my problem or am I the only one who considers it a problem?

I'm running kde in the maximum resolution on the screens.

---

### Post by wjp.reg on 2007-12-08
Can you tell us what kind of a video adapter you are running in your system?
In linux you can run the following command from the terminal:

```
 lspci | grep "Display"
```

and this information will be shown.  If not, just run "lspci" on it's own.

---

### Post by Bnei on 2007-12-08
> **wjp.reg said:**
> Can you tell us what kind of a video adapter you are running in your system?
In linux you can run the following command from the terminal:

```
 lspci | grep "Display"
```

and this information will be shown.  If not, just run "lspci" on it's own.

Thank you for answering but the problem is solved. At least for my pleasure since this is a problem with my view of how it looks.

The default dpi setting is not optimal for my tiny screen and the screen resolution I'm using. Now I have the value at 70 dpi and it looks a lot better. 

Compare:
**[Default dpi]("http://user.it.uu.se/~hajo7895/screens/snapshot1.png")**

With:
**[70 dpi]("http://user.it.uu.se/~hajo7895/screens/snapshot4.png")**

This is the solution when using kde:

Open:
```
/etc/kde3/kdm/kdmrc
```

and change:
```

SercerCmd=/user/bin/X -br
ServerArgsLocal= -nolisten tcp

```

to:
```

SercerCmd=/user/bin/X -br **_-dpi 70_**
ServerArgsLocal= **_-dpi 70_** -nolisten tcp

```

and change the dpi value until you are satisfied.

In gnome, go into the font settings and press "Details". From there you can edit the dpi value.

---

