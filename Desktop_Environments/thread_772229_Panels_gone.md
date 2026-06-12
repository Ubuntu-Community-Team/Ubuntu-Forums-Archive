---
title: "Panels gone"
date: 2008-04-28
forum: Desktop Environments
---

### Post by isomorph on 2008-04-28
Hi All,

I am an absolute noob. Just installed my first Ubuntu ever yesterday.

So today I started my laptop and the panels ( I think they are called panels, the bars on top and on the bottom of the desktop) were gone.

I only get the background image and the mouse is there too.

How do I get the panels back. 

Please give me a stpe by step advise like you would give your grandma:)

Cheers  iso

---

### Post by ryanhaigh on 2008-04-28
press alt-f2 to bring up the run application dialog, then enter gnome-panel and hit enter.

---

### Post by isomorph on 2008-04-28
No reaction when I press Alt+F2

cheers

Iso

---

### Post by anuban on 2008-04-28
Same here...
Nothing happend with Alt+F2.
Someone please help...

---

### Post by anuban on 2008-04-28
Got the trick:

[LIST]
[*] Press CTRL+ALT+F2
[*] Login and password
[*] sudo apt-get remove gnome-panel
[*] sudo apt-get install gnome-panel
[*] sudo apt-get install ubuntu-desktop.
[*] Restart...
[/LIST]
 everything should be fine.:)

Thanks for the help guys...

---

### Post by isomorph on 2008-04-28
I tried ctr alt F2 before.

But install the gnome did not really work.

So I decided this morning I install the whole system freshly.

No harm because I just started testing it so no data loss.

Thank you all anyway.

cheers

Iso

---

### Post by lenn-art on 2008-04-29
> **isomorph said:**
> I tried ctr alt F2 before.

But install the gnome did not really work.

So I decided this morning I install the whole system freshly.

No harm because I just started testing it so no data loss.

Thank you all anyway.

cheers

Iso
Did you remove Evolution?

---

### Post by isomorph on 2008-04-29
hey lenn-art,

Exactly that was the problem I found it out today.

I removed Evolution and then I saw that it will also remove gnome-panel.

Is there anyway to remove evolution (I use thunderbird) and only evolution?

cheers iso

---

### Post by taugust04 on 2008-05-08
> **isomorph said:**
> hey lenn-art,

Exactly that was the problem I found it out today.

I removed Evolution and then I saw that it will also remove gnome-panel.

Is there anyway to remove evolution (I use thunderbird) and only evolution?

cheers iso

Hate to bump this after a week, but... a friend of mine had this issue just yesterday.  Thankfully we found this thread and got it figured out.  Question... should this get filed as a bug?  Does anyone know why when uninstalling Evolution that gnome-panel gets uninstalled.  I know I was able to uninstall Evolution in 7.04 without an issue like this.  I'm just not a fan of Evolution and prefer Thunderbird.

A second related question... what would the correct command be to uninstall Evolution without uninstalling gnome-panel.  It seems that one is listed as a dependency of the other.

Thanks for your help!

---

### Post by flostre on 2008-06-06
I also have this problem from time to time: No panels, no right-click context-menu, alt+f2 does not work. Only my Pidgin contact list starts normally and the background image is there. However, when I reboot everything is fine and back to normal. Just restarting X does not work.

I did not remove Evolution, as a matter of fact, I only installed it on Monday (June 2nd). (I booted my laptop four times w/o problems after that so I think it is unrelated.) Also, gnome-panel and ubuntu-desktop are installed.

And gnome-panel is not only installed, it is also *running*, as can be verified on tty2 using ```
ps -A | grep panel
``` .

I am posting this from my office desktop PC. My laptop is currently in the discussed state. I have no ideas where to start a diagnosis.

Can anyone help?

flostre

---

### Post by flostre on 2008-06-06
Hi,
I'm now posting from my laptop using links2 (text-mode browser). I tried starting nautilus from a tty with ```
nautilus --display=:0.0
```. While that worked fine on my office pc, it did not on my laptop. I also tried other display number in a while loop but for :0.n, n=1,...,2000 I get the error ```
Xlib: connection to ":0.n" refused by server
Xlib: No protocol specified
``` and for :m.0, m=1,...150 I get ```
cannot open display: :m.0
```. Being able to start X programs would not solve the problem, but it could help in doing so.

The other thing I would try to do is to kill all running apps to see if maybe the gnome start-up sequence is being blocked by a hanging app. I already started with cupsd, but it did not work. I was gonna attach the output of ```
ps -A
```, but I found this not to be possible in links2. "Manage attachments" does not appear as a link. My suspects are the processes showing up with most processor time in top, namely gnome-cups-icon and hald. What is gconfd-2?

flostre

---

### Post by flostre on 2008-06-06
Sorry for bumping again, but:
While hints on how to diagnose or solve the problem are still welcome for the future, I have to report that I rebooted my laptop and so temporarily solved the problem. I also applied anuban's solution, maybe it is not just temporarily.

flostre

---

### Post by bigdee973 on 2008-10-01
you dont have to edit or do anything confucious you have 2 options

1)if you have NO PANELS go to Applications>Accessories>terminal and in terminal type in gnome-panel 

now if you JUST CREATED OR already have another panel somewhere on your desktop ...

2)You will have to recreate the panel yourself but do not fret it is quite simple to do.

1. on the other panel, right-click & choose "new panel"
2. then right click the NEW PANEL that was just created & click "add to panel"
3. now choose and add "menu bar", "quit", "notifiication Area", "clock", "volume control" one by one and you should have the original setup
4. right-click on each icon and you can choose "move" to move the icons and "lock to panel" to make the icon stay put and be still after that you should be all done.

now if want to create lil quick launch icons to launch certain applications such as FireFox just go to applications..highlight the application u want..rightclick it and click "add this launcher to panel". There are also other things you can add to the panel such "weather applet", "eyes", "system monitor", "fish" + more in "add to panel" when you right-click the panel which i think are cool.

---

### Post by unhopeful on 2011-07-18
I just installed Ubuntu today along side windows, it installed fine and everything was fine untill i done a restart ( the first restart ) and now when i log in all i get is my desktop Pic and no panels at all. i can right click on the screen to bring up the drop down menu, but that is about it. there is no start button to press as there is no panels at all. i tried a fix i found on this thread were i put in sudo commands to delete the panels and then re install them, but that didnt work either. im at my wits end. it done the same last night when i installed it and i thought it was one of the LOADS of updates i let it install, but today i didnt let it install them all and it still done it. and help would be greatfull as i want to get away from Win7

---

### Post by unhopeful on 2011-07-18
Hate to BUMP my own post, but this is realy anoting, tried everything and nothing works.

---

### Post by Indecline on 2011-09-15
Perhaps this will help? If nothing else, it's from a more recent thread that may prove useful for you..
 			 			 			 		   		 		 		> **wildmanne39 said:**
> Hi, run this in a terminal it may restore you desktop.
```
sudo apt-get install gdm
```Then restart your computer.
Thank you

> **vbnmu said:**
> Hi, I tried ```
sudo apt-get install  ubuntu-desktop
``` which seemed to have fixed it. Should I also  follow the above steps for a proper fix?

---

### Post by akiraaisha on 2013-04-06
Tnx It really works
Trick:
Press CTRL+ALT+F12
Then wait wait wait..
Memorize and type

[LIST]
[*] sudo apt-get remove gnome-panel
[*] sudo apt-get install gnome-panel
[*] sudo apt-get install ubuntu-desktop
[*]then type sudo Reboot. Done
[/LIST]

---

### Post by oldos2er on 2013-04-06
Closed, please don't bump old threads.

---

