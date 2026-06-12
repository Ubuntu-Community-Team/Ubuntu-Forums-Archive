---
title: "How to start gnome-terminal maximized vertically?"
date: 2010-07-13
forum: Desktop Environments
---

### Post by mark.altern on 2010-07-13
Hi, guys, I am trying to figure out how to start the gnome terminal with its window maximized vertically. 

Every time, I have to start it with my short key F1 and then my short key to maximize it vertically Alt+F12.  So is there any way to do this automatically? 

I know I can use the --geometry option but I would like an option that doesn't depends on the resolution of screen. Like the following command open gnome-terminal maximized:
```
 gnome-terminal --maximize 
```

Can I do something like that to start it maximized vertically? 

Thanks.

---

### Post by bruno9779 on 2010-07-13
you can edit your profile preferences in the terminal.

Edit > Profile preferences

On the main tab of the options, at the bottom, you ave an option to set the default size of the terminal.

The default is 80 x 24.

80 x 48 should do the trick (depending on your reolution, of course)

---

### Post by mark.altern on 2010-07-13
Thanks but I mentioned, I would like some method that doesn't depends on the resolution, since I switch between different machines and they all have different LCD. 

Thanks anyway, but any other ideas?

---

### Post by WinRiddance on 2010-07-13
> **mark.altern said:**
> Thanks but I mentioned, I would like some method that doesn't depends on the resolution, since I switch between different machines and they all have different LCD. 

Thanks anyway, but any other ideas?

Considering what bruno9779 just said, it would take you about the same amount of time to open a terminal, followed by entering the command to do what you want ... as it would to click on profile preferences instead, followed by changing the rows/columns there in a matter of 3 to 5 seconds. I mean, we are talking about just a few seconds of work here, right ... ???  ;)

You could also set up multiple terminals, each ready to go with it's own rows and columns. Then you could use whichever terminal for whichever LCD with whatever resolution that LCD is using.

---

### Post by mark.altern on 2010-07-13
You are right, but imagine, you have about 15 labs, in each of them, there are around 40-50 computers from different years, some has 17'' screen, some 19'' and others 20'', 22'' and etc. 

Now you want the gnome-terminal to start-up maximized vertically and bind the command to a shotkey, what should you do? Configuring each computer one-by-one is not what to expected from an admin. It will to hard to track each computer's LCD and do the management. 

Command like:
 ```
gnome-terminal --maximize 
```is something I wanted :-)

Any other ideas?

by the way, [WinRiddance]("http://ubuntuforums.org/member.php?u=1083274"), I am interested in your webside ( the one in your signature), there are a few screenshots you claim to be from ubuntu, but are actually from Macintosh. You don't want to deceive people into ubuntu by mac, do you? :-)

---

### Post by __B__ on 2010-10-27
```
gnome-terminal --window --maximize
```

---

### Post by Samineru on 2011-07-29
```
gnome-terminal --window --maximize
```

I am trying to combine this with the --window-with-profile= flag, but doing so yields two terminals. What offers this --window flag? It does not appear in the gnome-terminal man page.

---

