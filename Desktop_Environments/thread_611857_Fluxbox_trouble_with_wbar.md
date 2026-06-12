---
title: "Fluxbox trouble with wbar"
date: 2007-11-13
forum: Desktop Environments
---

### Post by benton on 2007-11-13
Hi there, I'm trying to run wbar on a minimalist Gutsy/Fluxbox install. If I start fluxbox and then open a terminal window and run wbar from the command line, wbar works great.

However if I edit fluxbox's startup file and add the wbar command there, fluxbox starts up with a weird screen cursor (I think it's the default X cursor) and right-click does not work (i.e. no menu pops up.) The wbar thing is shown, but somehow it "disables" fluxbox.

Any ideas? Thanks!

---

### Post by kerry_s on 2007-11-13
> **benton said:**
> Hi there, I'm trying to run wbar on a minimalist Gutsy/Fluxbox install. If I start fluxbox and then open a terminal window and run wbar from the command line, wbar works great.

However if I edit fluxbox's startup file and add the wbar command there, fluxbox starts up with a weird screen cursor (I think it's the default X cursor) and right-click does not work (i.e. no menu pops up.) The wbar thing is shown, but somehow it "disables" fluxbox.

Any ideas? Thanks!

did you put "&" on the end
example:
wbar &

---

### Post by Caffeine_Junky on 2007-11-13
@kerry_s

would the  --no-desktop  option help? 

eg:

[COLOR="Red"]wbar &  --no-desktop[/COLOR]

Maybe feh is needed aswell? (lol  just brainstorming here) :)
--------
@benton
Did you get "wbar" from Synaptic?    I did a search in Synaptic for wbar and the result I got was: 
> " bwbar     1.2.3-1    generates text and graphical readout of current bandwith use"

---

### Post by kerry_s on 2007-11-13
> **Caffeine_Junky said:**
> @kerry_s

would the  --no-desktop  option help? 

eg:

[COLOR="Red"]wbar &  --no-desktop[/COLOR]

i have no idea, never actually used wbar. "--no-desktop" is usually used with nautilus to keep it from managing the desktop. i'm very simple now, i use jwm, i just deal with 1 xml file to do everything and jwm already comes with a decent bar, i can get everything from desktop icons to launchers using just the 1 file.

---

### Post by benton on 2007-11-13
Thanks for your answers. I solved it by putting the **wbar &** command *before* the **xrdb -merge ~/.Xdefaults** command in fluxbox startup file. 

I much appreciate your help.

Regards,

-Benton

---

### Post by benton on 2007-11-13
> **kerry_s said:**
> i'm very simple now, i use jwm, i just deal with 1 xml file to do everything and jwm already comes with a decent bar, i can get everything from desktop icons to launchers using just the 1 file.

I'm the following the same route too. On my laptop I installed Ubuntu w/Gnome first, then went to xfce4 only (not Xubuntu) and now I'm running a "command line system" install + fluxbox + wbar. Though minimalist that is no more than I need on my laptop, and that's the beauty of Linux. I keep using the full Ubuntu/Gnome release on my desktop though. :)

Thanks again,

-Benton

---

### Post by Caffeine_Junky on 2007-11-13
Cool, glad ya sorted it benton :)

---

### Post by kerry_s on 2007-11-13
> **benton said:**
> Thanks for your answers. I solved it by putting the **wbar &** command *before* the **xrdb -merge ~/.Xdefaults** command in fluxbox startup file. 

I much appreciate your help.

Regards,

-Benton

any startup you put in fluxbox/startup needs to have & at the end, so it continues to load the next till it finally loads fluxbox.

wbar &
xrdb -merge ~/.Xdefaults &
conky &
etc &

---

### Post by kerry_s on 2007-11-13
> **benton said:**
> I'm the following the same route too. On my laptop I installed Ubuntu w/Gnome first, then went to xfce4 only (not Xubuntu) and now I'm running a "command line system" install + fluxbox + wbar. Though minimalist that is no more than I need on my laptop, and that's the beauty of Linux. I keep using the full Ubuntu/Gnome release on my desktop though. :)

