---
title: "TTY Size"
date: 2009-06-03
forum: General Help
---

### Post by Sum Requiem on 2009-06-03
Please help, I'm trying to get  a Nvidia graphics card to work but in order to do that I have to use the tty terminals. My big problem right now is that while a normal graphic interface works perfectly when I use the tty everything with the exception of the login prompt is below my screen. How do I make it so that I can actually see what I type? 

Thank You

P.S. sorry if this is a real basic question

---

### Post by Yellow Pasque on 2009-06-03
> everything with the exception of the login prompt is below my screen.
I can't picture this in my head. Can you describe it better?
You can pass a VGA argument to the kernel to specify the terminal resolution. You would add this argument to the boot line in /boot/grub/menu.lst

[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers)

---

### Post by Sum Requiem on 2009-06-05
Sorry for the bad description, lets see if a possibly better description and a bad picture are better.
When I first bring up the tty screen the login prompt and the tty info are visible but after I log in I can't see the "bottom" of the screen where the active prompt should be.

What a terminal session usually looks like (box represents computer screen):
_________________________________________________
|blank/old commands [COLOR="White"]You shouldn't see this, this is formating. [/COLOR]|
|blank/old commands [COLOR="White"]You shouldn't see this, this is formating. [/COLOR]|
|blank/old commands [COLOR="White"]You shouldn't see this, this is formating. [/COLOR]|
|blank/old commands [COLOR="White"]You shouldn't see this, this is formating. [/COLOR]|
|blank/old commands [COLOR="White"]You shouldn't see this, this is formating. [/COLOR]|
|currently active prompt [COLOR="White"]Same here, you shouldn't C this either[/COLOR]|
__________________________________________________


what my tty sessions look like:
__________________________________________________
|blank/old commands [COLOR="White"]You shouldn't see this, this is formating. [/COLOR]|
|blank/old commands [COLOR="White"]You shouldn't see this, this is formating. [/COLOR]|
|blank/old commands [COLOR="White"]You shouldn't see this, this is formating. [/COLOR]|
|blank/old commands [COLOR="White"]You shouldn't see this, this is formating. [/COLOR]|
|blank/old commands [COLOR="White"]You shouldn't see this, this is formating. [/COLOR]|
__________________________________________________

    
After I log on the prompt (where I type) goes "below" the screen so that I can't see what I'm typing instead I see what i had typed before. 


Can you clarify your instructions? I opened up the text file you mentioned but I could not find a boot line.

Thank you.

---

### Post by Yellow Pasque on 2009-06-05
It's the line that looks like:
```
kernel   root=<blah> splash quiet **vga=791**
```

---

