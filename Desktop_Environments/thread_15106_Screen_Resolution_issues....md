---
title: "Screen Resolution issues..."
date: 2005-02-12
forum: Desktop Environments
---

### Post by pilotcp on 2005-02-12
Hello all,

Today is my first day of Ubuntu linux, and i love it. the only problem i have right now is that i am unable to set my screen resolution for anything greater than 800x600. i also have the live cd, which i tried that as well, and it was able to do 1024 x 768. I than reinstalled ubuntu, and when the resolution selection box came up, i chose all the selections above 1024 x 768, so the system would be forced to allow 1024 x 768 and higher (if that is even possible for my laptop!) 

the bottom line is, i get good resolution on the live cd, so i know the system is capable of the higher resolution, but when linux is installed on the computer, i am unable to select a higher resolution than 800x600!
is there some command i can type in to allow for higher resolutions, or maybe a way for linux to rescan the available resolutions?

please help!

Thanks!



EDIT: sorry mods, i realize i posted this in the wrong spot...how do i delete posts??  :oops:

---

### Post by evangelion on 2005-02-12
The fastest way I can think of to do it is to manually edit your /etc/XF86Config-4 file, which might sound pretty scary, but it's really not too bad.
[For these instructions I'm going to assume you have no idea how to do this]

First open up a terminal,  (right click the desktop, go to open terminal or a similar option),  then type "sudo pico /etc/X11/XF86Config-4" (without the quotes)

Scroll down a lot untill you see a section like this
```

     Depth          24
     Modes      "1280x960 1024x768"

```
(as a matter of fact, you can press ctrl-w, and just type "Depth" and it will jump to that section)

Now all you need to do is throw "1024x768" in front of "800x600", so your section may look like this

```

     Depth  24
     Modes      "1024x768 800x600"

```

You can now press ctrl-x to exit and tell it yes when it asks if you want to save

Next you have to restart the X server
Log out of Gnome and at the log in screen press Alt-Ctrl-Backspace,  this should do the trick and you should be running at 1024x768 when the screen comes back up. 

Hope this helps, and if anyone knows an easier/better way to do this feel free to jump in

---

### Post by pilotcp on 2005-02-12
Thanks for the quick reply!

i followed the steps that you gave, and i saw that i've got it set starting at 1920 x 1440. maybe that is the problem? should put erase all of those and just leave 1024 x 768 so thats all linux can look for? 

i dunno...just making ideas!

---

### Post by evangelion on 2005-02-12
[QUOTE=pilotcp]Thanks for the quick reply!

i followed the steps that you gave, and i saw that i've got it set starting at 1920 x 1440. maybe that is the problem? should put erase all of those and just leave 1024 x 768 so thats all linux can look for? 
i dunno...just making ideas![/QUOTE]

Sure, it's worth a shot.  After you edit the file it might be usefull to completely kill X as well,   once you log out of gnome and are back at the login screen press Alt-F2,  log in as root and type "killall -9 gdm"    then you can type "exit" and press Alt-F1 to get back to your main terminal.  Then type "startx" to log back into X  (if it complains that some file like /tmp/X.0.lock exists, just "sudo rm" it  and startx again.  

Hopefully this helps otherwise I'm at a bit of a loss.


One more thing that might be worth noting,   make sure your the Modes you're setting ar actually the ones being used;  Check your DefaultDepth,  if that's 24,  then  edit the modes under "Depth 24".

Yet another thing to try;  Try pressing alt-ctrl-+ while in X and see if modes switch then.

---

### Post by pilotcp on 2005-02-12
[QUOTE=evangelion]Sure, it's worth a shot.  After you edit the file it might be usefull to completely kill X as well,   once you log out of gnome and are back at the login screen press Alt-F2,  log in as root and type "killall -9 gdm"    then you can type "exit" and press Alt-F1 to get back to your main terminal.  Then type "startx" to log back into X  (if it complains that some file like /tmp/X.0.lock exists, just "sudo rm" it  and startx again.  

Hopefully this helps otherwise I'm at a bit of a loss.


One more thing that might be worth noting,   make sure your the Modes you're setting ar actually the ones being used;  Check your DefaultDepth,  if that's 24,  then  edit the modes under "Depth 24".

Yet another thing to try;  Try pressing alt-ctrl-+ while in X and see if modes switch then.[/QUOTE]
 hehe...

thanks, but nothing yet...still stuck at 800 x 600...this is bizarre!

i don't get it..,800 x 600 wasn't even an option that i selected in the installation program, yet it can't go any higher from there! 

and like i said before, the live cd worked like a charm, and i had the 1024 x 768...is there some file or code that i can get off of the live cd maybe?

---

### Post by evangelion on 2005-02-12
Very weird indeed, could you post your XF86Config-4 file here so I can take a quick look at it?  There's got to be something, most likely obvious, that's slipping my mind.


I found this with a quick search,  it's worth a try at least

> 
How to fix monitor refresh rates in XFree86

01) Boot computer off Ubuntu Live CD
02) Copy /etc/X11/XF86Config-4 to a floppy
03) Reboot into Ubuntu Installation on HD
04) Copy modelines from floppy file into monitor section of /etc/X11XF86Config-4

05) Restart X and reset refresh rate to something higher than 60hz

***WARNING: Only copy modelines sections. If you use live CD's XF86Config-4 as is you will break your X installation.


Also you can try this command to reconfigure X
```

dpkg-reconfigure xserver-xfree86

```

---

### Post by pilotcp on 2005-02-12
[QUOTE=evangelion]Very weird indeed, could you post your XF86Config-4 file here so I can take a quick look at it?  There's got to be something, most likely obvious, that's slipping my mind.


I found this with a quick search,  it's worth a try at least[/QUOTE]

sure...let me try the livecd trick first!

---

### Post by pilotcp on 2005-02-12
well, i looked at the livecd's XF86Config-4, and i saw that the default depth was set to 16, so i changed mine, and now my login screen is 1024 x 768, but then after i logged in, it changed back. D'oh!

---

### Post by pilotcp on 2005-02-12
wait!
nevermind!

it worked! thanks evangelion!!

---

### Post by pilotcp on 2005-10-27
well folks, 
it happened again!
this time i upgraded to 5.04, and now the resolution is fine, but now the main picture is only half the size of what my monitor can do! 
does anyone know how to fix that? 
if anyone is wondering, i am using a compaq armada 1700...i know...kinda old, but its what i've got!

Thanks!
Charlie

---