Thanks again,

-Benton

i'm working with 450mhz 256 ram, so i need all the speed i can get. i use debian base though, debian is faster and more flexible, there's also no need to keep up with releases. in debian you just add the other repos and update when ever you feel like it, that means i can always run the latest with out needing to start over on the next release.

---

### Post by Caffeine_Junky on 2007-11-13
Actually, speaking of simple and Fluxbox, here is a theme that** LaRoza** was kind enough to share with us all

```
#############################################################################################
#                                     Title:black+white
#                                     Written By: LaRoza
#                                     Written On: 2007
#                                     Contact: LaRozaProgramming@hotmail.com
#############################################################################################
#COMMENTS:
#           This theme is meant to be simple. It is a result of being distracted by icons, 
#               menus, buttons, and other non-essential visual elements while programming.
#           The colours are: #000000 and #FFFFFF
#############################################################################################

style.name:	black+white
style.author: LaRoza <LarozaProgramming@hotmail.com>
style.date:	2007
style.credits: LaRoza <LaRozaProgramming@hotmail.com>
style.comments: Simplistic, and does not distract.

toolbar:                             Flat 
toolbar.color:                       #000000

toolbar.button.pressed:              Flat
toolbar.button.pressed.color:        #000000

toolbar.clock:                       Flat
toolbar.clock.color:                 #000000
toolbar.clock.textColor:             #FFFFFF

toolbar.label:                       Flat
toolbar.label.color:                 #FFFFFF
toolbar.label.textColor:             #000000

toolbar.windowLabel:                 Flat
toolbar.windowLabel.color:           #FFFFFF
toolbar.windowLabel.textColor:       #000000

toolbar.justify:                     Center



menu.title:                          Flat
menu.title.color:                    #000000
menu.title.textColor:                #FFFFFF
menu.title.justify:                  Center

menu.frame:                          Flat
menu.frame.color:                    #000000

menu.frame.textColor:                #FFFFFF
menu.frame.justify:                  Left

menu.hilite:                         Flat
menu.hilite.color:                   #FFFFFF


menu.hilite.textColor:               #000000

menu.bullet:                         Diamond
menu.bullet.position:                Left



window.title.focus:                  Flat
window.title.focus.color:            #000000

window.title.unfocus:                Sunken
window.title.unfocus.color:          #000000


window.label.focus:                  Flat
window.label.focus.color:            #000000
window.label.focus.textColor:        #FFFFFF

window.label.unfocus:                Flat
window.label.unfocus.color:          #000000
window.label.unfocus.textColor:      #000000


window.button.focus:                 Flat
window.button.focus.color:           #000000
window.button.focus.picColor:        #FFFFFF

window.button.unfocus:               Flat
window.button.unfocus.color:         #000000
window.button.unfocus.picColor:      #FFFFFF

window.button.pressed:               Flat
window.button.pressed.color:         #000000


window.frame.focus:                  Sunken
window.frame.focus.color:            #888888

window.frame.unfocus:                Sunken
window.frame.unfocus.color:          #888888

window.handle.focus:                 Flat
window.handle.focus.color:           #888888

window.handle.unfocus:               Flat
window.handle.unfocus.color:         #888888


window.grip.focus:                   Flat
window.grip.focus.color:             #FFFFFF

window.grip.unfocus:                 Flat
window.grip.unfocus.color:           #888888



window.tab.justify:                  Right
window.tab.label.unfocus:            Flat
window.tab.label.unfocus.color:      #888888

window.tab.label.unfocus.textColor:  #000000
window.tab.label.focus:              Flat
window.tab.label.focus.color:        #FFFFFF

window.tab.label.focus.textColor:    black
window.tab.borderWidth:              1
window.tab.borderColor:              #000000

window.tab.font:                     snap

window.justify:                      Center

toolbar.font:                        snap
window.font:                         snap
menu.title.font:                     -*-lucida-medium-r-*-*-*-100-*-*-*-*-*-*
menu.frame.font:                     -*-lucida-medium-r-*-*-*-100-*-*-*-*-*-*

#toolbar.font:                       -*-lucida-bold-r-*-*-*-100-*-*-*-*-*-*
#window.font:                        -*-lucida-bold-r-*-*-*-100-*-*-*-*-*-*
#menu.title.font:                    -*-lucida-bold-r-*-*-*-100-*-*-*-*-*-*
#menu.frame.font:                    -*-lucida-medium-r-*-*-*-100-*-*-*-*-*-*

borderColor:                         #FFFFFF

bevelWidth:                          2
borderWidth:                         2
handleWidth:                         3

background: Flat 
background.color: #000000
```

