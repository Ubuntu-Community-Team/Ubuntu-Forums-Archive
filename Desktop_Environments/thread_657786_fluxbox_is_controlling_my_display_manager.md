---
title: "fluxbox is controlling my display manager"
date: 2008-01-03
forum: Desktop Environments
---

### Post by Tyke91 on 2008-01-03
I was tinkering with alot of stuff and finally managed to screw up my computer to the point where I was too lazy to try to fix it... so I just backed up everything important to me and re-installed ubuntu. It took around an hour to get everything back to how I like it... except for the themes.

When I re-installed ubuntu, I decided to try out fluxbuntu 7.10. It's very cool, but I really like the feel of gnome (plus, I miss my compiz :) ), so I re-installed ubuntu-dekstop from the repositories. That worked and now I'm using gnome, but all the windows in metacity are coloured fluxbuntu-style and there's nothing I can do about it. I get a weird version of human where everything is lime green instead of  orange, and when I go to change themes, it gives me large question marks over every icon and will not allow me to change the colo

----------gnome JUST crashed while typing this ----------

Apparently, trying to switch the colors to make sure you are doing something correctly is not good, gnome just decided to quit on me there and I had to ctrl-alt-backspace out of the session. It wont let me log back in either, when I do, it will play the fluxbuntu startup sound and then go to a wallpaper, followed by a black screen of death. I think parts of Metacity and parts of Slim have been mish mashed into the default startup files, and now neither will work properly. I'm now typing this on fluxbox and I don't seem to have that startup sound. All my apps still work, but it's kind of a cheap work-around because I'm being forced into using a window manager that I'm not comfortable using right now,


anyway, how can I do a clean install of Gnome and metacity and make sure that all the defaults are set to them? I like fluxbox, but I don't want to use it if I don't feel like it at the moment :) 


PS: I've heard that you can group windows and flip through them with tabs in fluxbox. Is this true? if so, how do you accomplish this feat?

PPS: while we're on this topic... how can I set up the menus so that I don't have to keep typing "sudo update-menus" every time I install a new thing in fluxbox?

PPPS: How can I add desktop Icons to fluxbox? I have a few, but I want my own and I want to get rid of the ones I don't use.

---

### Post by Tyke91 on 2008-01-04
k... I managed to get back into Gnome and metacity, but I still have the original problem of the themes not working.

(rebooting from within fluxbox, with a sudo password seemed to do something... maybe part of fluxbox wasn't shutting down properly? )

---

### Post by Tyke91 on 2008-01-04
I've done some more experimenting and I've come to realize that the main colour of whatever fluxbox theme that I am using is being forced on every other theme. The shapes are the same (crux has those squares and glossy is the human look alike, but they are both forced to be lime green, no matter their base color) 

Human seems to be the only working theme (the green human that I mentioned before was just glossy, I forgot that it was on instead of human). Still stumped on how to fix this.

---

### Post by GSF1200S on 2008-01-04
> **Tyke91 said:**
> I've done some more experimenting and I've come to realize that the main colour of whatever fluxbox theme that I am using is being forced on every other theme. The shapes are the same (crux has those squares and glossy is the human look alike, but they are both forced to be lime green, no matter their base color) 

Human seems to be the only working theme (the green human that I mentioned before was just glossy, I forgot that it was on instead of human). Still stumped on how to fix this.

What happens when you are in Gnome if you do:

```
metacity --replace
```  ?? That may tell us something as the terminal could spit out some errors...

To get pack to pure Ubuntu, I would:

Open up synaptic and check to see what the fluxbox packages are called, and write them down. Then, kill X using:

```
sudo /etc/init.d/gdm stop
```

Hit Alt+F2 if youre at a black screen with a blinking cursor. Then do

```
sudo apt-get remove ubuntu-desktop
```

```
sudo apt-get remove <name of fluxbox stuff
```

```
sudo apt-get remove gdm xorg
```

```
sudo apt-get autoremove
```

Then reinstall the gnome you want...

```
sudo apt-get install ubuntu-desktop xorg gdm
```

You should still have all your settings, etc in your /home, and youll just need to reinstall any programs that dont come with the Ubuntu release.

This is how I would do it, but you may want to try another way...

Good Luck ;)

