---
title: "fluxbox menu won't change"
date: 2007-08-01
forum: Desktop Environments
---

### Post by killphil on 2007-08-01
I tried to change my fluxbox menu using this thread

[http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)

My menu didn't change after restart or reboot.  I checked ~/.fluxbox/custom-menu and ~/.fluxbox/init and both look good.

---

### Post by merlinus on 2007-08-01
My menu is at ~/.fluxbox/menu, and it changes whenever I add/remove anything.

Maybe try renaming the file.

-merlin

---

### Post by RedSquirrel on 2007-08-01
> **killphil said:**
> I tried to change my fluxbox menu using this thread

[http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)

My menu didn't change after restart or reboot.  I checked ~/.fluxbox/custom-menu and ~/.fluxbox/init and both look good.


Hmm... strange. It works for me.

Can you post the output of:

```
grep menuFile ~/.fluxbox/init
```

and

```
cat ~/.fluxbox/custom-menu
```

---

### Post by killphil on 2007-08-01
i set up a custom menu and then I changed it in the /init file.  ~/.fluxbox/menu  is my default menu.  I don't want to mess with it cause if something goes wrong I want a menu to fall back on.

---

### Post by killphil on 2007-08-01
something got screwed up
grep menuFile ~/.fluxbox/init

session.menuFile:    ~/.fluxbox/menu

cat shows no such file so I'll try again and post results.  Thanks

---

### Post by killphil on 2007-08-01
Now, it's getting really weird.  I exit fluxbox.  Log back in.  I check grep menuFile  and get fluxbox/menu  and cat  /custom-menu says no such file or directory.  I open up /custom-menu w/nano and all my info is there.  Then I open /init w/nano and session menuFile says /custom-menu.  I check grep and cat and they look good.  I restart and no change.  I check again grep and cat again and they look good.  I log out and back in.  Check grep and cat again...no good.  Open /custom-menu and /init and they are good.  Check grep and cat again...good.  Restart and no change.  WTF

Sorry, I hope you can make sense of this.  Basically it doesn't recognize my changes.

---

### Post by merlinus on 2007-08-01
As I alluded to earlier, this kept happening to me.  That's why I renamed it back to menu.

You can always copy the original to menu_backup, in case things get even more weird.

-merlin

---

### Post by killphil on 2007-08-01
Yeah,  I've already backed it up, so I'll have to try your way merlinus.  Thanks

---

### Post by RedSquirrel on 2007-08-01
It sounds to me like the files are not in the right place. It is important to get the paths exactly right. We could spend some time sorting this out, but it sounds to me like you are better off using whatever works for you.

---

