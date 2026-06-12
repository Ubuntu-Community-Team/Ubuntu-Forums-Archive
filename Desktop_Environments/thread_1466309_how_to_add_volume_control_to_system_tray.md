---
title: "how to add volume control to system tray"
date: 2010-04-30
forum: Desktop Environments
---

### Post by Dai777 on 2010-04-30
I seem to have lost the volume control from the system tray how to I add it back. It's no tin add to panel section.

---

### Post by note32 on 2010-04-30
is the notification area missing?

---

### Post by note32 on 2010-04-30
also check this thread out it might solve your problem:
[http://ubuntuforums.org/showthread.php?t=1357005](http://ubuntuforums.org/showthread.php?t=1357005)

---

### Post by Dai777 on 2010-04-30
> **note32 said:**
> is the notification area missing?

no have notification area only thing missing is the volume control. no volume control in add to panel, no volume anything in add to panel when right clicking on add to panel.

---

### Post by Dai777 on 2010-04-30
Volume control is now the indicator applet in add to panel (why? beats me)

---

### Post by yilmazcan on 2010-05-01
I come across the same problem. My volume control is now the indicator in add to panel menu. how can i change that?

---

### Post by lhaeh on 2010-05-01
Mine disappeared too, it is now called the "indicator applet."

---

### Post by Maharifu on 2010-05-01
Hi,

I don't use gnome panels, I removed them all. In Karmic, I had the volume control in systray. As I use a standalone systray (trayer) all was good.

Now in Lucid, volume control is back as an applet, so I don't see it. Is there any way that I can get a volume control back in the systray?

---

### Post by madmax1735 on 2010-05-02
try this in the terminal



```
gnome-volume-control-applet
```

---

### Post by Maharifu on 2010-05-02
> **madmax1735 said:**
> try this in the terminal



```
gnome-volume-control-applet
```

It works, just what I wanted. Thank you very much!! :D

---

### Post by suffer1989 on 2010-05-02
> **madmax1735 said:**
> try this in the terminal



```
gnome-volume-control-applet
```



How can you remove it from the top panel and add it to the bottom pannel ?

---

### Post by stinkeye on 2010-05-02
> **suffer1989 said:**
> How can you remove it from the top panel and add it to the bottom pannel ?
Add a notification area applet to the bottom panel.
I don't use chat or evolution so I removed the Indicator Applet and added
gnome-volume-control-applet
to startup applications.
This gives you the karmic style volume in the Notification Area.

---

### Post by cecilieaux on 2010-05-02
> **madmax1735 said:**
> try this in the terminal



```
gnome-volume-control-applet
```
I tried this and a button appeared, but when I closed the terminal it disappeared again.

---

### Post by PhilGil on 2010-05-02
You can also leave the indicator applet installed and remove the Me Menu and envelope icon using this command:

```
$ sudo apt-get remove indicator-messages indicator-me
```[http://www.omgubuntu.co.uk/2010/03/how-to-remove-social-network-features.html](http://www.omgubuntu.co.uk/2010/03/how-to-remove-social-network-features.html)

---

### Post by teachop on 2010-05-02
> **cecilieaux said:**
> I tried this and a button appeared, but when I closed the terminal it disappeared again.

Try adding it to the Startup Applications.

---

### Post by dandellion on 2010-05-21
> **Dai777 said:**
> Volume control is now the indicator applet in add to panel (why? beats me)

And why is it connected to chat??? It's utterly dumb.

---

### Post by beetlejuice321 on 2010-08-02
I had the exact same problem.  Had to what "lhaeh" said and use the "Indicator Applet".

Right-click on Gnome Panel then select "Add to Panel". Then choose "Indicator Applet".

So weird...

---

### Post by Gaygerbil on 2010-08-03
> **PhilGil said:**
> You can also leave the indicator applet installed and remove the Me Menu and envelope icon using this command:

```
$ sudo apt-get remove indicator-messages indicator-me
```[http://www.omgubuntu.co.uk/2010/03/how-to-remove-social-network-features.html](http://www.omgubuntu.co.uk/2010/03/how-to-remove-social-network-features.html)

This command worked well for me, the other one that launched the gnome launcher

```
 gnome-volume-control-applet 
```

This code can be run in terminal to see how it looks but it won't stay unless you leave your terminal open, that's why you need to run this command in start up apps if you want it like that. I would want it like that but I don't like the icon compared to the 10.04 icon, if someone knows how to change the icon on this one I'd prob switch to that.

But yeah just to get the empathy messenger icon back I'm guessing you use 

```
 sudo apt-get install indicator-messages indicator-me 
```

Right? Either way those are your options Ubuntu's got you pretty well covered for now.

---

### Post by ladymiw on 2010-12-13
i tried the gnome-volume-control-applet in terminal.
firstly it worked, then when i closed the terminal, the icon went missing again.
i don't know how the icon disappeared, but i think i might accidentally deleted it.
pleeeaaaase help. volume control icon is important because i like watching movie and listening to the music with my netbook.

tx. ;)


hooo!! it's solved!!

---

### Post by keef123 on 2011-01-18
> **madmax1735 said:**
> try this in the terminal



```
gnome-volume-control-applet
```

YES!!!

Thank you.

---

