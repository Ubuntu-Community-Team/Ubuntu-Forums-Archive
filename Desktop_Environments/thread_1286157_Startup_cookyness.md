---
title: "Startup cookyness"
date: 2009-10-08
forum: Desktop Environments
---

### Post by maxsideburn on 2009-10-08
I used Start-Up Manager to change my usplash and it didn't work, I just got a black screen no matter what theme I tried, so I switched back to stock......only problem is that before when I'd boot it would only take a few seconds and I'd see the Ubuntu logo on the screen. Now after GRUB it just sits at a blank screen for like 10-15 seconds, then I see my hard drive light come on and the Ubuntu logo shows up. Why is it "waiting" before trying to boot now?

Also I installed the xubuntu-desktop package through apt and now I get a light blue screen between my GDM login and my Gnome desktop loading. Know what I mean? I log in using GDM, the whole screen goes kinda light blue (like the default Xubuntu desktop), and then stays that way until my Gnome wallpaper appears. How can I change this back to black? (or was it brown?) I know it's minor, but it's annoying and ruins the look of my system when it's booting.

Running 9.04. Thanks.

---

### Post by ajgreeny on 2009-10-08
No idea about the first query, other tha suggesting you install bootchart to see if the chart produced by that gives you any clues, but forthe second question follow this below, but change the colour codes as needed.  I changed from brown to blue in the past, as I can't stand the default brown that used to appear.  Now it's black, so I have no need to do it any more.

How to change the colour of the brown splash screen that shows after I log in but before the desktop loads.  T change to light blue:-
Code:

gksudo gedit /etc/gdm/PreSession/Default

look for
Code:

# Default value  
      if [ "x$BACKCOLOR" = "x" ]; then  
              BACKCOLOR="#dab082"  
      fi

and change the "#dab082" to "97A7CD" or whatever colour code you want.
Code:  You can use the colour picker on the right click on desktop, Change desktop background to find a colour code.

# Default value  
      if [ "x$BACKCOLOR" = "x" ]; then  
              BACKCOLOR="#6093D5"  
      fi


I assume this is still OK for 9.04, but have not tried it myself.

---

### Post by maxsideburn on 2009-10-08
I run *bootchart* in the terminal and get

Parsing /var/log/bootchart
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 0
	at org.bootchart.Main.render(Unknown Source)
	at org.bootchart.Main.main(Unknown Source)

---

### Post by maxsideburn on 2009-10-08
oh, and I tried your suggestion......still getting the light blue screen even with it set at 0000000 (black)

---

### Post by ajgreeny on 2009-10-09
One too many zeros, if that is what you really used.

# Default value  
      if [ "x$BACKCOLOR" = "x" ]; then  
              BACKCOLOR="#000000"  
      fi

---

### Post by maxsideburn on 2009-10-09
no I actually used six zeros

---

