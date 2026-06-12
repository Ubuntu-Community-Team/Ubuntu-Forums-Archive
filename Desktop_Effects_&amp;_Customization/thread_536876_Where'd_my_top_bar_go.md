---
title: "Where'd my top bar go??"
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by weasel7711 on 2007-08-28
Somehow the top bar on all of my windows disappeared, now I cannot drag them around, maximize, minimize, or close them without right clicking on the bottom and selecting it...
help...


Also, possibly unrelated, the terminal wont show up... its just a white screen...
so... yeah...

---

### Post by seshomaru samma on 2007-08-28
are you using beryl ? compiz?

---

### Post by weasel7711 on 2007-08-28
lol i honestly have no idea

i am a newbie when it comes to ubuntu

how would i go about finding out

---

### Post by LukeCarrier on 2007-08-28
[FONT=Tahoma][SIZE=2][FONT=Lucida Console]Hello all,

Both Beryl and Compiz are programs which need to be installed seperately for Ubuntu, they do not come with the operating system. If you've never heard of them, the chances are you don't have them.
[/FONT]  [FONT=Lucida Console][COLOR=Red]
Only attempt this if you know what you're doing. If not, ask somebody 'technical' for a hand with it.[/COLOR][/FONT][FONT=Lucida Console]

**1. Open a terminal.**
Click Applications >> Accessories >> Terminal

**2. Start the setup wizard for X (graphics stuff).**
Type: "dpkg-reconfigure xserver-xorg" and press enter. No quotes!
[B]
3. Setup X correctly.[/B]
Just accept the defaults unless you know otherwise. Use the arrow keys to highlight the item you want to select, and then use the spacebar to select it.

**4. Did it work?**
Once you've gone through the prompts, the window will disappear. Log out, then back in, and see if everything is back to normal. Post back with the result when you're done.[/FONT]       
[/SIZE][/FONT]

---

### Post by Inxsible on 2007-08-28
or you could first simply try 

```
metacity --replace
``` and see if that works. If it does, then try and reboot and see if the window borders are still there. If not, you will need add metacity to the session and make it's order less than 40. But more on that later.

First try it out and reboot and see if that works.

---

### Post by weasel7711 on 2007-08-28
well the problem is when i go through the accessories menu to run the terminal, a big white box pops up with no borders or menu and there is no cursor... so I cant see anything I write.

---

### Post by weasel7711 on 2007-08-28
Ok my version of Linux is officially posessed by the devil... I just was scrolling down a webpage and it magically came back...


... i am so confused... I think I highlighted something, thats all i did...


and the terminal is back also

well whatever, thanks anyway guys

---

### Post by weasel7711 on 2007-08-28
Ok If I try to turn desktop effects back on, the title bars go away and my terminal gets weird.

I tried the metacity thing but that dididnt work so, id like to have desktop effects. Theres my new problem.

---

### Post by Rupertronco on 2007-08-28
That was your problem from the beginning. When you turn on desktop effects it changes your window manager from metacity to compiz. (Your window manager controls things like displaying your menu bars). You need to update your graphics drivers if you want the desktop effects to work correctly without sacrificing your window borders. 

What type of graphics card are you using? 

If the desktop effects are causing this problem (which they are) you should disable them until you get the driver situation addressed.

---

### Post by cevil203 on 2007-08-28
i just installed compiz-fusion from these instructions on this website [http://ubuntu4life.blogspot.com/2007/07/lets-get-started.html](http://ubuntu4life.blogspot.com/2007/07/lets-get-started.html)

and now my windows also dont have the minimize,maximize, close (x) option...how do i get them back plzzzz this is baddd

---

### Post by cevil203 on 2007-08-28
automatix says that my nvidia driver is already installed....o snap

---

### Post by Rupertronco on 2007-08-28
> **cevil203 said:**
> i just installed compiz-fusion from these instructions on this website [http://ubuntu4life.blogspot.com/2007/07/lets-get-started.html](http://ubuntu4life.blogspot.com/2007/07/lets-get-started.html)

and now my windows also dont have the minimize,maximize, close (x) option...how do i get them back plzzzz this is baddd

Start by making your own thread instead of asking for help in someone else's thread.

---

### Post by cevil203 on 2007-08-28
its on the same topic..why need for multiple threads...

---

### Post by Inxsible on 2007-08-28
> **cevil203 said:**
> its on the same topic..why need for multiple threads...
Have you already tried what was listed in this thread then ? and it still doesnt work ?

---

### Post by Chymera on 2007-08-28
> **weasel7711 said:**
> Ok If I try to turn desktop effects back on, the title bars go away and my terminal gets weird.

I tried the metacity thing but that dididnt work so, id like to have desktop effects. Theres my new problem.

yes, it is "normal" behaviour. your terminal starts to look strange because it gets some effects applied, which seem to have a problem with you gfx card. Same goes for the borders.

try ```
emerald --replace
``` or ```
emerald --replace &
``` or ```
metacity --replace
```

if these won't work its probably means you have an unsupported gfx card or simply not the right drivers. 
specs pleas? (if you dont know how to find out your specs go to applications>system tools>sysinfo and copy paste what you see)

---

### Post by weasel7711 on 2007-08-28
I'm using an NVIDIA GeForce 7600 GX -agp slot
Other System Specs:
Intel Core2Duo 1.8Mhz
1 Gb DDR2 Ram
ASRock 4coredual VSTA motherboard


I thought my drivers were up to date but i'll search for updated ones.

---

### Post by weasel7711 on 2007-08-28
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

which driver should I download???

---

### Post by cevil203 on 2007-08-28
after typing     compiz --replace..they would reappear then disappear once i exited the terminal. so i typed compiz -replace and that seemed to have fixed it.

---

### Post by weasel7711 on 2007-08-30
help... still...

read specifically my last post

---

### Post by saru411 on 2007-08-30
> **cevil203 said:**
> after typing     compiz --replace..they would reappear then disappear once i exited the terminal. so i typed compiz -replace and that seemed to have fixed it.

when you exit terminal you close the sub programs that run your tiltle bars/menu bars...you can do one of 2 things...leave the terminal open and minimize it...or type exit in terminal to close it rather than hitting the X to close it.

---

### Post by saru411 on 2007-08-30
> **weasel7711 said:**
> help... still...

read specifically my last post

 you sound extremely inexperienced in linux/ubuntu...you should just try installing envy and letting it install the correct graphics driver for you(aka n00b proof).

envy can be found here - [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

once it is installed applications>system tools>envy and pick nvidia if thats the card you are using

---

### Post by weasel7711 on 2007-08-31
the problem seemed to fix itself last night, i hadnt done anything differently

anyway

thanks to the people who hijacked my thread

---

### Post by Footissimo on 2007-09-02
I found my title bar disappearing when I use desktop effects / compiz - if you have a nvidia gfx card then try:

```
sudo nvidia-xconfig --add-argb-glx-visuals
```

It's a known bug.

---

