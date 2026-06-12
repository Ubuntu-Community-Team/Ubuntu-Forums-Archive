---
title: "trouble modifying fluxbox startup"
date: 2009-05-29
forum: Desktop Environments
---

### Post by zigmo on 2009-05-29
I'm using fluxbox and trying to edit my background image to better display a conky monitor I'm playing with.
A background is being displayed, but none was listed in ~/home/[my home]/.fluxbox/startup.
I'm trying to figure out why isn't that startup file controlling my fluxbox behavior, what is and how can I correct this?
I've prowled around for other fluxbox references, but none seem to refer to the background that is being set.
Any help would be appreciated.

update: I restarted my session and it is setting the background in .fluxbox/startup and then setting it a wallpaper that is in /usr/share/fluxbox.
If I execute the fluxbox configuration file in /usr/share/xsessions it sets it to what I set in my .fluxbox/startup file.

---

### Post by Locutus_of_Borg on 2009-05-29
do you mean the pattered/solid color background?

i dont have fluxbox, but blackbox stores that setting in ~/.blackboxrc which will point to a theme file located in /usr/share/blackbox/styles
check for a ~/.fluxboxrc file, or look in ~/.config for a fluxbox directory with a similar file

the line in the theme file that controls the background is:
```
rootCommand:      
```
you can set it with options like:
"bsetroot -gradient interlacedflatcrossdiagonalgradient -from rgb:4c/04/03 -to black"

or

"bsetroot -solid grey2"

so for a plain black background, the line would read:
rootCommand: bsetroot -solid black


or you can use something like feh to set an image for a background, just put it in the file that starts blackbox, right before the "exec /usr/bin/blackbox" and end it with an &

```

feh ~/images/background.png&
exec /usr/bin/blackbox

```
for example

that file would be .xinitrc or something else depending on your set-up

---

### Post by zigmo on 2009-06-16
Thanks for the advice. It answered some questions but opened up the door for more.
So, when I start up, fluxbox briefly sets my background before reverting to whatever style I have set (in my case, bora blue).
My /home/ian/.fluxbox/startup file sets my background and running applications (conky, for one).
My /home/ian/.fluxbox/init file is setting the background theme (bora blue).
It looks like the startup files is getting processed before the init file, which is overwriting my background setting. So conky is still running, but the background switches to whatever the style dictates.
Do you think there's a way to control this behavior or should I just edit the style file to manually include the background I want?

---

