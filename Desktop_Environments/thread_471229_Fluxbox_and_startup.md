---
title: "Fluxbox and startup"
date: 2007-06-11
forum: Desktop Environments
---

### Post by saggio on 2007-06-11
I have been able to successfully install and configure fluxbox to my liking. However, I have been unable to get the ~/.fluxbox/startup file to work! I was able to get fbsetbg -l working by adding it to the .rootCommand in ~/fluxbox/init, but I can't do that for all the programs I want to start on login (gkrellm, xbindkeys, etc).

What might be the problem? Do I have to change the permissions of the startup to work? Is there a special syntax that I need to use to get my entries to start? 

Right now, my ~/.fluxbox/startup looks something like this: 
```

# fluxbox startup-script
#
#
gkrellm &
xbindkeys &

```

Thanks.

---

### Post by RedSquirrel on 2007-06-11
```

# fluxbox startup-script
#
#
gkrellm &
xbindkeys &

[COLOR=Red]# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/fluxbox
# or if you want to keep a log:
# exec /usr/bin/fluxbox -log "/home/user/.fluxbox/log"[/COLOR] 
```Do you have the lines in red in your startup? If not, add them and see if that helps...

---

### Post by dolphin_oracle on 2007-06-11
I don't know if you just didn't post it or what, but I have one more line in my startup file that you don't show

exec /usr/bin/fluxbox

according to the sample "startup" that line needs to be last.

And I start gkrellm the same as  you, but docked

gkrellm -w &

hope that helps.

edit:  ***red squirrel beat me to it! ***

---

### Post by saggio on 2007-06-11
Okay, well, neither of those worked, but I figured out what the problem was. I use ~/.xsession to start fluxbox, so the ~/.fluxbox/startup doesn't get used. I just had to put all the stuff I had in my startup file into my .xsession to have it load on login.

Thanks for the quick replies, though!

---

### Post by RedSquirrel on 2007-06-11
How are you starting Fluxbox in .xsession? It should be like this:

```
exec startfluxbox
```

If you run the script startfluxbox it will run your ~/.fluxbox/startup.

---

### Post by oldcpu on 2007-06-11
Hi, I missed this topic earlier.  I have the same problem.

Would you please post your ~/.xsession?  I do not have one by default.  I need to know what exactly goes in there.  Thanks.

---

### Post by Jolly-Swagman on 2007-06-12
Hi all have been trying to get fluxbox to work but having few problems error no /etc/X11/X files

 After doing search thru files found there was no xserver,,, or any x enviroment so downloading xubuntu- desktop hope this should solve my problems 

still lots of errors reading pkgs and then halts as to many errors found,, 

Jolly Swagman


Any help much appreciated as have tried all the how to's so far and hasnt solved

---

### Post by jseiser on 2007-06-12
i installed fluxbox with just ... sudo aptitude install xorg fluxbox mc htop rxvt-unicode cplay rtorrent elinks feh leafpad

i believe the xserver is in the xorg package.   Then you just sudo dpkg-reconfigure xserver-xorg and set up your graphics card and monitor etc.

then startx
copy over your menu files from /etc/X11/fluxbox and rename it as "menu"

create a ~/.xinitrc and put your start up files in there.  

This is how i did it from a server install.  This gives you a complete desktop and it will not take long to download at all.  I think this would run on a pretty old machine as well, havent tried it on one but with everything running htop reports 1% usage.  

then just put this in your menu

[submenu] (Wallpaper)
     [wallpapers] (/home/justin/) {feh --bg-scale}
[end]

changing my directory to whereever you store images you would then want to use as a background.  Clicking on that filename sets it as your background.  then just put
eval `cat ~/.fehbg` in your ~/.xinitrc file. and it will load your last chose wallpaper on start up.

---

### Post by saggio on 2007-06-12
> **oldcpu said:**
> Hi, I missed this topic earlier.  I have the same problem.

Would you please post your ~/.xsession?  I do not have one by default.  I need to know what exactly goes in there.  Thanks.

```
 
gkrellm -w &
xbindkeys &
exec /usr/local/bin/fluxbox

```

But you don't necessarily need to have an .xsession file. If you start from the commandline, you have to use ~/.xinitrc instead. 
[quote="RedSquirrel"] 	How are you starting Fluxbox in .xsession?[/quote]

The official documentation recommends using .xsession if you use a graphical login manager. All the other times I used Fluxbox I never used GDM/KDM, so I couldn't figure out why my .xinitrc wasn't working (even after trying the startup file and everything, like I posted).

---

### Post by RedSquirrel on 2007-06-12
> **saggio said:**
> The official documentation recommends using .xsession if you use a graphical login manager. All the other times I used Fluxbox I never used GDM/KDM, so I couldn't figure out why my .xinitrc wasn't working (even after trying the startup file and everything, like I posted).

If you put

```
exec **startfluxbox**
```as the last line in your ~/.xinitrc or ~/.xsession, it will work. (You could specify the absolute pathname if you want.) 

You are using /usr/local/bin/fluxbox, when it is much better to use **/usr/local/bin/startfluxbox**. They are not the same thing. startfluxbox is a script that will (among other things) run the ~/.fluxbox/startup script (if one does not already exist it will create it and then run it).

Have a look at the startfluxbox script (with more or less or vi, etc.) and you'll see what it does.

I have never had any problems getting the ~/.fluxbox/startup script to work. I can use ~/.xinitrc, ~/.xsession, or /usr/share/xsessions/fluxbox.desktop (for gdm) and they all work just fine as long as I call startfluxbox.