---

### Post by p_quarles on 2008-01-04
One other thing to try, before anything complicated: I suspect that the problem may be Fluxbuntu's display manager: Swift. It's not in the normal Ubuntu repos, and may not have offered the option to replace it with GDM when you installed ubuntu-desktop. So, try this first:
```
sudo dpkg-reconfigure gdm
```

---

### Post by jviscosi on 2008-01-04
> **Tyke91 said:**
> I've heard that you can group windows and flip through them with tabs in fluxbox. Is this true? if so, how do you accomplish this feat?


Yes, this is true.  You click and hold with mouse button 2 (it's customizable in later versions of Fluxbox) on the titlebar of one window and drag it onto the titlebar of another, and they get grouped with tabs.  Tabs can be internal or external to the window (I use external ones).  There are writeups about tabbing windows [here]("http://fluxbox.sourceforge.net/features/tabs.php") and [here]("http://fluxbox.sourceforge.net/docbook/en/html/chap-tabs.html").

> **Tyke91 said:**
> 
PPS: while we're on this topic... how can I set up the menus so that I don't have to keep typing "sudo update-menus" every time I install a new thing in fluxbox?


Red Squirrel has a [big how-to]("http://ubuntuforums.org/showthread.php?t=371144") about Fluxbox menus that might help you out with the menu issue.

---

### Post by Tyke91 on 2008-01-04
both metacity --replace and sudo dpkg-reconfigure gdm work without errors and  I have changed the default display manager to gdm instead of slim, but I still get the same theme problem. 

I think your "long method" of doing this would leave out one large thing - I'd like to keep fluxbox, and removing part of it's display manager definitely isn't good for the desktop environment on the whole. I like the way it acts, I just need to keep gnome for now while I test out fluxbox and learn to use it.

btw: thx for the tips :) jviscosi and thank you both for your speedy help :)

---

### Post by Tyke91 on 2008-01-04
hmm... so, I've figured out how to cause the bug.

trying to customize the of any theme will set this off. Your gnome will immediately lock up, the mouse will be mobile, but no buttons will work. The keyboard is still functional, and you canpress ctrl+alt+backspace to get out of the session. I haven't tried ctrl+alt+F(1-6) because it's a tedious bug to work around and I didn't really feel like it, but I suspect that those virtual consoles will work as well. 

to fix this, you will have to restart gnome. you will find two blank panels and a desktop with functional icons. you will also be able to right click. Right click the desktop and select "change desktop background" wait a minute or two and an error will come up saying "unable to start gdm daemons" then the appearance manager will come up. click on the theme tab and re-select human as your theme. ctrl+alt+backspace out and log into a fluxbox session. Restarting from within the fluxbox session and then logging into a gnome session will temporarily fix the bug, but the colours still wont work.

I have no clue how to permanently fix this, and I'm close to just nuking the whole thing and doing a clean install of plain old vanilla Ubuntu 7.10

---

### Post by RedSquirrel on 2008-01-04
> **Tyke91 said:**
> I'm close to just nuking the whole thing and doing a clean install of plain old vanilla Ubuntu 7.10

I don't like nukes, but that's what I would do.

If I wanted to use GNOME primarily and Fluxbox occasionally, I would install the official Ubuntu (with GNOME) and then just install the fluxbox package from the repositories (or build fluxbox from source). That way, I would have GNOME and all its fancy applications but I could play with them in Fluxbox whenever I felt like it.

With regard to the menu, if everything is working properly, there is a script that updates the menu files each time you install software. The script is /etc/menu-methods/fluxbox and the files it generates are:

/etc/X11/fluxbox/fluxbox-menu 
/etc/X11/fluxbox/menudefs.hook

These files should be update *automatically* when you install new packages.

If these are not updated, you can run 'sudo update-menus' to force them to be updated.

If the files *were* updated, but your menu looks the same, you can try **Fluxbox menu -> Reconfigure** (AKA "Reload config") OR **Fluxbox menu -> Restart**.

---