### Post by kerry_s on 2007-08-01
if you did a fluxbox only install and did not select fluxbox in the session menu, it defaults to only reading /etc/X11/fluxbox/*

you can try deleting or renaming the ~/.fluxbox folder logout and select fluxbox in session than log back in it should create a new working skel for ~/.fluxbox.

---

### Post by killphil on 2007-08-01
No.  I've double checked the paths and they are good.  I don't know what's up.  I've changed some things in the /menu file and the changes are working.  I've got the original backed up so I'm good.  Thanks for the help.

---

### Post by kerry_s on 2007-08-02
> **RedSquirrel said:**
> It sounds to me like the files are not in the right place. It is important to get the paths exactly right. We could spend some time sorting this out, but it sounds to me like you are better off using whatever works for you.


Hey RedSquirrel, has roxterm hit the ubuntu repos yet? you got to try that 1, it's pretty sweet, smaller than xterm, as fast as rxvt,aterm. easy as hell to mess with the settings. desktop independent.

---

### Post by RedSquirrel on 2007-08-02
> **killphil said:**
> No.  I've double checked the paths and they are good.  I don't know what's up.  I've changed some things in the /menu file and the changes are working.  I've got the original backed up so I'm good.  Thanks for the help.

I have been planning to update the howto for some time now and in the latest revision (completed today :)) I have removed the steps that involved changing the init file just to keep things simple.

I haven't had any problems when I have changed the value of the menuFile resource in init. These days I have it pointing to ~/.fluxbox/my-menu which is actually a symbolic link that I can point to the menu file I feel like using (I have a few of them). In any case, I guess it's safest for the howto to leave menuFile pointing to ~/.fluxbox/menu. ;)

---

### Post by RedSquirrel on 2007-08-02
> **kerry_s said:**
> Hey RedSquirrel, has roxterm hit the ubuntu repos yet? you got to try that 1, it's pretty sweet, smaller than xterm, as fast as rxvt,aterm. easy as hell to mess with the settings. desktop independent.

Looks interesting. Thanks for the tip.

I don't see it in the feisty repositories. Oh, but there is an [SVN version]("http://roxterm.sourceforge.net/#download")... drool... :grin:

---

### Post by kerry_s on 2007-08-02
> **RedSquirrel said:**
> Looks interesting. Thanks for the tip.

I don't see it in the feisty repositories. Oh, but there is an [SVN version]("http://roxterm.sourceforge.net/#download")... drool... :grin:

i thought you was using gutsy?

yeah, i totally replaced xterm with it, it's nice, half the size of xterm with some neat features, transparency works somewhat, i think it still needs work. i can't get mc to go transparent in it though, it just go's black and white. theres also no command to set the title, for example: when i use mcedit as root i used> xterm -T "Root" -e sudo mcedit "$@" <in roxterm there's no option to change the title so i just changed the color> roxterm -e sudo mcedit -b "$@" <which makes it black & white, not perfect, but i can tell them apart, it will do for now :)

---

### Post by RedSquirrel on 2007-08-02
> **kerry_s said:**
> i thought you was using gutsy?

No, I'm still using feisty (server). It seems to work fairly well for my needs, so I'm not in a rush to try gutsy just yet. :)

(I just checked on [http://packages.ubuntu.com](http://packages.ubuntu.com) for gutsy and I didn't see *roxterm* there either.)

I just installed rox-filer... my new toy for this evening. I don't normally use a file manager, but I figured it's worth a try. ;)

---

### Post by kerry_s on 2007-08-02
> **RedSquirrel said:**
> No, I'm still using feisty (server). It seems to work fairly well for my needs, so I'm not in a rush to try gutsy just yet. :)

(I just checked on [http://packages.ubuntu.com](http://packages.ubuntu.com) for gutsy and I didn't see *roxterm* there either.)

I just installed rox-filer... my new toy for this evening. I don't normally use a file manager, but I figured it's worth a try. ;)

LOL, i mostly use mc, but i have been trying to use rox more. since i want to play with roxterm i put my mc launcher back though, so i guess rox-filer will just have to take a break till i get bored. :lolflag:

you can do like me and still use mcedit for your editor in rox.
xterm -e mcedit "$@"

you still use mc right?

---

### Post by RedSquirrel on 2007-08-02
> **kerry_s said:**
> you can do like me and still use mcedit for your editor in rox.
xterm -e mcedit "$@"

you still use mc right?

Actually, I don't think I've ever used mc (I have heard of it, of course.)

I'm comfortable manipulating everything on the command line, so I generally have no need for a file manager. I was thinking last night that I should create an entry in my menu that is labeled "File Manager" and have it open uxterm! :evil: :grin:

One thing I find a graphical file manager excels at is tidying up a mess of files. I have been rather lazy and my home directory is full of miscellaneous files that should be moved to more suitable locations. I can certainly move those files around using the command line, but when there are so many of them, sometimes I find it's easier to perform that task by looking at large icons in a file manager rather than a list of files (the same way that you would move papers into folders in the real world). If I hadn't dumped all those files into ~ in the first place then I wouldn't really need to use a file manager. (This is the same thing that happens with my bookmarks file. :() Oh, well. Time for a cleanup. 

Anyway, for editors I use vim, gvim, and leafpad. I tried scite for a little while just to see what it was like, but I prefer vim/gvim.

---

### Post by Nythain on 2007-08-03
> **kerry_s said:**
> i thought you was using gutsy?

yeah, i totally replaced xterm with it, it's nice, half the size of xterm with some neat features, transparency works somewhat, i think it still needs work. i can't get mc to go transparent in it though, it just go's black and white. theres also no command to set the title, for example: when i use mcedit as root i used> xterm -T "Root" -e sudo mcedit "$@" <in roxterm there's no option to change the title so i just changed the color> roxterm -e sudo mcedit -b "$@" <which makes it black & white, not perfect, but i can tell them apart, it will do for now :)
damn, you almost had me sold till you mentioned the lack of transparency with MC... my main file manager... then again, since i run a black and white desktop i guess i could run mc -b and it should blend in close enough... gonna have to look into this... been looking for a suitable terminal replacement... thanks

---

### Post by kerry_s on 2007-08-03
> **Nythain said:**
> damn, you almost had me sold till you mentioned the lack of transparency with MC... my main file manager... then again, since i run a black and white desktop i guess i could run mc -b and it should blend in close enough... gonna have to look into this... been looking for a suitable terminal replacement... thanks

yeah can't figure it out, "mc -b" on a transparent background is suppose to make mc transparent right?
this is what it looks like with mc -b->

---

### Post by Nythain on 2007-08-03
well... i can get mc as transparent as usual... still kind of ugly grey and black in parts, but for the most part its transparent... is there a way to run roxterm without the titlebar... i mean i figured out --hide-menubar but it still runs with the fluxbox titlebar wich is going to keep me from switchign from eterm for it

---

### Post by kerry_s on 2007-08-03
> **Nythain said:**
> well... i can get mc as transparent as usual... still kind of ugly grey and black in parts, but for the most part its transparent... is there a way to run roxterm without the titlebar... i mean i figured out --hide-menubar but it still runs with the fluxbox titlebar wich is going to keep me from switchign from eterm for it

in fluxbox, i would just set the window to remember the decoration, then toggle the decoration off. do you have toggle setup?

Mod4 t :ToggleDecor

ToggleDecor	
Toggles whether or not current window has a border, buttons, and titlebar.

[http://fluxbox.sourceforge.net/docs/en/newdoc.keybindings.php](http://fluxbox.sourceforge.net/docs/en/newdoc.keybindings.php)

oh, you also don't need to use --hide-menubar, right click the in roxterm window> preferences>edit current profile, in the first tab just untick "show menubar by default"

---

### Post by kerry_s on 2007-08-03
> **Nythain said:**
> well... i can get mc as transparent as usual... still kind of ugly grey and black in parts, but for the most part its transparent... is there a way to run roxterm without the titlebar... i mean i figured out --hide-menubar but it still runs with the fluxbox titlebar wich is going to keep me from switchign from eterm for it

Oh yeah, i found the fix my friend. you just need to add a line to the end of your ~/.mc/ini 
you don't even need to use the "-b" option any more.
this line will give you full transparency in everything and i mean everything!
```

[Colors]
base_color=normal=,default:marked=,default:selected=,default:markselect=,default:errors=,default:input=,default:gauge=,default:reverse=,default:menu=,default:menusel=,default:menuhot=,default:menuhotsel=,default:dnormal=,default:dfocus=,default:dhotnormal=,default:dhotfocus=,default:helpnormal=,default:helpitalic=,default:helpbold=,default:helplink=,default:helpslink=,default:viewunderline=,default:executable=,default:directory=,default:link=,default:stalelink=,default:device=,default:special=,default:core=,default:editnormal=,default:editbold=,default:editmarked=,default

```

---

### Post by kerry_s on 2007-08-03
Alright Nythain, here's my final result i put alittle blue tint in to the transparency to give it that good old mc feeling.

---

### Post by Nythain on 2007-08-03
god bless these forums... that is slick... ill play around with it this weekend when i have some time... been thinkin of playin around with my theme lately anyways... ill post a pic when im done... thanks much for the total transparency info

---

### Post by kerry_s on 2007-08-03
> **Nythain said:**
> god bless these forums... that is slick... ill play around with it this weekend when i have some time... been thinkin of playin around with my theme lately anyways... ill post a pic when im done... thanks much for the total transparency info

yeah i'm still playing with the colors, the total is a bit much for me, it's pretty easy to figure out, i tried to cover all the settings, it took me forever to find them.
just find the corresponding word for the thing you want and just put the color in front of the "=". ":" is the spacing to the next item."default" is the fallback.

example:
base_color=normal=black,default: <this is 1 item
marked=black,default: <-this is the next item

you'll just have to play with it, it's hard to get a good balance on dark themes. :)

---

### Post by merlinus on 2007-08-03
> 
Oh yeah, i found the fix my friend. you just need to add a line to the end of your ~/.mc/ini 
you don't even need to use the "-b" option any more.
this line will give you full transparency in everything and i mean everything!
Hi Kerry.  I have installed mc, but there is no ini file in ~/.mc

I just ran mc from a terminal to see if that would create the ini, but no.

And no ini file in /usr/share/mc either.

Finally, what change in the color code gave you the blue tint and white text?

Many thanks!

-merlin

---

### Post by kerry_s on 2007-08-03
> **merlinus said:**
> Hi Kerry.  I have installed mc, but there is no ini file in ~/.mc

I just ran mc from a terminal to see if that would create the ini, but no.

And no ini file in /usr/share/mc either.

Finally, what change in the color code gave you the blue tint and white text?

Many thanks!

-merlin


my guess is you haven,t made any change in the mc preference. on the top were you see "option" just make a change, uncheck a box and click save, then quit and start it back up again and put the setting back. that should make it create a personal setting.

the blue tint is from the color scheme, not the code, i currently have directories set to blue and full transparency so i have the color turned off.

here's my current code:

```

[Colors]
base_color=normal=black,default:marked=black,default:selected=gray,default:markselect=,default:errors=,default:input=,default:gauge=,default:reverse=,default:menu=,default:menusel=,default:menuhot=,default:menuhotsel=,default:dnormal=,default:dfocus=,default:dhotnormal=,default:dhotfocus=,default:helpnormal=,default:helpitalic=,default:helpbold=,default:helplink=,default:helpslink=,default:viewunderline=,default:executable=,default:directory=blue,default:link=,default:stalelink=,default:device=,default:special=,default:core=,default:editnormal=,default:editbold=,default:editmarked=,default

```

The pic's don't do it justice, the blue's alot brighter on my end. :)
i added a white tint so you could see it better.

---

### Post by merlinus on 2007-08-03
Thanks for your help, but clearly I am missing something big-time.

I am using chthulain as my fluxbox style, and the terminal is unreadable with the color code I added to ~/.mc.  The desktop background is dark grey, so that is probably the problem.

The directories do not show up as blue, either.

Also, will this only work with RoxTerm?  If so, I will have to find and install it.

BTW, although it must be obvious -- I have only recently begun playing around with fluxbox.

-merlin

---

### Post by kerry_s on 2007-08-03
what terminal are you using?
i can install it to test on my end and get it to the colors you want.
do you have any ~/.xdefaults settings for term color?

also, why's your background darkgrey? chthulain has a blue background, that's what i used in fluxbox, you might not have the updated themes. check in /usr/share/fluxbox/styles and look in the theme file, i bet you it has bsetbg, instead fbsetbg which i think was used in fiesty fluxbox. in the newer fluxbox themes they did away with that setting and use a color code.

---

### Post by merlinus on 2007-08-03
terminal and gnome-terminal are in my fluxbox menu.  either one is fine.

mc looks the same in both.

When I run mc in xterm, it is black on white.

When roxterm hits the ubuntu repos, I will install that as well.

And  no ~/.xdefaults file.

Many thanks!

-merlin

---

### Post by kerry_s on 2007-08-03
> **merlinus said:**
> terminal and gnome-terminal are in my fluxbox menu.  either one is fine.

mc looks the same in both.

When I run mc in xterm, it is black on white.

When roxterm hits the ubuntu repos, I will install that as well.

And  no ~/.xdefaults file.

Many thanks!

-merlin

black on white? is that the xterm or mc?
ooh, i don't want to do gnome-terminal that's bloatware, it like wants me to install almost all of gnome.

try this one:

```
base_color=normal=black,default:marked=red,default:selected=white,default:markselect=,default:errors=,default:input=,default:gauge=,default:reverse=,default:menu=black,default:menusel=,default:menuhot=green,default:menuhotsel=green,default:dnormal=,default:dfocus=,default:dhotnormal=,default:dhotfocus=,default:helpnormal=,default:helpitalic=,default:helpbold=,default:helplink=,default:helpslink=,default:viewunderline=,default:executable=,default:directory=blue,default:link=,default:stalelink=,default:device=,default:special=,default:core=,default:editnormal=black,default:editbold=,default:editmarked=,default
```

the other one should have worked though, mc color is independent of the terminal.

---

### Post by kerry_s on 2007-08-03
okay my bag, dont use that 1 above it's set up for black text.
here's 1 for xterm's white black settings.

```
base_color=normal=white,default:marked=red,default:selected=white,default:markselect=,default:errors=,default:input=,default:gauge=,default:reverse=,default:menu=white,default:menusel=,default:menuhot=green,default:menuhotsel=green,default:dnormal=,default:dfocus=,default:dhotnormal=,default:dhotfocus=,default:helpnormal=,default:helpitalic=,default:helpbold=,default:helplink=,default:helpslink=,default:viewunderline=,default:executable=,default:directory=blue,default:link=,default:stalelink=,default:device=,default:special=,default:core=,default:editnormal=white,default:editbold=,default:editmarked=,default
```

look like this->

---

### Post by merlinus on 2007-08-03
Thanks!  Other than changing marked to green, because the red did not show up wll, it works great!

Another question, if you will.  I have chthulain selected as my theme, but when I select other themes, the desktop background color remains the same.

Is this how it should be?

And where can I find eterm?

-merlin

---

### Post by yabbadabbadont on 2007-08-03
> **merlinus said:**
> Thanks!  Other than changing marked to green, because the red did not show up wll, it works great!

Another question, if you will.  I have chthulain selected as my theme, but when I select other themes, the desktop background color remains the same.

Is this how it should be?

And where can I find eterm?

-merlin

Newer versions of fluxbox do not allow the theme to change the background any more.

To get eterm, you need to install the ....  wait for it....  eterm package.  :D  (once you do install it, the name of the program is Eterm, with a capital E)

---

### Post by merlinus on 2007-08-03
Yeah, I should have searched in Synaptic for eterm before asking....

> 
Newer versions of fluxbox do not allow the theme to change the background any more.


OK.  So how do I do this manually?  Is there a config file to edit?

Many thanks!

-merlin

---

### Post by kerry_s on 2007-08-03
post your /usr/share/fluxbox/styles/chthulain here so i can look at it, i know i fixed mine so that it works. once you grab eterm though you can set wallpaper's/backgrounds.

(assuming you have gedit)
gedit /usr/share/fluxbox/styles/chthulain

right click select all and middle click here to paste it.

---

### Post by yabbadabbadont on 2007-08-03
Which version of fluxbox are you using?  What does the "About" option on the fluxbox menu show?

---

### Post by merlinus on 2007-08-03
/usr/share/fluxbox/styles/Cthulhain:
> 
! Title:    cthulhain
! By:        cthulhain ([http://lordzork.com/blackbox/](http://lordzork.com/blackbox/)
! Email:    [EMAIL="cthulhain@lordzork.com"]cthulhain@lordzork.com[/EMAIL]
! Comment:    no comment

! ***** toolbar *****
toolbar:                raised gradient vertical
     toolbar.color:            #585858
     toolbar.colorTo:            #0f1319

toolbar.label:                parentrelative
     toolbar.label.textColor:        #cccccc

toolbar.windowLabel:                sunken gradient crossdiagonal
     toolbar.windowLabel.color:        #151a22
     toolbar.windowLabel.colorTo:    #7a8290
     toolbar.windowLabel.textColor:    #ffffff

toolbar.clock:                parentrelative
     toolbar.clock.textColor:        #cccccc

toolbar.button:                parentrelative
     toolbar.button.picColor:        #cccccc

toolbar.button.pressed:            flat gradient vertical
     toolbar.button.pressed.color:    #0f1319
     toolbar.button.pressed.colorTo:    #7a8290

toolbar.workspace:            parentrelative
     toolbar.workspace.borderWidth:    0
     toolbar.workspace.color:        #585858
     toolbar.workspace.colorTo:     #0f1319

! ***** menu *****
menu.title:                raised gradient crossdiagonal
     menu.title.color:            #151a22
     menu.title.colorTo:        #7a8290
     menu.title.textColor:        #ffffff

menu.frame:                sunken gradient crossdiagonal
     menu.frame.color:            #0f1319
     menu.frame.colorTo:        gray40
     menu.frame.textColor:        #cccccc

menu.hilite:                sunken gradient crossdiagonal
     menu.hilite.color:            #151a22
     menu.hilite.colorTo:        #7a8290
     menu.hilite.textColor:        #ffffff

menu.bullet:                triangle
     menu.bullet.position:        right


! ***** window focused *****
window.title.focus:            raised gradient diagonal
     window.title.focus.color:        gray40
     window.title.focus.colorTo:    #0f1319

window.label.focus:            sunken gradient crossdiagonal
     window.label.focus.color:        #151a22
     window.label.focus.colorTo:    #7a8290
     window.label.focus.textColor:    gray90

window.button.focus:            parentrelative
     window.button.focus.picColor:    #cccccc

window.button.pressed:            flat gradient vertical
     window.button.pressed.color:    #0f1319
     window.button.pressed.colorTo:    #7a8290

window.handle.focus:            raised gradient diagonal
     window.handle.focus.color:        gray50
     window.handle.focus.colorTo:    #0f1319

window.grip.focus:            raised gradient diagonal
     window.grip.focus.color:        #7a8290
     window.grip.focus.colorTo:        #151a22

window.frame.focusColor:        #858585
window.frame.focus.color:        #858585


! ***** window unfocused *****
window.title.unfocus:            raised gradient diagonal
     window.title.unfocus.color:    gray40
     window.title.unfocus.colorTo:    #0f1319

window.label.unfocus:            parentrelative
     window.label.unfocus.textColor:    #808080

window.button.unfocus:            parentrelative
     window.button.unfocus.picColor:    #727272

window.handle.unfocus:            raised gradient diagonal
     window.handle.unfocus.color:    gray50
     window.handle.unfocus.colorTo:     #0f1319

window.grip.unfocus:            raised gradient diagonal
     window.grip.unfocus.color:        gray50
     window.grip.unfocus.colorTo:    #0f1319

window.frame.unfocusColor:        #5e6166
window.frame.unfocus.color:        #5e6166


! ***** fonts *****
*.font:                    -*-lucida-medium-r-*-*-*-100-*-*-*-*-*
    toolbar.justify:            center
    window.justify:            right
    menu.title.justify:            center
    menu.frame.justify:            right

! ***** the rest *****
borderColor:                #202020
borderWidth:                1
bevelWidth:                2
handleWidth:                4
frameWidth:                0

background: flat
background.color: #3a404b

! ***** bbpager *****
bbpager.frame:                sunken gradient crossdiagonal
    bbpager.frame.color:        #151a22
    bbpager.frame.colorTo:        #7a8290

bbpager.desktop:            parentrelative

bbpager.desktop.focus:             flat gradient vertical
    bbpager.desktop.focus.color:     #0f1319
    bbpager.desktop.focus.colorTo:     gray40

bbpager.window:                raised gradient vertical
    bbpager.window.color:        gray40
    bbpager.window.colorTo:        #0f1319

bbpager.window.focus:            raised gradient crossdiagonal
    bbpager.window.focus.color:        #151a22
    bbpager.window.focus.colorTo:    #7a8290

bbpager.desktop.focusStyle:        border
bbpager.active.window.borderColor:    #202020
bbpager.inactive.window.borderColor:    #202020
bbpager.active.desktop.borderColor:    #0f1319


---

### Post by merlinus on 2007-08-03
> **yabbadabbadont said:**
> Which version of fluxbox are you using?  What does the "About" option on the fluxbox menu show?

No "About" option in fluxbox menu, but Synaptic says:

0.9.15.1+1.0RC2-1

-merlin

---

### Post by RedSquirrel on 2007-08-03
From running:

```
grep background /usr/local/share/fluxbox/styles/*
```

... it looks like all of the themes in /usr/share/fluxbox/styles specify a background except "Emerge" and "BlueFlux". Are you saying your background doesn't change when you select (for example) "Operation"?

---

### Post by merlinus on 2007-08-03
Correct.  I can run through the entire list (27 total) and the desktop background remains the same.

-merlin

---

### Post by yabbadabbadont on 2007-08-03
Edit: From reading the current manpage for fluxstyle, it appears that I am completely wrong...  :oops:  Sorry.

---

### Post by yabbadabbadont on 2007-08-03
Assuming that you are using a login manager like GDM or KDM, check your ~/.xsession-errors file to see if fluxbox is spitting out any errors when you change styles.

---

### Post by merlinus on 2007-08-03
No errors.

Thanks...

-merlin

---

### Post by yabbadabbadont on 2007-08-03
Well, if you just want to have a single background, you can set it in your ~/.fluxbox/startup or using the rootCommand line in ~/.fluxbox/init or by creating a ~/.fluxbox/overlay file and setting the background option there.

---

### Post by kerry_s on 2007-08-03
i think i remember the problem, the theme has already been updated to the newst version, but fluxbox is still looking for the "fbsetroot" line. so that's do a simple test, in your terminal run this> fbsetroot -solid blue
now just let us know if it changed.

i thought you grabbed eterm? if you did you can set a background.

i'll up load my background, i only have 1, stick it in ~/.fluxbox/backgrounds/
then run this in terminal> fbsetbg ~/.fluxbox/backgrounds/piss.jpg
it should match your theme,since i was using that same theme. :)

click on it>right click>save image as

---

### Post by merlinus on 2007-08-03
> **kerry_s said:**
> i think i remember the problem, the theme has already been updated to the newst version, but fluxbox is still looking for the "fbsetroot" line. so that's do a simple test, in your terminal run this> fbsetroot -solid blue
now just let us know if it changed.

yes.

> 
i thought you grabbed eterm? if you did you can set a background.


I cannot figure out how to do this, after looking through eterm files.  It alternates between only two, although there are lots in /usr/share/Eterm/themes.

Many thanks!

-merlin

---

### Post by yabbadabbadont on 2007-08-04
Once you have installed eterm, the Esetroot command is also included.  Now you can use fbsetbg (it comes with fluxbox) to set your background.  Just run "fbsetbg -h" in a terminal window to see how to use it.

---

### Post by kerry_s on 2007-08-04
> **merlinus said:**
> yes.



I cannot figure out how to do this, after looking through eterm files.  It alternates between only two, although there are lots in /usr/share/Eterm/themes.

Many thanks!

-merlin

Huh? you must be talking about eterm-themes, you don't need that. did you grab the picture and use the command to set your fluxbox background? just to let you know eterm can do transparency, but it is not utf-8, so mc looks like crap in it.

---

### Post by merlinus on 2007-08-04
I can run fbsetbg and add a parameter to a background graphic.  To make it run after restarting, looks like it has to be added to ~/.fluxbox/startup, no?

Then I can set Eterm to a transparent background.  But whenever I restart it, it is no longer that way.  Any method to have it be transparent at startup?

 Can rox also be set to transparent?  Could not find that choice in options.

Thanks for the expertise and assistance!

-merlin

---

### Post by kerry_s on 2007-08-04
> **merlinus said:**
> I can run fbsetbg and add a parameter to a background graphic.  To make it run after restarting, looks like it has to be added to ~/.fluxbox/startup, no?

Then I can set Eterm to a transparent background.  But whenever I restart it, it is no longer that way.  Any method to have it be transparent at startup?

 Can rox also be set to transparent?  Could not find that choice in options.

Thanks for the expertise and assistance!

-merlin

you can add> fbsetbg -l <to ~/.fluxbox/init and it will set the last background used.look for> session.screen0.rootCommand:    fbsetbg -l

for eterm click> eterm > "save user settings" after you set it up like you want.

no, rox does not support transparency.

some tips:
add this to your menu 

[submenu] (Backgrounds)
[wallpapers] (~/.fluxbox/backgrounds)
[wallpapers] (/usr/share/fluxbox/backgrounds)
[end]

what ever pics you put in the backgrounds folder will show up in the menu & you can just click to set it.

---

### Post by merlinus on 2007-08-04
Great tips, Kerry.  Any other transparent desktop apps worth installing?

Maybe one of these days the fluxbuntu forum will be back online so I can learn more.

Thanks again!

-merlin

---

### Post by kerry_s on 2007-08-04
> **merlinus said:**
> Great tips, Kerry.  Any other transparent desktop apps worth installing?

Maybe one of these days the fluxbuntu forum will be back online so I can learn more.

Thanks again!

-merlin

nothing comes to mind. :confused:

---

### Post by merlinus on 2007-08-04
What about system monitoring tools and dockapps?

Thought I saw a few of those in some of your screenshots...

-merlin

---

### Post by xdarkxanarchyx on 2007-08-04
About the OT.. If I remember correctly, and I'm sorry if I'm wrong, I think Fluxbox has it's real menu somewhere like /etc/fluxboxmenu or something. I remember in Debian 4.0 Unstable there was. The ~/.fluxbox menu directed me to that but I just commented it out. That menu for me was empty for the most part so I copy/pasted the real one in to ~/.fluxbox and edited it to my liking.

---

### Post by kerry_s on 2007-08-04
> **merlinus said:**
> What about system monitoring tools and dockapps?

Thought I saw a few of those in some of your screenshots...

-merlin

i use conky for the monitor. don't have dockapps. rox does my desktop icons.

---

### Post by RedSquirrel on 2007-08-04
> **xdarkxanarchyx said:**
> About the OT.. If I remember correctly, and I'm sorry if I'm wrong, I think Fluxbox has it's real menu somewhere like /etc/fluxboxmenu or something. I remember in Debian 4.0 Unstable there was. The ~/.fluxbox menu directed me to that but I just commented it out. That menu for me was empty for the most part so I copy/pasted the real one in to ~/.fluxbox and edited it to my liking.

In Fluxbox on Ubuntu (well, the one from the repositories), the default menu is generated by running 'sudo update-menus'. The generated file is /etc/X11/fluxbox/fluxbox-menu.

The file ~/.fluxbox/menu points to that file like this:

```
[begin] (fluxbox)
[include] (/etc/X11/fluxbox/fluxbox-menu)
[end]

```That is the default setup. Just like everything else in Fluxbox, the file that is used for the menu and the contents of the menu can be changed to suit individual preferences.

[If you compile Fluxbox from source then the default menu is generated by the program 'fluxbox-generate_menu' and is located at /usr/local/share/fluxbox/menu.]

---

### Post by Nythain on 2007-08-04
as far as transparent apps... conky is a great monitor... then what i do is have multiple transparent terminals each with thier own fun ncurses app... midnight commander in one, centericq in another, rtorrent, ncmpc, top, and finally a small open term so i dont have to open one up all the time... it works out pretty sweet and they are all transparent (or at least as transparent as i could get them) because theya re running in the trans terminal... at the moment i just have a very minimal looking black and white desktop, but im currently working on designing one with a background image and color scheme to match... maybe throw some tint and shade on the terminals... change my theme up a bit... gotta love computers, always a work in progress

---

### Post by merlinus on 2007-08-04
> **Nythain said:**
> as far as transparent apps... conky is a great monitor... then what i do is have multiple transparent terminals each with thier own fun ncurses app... midnight commander in one, centericq in another, rtorrent, ncmpc, top, and finally a small open term so i dont have to open one up all the time... it works out pretty sweet and they are all transparent (or at least as transparent as i could get them) because theya re running in the trans terminal... at the moment i just have a very minimal looking black and white desktop, but im currently working on designing one with a background image and color scheme to match... maybe throw some tint and shade on the terminals... change my theme up a bit... gotta love computers, always a work in progress

Sounds great!  I will have to continue playing around with the transparent terminals.  Do you use any one in particular?

MC is unreadable in Eterm, though.  Guess it's because it is not utf-8 compliant.

Also, perhaps the Saturday vibes have gotten me totally spaced, but...

I installed conky, ran the command from a terminal, but could not figure out how to kill it.  Even looking at the man page on the website did not help.

Lots of stuff about command-line parameters, config files, etc., but zero on how to end it.

Had to restart.

-merlin

---

### Post by Nythain on 2007-08-04
i at the moment use eterm, though i was recently turned on to roxterm, im still playign with it.

to get mc to display right in eterm and aterm requires you to add a line to your .bashrc and .profile... i put it at the top it lookes like this
```

export LANG=C

```
that will fix all the wonky characters

as far as conky, you can tell it to only run once instead of updating every set interval, but thats useless, most have it running constantly as a monitor. to kill it, in terminal type
```

pidof conky
sudo kill <pid from above command>

```
thats about the only way i know how to effectively end it when its running continuously.

the line in the .conkyrc file looks something like this
```

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

```
and is usually located somewhere near the top of the file

---

### Post by yabbadabbadont on 2007-08-04
There is a monster thread on configuring conky, complete with screenshots of the results.

See here: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by merlinus on 2007-08-04
Thanks for the tips and thread link.

Looked through the Eterm man pages, but cannot figure out how to copy and paste.  No menu option as in terminal or gnome-terminal.

Thanks again.

-merlin

---

### Post by kerry_s on 2007-08-04
> **merlinus said:**
> Thanks for the tips and thread link.

Looked through the Eterm man pages, but cannot figure out how to copy and paste.  No menu option as in terminal or gnome-terminal.

Thanks again.

-merlin

hold left click & drag your mouse to high light, middle click to paste.

---

### Post by merlinus on 2007-08-04
> 
hold left click & drag your mouse to high light, middle click to paste. 	


Thanks!

-merlin

---

### Post by Nythain on 2007-08-04
shift+insert will also paste in eterm if middle clicking is a pain

---

### Post by RedSquirrel on 2007-08-05
A neat trick I've found useful (from the man page for conky):

To restart conky after you have modified ~/.conkyrc, you can just do:

```
killall -SIGUSR1 conky
```

rather than killing and then restarting.

---

### Post by merlinus on 2007-08-05
> **RedSquirrel said:**
> A neat trick I've found useful (from the man page for conky):

To restart conky after you have modified ~/.conkyrc, you can just do:

```
killall -SIGUSR1 conky
```rather than killing and then restarting.

Thanks.  This is enormously helpful.

A conky question, please.

I have two versions, both gotten from the 46+ page thread mentioned by yabbadabbadont.

But one will shut down if I close the Eterm window whilst the other does not.

Any ideas as to why?  No obvious info at [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

-merlin

---

### Post by Nythain on 2007-08-05
kind of retro here... so as great as the color line in mc is, im noticing some problems...namely different parts of mc using the same color thingy... example changing the default:marked and default:selected changes more of mc than just marked and selected... so back to black and white i go till i get around to magically stumbling upon just the right image that will allow for wonky colors

---

### Post by kerry_s on 2007-08-05
> **Nythain said:**
> kind of retro here... so as great as the color line in mc is, im noticing some problems...namely different parts of mc using the same color thingy... example changing the default:marked and default:selected changes more of mc than just marked and selected... so back to black and white i go till i get around to magically stumbling upon just the right image that will allow for wonky colors

I hear ya, i went all the way back to stock. the problem is i use mc in both gui and non-gui, what looks great in gui, looks like crap in a plain black console, making it harder to read, thus making tasks take longer than they should. :(
i think they must have really put alot of time into the colors, because it's just perfect the way it is. :)

---