---

### Post by Jolly-Swagman on 2007-06-12
> **jseiser said:**
> i installed fluxbox with just ... sudo aptitude install xorg fluxbox mc htop rxvt-unicode cplay rtorrent elinks feh leafpad

i believe the xserver is in the xorg package.   Then you just sudo dpkg-reconfigure xserver-xorg and set up your graphics card and monitor etc.

then startx
copy over your menu files from /etc/X11/fluxbox and rename it as "menu"

create a ~/.xinitrc and put your start up files in there.  

This is how i did it from a server install.  This gives you a complete desktop and it will not take long to download at all.  I think this would run on a pretty old machine as well, havent tried it on one but with everything running htop reports 1% usage.  

then just put this in your menu

[submenu] (Wallpaper)
     [wallpapers] (/home/justin/) {feh --bg-scale}
[end]

changing my directory to whereever you store images you would then want to use as a background.  Clicking on that filename sets it as your background.  then just put
eval `cat ~/.fehbg` in your ~/.xinitrc file. and it will load your last chose wallpaper on start up.



THANKYOU !!!!     Very Much Mate!


that was the trick that did it, the other way I was following was similar dont no why it didnt work , but again tankyou to you and all that have helped, was giving me a headache, but I Knew that it was just something simple that I missed,,,,,,,Hooray its done,

now just have to work out the web server parts and configs ahhh more reading and all the other things like setting my domain names / ns1 ns2 but it will be all worth it in the end.

and another learning curve mastered 

thanks again   Jolly swagman

---

### Post by oldcpu on 2007-06-12
> i believe the xserver is in the xorg package. Then you just sudo dpkg-reconfigure xserver-xorg and set up your graphics card and monitor etc.
I did not do that and my video and screen is working fine.

Anyone got a second opinion if I should do this or not?

I do not want to risk breaking anything, but at the same time, I would like my system to be properly set up.

> If you start from the commandline, you have to use ~/.xinitrc instead. 
After making a ~/.xinitrc file, fluxbox would not start.  A message appears, but quickly goes away.  Perhaps there is no /usr/local/bin/fluxbox nor /usr/local/bin/startfluxbox?

---

### Post by RedSquirrel on 2007-06-12
> **oldcpu said:**
> I did not do that and my video and screen is working fine.

Anyone got a second opinion if I should do this or not?

I do not want to risk breaking anything, but at the same time, I would like my system to be properly set up.

When you install xorg, it asks you some questions about your video. If you run 'sudo dpkg-reconfigure xserver-xorg' it should make backup copy of xorg.conf which you can use if your new setup is no good. You can also manually create a backup before you reconfigure with:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```



> **oldcpu said:**
>  After making a ~/.xinitrc file, fluxbox would not start.  A message appears, but quickly goes away.  Perhaps there is no /usr/local/bin/fluxbox nor /usr/local/bin/startfluxbox?

Find out with

```
which startfluxbox
```

If you're using the Fluxbox from the Ubuntu repositories, then it's probably in /usr/bin, not /usr/local/bin.

---

### Post by oldcpu on 2007-06-12
> 
Find out with

```
which startfluxbox
```

If you're using the Fluxbox from the Ubuntu repositories, then it's probably in /usr/bin, not /usr/local/bin.
Thanks, that worked!  Even my ~/.Xdefaults is working now.

> When you install xorg, it asks you some questions about your video. If you run 'sudo dpkg-reconfigure xserver-xorg' it should make backup copy of xorg.conf which you can use if your new setup is no good.
Weird...  When I installed xorg, it did not ask my about my video.  I installed xorg, then fluxbox, then used `startx` and got a desktop environment.

So... should I still go ahead with the 'sudo dpkg-reconfigure xserver-xorg'?

---

### Post by RedSquirrel on 2007-06-12
> **oldcpu said:**
> Thanks, that worked!  Even my ~/.Xdefaults is working now.

Great! :)


> **oldcpu said:**
>  So... should I still go ahead with the 'sudo dpkg-reconfigure xserver-xorg'?

It's up to you. If you make a backup of xorg.conf as I mentioned above, then you can restore your settings with (on the console)

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf 
```

---

### Post by oldcpu on 2007-06-12
It asked me so many questions about my hardware that I do not even have answers for!  I just kept on hitting Enter on many things.  I thought it was going to be an automated thing.

Is there an easier way to compare what differences were made between the new xorg.conf and the old one?

---

### Post by RedSquirrel on 2007-06-12
Open the files side by side and compare, or you could use diff.

```
man diff
```

PS - Re: your sig. Fluxbox is a _window_ manager not a desktop manager. ;)

---

### Post by oldcpu on 2007-06-12
There are really no difference between the old and new xorg.conf.  Only thing was the caps lock remapping that I did.

Thanks for the correction.  I always get window and desktop manager mixed up.

---

### Post by Raavea on 2007-09-01
I don't seem to have a .xinitrc or a .xsessions though I do have a .xsessions-errors which is rather full. My startup isn't working at all. Should I do *sudo dpkg-reconfigure xserver-xorg* to fix this? :S

---

### Post by kerry_s on 2007-09-01
> **Raavea said:**
> I don't seem to have a .xinitrc or a .xsessions though I do have a .xsessions-errors which is rather full. My startup isn't working at all. Should I do *sudo dpkg-reconfigure xserver-xorg* to fix this? :S

you create it, one or the other but not both.

---