It is simple and clean "Black and White"   basic but cool imo

A big thanks to **LaRoza**

---

### Post by benton on 2007-11-13
> **kerry_s said:**
> i'm working with 450mhz 256 ram, so i need all the speed i can get. i use debian base though, debian is faster and more flexible, there's also no need to keep up with releases. in debian you just add the other repos and update when ever you feel like it, that means i can always run the latest with out needing to start over on the next release.

Sounds great. I was tempted to run Debian Etch on my laptop instead of Gutsy, but one thing that sort of "scared" me away of this idea was the somewhat outdated Etch repositories. The ubuntu repos have more recent versions of the software I use the most. That'd let me with the option of installing from source code I know, but I'm not very fond of that (yet) :D

I am curious... why a Debian "custom" install would be faster than Ubuntu's "command line system" install?

---

### Post by benton on 2007-11-13
> 
Maybe feh is needed aswell? (lol  just brainstorming here) :)
--------
@benton
Did you get "wbar" from Synaptic?    I did a search in Synaptic for wbar and the result I got was:

Sorry Caffeine_Junky, I missed your question before. I got a wbar Debian package from it's official web page. Seems to be the latest version. Cheers!

[http://freshmeat.net/projects/wbar/](http://freshmeat.net/projects/wbar/)

---

### Post by RedSquirrel on 2007-11-13
> **Caffeine_Junky said:**
> Actually, speaking of simple and Fluxbox, here is a theme that** LaRoza** was kind enough to share with us all ... It is simple and clean "Black and White"   basic but cool imo

I use a modified [Noir]("http://customize.org/fluxbox/themes/49534") theme for similar reasons.

---

### Post by kerry_s on 2007-11-13
> **benton said:**
> Sounds great. I was tempted to run Debian Etch on my laptop instead of Gutsy, but one thing that sort of "scared" me away of this idea was the somewhat outdated Etch repositories. The ubuntu repos have more recent versions of the software I use the most. That'd let me with the option of installing from source code I know, but I'm not very fond of that (yet) :D

I am curious... why a Debian "custom" install would be faster than Ubuntu's "command line system" install?

yeah, i started with etch base then added the lenny repo and updated, then added the sid repo. you have to do it in steps or you'll get a out of memory error. there's also the option of using expert mode and jumping straight to lenny. ubuntu is just a snap shot of debian sid, you can run lenny/sid and be more up to date than even the latest ubuntu. i rarely if ever use source, i don't even keep those repos.

it's just faster, can't explain it, you can just feel the difference. i use the net installer and when it comes to package selection i just uncheck everything to get the base install.
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso)

here's my repo list, i run lenny/sid with etch security for the 2.6.18 kernel->

```

deb http://www.debian-multimedia.org sid main
deb http://ftp.debian.org/debian/ lenny main non-free contrib 
deb http://ftp.debian.org/debian/ sid main non-free contrib 
deb http://security.debian.org/ etch/updates main contrib non-free 
deb http://security.debian.org/ lenny/updates main contrib non-free 


```

---

### Post by RedSquirrel on 2007-11-14
@kerry_s: Just out of curiosity, have you tried Arch? I'm having quite a good time with it. :)

---

### Post by kerry_s on 2007-11-14
> **RedSquirrel said:**
> @kerry_s: Just out of curiosity, have you tried Arch? I'm having quite a good time with it. :)

not recently, i don't have a working burner right now. looking through my stack the last 1 i used was 0.8, i don't really jump around as much as i use to, i kinda found my peace in debian. :)

---

