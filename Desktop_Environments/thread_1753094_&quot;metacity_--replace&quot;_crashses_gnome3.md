---
title: "&quot;metacity --replace&quot; crashses gnome3"
date: 2011-05-08
forum: Desktop Environments
---

### Post by maizuddin35 on 2011-05-08
Hello guys.   I just change from unity to gnome3, from the hardwork and patient, I manage to make gnome3 comfort enough for me to stay with . A little of patient learning gnome3 and its done.  

So, here is the main problem...I want to disable compiz on gnome3 so that I can play games much more smoother .I found a [link ]("http://z-computer-z.blogspot.com/2009/12/cara-mudah-mematikan-compiz-untuk.html")that tell me to replace metacity and there has a compiz switcher so that I can switch on and off compiz, but the thing is, disabling compiz make gnome3 crashes.   Anyone have any idea on how to fix this? sorry for my "not so unbelievable" english. Thanks in advance.(please let me know if you guys dont understand)

---

### Post by maizuddin35 on 2011-05-09
I cannot disable compiz by "metacity --replace" cause it will crash the gnome3 . even when I install compiz fusion icon, and when I check the metacity as the decorator for the gnome it will crash also. 
any gnome3 users here?

---

### Post by mcduck on 2011-05-09
Gnome 3 uses Mutter as it's window manager, and you can't replace it (The Gnome Shell basically runs as a plugin for Mutter, just like Unity runs as a Compiz plugin).

I'm not sure if you can disable compositing in Mutter, if not then running a different desktop environment when playing games would pretty much be the only option.

---

### Post by maizuddin35 on 2011-05-11
like last time if I want to play games in ubuntu, i will disable compiz to make the game performance better. is there in other way to make the game perform better in gnome3?

---

### Post by el_koraco on 2011-05-11
> **maizuddin35 said:**
> I cannot disable compiz by "metacity --replace" cause it will crash the gnome3 . 

It will crush Unity as well. In 2009. Compiz and metacity were designed to coexist and be easy to switch out. Now, Gnome Shell uses Mutter, and Unity Compiz, exclusively. Replacing them with metacity will obviously crash the desktop. If you got Natty, you can try logging into "Classic without effects", which I think is based on metacity alone, so there's no compositing.

---

### Post by maizuddin35 on 2011-05-11
I am using Natty right now, but with gnome3 . I think I should try login in in classic , if there is any , and hope it is working.

---

### Post by ttanev on 2011-06-03
Hello guys, I was using this script for a while:
[http://ubuntuforums.org/showthread.php?t=867562](http://ubuntuforums.org/showthread.php?t=867562)
Then found this one
[http://www.techytalk.info/2010/06/compiz-nvidia-ati-games-auto-switch-scripts/](http://www.techytalk.info/2010/06/compiz-nvidia-ati-games-auto-switch-scripts/)
Which worked more smoothly, but stopped working in Natty and I got back on the first one. As I'm using Arch right now, I think that the best solution is to start every game in new xserver, but don't know how to do it on the rootless Ubuntu. In Arch there's an "xlaunch" script in AUR, but in Natty doesn't work in a similar fashion.
[http://ubuntuforums.org/showthread.php?t=51486](http://ubuntuforums.org/showthread.php?t=51486)
```
#!/bin/bash xinit $* -- :1 > /dev/null
```But it produces 
```
X: user not authorized to run the X server, aborting.


```The first one of course is still working in Natty, but with it's shortcomings.

---

### Post by maizuddin35 on 2011-06-03
so, where exactly I should start this ... command/script ?

---

### Post by ttanev on 2011-06-03
If you're asking about the first one, it's pretty straightforward, I'll quote ad_267's post from there:
> **ad_267 said:**
> I have problems running full screen games with  compiz (games will be randomly minimized and I lose control) so I wrote  this script. It's pretty basic but I still thought it might be useful  for someone else. All it does is runs "metacity --replace," executes the  commands given to it and then runs "compiz --replace."

Installation:

Open a terminal and enter:
```
gksu gedit /usr/games/playgame
```I put mine in /usr/games but it can be anywhere in your path, eg /usr/bin or ~/bin

Enter:
```

#!/bin/bash

if [ $# -lt 1 ]; then
    echo "Usage: playgame game_name game_options" 1>&2
    exit
fi

# Replace compiz with metacity to prevent issues
metacity --replace &

# Run game
$@

# Replace metacity with compiz
compiz --replace

```Save that and close gedit then in the terminal enter:
```
sudo chmod +x /usr/games/playgame
```Now run alacarte or right  click on your menu and select edit menus. Find the launchers for any  games you want to use this with and right click and select properties.  Where it says "Command:," keep the same command but just put "playgame "  in front (without the quotes and with a space after). Eg to play alien  arena, the command is "alienarena" which I changed to "playgame  alienarena"

Now compiz will be replaced with metacity while you play these games.

Known Issues:
Metacity and compiz handle workspaces differently so if you have a lot  of applications spread out on different workspaces and run this they  will end up all on the first workspace.

Note:
Don't run "playgame game_name" in a terminal as when you close the  terminal this will cause compiz to exit and you will lose your window  borders and window management.

P.S. Forgot to say that this in gnome-classic mode of Natty.

---

### Post by maizuddin35 on 2011-06-03
> P.S. Forgot to say that this in gnome-classic mode of Natty.

I thought about that also, so , I need to get into gnome2 classic first, then I run the script. thanks.:)

---

