---
title: "help choosing a desktop environment - lightweight, extensible, fast..."
date: 2014-01-05
forum: Desktop Environments
---

### Post by ljwobker on 2014-01-05
I'm starting to poke around with a small VPS server running ubuntu... I've got a number of home machines that have always just run the "stock" Unity as I've never really had the need to try and make them lighter-weight.  However, now that I'm living on remote machines that only have 256/512M of memory, I need to figure out something that will solve the following requirements:



[LIST]
[*]a marginally decent window manager.  I do 90% of my work in bash anyway, BUT the main benefit I get out of an X display is the ability to run something like NoMachine (similar to but better than VNC) for remote X connections.  Some will say "just ssh to your server" but my connections are not reliable, and if the network drops, so do all my SSH sessions.  If I run a remote desktop and lose that connection, all my coding and other stuff is exactly as I left it when I reconnect.
[*]I don't even entirely understand what the difference is between a "desktop environment" and a "display manager".  Back in the mid-90's when I was actually good at this stuff, all we had to do was pick a window manager and type "startx"   -- I read somewhere that you can run the window manager without the display manager and save memory... but it was not at all clear to be how this actually works.
[*]I will spend 95% of my time running only three applications:  Kate (for code editing), Chrome, and Terminal.
[*]Having a launcher (preferably one that works like the windows button in win7, that's one of the few things that they got really right) would be a plus
[*]A simple window manager is fine, but preferably one that's at least extensible should I decide there's more stuff I need down the road.
[/LIST]

would love to hear thoughts from the crowd.  ;-)

---

### Post by ibjsb4 on 2014-01-06
> I read somewhere that you can run the window manager without the display manager and save memory

Yes, thats the way I do it, with a script to autostart X.  I can see a difference on older machines doing this, but I find on newer machines there is little performance gain and 'lightdm' works just about as well.

I think Arch explains it well.

Edit:  I should add that on download lightdm takes about 300MB and just loading xorg takes about 100MB.  Myself, I start with xserver-xorg and that takes about 75MB.

[https://wiki.archlinux.org/index.php/xinitrc](https://wiki.archlinux.org/index.php/xinitrc)

---

### Post by jan-goebel-g on 2014-01-06
Ill make it short: Unity, cinnamon, Mate(same base just less apps, once u intall the functions u want or uninstall those u dont its about the same), even kde are all pretty alright on the cpu.
You disable animations and you are set. Disabling composite shouldnt result in better performance, im not sure about your gpu so you could try it using 2d unity or non compositing cinnamon.

If you have 256mb of ram u wont get along with any of those, ur on swap all the time, all of them are well about 300mb of usage at boot.


Xfce is a little bit better on pure memory, on performance its the same (actually compiz and kde take LESS cpu power to move and resize a browser window from my tests. could vary with drivers though).


I dont know about the lxde this year, but last time i checked the ubuntu version was very well optimized and could fit your needs.
Then there is openbox ofc which will definitely fit your needs and which i can recommend to you, if u wanna try without hassle try the manjaro live cd which shows nice implementation of openbox and its limitations.

Alright now here comes the cool stuff:
-Tiling wm managers such as i3 wont use a lot of memory but it will also add up once u install functions that u want and u will be limited on window management.
-Awesome while still being a twm i feel is smooth to use and it has some nice little mouse usage that you could like.


IN the end u gotta try for your hardware, dont think that unity is heavy on ressources anymore, there is a big difference in between 12.04 and 13.10 and kde did well too.
Cinnamon, unity and mate are all gnome3, u get that there is no major differences, forks look different and can provide nice extra but they cant break limitations.

Id recommend u to try awesome, if you use 90%of console you are BETTER off 90%of the time and only a little bit less convenient at 10%of the time, all applications run perfectly on it.
If you want to do more get i3 or the ratpoison thing which is great too.

>>[COLOR=#000000]Having a launcher (preferably one that works like the windows button in win7, that's one of the few things that they got really right) would be a 
I wanted to ignore it but i cant.
Menus steal your time, typing pbrush is faster then clicking a button and going to applications and go down clicking pbrush. Period.
Putting the 5 programs u frequently use on the panel of any kind beats everything if u need to click it while playing scratching your balls with the other hand.Period:-)
The best thing they did was to remove this historical feature(they didnt of course, its all the same but if the windows donkeys stop to see the button they wont try to click the corner so it goooone), app launchers are the way to go and both apple and microsoft offer both for a reason (one for dinosaurs, the other one for the efficient users).
That being said, the win7 button and all the DE offer you some button u click on and get a solution to browser through your apps.
All of them give u some non-fuzzy search function so if i type gimp after clicking the ubuntu button (or super) or the cinnamon button (or super) or (...) u get gimp and in most of them u can even look for files.
On Awesome u get a right click menu like openbox, thats why i recommended it to you and of course there is a run: command too that uses system autocompletion so doing gi[tab] might give u gimp too.
On all of them u can install some app launcher, there is multiple depending on your style.

[/COLOR]

---

