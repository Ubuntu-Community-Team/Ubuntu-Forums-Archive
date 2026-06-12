---
title: "Fluxbox Fast and Cool!"
date: 2007-06-24
forum: Desktop Environments
---

### Post by steveneddy on 2007-06-24
I haven't had Flux installed on anything for over a year, so I installed it on my Feisty install with Compiz-Fission ( not with Fission!) and it looks great!

I had forgotten how fast it is and how customizable it can be for a tweaker like myself.

One thing to mention. If you are installing it and coming from a Gnome environment, you need to run

```
sudo update-menus
```

to get the right click menus working in the new Fluxbox install.

Sweet.

EDIT:

I don't have Fission running with Fluxbox. I was tired when I typed this and it is a mistake. 

But if someone knows how to get Flux and Fission together, please, do tell.

---

### Post by kerry_s on 2007-06-25
Yep, fluxbox user's always come back to fluxbox. ;)

how about a pic of yours?

---

### Post by steveneddy on 2007-06-25
I like simple and green.

---

### Post by yabbadabbadont on 2007-06-25
So the new compiz merged program isn't a window manager and can be used with Flux?!?  Woo hoo!

/me runs off to read howto's.

---

### Post by Nythain on 2007-06-25
send a link my way if you get that one figured out yabbadabbadont

---

### Post by steveneddy on 2007-06-25
> **yabbadabbadont said:**
> So the new compiz merged program isn't a window manager and can be used with Flux?!?  Woo hoo!

/me runs off to read howto's.

Yeah - throw some links my way, too! I was thinking of posting a thread asking if Compiz-Fission will run on Fluxbox......cool.

EDIT:

This post is 500 beans

---

### Post by yabbadabbadont on 2007-06-25
> **steveneddy said:**
> Yeah - throw some links my way, too! I was thinking of posting a thread asking if Compiz-Fission will run on Fluxbox......cool.

EDIT:

This post is 500 beans

Ummmm.... **you** are the one who said he had Flux with Compiz-Fission ....  I know that you **cannot** run Flux with Beryl but you could with xcompmgr and transet.  Since it appears that I misunderstood your post, the outlook for this probably isn't good.  :(

---

### Post by steveneddy on 2007-06-25
> **yabbadabbadont said:**
> Ummmm.... **you** are the one who said he had Flux with Compiz-Fission ....  I know that you **cannot** run Flux with Beryl but you could with xcompmgr and transet.  Since it appears that I misunderstood your post, the outlook for this probably isn't good.  :(

You are correct. I did say that. It must have been late. Hmmm...well, it gives me something to try later.

I apologize for typing that - I will correct it.

I just logged into Flux and typed compiz --replace in the terminal and this is what I got.

```
steve@ubuntu:~$ compiz --replace/usr/bin/compiz.real (core) - Error: Another window manager is already running on screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Warning: Failed to open file(/usr/share/fluxbox/nls/en_US.UTF-8/fluxbox.cat)
for translation, using default messages.
apps file failure
BScreen::BScreen: an error occured while querying the X server.
        another window manager already running on display :0.0
Error: Couldn't find screens to manage.
Make sure you don't have another window manager running.
Fatal: Can't run fluxbox


```

I wonder how i can get compiz-fission to run on Flux?

hmmmmm....

---

### Post by Nythain on 2007-06-25
and there go those hopes... :(

---

### Post by yabbadabbadont on 2007-06-25
> **steveneddy said:**
> You are correct. I did say that. It must have been late. Hmmm...well, it gives me something to try later.

You can try it, but I'm willing to bet that it won't work.  I was reading through some of the tutorials and they show launching the new program using the "--replace" option.  That means that the program being launched is going to replace the running window manager.  (which would be fluxbox in this instance :?)

Edit: Damn, I type too slow.  It's nice to see that I was correct though.  ;)

---

### Post by kerry_s on 2007-06-26
Hey, what flubox version is ubuntu up to. I'm using debian lenny/sid and it has 1.0rc3 which looks like its trying to get transparency on everything, but when i try to use it my X crashes, i don't think this system can handle it. :(

---

### Post by yabbadabbadont on 2007-06-26
> **kerry_s said:**
> Hey, what flubox version is ubuntu up to. I'm using debian lenny/sid and it has 1.0rc3 which looks like its trying to get transparency on everything, but when i try to use it my X crashes, i don't think this system can handle it. :(

Build it from SVN like all the cool kids are doing...   ;)
```
/home/daffy $ fluxbox -i
Fluxbox version: 1.0rc3
SVN Revision: 4939
Compiled: Jun 23 2007 16:10:51
Compiler: GCC
Compiler version: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

Defaults:
    menu: /usr/share/fluxbox/menu
   style: /usr/share/fluxbox/styles/Clean
    keys: /usr/share/fluxbox/keys
    init: /usr/share/fluxbox/init
     nls: /usr/share/fluxbox/nls

Compiled options (- => disabled): 
-DEBUG
EWMH
GNOME
IMLIB2
KDE
NLS
REMEMBER
RENDER
SHAPE
SLIT
TOOLBAR
XFT
XINERAMA
XMB
XPM

```

---

### Post by yabbadabbadont on 2007-06-26
As for your problem, you might try changing the following setting in your ~/.fluxbox/init file and see if it helps:
```
session.forcePseudoTransparency:        true
```
Just try changing it to be the opposite of whatever it is currently set to.

---

### Post by kerry_s on 2007-06-26
no, i didn't mean it that way, i only have 450mhz 256ram neomagic vid with 2kb mem. with simple tranparency like the toolbar or right click menu it works but slows things down, so trying to do something like my file manager or even the notepad or browser, i think it's just to much for X.
i also have aiglx and composite disabled so that might also be why, any which way, don't really need it, i'm just glad this thing works at all. ;)

second pic is with transparent menu & bar, as soon as i tried the window X crashed as usual.

---

### Post by steveneddy on 2007-06-26
I think I've decided that since I can turn my Fission on and off with a task bar launcher, I will leave my Flux for fast, reliable surfing and the Gnome sessions for Fission Fun-ness.

I don't really use the Fission stuff all the time anyway, but it is fun to look at. Kinda addicting. 

I'm gonna leave Flux mostly stock for now.

Someone show pics of the customized Flux. I like the idea of Conky on the desktop of Flux. I may do that on mine.

Hey, yabbadabbadont - show screenshots of your Fluxbox desktop.

---

### Post by yabbadabbadont on 2007-06-26
It isn't very exciting.  I've found a setup that I like and I pretty much stick with it.

---

### Post by steveneddy on 2007-06-26
My present Flux Desktop.

I had forgotten how much I really like Flux. So simple. So easy. So fast. This is cool. 

:popcorn:

---

### Post by Concorde on 2007-06-26
I read a post earlier about using Fluxbox as a light-weight window manager for gaming. I am going to try DOD:Source next week as I have not played that regulary on Windows due to the lack of fps.

---

### Post by RedSquirrel on 2007-06-26
Here's how mine looks at the moment...

---

### Post by steveneddy on 2007-06-26
> **RedSquirrel said:**
> Here's how mine looks at the moment...

Very cool - what is that in the background, the man page.

Dude - the more i do - this thing is so F-N fast!

I have a Core 2 Duo @ 2 Ghz and 2 GIG RAM and this thing FLIES!

---

### Post by yabbadabbadont on 2007-06-26
> **steveneddy said:**
> Very cool - what is that in the background, the man page.

Looks like it is just a transparent terminal without the border decorations.  Probably one of aterm, eterm, or urxvt.

---

### Post by RedSquirrel on 2007-06-26
> **steveneddy said:**
> Very cool - what is that in the background, the man page.

Thanks.

Yes, it is the man page in a transparent terminal... tilda actually.

```
sudo apt-get install tilda
```The background is from tenr.de (see sig).

> **steveneddy said:**
>  Dude - the more i do - this thing is so F-N fast!

I have a Core 2 Duo @ 2 Ghz and 2 GIG RAM and this thing FLIES!

Glad you're having fun with Fluxbox. I know I do. :D

> **yabbadabbadont said:**
> Looks like it is just a transparent terminal without the border decorations. Probably one of aterm, eterm, or urxvt.

I played with eterm and aterm for a bit and moved on to tilda... but now I am back to my plain xterm. ;)

What do you use for a terminal, by the way?

I'm considering making my pager a 2x3 grid instead of 1x4. I'll have to see if I can setup keyboard shortcuts to move vertically through the workspaces (that is *easy* in Xfce, for instance).

---

### Post by yabbadabbadont on 2007-06-26
> **RedSquirrel said:**
> Yes, it is the man page in a transparent terminal... tilda actually.
I almost included tilda in my list, but I didn't realize that you could make it fully transparent.  Live and learn.  :D

> **RedSquirrel said:**
> What do you use for a terminal, by the way?
```
/home/daffy $ grep xterm .fluxbox/keys 
Mod4 t :Execute uxterm -geometry 127x44+0+0 -fg gray80 -bg gray20 -sl 2000 -fn "-xos4-terminus-medium-r-normal-*-16-*-*-*-*-*-iso10646-1"
```

Edit: Since you have included it in your signature, I guess you liked Tenr's themes.  ;)

---

### Post by kerry_s on 2007-06-26
> **RedSquirrel said:**
> Thanks.

Yes, it is the man page in a transparent terminal... tilda actually.

```
sudo apt-get install tilda
```The background is from tenr.de (see sig).



Glad you're having fun with Fluxbox. I know I do. :D



I played with eterm and aterm for a bit and moved on to tilda... but now I am back to my plain xterm. ;)

What do you use for a terminal, by the way?

I'm considering making my pager a 2x3 grid instead of 1x4. I'll have to see if I can setup keyboard shortcuts to move vertically through the workspaces (that is *easy* in Xfce, for instance).


Very nice RedSquirrel, yeah i agree the pager should be bigger. what pager is that? it looks like a stock fbpager. i just said screw it and put mine right in the middle of the desktop. mine's fbapger, i call it to the top by middle clicking on the title bar.

---

### Post by RedSquirrel on 2007-06-26
> **yabbadabbadont said:**
> Since you have included it in your signature, I guess you liked Tenr's themes.  ;)

Yes, they are a great deal better than most of what I saw on box-look. (...and I couldn't fit both in my sig so I had to make a choice!)

I bookmarked that site months ago but I guess I never looked through it very thoroughly. [EDIT: Thanks again for the reminder about that site.]

I was using the theme you have in your screenshots just yesterday! Today, it's "centurion_blue". ;)

---

### Post by yabbadabbadont on 2007-06-26
I like his "centurion" line, but the "trivial" theme I am now using is nice and thin.  It gives me just that little extra bit of screen real estate on my old monitor.  ;)

---

### Post by RedSquirrel on 2007-06-26
> **kerry_s said:**
> Very nice RedSquirrel

Thanks.

> **kerry_s said:**
> yeah i agree the pager should be bigger. what pager is that? it looks like a stock fbpager. i just said screw it and put mine right in the middle of the desktop. mine's fbapger, i call it to the top by middle clicking on the title bar.

LOL. My pager was about 20 pixels high for a while, but I decided maybe that was too small so now it's 32. [In fact, it's 40x32 for each workspace, which matches the 5:4 aspect ratio of my monitor. :D]

It is fbpager. I have moved it all over the screen, but I put it back at 0,0 because of the pretty drawing in the bottom-right corner and I kind of wanted conky in the top-right.

I wish there was a pager that provided thumbnail previews of each workspace. Enlightenment has this (and so did sawfish + GNOME back in the day). I think I've already complained to you about this in another thread, so I'll *stop* now. ;)

Your idea of putting it in the middle is a good one. I might try that too.

I think my idea of moving vertically among the workspaces with arrow keys is going to be difficult to achieve. Maybe I could add that to the code myself. Hmm...

---

### Post by Nythain on 2007-06-27
guess ill post my most current screenshot, nothin fancy, but very informative, and light on the gui side of things... very easily navigated without mouse, now if only i can figure out how to get the damn winblows key to work, runnin out of alt and control combinations

---

### Post by yabbadabbadont on 2007-06-27
> **Nythain said:**
> guess ill post my most current screenshot, nothin fancy, but very informative, and light on the gui side of things... very easily navigated without mouse, now if only i can figure out how to get the damn winblows key to work, runnin out of alt and control combinations

You just refer to it as "Mod4" in your ~/.fluxbox/keys file.  Like in my uxterm example above.

---

### Post by Nythain on 2007-06-27
yeah, tried that, does nothing... think it might have something to do with the fact that im using a logitech wireless keyboard connected usb->ps2 converter... xev wont give me any output on any keypresses for that matter... pics up mouse clicks and movements, but nothing for keyboard button presses

---

### Post by yabbadabbadont on 2007-06-27
If xev doesn't see it, then it aint a gonna work.  :D

---

### Post by Nythain on 2007-06-27
yeah, unfortunately the answer i knew but hoped was wrong :(

---

### Post by kerry_s on 2007-06-27
> **Nythain said:**
> yeah, tried that, does nothing... think it might have something to do with the fact that im using a logitech wireless keyboard connected usb->ps2 converter... xev wont give me any output on any keypresses for that matter... pics up mouse clicks and movements, but nothing for keyboard button presses

What keyboard # are you useing in xorg.conf, i had to change mine to 105 for the win key to work.

```
Option		"XkbModel"	"pc105"
```

---

### Post by slackmaGic on 2007-06-27
I'm not on Ubuntu, but it's fluxbox nonetheless :P

Let's see what we have here: we've got conky, a few mrxvt terms up one of which shows irssi which is being run through screen, rox-filer (barely use it but had to show it with those superb looking alienware icons)

Hm..I don't use fluxbox's toolbar...that's what my $HOME/.fluxbox/keys is for ---> keyshortcuts 'R Us! (get to easily switch quickly when someone walks into the room so I can hide what I was doing on any of my other workspaces *grins*)

Have fun!


[[IMG]http://www.slackmagic.com/uploads//files/thumbnail.png[/IMG]](http://www.slackmagic.com/uploads//files/06272007_2722_1680x1050.png)

---

### Post by kerry_s on 2007-06-28
slackmaGic, that's pretty sweet, i can tell your one of those that think outside the box. ;)

---

### Post by RedSquirrel on 2007-06-28
@slackmaGic:

That's a nice desktop. :)

Where did you get the background?

---

### Post by slackmaGic on 2007-06-28
> **RedSquirrel said:**
> @slackmaGic:

Where did you get the background?

Here we go:

[http://www.deviantart.com/deviation/35378234/]("http://www.deviantart.com/deviation/35378234/")

---

### Post by RedSquirrel on 2007-06-28
Great! Thanks. (I had a feeling it was from deviantART... ;))

---

### Post by yabbadabbadont on 2007-06-29
Since I've just restaged my machine with Gentoo, I decided to try out Openbox 3.4.2.  In an amusing bit of irony, Gentoo welcomed me home by presenting me with both glibc and gcc updates after my first sync of the portage tree.  At least now I know that it takes almost exactly three hours to completely rebuild the base system on this machine.  :lol:

---

### Post by kerry_s on 2007-06-29
Hey slackmaGic, can i get a shot of your pstree, i want to see how it looks in slack, what it runs? I hear slack is pretty fast, whats your take on the speed?

---

### Post by RedSquirrel on 2007-06-29
> **yabbadabbadont said:**
> Since I've just restaged my machine with Gentoo, I decided to try out Openbox 3.4.2.  In an amusing bit of irony, Gentoo welcomed me home by presenting me with both glibc and gcc updates after my first sync of the portage tree.  At least now I know that it takes almost exactly three hours to completely rebuild the base system on this machine.  :lol:

Yeah, I recall vividly one of the things you need to compile glibc is "plenty of time"... [http://www.gnu.org/software/libc/FAQ.html#s-1.7](http://www.gnu.org/software/libc/FAQ.html#s-1.7)

They're not kidding! :)

After seeing slackmaGic's comment about not using the Fluxbox toolbar, I've decided to turn mine off too. I don't need it since I have a *real* clock on my desk and I now "shade" windows instead of minimizing them. It's actually quite a liberating feeling not having any sort of toolbar in the way. I've also turned off conky and fbpager since both have some issues for me. I'm having has some graphics problems with conky where it will occasionally show some buffer contents and yesterday it suddenly quit altogether. I have enabled double buffering and so on, but I may have to look around and see if there's something else I'm missing.

I was thinking of giving the new Openbox a try, but I think I'll stick with Fluxbox for now. I spend most of my time with applications and tinkering with my own programs so I'm not really in the mood to try out new working environments. Fluxbox suits my needs and it stays out of my way. ;)

---

### Post by slackmaGic on 2007-06-29
> **kerry_s said:**
> Hey slackmaGic, can i get a shot of your pstree, i want to see how it looks in slack, what it runs? I hear slack is pretty fast, whats your take on the speed?

```

$ pstree
init-+-5*[agetty]
     |-atd
     |-bash---startx---xinit-+-X
     |                       `-fluxbox-+-conky
     |                                 `-mrxvt---bash---screen---screen---2*[bash]
     |-bdflush
     |-crond
     |-dhcpcd
     |-httpd---5*[httpd]
     |-inetd
     |-keventd
     |-khubd
     |-3*[kjournald]
     |-klogd
     |-ksoftirqd_CPU0
     |-kswapd
     |-kupdated
     |-mdrecoveryd
     |-server_linux---server_linux---7*[server_linux]
     |-sshd---sshd---sshd---bash---pstree
     `-syslogd

```


Here is pstree off my laptop ('slacklap').

It's usually quite easy to hear good and bad stuff about something, but you personally won't be able to associate with it until you actually get to experience it yourself.

In my opinion, slackware is fast enough for me. My three systems at home are pretty much 5-7 years old. My main system (desktop) is a P4 1.3 Ghz with 512 old RDRAMs. I do most of my stuff on it and it has never quit on me and to me that really speaks for stability and even "performance". Yep, my first slackware install (version 10.0) 3 years ago still serves me right as I type this and it has never crashed on me (except for a few faulty apps perhaps).

So speed, stability and the fact that it's quite simple once you learn the ropes of it are the main reasons why I'm still and probably will always be on slackware.

I've tried other distributions. Some are good, some are decent, yet there are some I didn't like due to the fact that they have set things up with the idea of getting things done "their-way".

Learning Slackware is definetely a fun experience. For the most part you compile things yourself, there is no real decendency check (except you want to use some 3rd-party software). You read a lot. You edit a lot of config files. You compile lots of things, oh I did already say that :)

I can say this though. Once you've spent time with slackware, and then you try out other distros again, you definetely appreciate the KISS philosophy of keeping things simple, stupid simple. 

So, here is my advice to you. Try slackware out. Give it some time. Read the slackbook.org, check out Linuxquestions.org for slackware (as that is its official slackware support forum), hang out on ##slackware @ freenode if you like.

Do that, come back a few weeks/months later and let me know if slackware is fast to you because I think you've gotta try it before you can really tell for yourself.


Have fun!

---

### Post by kerry_s on 2007-06-29
thanks slackmaGic, your pstree just confirms what i thought, slack runs a heck of alot less services than debian, i think i will just try to work on removing some more services.
i hate compiling, i had enough of that with gentoo, i decided back then i'm not compiling any more unless i absolutely have to. this system i'm using now is only 450mhz with 256ram(the max), so compiling is a chore. i been looking into debian-builder which is suppose to let me just rebuild individual packages, but i haven't tried it yet. anyways thanks alot, i'm off to tinker.

---

### Post by slackmaGic on 2007-06-29
you're welcome kerry_s.


Services are there to be started or stopped and since it's just my old laptop, I didn't have any need for some of those services to be started.

Your system would have no problem with slackware to say the least. But as with any older system, resource-hungry apps are always a pain to work with of course.

Anyways, it's up to you what you'd like to do. I've quite a few friends that use debian and are happy with it and as long as they're happy with it, I'm happy for 'em too :D

---

### Post by kerry_s on 2007-06-29
yeah, i'm getting there. i just need to read up on kthread and figure out how it works. it's like the say it's not the number of applications you have it's what's running. ;)
i see in yours you don't have kthread, it looks like you have keventd which is way better, i'm looking into that right now.

---

### Post by iluvdrbonner on 2007-07-05
> **slackmaGic said:**
> you're welcome kerry_s.


Services are there to be started or stopped and since it's just my old laptop, I didn't have any need for some of those services to be started.

Your system would have no problem with slackware to say the least. But as with any older system, resource-hungry apps are always a pain to work with of course.

Anyways, it's up to you what you'd like to do. I've quite a few friends that use debian and are happy with it and as long as they're happy with it, I'm happy for 'em too :D
hey slackmaGic, 

would you mind posting your conkyrc i really liked how you spread it all out. Nice setup. Thanks in advance.

---

### Post by slackmaGic on 2007-07-05
> **iluvdrbonner said:**
> hey slackmaGic, 

would you mind posting your conkyrc i really liked how you spread it all out. Nice setup. Thanks in advance.


```

background yes
use_xft yes
xftfont dungeon-9
xftalpha 0.7
update_interval 1
own_window no
minimum_size 20 5
draw_shades no
draw_outline no
draw_borders no
double_buffer yes
stippled_borders 0
border_margin 1
border_width 1
default_color white
default_shade_color darkgrey
default_outline_color black
alignment top_left
gap_x 10
gap_y 5
no_buffers yes
uppercase no

TEXT
   ${color #CCCCCC}cpu|${color #FFD582} $cpu%   ${color #CCCCCC}mem|${color #FFD582} $memperc%   ${color #CCCCCC}eth0.down|${color #45DE44} ${downspeedf eth0}${color #ffffff}   ${color #CCCCCC}eth0.up|${color #45DE44} ${upspeedf eth0}   ${color #CCCCCC}procs| ${color #AAAAAA}$processes${color #444444}   ${color #444444}root ${color #FFD582}${fs_free /}   ${color #444444}home ${color #FFD582}${fs_free /home}   ${color #444444}storage ${color #FFD582}${fs_free /storage}${color #777777}                                                                                                                                                                                                                                                                    ${font HandelGotDLig-11}${color #FFD582}${time %a, }${color #FFD582}${time %e %B %G}  ${time %H}:${time %M}

${font HandelGotDBol-12}${color #FFD582}${exec ps gaxo %cpu,%mem,comm | sort +0nr | head -n 6}

```

Here we go iluvdrbonner

My [color=blue]$HOME/.conkyrc-oneliner-greenlime[/color] is set up for the LCD with 1680x1050 resolution, so you'll have to modify stuff to mostly fit it (spacewise) onto your screen if you're running a different resolution.

The time on the right top I don't really need because in my [color=blue]$HOME/.fluxbox/keys[/color] I also have

```
Control Mod4 d            :ExecCommand date | osd_cat -c green -f -*-dungeon-*-*-*-*-30-*-*-*-*-*-*-* -o 20 -p top -A center

```

which means I just hold down CTRL + window key + d and it displays the time/date for a specific timeframe on my screen whenever I need to know what day/time it is.

So it's totally up to you if you want to keep that or just remove it completely and keep it all minimal to the left top of the screen.


You'll need   [color=blue]Dungeon.ttf / HandelGotDBol / HandelGotDLig[/color] fonts to make it look like how I have it (I'm sure you'll find it through google otherwise I don't mind emailing you the fonts)

Have fun!

---

### Post by ghandi69_ on 2007-07-05
Hey guys... I'm a "new" user of fluxbox, and I don't have my desktop to where I want it yet, but I know that flux can offer everything I want so I'm going to stick with it.

Question #1.)  How do I adjust mouse sensitivity in fluxbox??  I use a laser mouse and it is very sensitive and I can't figure out how to tone it down.... I've looked through the init file but couldn't find much.

Question #2.)  Automount doesn't seem to be supported in flux, or at least it doesn't show up on the desktop(which makes sense, because flux doesn't support desktop icons)... but what is you fellers preferred method for hooking up and reading things like external hard drives/dvds/usb storage devices?

Question #3.)  This is a pretty general question, but to me, the text seems a bit grainy on certain applications and certain instances (minimized apps in the menubar for instance). Is there a way to improve the way this looks?

Question # 4.)  Is this the kind of thing where.. if my video card was detected in KDE, then it is in Flux as well?   When I have the setting set up where I can see the window as I move it around(as opposed to just the outline) it stutters quite a bit.  I have a decent setup (7600 Gt, 1 gig ram) so I would think if things were running correctly it shouldn't do that.

---

### Post by RedSquirrel on 2007-07-05
> **ghandi69_ said:**
> Hey guys... I'm a "new" user of fluxbox, and I don't have my desktop to where I want it yet, but I know that flux can offer everything I want so I'm going to stick with it.

Question #1.)  How do I adjust mouse sensitivity in fluxbox??  I use a laser mouse and it is very sensitive and I can't figure out how to tone it down.... I've looked through the init file but couldn't find much.

Question #2.)  Automount doesn't seem to be supported in flux, or at least it doesn't show up on the desktop(which makes sense, because flux doesn't support desktop icons)... but what is you fellers preferred method for hooking up and reading things like external hard drives/dvds/usb storage devices?

Question #3.)  This is a pretty general question, but to me, the text seems a bit grainy on certain applications and certain instances (minimized apps in the menubar for instance). Is there a way to improve the way this looks?

Question # 4.)  Is this the kind of thing where.. if my video card was detected in KDE, then it is in Flux as well?   When I have the setting set up where I can see the window as I move it around(as opposed to just the outline) it stutters quite a bit.  I have a decent setup (7600 Gt, 1 gig ram) so I would think if things were running correctly it shouldn't do that.

1.

You could use xset with the 'm' option. Check the man page:

```
man xset
```You'll have to play around with the two values to see what works for you. Something like:

```
xset m 1/5 1
```might work. You can run the command on the command line (that is, in a terminal) and see how it affects your mouse motion. You can reset to the defaults with:

```
xset m
```Once you have it working the way you want, add the xset command to your ~/.fluxbox/startup file.


2. Some people use gnome-volume-manager or ivman. I have heard that thunar has a plugin that handles automounting. I prefer to mount things manually, so I don't use any of these tools.


3. Have you set your DPI to 96? Setting this in xorg.conf can be a challenge since there's a bug in Xorg in feisty. I'm using the ~/.Xresources file right now with this in it:

```
Xft.dpi: 96
```I also fiddle with my monitor settings to make fonts look better.

4. Things should be setup properly for your video card in /etc/X11/xorg.conf. If it worked in KDE, chances are that Fluxbox is OK too. 

I don't normally use the setting you described, but I just tried it again now and it's fine for windows with not much in them (e.g., a text editor) but it's a little "smeared" if I try to move a web browser window. I'm not sure how well that's supposed to work. If anyone else has this feature working *really* well, please let us know...

---

### Post by kerry_s on 2007-07-05
> **ghandi69_ said:**
> Hey guys... I'm a "new" user of fluxbox, and I don't have my desktop to where I want it yet, but I know that flux can offer everything I want so I'm going to stick with it.

Question #1.)  How do I adjust mouse sensitivity in fluxbox??  I use a laser mouse and it is very sensitive and I can't figure out how to tone it down.... I've looked through the init file but couldn't find much.

Question #2.)  Automount doesn't seem to be supported in flux, or at least it doesn't show up on the desktop(which makes sense, because flux doesn't support desktop icons)... but what is you fellers preferred method for hooking up and reading things like external hard drives/dvds/usb storage devices?

Question #3.)  This is a pretty general question, but to me, the text seems a bit grainy on certain applications and certain instances (minimized apps in the menubar for instance). Is there a way to improve the way this looks?

Question # 4.)  Is this the kind of thing where.. if my video card was detected in KDE, then it is in Flux as well?   When I have the setting set up where I can see the window as I move it around(as opposed to just the outline) it stutters quite a bit.  I have a decent setup (7600 Gt, 1 gig ram) so I would think if things were running correctly it shouldn't do that.

1. RedSquirrel's got ya covered there
2. sudo apt-get install ivman < it will be automounted in your file manager, i do mine manually.
3. Some theme's have a crappy font selection, i change mine to this->

```
*.font:				DejaVu-12
```

just look for that line in the style your using, i'll attach mine in case you want to try that it's a modified "cthulhain" style.( tar xvf fluxbox_style.tar ) move to ~/.fluxbox/styles

4. are you running a mixed system with kde and fluxbox? if not you might have to set up your driver.

---

### Post by Nythain on 2007-07-05
thanks for the info on setting dpi to 96 in fluxbox... i havent had many font problems, but its a good bit of info to know

thanks for the info on the line to edit in the style to change the font

i currently am in love with black glass borderless... i dont think i can ever go back to another de/window manager again

---

### Post by RedSquirrel on 2007-07-06
> **kerry_s said:**
> 3. Some theme's have a crappy font selection

Good point. I have found that adding 'bold' looks a bit better too, but this is one of those "eye of the beholder" things, I guess. :)

```
sans-10:bold
```

> **Nythain said:**
> thanks for the info on setting dpi to 96 in fluxbox... i havent had many font problems, but its a good bit of info to know

I think with nvidia cards there is an option in xorg.conf which is something like (in the Monitor section):

```
Option          "DPI"   "96 x 96"
```You can also set the DisplaySize to suitable values to get DPI of 96, but you have to use the "NoDDC" option in the Device section due to a bug in Xorg. Really, it's probably just easier to use ~/.Xresources. ;)

---

### Post by JMO707 on 2007-07-08
Got a question!

I want to make a script to change at the same time: Wallpaper, Fluxbox style & Gtk theme.
I cant find a way to change the Fluxbox style via command line. What do you suggest?

---

### Post by kevCast on 2007-07-10
I was wondering, in Fluxbox, how do I get rid of the tabs at the top left of the window I'm in? Also, what's a good volume manager for Fluxbox? Oh, and how do I get something to where I can get icons in thunar versus the standard sheets of paper? I was thinking something like a gtk plugin or something.

Here's a snapshot of my current desktop.

---

### Post by RedSquirrel on 2007-07-10
> **kevCast said:**
> I was wondering, in Fluxbox, how do I get rid of the tabs at the top left of the window I'm in? 

fluxbox menu -> Configure -> Tab Options -> Tabs in Titlebar

> **kevCast said:**
> Also, what's a good volume manager for Fluxbox? 

ivman, gnome-volume-manager, thunar-volman-plugin.

> **kevCast said:**
> Oh, and how do I get something to where I can get icons in thunar versus the standard sheets of paper? I was thinking something like a gtk plugin or something.

Add this to your ~/.gtkrc-2.0 file (create that file if it doesn't exist):

```
gtk-icon-theme-name = "Tango"
```Replace "Tango" with whatever icon theme you want to use.

> **kevCast said:**
>  Here's a snapshot of my current desktop.

Nice. Interesting color selection. Where did you get the background? Did you make it yourself? I like the way the cubes reflect on the surface. That XMMS theme is *crazy*.

---

### Post by RedSquirrel on 2007-07-10
> **JMO707 said:**
> Got a question!

I want to make a script to change at the same time: Wallpaper, Fluxbox style & Gtk theme.
I cant find a way to change the Fluxbox style via command line. What do you suggest?

I have not heard of a way to change the Fluxbox style on the command line.

The only ways that I know of are in the menu and using the keys file. Here are the relevant keys file commands:

```
Reload Style           # Reloads the style if any files were changed
SetStyle <argument>    # Sets a specific style. useful for a standard style for testing purposes
```You could setup a keyboard shortcut to do two things: 

(1) run your script (change wallpaper and gtk theme) and 
(2) set the style. 

Try MacroCmd to achieve this.

Have a look at the wiki entry for keyboard shortcuts:

[http://fluxbox-wiki.org/index.php/Keyboard_shortcuts](http://fluxbox-wiki.org/index.php/Keyboard_shortcuts)


EDIT: You could also change the Fluxbox source code to allow style changes from the command line, but setting it up as a keyboard shortcut would be a great deal easier. ;)

---

### Post by Happy_Man on 2007-07-10
You guys are all crazy. KDE ftw! :p

---

### Post by Nythain on 2007-07-10
ok, so got another question on the keybindings here
this stupid effen windows key, is it
A. Mod4
or
B. Super_L / Super_R

im tryin to get it set up so that the left windows key opens up the RootMenu and i see different refernces to what that key is actually called... is there an easy way to find out on my machine... 

Also as a side note... is there a command to cycle through windows including minimized ones... Alt+Tab only cycles through open windows, and skips the minimized ones... if there's a more advance program cycle command besides just NextWindow and PrevWindow that includes minimized ones, that would be great

And again another question, any clue what the PrtScr button is called in the keys file... im trying to set it up to run the standart screenshot script but i dont know how to word that button in the keys file

And finally, personall preference question... if you had to use a key combo to shade and unshade windows, wich do you think is most ergonomically comfortable???

---

### Post by yabbadabbadont on 2007-07-10
> **Nythain said:**
> ok, so got another question on the keybindings here
this stupid effen windows key, is it
A. Mod4
or
B. Super_L / Super_R

im tryin to get it set up so that the left windows key opens up the RootMenu and i see different refernces to what that key is actually called... is there an easy way to find out on my machine... 
Mod4

Open a terminal window and run xev.  Then start hitting keys.  Their names will be printed in the window.  Keep your mouse out of the xev window or mouse events will be printed too.

> **Nythain said:**
> And again another question, any clue what the PrtScr button is called in the keys file... im trying to set it up to run the standart screenshot script but i dont know how to word that button in the keys file

None Print

Mod1 Sys_Req  (alt print screen)

Here is my keys file just as an example: ```
/home/daffy $ cat .fluxbox/keys 
OnDesktop Mouse1 :HideMenus
OnDesktop Mouse2 :WorkspaceMenu
OnDesktop Mouse3 :RootMenu
OnDesktop Mouse4 :PrevWorkspace
OnDesktop Mouse5 :NextWorkspace

Mod1 Tab :NextWindow
Mod1 Shift Tab :PrevWindow
Mod1 F1 :Workspace 1
Mod1 F2 :Workspace 2
Mod1 F3 :Workspace 3
Mod1 F4 :Workspace 4
None Print :Execute grab-screen
Mod1 Sys_Req :Execute grab-selection
Mod1 F11 :Execute wallpaper-set-random
Mod1 F12 :Execute xmessage -default okay -center -file ~/.current-wallpaper-name
Mod4 t :Execute uxterm -geometry 127x44+0+0 -fg gray80 -bg gray20 -sl 2000 -fn "-xos4-terminus-medium-r-normal-*-16-*-*-*-*-*-iso10646-1"
Control Mod1 q :Quit
Control Escape :RootMenu

```

---

### Post by Nythain on 2007-07-10
thanks for the answers and teh example keys file...

i dont know where id be without you and redsquirrel, oh yeah i do... running kde :(

---

### Post by RedSquirrel on 2007-07-10
> **Nythain said:**
> ok, so got another question on the keybindings here
this stupid effen windows key, is it
A. Mod4
or
B. Super_L / Super_R

If you only have one windows key, Mod4 should be fine. I have two windows keys (I'm spoiled :)), so I must use Super_L and Super_R.

> **Nythain said:**
> Also as a side note... is there a command to cycle through windows including minimized ones... Alt+Tab only cycles through open windows, and skips the minimized ones... if there's a more advance program cycle command besides just NextWindow and PrevWindow that includes minimized ones, that would be great

```
Mod1 Tab :MacroCmd {Deiconify LastWorkspace} {NextWindow 0}

```This will "deiconify" any windows that are minimized and then you can Tab through them. If you want them to stay minimized, you will have to experiment. I was happy with the *deiconifying* when I used to minimize windows, but now I don't minimize them at all; I just shade them.

> **Nythain said:**
>  And finally, personall preference question... if you had to use a key combo to shade and unshade windows, wich do you think is most ergonomically comfortable???

I'm using the up/down arrow keys with Alt (Mod1):

```
Mod1 Up   :Shade
Mod1 Down :Shade

```You can just use one key to shade/unshade, but I think it's kind of intuitive having the arrows up/down corresponding to shade up/down. ;)

The wiki entry for keyboard shortcuts is fairly good:

[http://fluxbox-wiki.org/index.php/Keyboard_shortcuts](http://fluxbox-wiki.org/index.php/Keyboard_shortcuts)

---

### Post by Nythain on 2007-07-10
ok, so finally, thanks to all your help, i have my keys file set up pretty spiffy... thats one more task down. Im runnin out of stuff to accomplish, dont know what im gonna occupy myself with once im done with all this... guess i could go back up playing games

---

### Post by kevCast on 2007-07-11
> **RedSquirrel said:**
> fluxbox menu -> Configure -> Tab Options -> Tabs in Titlebar



ivman, gnome-volume-manager, thunar-volman-plugin.



Add this to your ~/.gtkrc-2.0 file (create that file if it doesn't exist):

```
gtk-icon-theme-name = "Tango"
```Replace "Tango" with whatever icon theme you want to use.



Nice. Interesting color selection. Where did you get the background? Did you make it yourself? I like the way the cubes reflect on the surface. That XMMS theme is *crazy*.
I'm just using aumix now.

I couldn't get the icons to work, do I have to log out after editing the script?

No, I didn't make it myself, I got it from DeviantART.

[http://www.deviantart.com/deviation/59429427/]("http://www.deviantart.com/deviation/59429427/")

Here's the XMMS theme.

[http://www.deviantart.com/deviation/2289219/?q=cube+winamp&qh=boost%3Apopular+age_sigma%3A24h+age_scale%3A5]("http://www.deviantart.com/deviation/2289219/?q=cube+winamp&qh=boost%3Apopular+age_sigma%3A24h+age_scale%3A5")

The fluxbox theme is Jello. The author of this style is amazing at what they do, I'd recommend checking out all of their themes.

[http://box-look.org/content/show.php/Jello?content=59734]("http://box-look.org/content/show.php/Jello?content=59734")

And the gtk2 theme is Tempura by Lokheed, an incredible gtk2 theme designer.

[http://www.deviantart.com/deviation/32162210/?qo=2&q=tempura&qh=boost%3Apopular+age_sigma%3A24h+age_scale%3A5]("http://www.deviantart.com/deviation/32162210/?qo=2&q=tempura&qh=boost%3Apopular+age_sigma%3A24h+age_scale%3A5")

It was a really strange coincedence that I found that wallpaper, because I found the Winamp theme first and was amazed, and found the wallpaper on accident.

And thank you RedSquirrel, you've helped a lot. You're posts were actually a big part of what made me try Fluxbox, and am now a happy fulltime Fluxbox user.

---

### Post by RedSquirrel on 2007-07-11
> **Nythain said:**
> ok, so finally, thanks to all your help, i have my keys file set up pretty spiffy... thats one more task down. Im runnin out of stuff to accomplish, dont know what im gonna occupy myself with once im done with all this... guess i could go back up playing games

Would you mind posting your keys file? I would like to to steal your ideas... err... see what you came up with. ;)

I don't think I'll ever be done tinkering with Fluxbox. It's inevitable that someone will make a post with an idea that will inspire me to try it out on my own setup.

Are you using the SVN version? It has some new features that the version out of the Ubuntu repositories does not have. If you would prefer not to try the SVN, you could compile the plain 1.0rc3 source which is available on the Fluxbox homepage. There's a "What's new in rc3" link on there too. Of course, if you're happy with the version from the repositories then stick with that.

Have you done any programming? I would recommend playing with that. It can consume enormous amounts of time, probably even more than gaming...

---

### Post by RedSquirrel on 2007-07-11
> **kevCast said:**
> I'm just using aumix now.

I couldn't get the icons to work, do I have to log out after editing the script?

No, I didn't make it myself, I got it from DeviantART.

And thank you RedSquirrel, you've helped a lot. You're posts were actually a big part of what made me try Fluxbox, and am now a happy fulltime Fluxbox user.

Great! :)

Thanks for the details on your desktop setup.


volume:

I just switched to amixer:

```
XF86AudioMute :Exec amixer set PCM toggle
XF86AudioLowerVolume :Exec amixer set PCM 1%-
XF86AudioRaiseVolume :Exec amixer set PCM 1%+
```


icons:

No need to logout; it should work the next time you start the application. I wasn't using a special icon theme for a while, but I just setup Tango again and it worked for me. I tested it with pcmanfm. You have to install the icon theme you want to use from the repositories (e.g., tango-icon-theme). I haven't used Thunar for a while, but I think the icon themes worked fine with it (I would think they should). Make sure you named the file **.gtkrc-2.0** (with a "." in front).

---

### Post by kevCast on 2007-07-11
> **RedSquirrel said:**
> Great! :)

Thanks for the details on your desktop setup.


volume:

I just switched to amixer:

```
XF86AudioMute :Exec amixer set PCM toggle
XF86AudioLowerVolume :Exec amixer set PCM 1%-
XF86AudioRaiseVolume :Exec amixer set PCM 1%+
```


icons:

No need to logout; it should work the next time you start the application. I wasn't using a special icon theme for a while, but I just setup Tango again and it worked for me. I tested it with pcmanfm. You have to install the icon theme you want to use from the repositories (e.g., tango-icon-theme). I haven't used Thunar for a while, but I think the icon themes worked fine with it (I would think they should). Make sure you named the file **.gtkrc-2.0** (with a "." in front).
amixer looks good.

I got the icons working now. I made the blatant mistake of forgetting to install Tango. :oops:

Thanks RedSquirrel!

---

### Post by yabbadabbadont on 2007-07-11
@RedSquirrel: Which SVN revision are you currently using?  I need to checkout the changelog and see if they have fixed the crashes that I encountered.

---

### Post by RedSquirrel on 2007-07-11
> **kevCast said:**
> amixer looks good.

I got the icons working now. I made the blatant mistake of forgetting to install Tango. :oops:

Thanks RedSquirrel!


Glad you got the icons working. It would have been better if I had mentioned straight off that you have to install them.

Here are the latest settings for the amixer (thanks to kerry_s):

```
XF86AudioMute :Exec amixer set PCM toggle > /dev/null 
XF86AudioLowerVolume :Exec amixer set PCM 1%- > /dev/null 
XF86AudioRaiseVolume :Exec amixer set PCM 1%+ > /dev/null 

```It's a good idea to add the /dev/null part; without it, your ~/.xsession-errors will fill up with junk (not really errors, just a slew of "notifications").

---

### Post by RedSquirrel on 2007-07-11
> **yabbadabbadont said:**
> @RedSquirrel: Which SVN revision are you currently using?  I need to checkout the changelog and see if they have fixed the crashes that I encountered.

SVN 4983. I have been using it for about 3 days, no trouble so far.

PS - Glad you're back. :)

---

### Post by yabbadabbadont on 2007-07-11
> **RedSquirrel said:**
> SVN 4983. I have been using it for about 3 days, no trouble so far.

PS - Glad you're back. :)

Thanks.  There wasn't any mention of fixing something that would explain the crashes I was having, but I am unable to reproduce them using the current SVN (which is still 4983).  It's nice to be home again.  :D

---

### Post by RedSquirrel on 2007-07-11
I noticed they changed the configure script to enable nearly everything except DEBUG and NLS. That was a bit of a surprise, but not really an unpleasant one.

---

### Post by yabbadabbadont on 2007-07-12
> **RedSquirrel said:**
> I noticed they changed the configure script to enable nearly everything except DEBUG and NLS. That was a bit of a surprise, but not really an unpleasant one.

They should probably enable NLS by default too.  That way when a noob builds flux from source they get everything they could possibly need by default.  Those of us who know what we are doing can disable the parts we don't need.

---

### Post by maybeway36 on 2007-07-12
Is there a boring gray theme available for Fluxbox? I prefer the look of Blackbox but I like Fluxbox's system tray.

---

### Post by yabbadabbadont on 2007-07-12
> **maybeway36 said:**
> Is there a boring gray theme available for Fluxbox? I prefer the look of Blackbox but I like Fluxbox's system tray.

Sure.  Head over to [www.tenr.de](www.tenr.de) and browse through his hundreds of themes.  There are several gray themes there.

Edit: This one is nice -- [http://www.tenr.de/files/fluxboxstyles_archives/plain_gray.tar.bz2](http://www.tenr.de/files/fluxboxstyles_archives/plain_gray.tar.bz2)

---

### Post by Nythain on 2007-07-12
so after reading up on the more recent changes between the version in the repos and the latest release candidate... any advice on compiling from scratch???
list of dependencies im going to have to take care of first???
any configure or make options recommended that arent default???
am i going to have to start from scratch or can i build on top of the version i have currently installed???

how does one go about doin up SVN... i've never really had to mess with CVS or SVN so im a totall newb in that department

thanks again

---

### Post by yabbadabbadont on 2007-07-12
> **Nythain said:**
> so after reading up on the more recent changes between the version in the repos and the latest release candidate... any advice on compiling from scratch???
list of dependencies im going to have to take care of first???
any configure or make options recommended that arent default???
am i going to have to start from scratch or can i build on top of the version i have currently installed???

how does one go about doin up SVN... i've never really had to mess with CVS or SVN so im a totall newb in that department

thanks again

Assuming that you already have the basic build environment installed...  just run ```
sudo apt-get build-dep fluxbox
```  That will pull in all the fluxbox specific dependencies.  You will also need to install subversion in order to checkout a copy of the current SVN code.  The fluxbox download page has the instructions on pulling the code from SVN and how to build it.  The only option that the current SVN doesn't enable by default, and that you might need, is "--enable-nls".  Just include that when you run the "./configure" step.  You will want to "apt-get remove fluxbox" before you install the SVN version.  You can either use the "sudo make install" to install it after you build it, or use the checkinstall program to create a deb for the svn version.  I can provide detailed instructions on how I setup the build environment and build fluxbox, but they are rather lengthy and I don't feel like typing them out unless truly needed.  Besides, I think that there is already a "How to compile fluxbox" thread around here somewhere.  I'll edit this post and add a link if I find it.

Edit: Found it -- [http://ubuntuforums.org/showthread.php?t=116759](http://ubuntuforums.org/showthread.php?t=116759)

---

### Post by Nythain on 2007-07-13
muchos gracias... reading over the instructions on the fluxbox site at the moment, so far it seems pretty easy and straightforward

---

### Post by RedSquirrel on 2007-07-13
I believe you have to install 'automake' as well; without it, the './autogen.sh' step will fail.

EDIT: ...and the 'libtool' package as well. ;)

---

### Post by chm0d on 2007-07-13
Nice screenshots guys.   I installed fluxbox today because I wanted a change.  I have questions.  I am able to get my right-click menus transparent but as for a terminal I cannot.  I go to the transparency option and mess with focused and unfocused window but that does not do anything.  Can anyone shed some light on that subject?  Once I get this the way I want I will post a screenshot :)

Rich

---

### Post by yabbadabbadont on 2007-07-13
> **chm0d said:**
> Nice screenshots guys.   I installed fluxbox today because I wanted a change.  I have questions.  I am able to get my right-click menus transparent but as for a terminal I cannot.  I go to the transparency option and mess with focused and unfocused window but that does not do anything.  Can anyone shed some light on that subject?  Once I get this the way I want I will post a screenshot :)

Rich

If you don't have the COMPOSITE extension enabled in your /etc/X11/xorg.conf then you need to turn on the "Force Pseudo-Transparency" option.  Even then, it will only affect the window borders as they are the only part of the window that Fluxbox draws itself.  Most transparent terminals that you see in screenshots with Fluxbox are not using true transparency.  Aterm, Eterm, rxvt, mrxvt, are some of the terminals that offer pseudo-transparency themselves.  For true transparency, you have to use xcompmgr and transset.  Both of them are in the Ubuntu repositories so you can install them with Synaptic, aptitude, apt-get, ...

See the following for details:
[http://fluxbox-wiki.org/index.php/Transparency](http://fluxbox-wiki.org/index.php/Transparency)  -- fairly old, but should still work.

---

### Post by chm0d on 2007-07-13
yabbadabbadont, thanx for the reply.  I do have aterm installed and also have composite enabled in xorg.conf.  I have tried clicking on transparency for aterm but nothing happens?  Is there something else I need to know?

Thx again.

---

### Post by yabbadabbadont on 2007-07-13
As I said before, the transparency settings in the Fluxbox menu only control the window borders since those are the only part that Fluxbox draws itself.  You have to read the man page for aterm to learn the correct command line parameters it needs in order to enable its pseudo-transparency.

---

### Post by Nythain on 2007-07-13
yeah, you could try running aterm with its transparency option... not sure what it is in aterm as i use eterm... and its transparency as mentioned will only be psuedo, it copies the section of the desktop under it and uses that as its background, so if its on top of another app then it will look funky, like the terminal is a cookie cutter cutting a hole straight down to your desktop.

---

### Post by RedSquirrel on 2007-07-14
> **chm0d said:**
> yabbadabbadont, thanx for the reply.  I do have aterm installed and also have composite enabled in xorg.conf.  I have tried clicking on transparency for aterm but nothing happens?  Is there something else I need to know?

Thx again.

When I was playing with aterm, I tried some of the sample commands from the homepage ([http://www.afterstep.org/aterm.php](http://www.afterstep.org/aterm.php)) and they worked for me.

For example:
```
aterm -tr -sh 50
```

---

### Post by yabbadabbadont on 2007-07-14
@Nythain: Which eterm package are you using?  The default one doesn't seem to handle utf8 encoding properly on my system.

---

### Post by Carbon Tiger on 2007-07-14
I've been having fun with GNOME but I wanted to try something a bit more lightweight. Fluxbox took a while to get used to but with the good advice from this thread I finaly have a 2nd set up that I think is pretty cool. Decided to attach an image :)

---

### Post by yabbadabbadont on 2007-07-14
> **Carbon Tiger said:**
> I've been having fun with GNOME but I wanted to try something a bit more lightweight. Fluxbox took a while to get used to but with the good advice from this thread I finaly have a 2nd set up that I think is pretty cool. Decided to attach an image :)

Did you forget to run wmmount with the "-w" parameter?  ;)

---

### Post by Carbon Tiger on 2007-07-15
> **yabbadabbadont said:**
> Did you forget to run wmmount with the "-w" parameter?  ;)

Well one thing at a time ;) Been wondering how to group it in with the rest of the icons, thanks. Still the learning aspect is most fun.

EDIT: Looking at the startup list I already have it tagged as -w & I wonder why it isn't grouping with the other 'wm' apps. The other ones didn't even need the -w tag. Hmmm weird.

---

### Post by Nythain on 2007-07-15
im using the package from the repos...
it didnt like to show a lot of stuff correctly (my main problem was midnight commander) and after a little googling i found a workaround by editing my .bashrc and or .profile and adding at the top
export LANG=C
not sure if thats a fix for the utf8 encoding completely, but it definately fixed mc displaying correctly

---

### Post by JMO707 on 2007-07-18
Mmm, recently I got a problem with the *keys* file, so I had to rewrite it. Now, on the Alt+F1 combination I had some nifty run dialog from Fluxbox (like the one in Gnome, with Alt+F2). 

I really cant find the command to call it back =S

---

### Post by yabbadabbadont on 2007-07-18
> **JMO707 said:**
> Mmm, recently I got a problem with the *keys* file, so I had to rewrite it. Now, on the Alt+F1 combination I had some nifty run dialog from Fluxbox (like the one in Gnome, with Alt+F2). 

I really cant find the command to call it back =S

fbrun is the name of the Fluxbox run dialog like the Alt-F2 used by default with Gnome.

---

### Post by stealth17 on 2007-07-19
I checked out the SVN and I'm at revision 4988. It doesn't have the stuff needed for ./configure when you download it so you have to run ./autogen.sh first.

When I run that I get this error:

```
stealth17@stealth17-desktop:~/fluxbox$ ls
acinclude.m4  autogen.sh  ChangeLog     COPYING  doc       INSTALL     ltconfig     missing        NEWS  README   src         TODO  version.h.in
AUTHORS       BUGS        configure.in  data     Doxyfile  install-sh  Makefile.am  mkinstalldirs  nls   RoadMap  stamp-h.in  util

stealth17@stealth17-desktop:~/fluxbox$ ./autogen.sh
./autogen.sh: 15: libtoolize: not found
Executing:  aclocal -I .

./autogen.sh: 17: aclocal: not found
-e 
 ERROR: Carefully read the error message and
        try to figure out what went wrong.

```I cannot find a package called libtoolize or aclocal so I dunno what to do from here :confused:


**EDIT:** Found the solution. Run this to fix:

```
$ sudo apt-get install automake libtool
```

---

### Post by RedSquirrel on 2007-07-19
> **stealth17 said:**
> I checked out the SVN and I'm at revision 4988.

Darn. After waiting a couple of days to update from 4983, I just built 4987 a couple of *hours* ago. Oh well... :roll:

---

### Post by stealth17 on 2007-07-19
> **RedSquirrel said:**
> Darn. After waiting a couple of days to update from 4983, I just built 4987 a couple of *hours* ago. Oh well... :roll:

Would it be helpful to others if I uploaded the deb file? or is it still better to compile yourself?

Also, when I compiled it says i386. Is it possible to compile for i646 or something? I have an AMD64 with 32-bit Ubuntu.

**EDIT:** Also, how would I start dhcp3-server with Fluxbox? Would I put "/etc/init.d/dhcp3-server start &" in my ~/.fluxbox/startup file?

---

### Post by RedSquirrel on 2007-07-20
> **stealth17 said:**
> Would it be helpful to others if I uploaded the deb file? or is it still better to compile yourself?

Also, when I compiled it says i386. Is it possible to compile for i646 or something? I have an AMD64 with 32-bit Ubuntu.

**EDIT:** Also, how would I start dhcp3-server with Fluxbox? Would I put "/etc/init.d/dhcp3-server start &" in my ~/.fluxbox/startup file?

The SVN version is updated fairly often so I'm not sure it's worth it to upload anything. (just my opinion ;))

You can probably play around with the architecture settings but I just use the defaults for my old system. 

I don't use dhcp3-server but I was under the impression that it starts automatically.

---

### Post by RedSquirrel on 2007-07-20
@yabbadabbadont:

Have you tried urxvt (package: rxvt-unicode)? I've been playing with it for a while today and it seems pretty nice. Might be a substitute for eterm.

---

### Post by kerry_s on 2007-07-20
> **RedSquirrel said:**
> @yabbadabbadont:

Have you tried urxvt (package: rxvt-unicode)? I've been playing with it for a while today and it seems pretty nice. Might be a substitute for eterm.

i replaced xterm with it, i'm using rxvt-unicode-lite. i run the daemon urxvtd so my launcher is the client urxvtc, it makes it fricken fast and uses less resources. :)

---

### Post by yabbadabbadont on 2007-07-22
> **RedSquirrel said:**
> @yabbadabbadont:

Have you tried urxvt (package: rxvt-unicode)? I've been playing with it for a while today and it seems pretty nice. Might be a substitute for eterm.

Now days, I don't care much about transparency.  I just use uxterm with gray80 text on a gray20 background.  I've found that combination to be nice for long coding sessions in vim.

---

### Post by RedSquirrel on 2007-07-22
> **yabbadabbadont said:**
> Now days, I don't care much about transparency.  I just use uxterm with gray80 text on a gray20 background.  I've found that combination to be nice for long coding sessions in vim.
I just thought I'd mention it since eterm wasn't working too well.

I think transparency looks nice for a screenshot, but I find it doesn't take long for me to switch back to a solid background. I'm using uxterm with black text and lightyellow background. ;)

PS - installed SVN 4991 today. Seems OK so far.


> **kerry_s said:**
> i replaced xterm with it, i'm using rxvt-unicode-lite. i run the daemon urxvtd so my launcher is the client urxvtc, it makes it fricken fast and uses less resources. 

I was having fun with the transparency but I think it's back to (u)xterm for now... :grin:

---

### Post by kerry_s on 2007-07-22
i went back to xterm to, that mc on rxvt slow load bug was just bugging the heck out of me, i looked for a fix but didn't find one. i use mc alot so that just wouldn't do, shame to urxvt was so fast at everything else, plus i liked the daemon feature. :(
1 thing i missed on xterm that i'm glad to have back is the ctrl+right click font size selection.

---

### Post by ghandi69_ on 2007-07-24
Hey guys,

I wanted to thank you for all your help, as of now I have been running fluxbox for the last two or 3 days and I'm loving it!!

A couple more questions though.....

I have noticed my "printscreen" key does not seem to work in flux, do I have to add it somehow to that 'keys' file in .fluxbox?

I have synaptic and aptitude for package management, but what program do I need to install for updates?  I havent seen any since I've been running flux, and I'm figuring I need to install something.

I have been using conky for some nice eye candy on the desktop, I can get it to look pretty much how I want it, but I noticed other people used things like...."execi" to get temperatures for processors and drives and weather updates... Is this something I need to install?  Because I'm not getting any output for those commands...

I guess these are not really flux questions... but oh well

any takers??

---

### Post by yabbadabbadont on 2007-07-24
```
/home/daffy $ cat .fluxbox/keys 
OnDesktop Mouse1 :HideMenus
OnDesktop Mouse2 :WorkspaceMenu
OnDesktop Mouse3 :RootMenu
OnDesktop Mouse4 :PrevWorkspace
OnDesktop Mouse5 :NextWorkspace

Mod1 Tab :NextWindow
Mod1 Shift Tab :PrevWindow
Mod1 F1 :Workspace 1
Mod1 F2 :Workspace 2
Mod1 F3 :Workspace 3
Mod1 F4 :Workspace 4
None Print :Execute grab-screen
Mod1 Sys_Req :Execute grab-selection
Mod1 F11 :Execute wallpaper-set-random
Mod1 F12 :Execute xmessage -default okay -center -file ~/.current-wallpaper-name
Mod4 t :Execute uxterm -geometry 127x44+0+0 -fg gray80 -bg gray20 -sl 2000 -fn "-xos4-terminus-medium-r-normal-*-16-*-*-*-*-*-iso10646-1"
Control Mod1 q :Quit
Control Escape :RootMenu
```
Notice the "grab-screen" and "grab-selection" lines.  (those are two scripts that I wrote)

The update manager provided with ubuntu pretty much requires that you install all of gnome in order to use it...  :?  Personally, I just run "sudo apt-get update" and "sudo apt-get dist-upgrade" manually once a day.

To get temperature readouts, you will need to make sure that the correct modules for your motherboard's sensor chips are loaded.  (Usually by adding them to /etc/modules)  If you have no idea which modules you need for your sensors, then install the lm-sensors package and do some research on how to use (I think it is called) sensors-detect.  My current motherboard doesn't need lm-sensors, so it has been several years since I've configured lm-sensors and am not in much of a position to tell you how.  I did find a howto thread though here: [http://ubuntuforums.org/showthread.php?t=2780&highlight=sensors+howto](http://ubuntuforums.org/showthread.php?t=2780&highlight=sensors+howto)

It is a few years old so you will need to read through the 20 or so pages to make sure that you get the latest information.  The posts get into 2007 on page 15 by the way.  (I would read through the whole thing before trying anything though)

---

### Post by ghandi69_ on 2007-07-24
Thanks for the help, 

Any chance I could get a copy of those scripts for printing the screen so I could use them?

And as for the motherboard sensors, that looks like something I'm going to have to put away until a rainy day, thanks for the link though.

---

### Post by urukrama on 2007-07-24
> **yabbadabbadont said:**
> Notice the "grab-screen" and "grab-selection" lines.  (those are two scripts that I wrote)

Could you not bind scrot (with all the options you want) to those keys instead? That is what I do in Openbox.

---

### Post by RedSquirrel on 2007-07-24
> **ghandi69_ said:**
> I have noticed my "printscreen" key does not seem to work in flux, do I have to add it somehow to that 'keys' file in .fluxbox?

Here's what I am using:

```
Print :Exec import -pause 5 -window root ~/misc/screenshots/screenshot-`date +%Y-%m-%d_%T`.jpg
Mod1 Sys_Req :Exec import -frame ~/misc/screenshots/window-`date +%Y-%m-%d_%T`.jpg

```

The first one is for PrintScreen and it takes a shot of the whole desktop after 5 seconds. The second one is Alt-PrintScreen. It changes your mouse cursor into a crosshair that you can use to click on windows (to take a shot of that window alone) or you can click & drag the crosshair to take a shot of a selection.

You have to install imagemagick to get those commands to work.

```
sudo aptitude update && sudo aptitude install imagemagick
```scrot is another program you can use for screenshots as urukrama suggested.



> **ghandi69_ said:**
>  I have synaptic and aptitude for package management, but what program do I need to install for updates?  I havent seen any since I've been running flux, and I'm figuring I need to install something.

update-manager is the graphical tool that you're probably used to. I don't think it has many dependencies, but you don't really need it. You could do what yabbadabbadont suggested or use Synaptic. Just click 'Reload' and then 'Mark All Upgrades' then 'Status' then 'Installed (upgradeable)' to see what there is to be upgraded. Then just click 'Apply' to install the upgrades.

update-notifier is the other program related to updates. It will provide you with notification when updates are available. It's a nice idea, but this one does have a lot of GNOME dependencies which makes it undesirable for a lightweight install.

---

### Post by kerry_s on 2007-07-24
sudo apt-get install scrot

Print :Exec scrot %T.jpg

---

### Post by ghandi69_ on 2007-07-24
Thanks guys... I'll try that afte work(only 1 more week left of work, and then back to school!!! can't wait)

I was wondering what programs you guys would recommend that have good custimizable themes and run well in flux.

I'm using opera and thunderbird, which both can be custimzed to match my theme very well..

However, my KDE apps are starting to stick out like a sore thumb..

k3b
amarok
ktorrent

and they seem to have some issues running in flux anyway (when I start them, about 5 error messages saying klauncher cannot be reached), then they run fine after that.

Are there good alternatives that work well and custimize well with flux?

---

### Post by yabbadabbadont on 2007-07-24
> **urukrama said:**
> Could you not bind scrot (with all the options you want) to those keys instead? That is what I do in Openbox.

The scripts call the import command from imagemagick in pretty much the same way that RedSquirrel posted.  I reinstall and switch out which flavor of linux I use fairly often.  I also change back and forth between window managers a lot.  Putting the commands in scripts with simple descriptive names just makes it easier for me when I have to configure a new setup.

```
/home/daffy $ cat bin/grab-screen 
#!/bin/bash
import -window root /media/images/Screenshots/$(date +%Y%m%d%H%M%S)-full.png
/home/daffy $ cat bin/grab-selection 
#!/bin/bash
import /media/images/Screenshots/$(date +%Y%m%d%H%M%S)-selection.png

```

---

### Post by RedSquirrel on 2007-07-26
> **yabbadabbadont said:**
> I just use uxterm with gray80 text on a gray20 background.  I've found that combination to be nice for long coding sessions in vim.

Do you use any other colors with that setup or is everything gray80? I have been playing around with colors in vim, gvim, and uxterm. Just wondering what color scheme you use, if anything. Thanks. :)

---

### Post by yabbadabbadont on 2007-07-26
> **RedSquirrel said:**
> Do you use any other colors with that setup or is everything gray80? I have been playing around with colors in vim, gvim, and uxterm. Just wondering what color scheme you use, if anything. Thanks. :)

Just the default vim syntax highlighting for a dark background.

Edit: attached an image for illustrative purposes.  :)  

Note: that is gnome-terminal as I recently did a full install of the default desktop in an effort to debug a CUPS issue with my previous custom install.

---

### Post by JMO707 on 2007-08-01
Someone can ilustrate me on how can I have a different GTK theme on the Fluxbox session, from the one on the Gnome session?

---

### Post by kerry_s on 2007-08-01
> **JMO707 said:**
> Someone can ilustrate me on how can I have a different GTK theme on the Fluxbox session, from the one on the Gnome session?

you can't, they both use the same source.

Wait, you can use a different user name, have 1 user setup for only fluxbox and 1 for only gnome.

---

### Post by JMO707 on 2007-08-02
Cant I use some kind of startup file to set-it up when the session beggin?

---

### Post by yabbadabbadont on 2007-08-02
> **JMO707 said:**
> Cant I use some kind of startup file to set-it up when the session beggin?
When gnome is running, gnome-settings-demon takes care of the GTK2 settings and it uses .gtkrc-1.2-gnome2 for GTK1 apps.  If you don't start gnome-settings-demon in your ~/.fluxbox/startup file, then GTK1 will use .gtkrc and GTK2 will use .gtkrc-2.0 for their settings.  What I would do is to save your .gtkrc and .gtkrc-2.0 files under different names then, in your ~/.fluxbox/startup file, rename or copy them to the correct names at the top of the file and back to the saved names at the end of the file.  Example:
```
cp /home/daffy/.gtkrc-save /home/daffy/.gtkrc
cp /home/daffy/.gtkrc-2.0-save /home/daffy/.gtkrc-2.0
#Also copy the .gtkrc*.mine files if you use them

fbsetroot -solid '#0e4681'

xset -b r rate 250 30 -dpms s off

numlockx on

fluxbox -log "/home/daffy/.fluxbox/log" &
fluxpid=$!

wallpaper-set-rotate 300 &
wsrpid=$!

sleep 2

gkrellm -w &
gkpid=$!

sleep 2

fbpanel &
fbpid=$!

wait $fluxpid

kill $wsrpid
kill $gkpid
kill $fbpid

rm -f /home/daffy/.gtkrc /home/daffy/.gtkrc-2.0
```

---

### Post by RedSquirrel on 2007-08-02
> **yabbadabbadont said:**
> Just the default vim syntax highlighting for a dark background.

Edit: attached an image for illustrative purposes.  :)  

Thanks. I've attached one too. I'm using the colors from the bottom of this page:

[http://gentoo-wiki.com/TIP_Linux_Colors_in_Aterm/rxvt](http://gentoo-wiki.com/TIP_Linux_Colors_in_Aterm/rxvt)

They're quite *soothing*.


> **yabbadabbadont said:**
> Note: that is gnome-terminal as I recently did a full install of the default desktop in an effort to debug a CUPS issue with my previous custom install.

I had fun with CUPS too. I was missing a crucial package and it took me a little while to figure out which one it was. ;)

EDIT: this was post _666_ :evil:


Screenshot...

---

### Post by yabbadabbadont on 2007-08-02
> **RedSquirrel said:**
> I had fun with CUPS too. I was missing a crucial package and it took me a little while to figure out which one it was. ;)
What was your issue and which package was missing?  Mine was that everything would print correctly but CUPS would never show the job as complete and I would have to manually remove it.  It didn't matter if I printed to a physical printer or the cups-pdf driver either.  I've been busy since I reinstalled so I haven't yet tested to see if the issue still exists.  (time to get off my butt I guess  :lol:)
> **RedSquirrel said:**
> EDIT: this was post _666_ :evil:
I just noticed that my bean description has changed, but I didn't see which post did it...  I know it didn't change when I hit 2600 though.

---

### Post by RedSquirrel on 2007-08-02
> **yabbadabbadont said:**
> What was your issue and which package was missing?

It wouldn't print.

I installed 'gimp-print' (and cupsys/cupsys-client) and I was under the impression that that would be sufficient. It took a bit more digging to find out that I needed 'cupsys-driver-gutenprint' print as well. :oops:


> **yabbadabbadont said:**
> I just noticed that my bean description has changed, but I didn't see which post did it...  I know it didn't change when I hit 2600 though.

I like the sound of that "chocolate-covered...". Only 2000 more posts to go. :grin:

---

### Post by stealth17 on 2007-08-02
Is there anyway to make the menu auto-update when you install an app, like it does in Gnome? I do like the fluxbox style menu where you can edit it with a text editor, but it is a bit of a pain to add the apps every time i install one, you know?

thanks guys

---

### Post by Gremlinzzz on 2007-08-02
fluxbox is more of a barebone theme system i use ubuntu with the ubuntustudio theme looks good and still has the power of gnome
:guitar:[IMG]http://file:///home/pepe/Desktop/Screenshot.png[/IMG]f/Screenshot.png

---

### Post by RedSquirrel on 2007-08-02
> **stealth17 said:**
> Is there anyway to make the menu auto-update when you install an app, like it does in Gnome? I do like the fluxbox style menu where you can edit it with a text editor, but it is a bit of a pain to add the apps every time i install one, you know?

thanks guys

If the application is one that can appear in the 'Apps' section of your menu, then it should show up without you having to edit the menu file yourself. You might have to click Fluxbox menu -> Reconfigure (or 'Reload config' as it is sometimes called) after you have installed the app.

If you use a combination of the Debian Menu and fluxbox-generate_menu, then you would just have to "regenerate" the menu (which is usually an option in your menu when you use fluxbox-generate_menu).

Have a look at the howto in my signature.

---

### Post by stealth17 on 2007-08-02
> **RedSquirrel said:**
> If the application is one that can appear in the 'Apps' section of your menu, then it should show up without you having to edit the file yourself. You might have to click Fluxbox menu -> Reconfigure (or 'Reload config' as it is sometimes called) after you have installed the app.

If you use a combination of the Debian Menu and fluxbox-generate_menu, then you would just have to "regenerate" the menu (which is usually an option in your menu when you use fluxbox-generate_menu).

Have a look at the howto in my signature.

ahh nice guide, thanks. I am using the Debian Menu and the fluxbox-generate_menu method. I compiled fluxbox from the subversion, so nothing was used from the repo's. When I run sudo update-menus it says command cannot be found. What is the name of the package that I am missing for that?

---

### Post by RedSquirrel on 2007-08-02
> **stealth17 said:**
> ahh nice guide, thanks. I am using the Debian Menu and the fluxbox-generate_menu method. I compiled fluxbox from the subversion, so nothing was used from the repo's. When I run sudo update-menus it says command cannot be found. What is the name of the package that I am missing for that?
The 'menu' package. But you'll also need the script in /etc/menu-methods for Fluxbox.

** [COLOR=Red]EDIT:[/COLOR]**[COLOR=Red] Just to be absolutely safe, make a copy of /usr/share/xsessions/fluxbox.desktop (if you use gdm) and backup your ~/.fluxbox directory:
[/COLOR] 
```
cd ~
cp /usr/share/xsessions/fluxbox.desktop .
tar czf fluxbox_backup.tar.gz .fluxbox 
```Can you uninstall your subversion version, install the package from the repositories, then do 

```
sudo apt-get remove fluxbox
```That will remove the fluxbox binary but leave the configuration files in place.

```
sudo chmod +x /etc/menu-methods/fluxbox
```Then reinstall your svn version and try 'sudo update-menus' again.

Are you using checkinstall to install your svn version? It's not absolutely necessary, but it does make the process easier.

---

### Post by stealth17 on 2007-08-02
> **RedSquirrel said:**
> The 'menu' package. But you'll also need the script in /etc/menu-methods for Fluxbox.

** [COLOR=Red]EDIT:[/COLOR]**[COLOR=Red] Just to be absolutely safe, make a copy of /usr/share/xsessions/fluxbox.desktop (if you use gdm) and backup your ~/.fluxbox directory:
[/COLOR] 
```
cd ~
cp /usr/share/xsessions/fluxbox.desktop .
tar xzf fluxbox_backup.tar.gz .fluxbox 
```Can you uninstall your subversion version, install the package from the repositories, then do 

```
sudo apt-get remove fluxbox
```That will remove the fluxbox binary but leave the configuration files in place.

Then reinstall your svn version and try 'sudo update-menus' again.

Are you using checkinstall to install your svn version? It's not absolutely necessary, but it does make the process easier.

hmmm not sure I want to get that deep into it :( Yeah I used checkinstall when I compiled it. I guess it's not that big of a deal but if I get some time on the weekend then I'll see what I can do.

Thanks for the help.

---

### Post by yabbadabbadont on 2007-08-02
> **stealth17 said:**
> hmmm not sure I want to get that deep into it :( Yeah I used checkinstall when I compiled it. I guess it's not that big of a deal but if I get some time on the weekend then I'll see what I can do.

Thanks for the help.

```
/home/daffy $ cat /etc/menu-methods/fluxbox 
#!/usr/bin/install-menu
#
# Generates fluxbox menus for all registered applications.
# (taken from Blackbox)
compat="menu-1"
outputencoding="LOCALE"

!include menu.h

genmenu="menudefs.hook"
examplercfile="system.fluxbox-menu"
rcfile="fluxbox-menu"
rootprefix="/etc/X11/fluxbox/"
userprefix=".fluxbox/"
treewalk=M)

supported
    x11=   nstring(level(), "   ") "[exec] (" esc($title, ")") ") {" esc($command, "()") "} <" esc($icon, "<>") ">\n" 
    wm=    nstring(level(), "   ") "[restart] ("  esc($title, ")")  ")  {" esc($command, "()") "}\n" 
    text=  nstring(level(), "   ") "[exec] (" esc($title, ")") ") { x-terminal-emulator -T \"" $title "\" -e " esc($command, "()") "} <" esc($icon, "<>") ">\n"
    fluxbox= nstring(level(), "   ") "[" esc($command, "()") "] (" esc($title, ")") ")\n"
endsupported

#preoutput= \
#  "# Automatically generated file. Please do not edit (see /usr/share/doc/menu/README)\n\n\n\nDebian MENU\n\n[begin] (Debian)\n"
#postoutput= \
#   "\nDebian END\n"

startmenu= ""
submenutitle= nstring(level(), "   ") "[submenu] (" esc($title,"()") ") {" esc($longtitle,"()") "}\n"
endmenu= ifneq( level(), "0",  nstring(level(), "   ") "[end]\n" )


```
Make sure to make it executable.

Edit: You will need to install "menu" first.

---

### Post by RedSquirrel on 2007-08-02
@stealth17:

Forget the lengthy solution I posted above. That will work, but all you need is the script that yabbadabbadont provided. I knew for certain that you needed that file, but I thought you might need some other files as well. It turns out you don't need those other files to generate the Debian menu file, 'menudefs.hook'. This is rather convenient. ;)

So, the recipe is simple:

Install menu:

```
sudo apt-get install menu
```Then just save the script that yabbadabbadont has posted as /etc/menu-methods/fluxbox and make it executable.

```
sudo chmod +x /etc/menu-methods/fluxbox
```Then run:

```
sudo update-menus
```That will create the file /etc/X11/fluxbox/menudefs.hook which is what you want to include in your menu.

Nice and easy. :)

---

### Post by TeaSwigger on 2007-09-22
It's me again hittin' up a fluxbox thread. Have plenty else to do, but you know I just can't leave this fluxbox thing alone... Just the most trivial stuff this time, happy to say :)

Any suggestions for a fluxbox clipboard tool? No big as I'm using KDE's rather nice klipper in the fluxbox bar (simply put 'klipper &' in the startup and viola!) but I get the feeling it's probably a hair generous for the context if you know what I mean. ;)

Red Squirrel, if this catches you; remember my wanting to use the teatimer Gnome toolbar applet? Can't figure that one out, but I did get KDE's similar TeaCooker toy in the fluxbox docker. Works fine! Now there's less risk of me blissfully puttering on the PC whilst my tea is becoming fit to run a diesel engine. But that left another puzzle in its place; why it is that Gnome's nicer tea toy applet is much more suited to KDE while KDE's tea toy applet is much more suited to Gnome... Yeah but it's a mystery that goes well with a cup of Darjeeling. :p

---

### Post by mojoman on 2007-09-22
Damn, there's some pretty good stuff in this thread. How could I have missed it?

Steveneddy: Is that xmms you're running? If so, what skin is that? Awesome!

RedSquirrel: Looks like you've got just the bar showing on one window. (Same as one can do in Xfce.) Is it? If so, how is it enabled? I love that function but I seldom log into Xfce these days.

I'm running the fluxbox out of feisty's repository but the transparancy looks good. I should probably start compiling from source to get the latest and greatest...

cheers
/mojoman

---

### Post by RedSquirrel on 2007-09-22
> **TeaSwigger said:**
> Have plenty else to do, but you know I just can't leave this fluxbox thing alone... 

I know exactly what you mean. :grin:


> **TeaSwigger said:**
>  Any suggestions for a fluxbox clipboard tool?

I'm not sure. I don't use one. Perhaps kerry_s will see your question. His knowledge of applications for *this & that* never ceases to amaze me. :)


> **TeaSwigger said:**
> ... I did get KDE's similar TeaCooker toy in the fluxbox docker. Works fine! ... But that left another puzzle in its place; why it is that Gnome's nicer tea toy applet is much more suited to KDE while KDE's tea toy applet is much more suited to Gnome... Yeah but it's a mystery that goes well with a cup of Darjeeling. :p

Glad you got something to work so your tea doesn't steep too long. It's a real shame when that happens. Not sure about the mystery.

---

### Post by RedSquirrel on 2007-09-22
> **mojoman said:**
> RedSquirrel: Looks like you've got just the bar showing on one window. (Same as one can do in Xfce.) Is it? If so, how is it enabled? I love that function but I seldom log into Xfce these days.

I'm running the fluxbox out of feisty's repository but the transparancy looks good. I should probably start compiling from source to get the latest and greatest...

cheers
/mojoman

The window with only the titlebar showing is "shaded". You can achieve this by double-clicking on the titlebar.

I also use the following shortcut keys:

```
! Shade/Unshade windows
Mod1 Up   :Shade
Mod1 Down :Shade

```

(Just to be clear: the Up/Down are the *arrow* keys.)

The transparency of the version from the repositories should work fine. The only difference I can recall is that the older version requires you to **restart** Fluxbox (from the menu) to make the transparency settings take effect. The 1.0-rc3 version changes the transparency *on the fly* as you adjust it from the menu (which is pretty cool).

... but by all means, compile your own if you like. I have been building the SVN version usually once a week for quite a while now and it's usually worked out fine (say, 99% of the time). If there's a problem I just rollback to my older SVN version. ;)

---

### Post by mojoman on 2007-09-22
> **RedSquirrel said:**
> The window with only the titlebar showing is "shaded". You can achieve this by double-clicking on the titlebar.

Well, what do you know! I had it enabled all the time. Thanks. I just love the stuff I keep stumbling over in fluxbox! :)

Now I'm gonna check out some transparency as well. Should keep me busy for a couple of hours...

---

### Post by TeaSwigger on 2007-09-24
Howdy strangers ;) I'm trying rxvt. To most around my RL area, that just might have them thinking I'm referring to some substance tried and tripped over, while the rest may assume I'm trying a hand at home improvement. At least here there's someone I can talk to who just may know that yes indeed, I'm speaking of the famed Terminal Emulator by that oh-so memorable, evocative and picturesque name, rxvt. So I put forth the crucial inquiry... 

How do I get rxvt to open at say 800x600 in fluxbox?

---

### Post by kerry_s on 2007-09-24
**rxvt -g 800x600**

man rxvt

---

### Post by RedSquirrel on 2007-09-24
> **TeaSwigger said:**
>  How do I get rxvt to open at say 800x600 in fluxbox?

rxvt, like xterm, uses height and width measured in characters. This means that the size of your terminal is affected by the font you choose.

In my experience, once you have chosen a font, you sort of have to play around with different geometry settings until you find one you like. Start small and go from there:

rxvt -g 80x40 -fa dejavusansmono -fs 11
.
.
.
rxvt -g 127x44 -fa dejavusansmono -fs 11


N.B.: Using 800x600 characters will produce an *enormous* terminal. :)

Have a look at this link to get a general idea of what's going on:

[http://www.xfree86.org/current/X.7.html#sect6](http://www.xfree86.org/current/X.7.html#sect6)

---

### Post by yabbadabbadont on 2007-09-24
To follow up on RedSquirrel's excellent advice, here is what I do in this situation.  As he suggested, I pick out a font and font size that looks good to me.  Next, I just open a default sized terminal window.  (Using my chosen font and font size of course ;))  Then I resize the window to the desired dimensions.  Finally, I find the size in text characters thusly:
```
echo $COLUMNS $LINES
```  Now you have the correct parameters to pass to the terminal with the "-geometry" option.

:D

---

### Post by RedSquirrel on 2007-09-24
> **yabbadabbadont said:**
> Then I resize the window to the desired dimensions.  Finally, I find the size in text characters thusly:
```
echo $COLUMNS $LINES
```  Now you have the correct parameters to pass to the terminal with the "-geometry" option.

:D

That's a great approach (and you get bonus points for using the word "thusly"). :)

---

### Post by TeaSwigger on 2007-09-24
Ah ah ha so one issues a size for a terminal in the command and not setting a size in fluxbox. And the size is by characters. I'd read the rxvt man but that didn't fall into place. Thanks :) After the kind responses and re-reading the man, confusion remains, 'cause I tried all the -fn's and -fs's in every possible form, like so:

```
rxvt -g 80x40 -fa dejavusansmono -fs 11
```

... and not one thing actually works.  :-k All I get is "can't load font [name]" for every one I've tried. dejavu, sans, freesans, loads of 'em. It always goes ahead and uses the default font at the default size. The man has this to say about that:

```
font: fontname
Select the main text font used [default 7x14]; option -fn.
```

...Anybody have a font to set in the rxvt in oh, 7x14? Now it does sound like we're talking home improvement :lol:

Sounds like this is outside the thread though, hope its ok carrying on. Thought it was fluxbox related :p

---

### Post by RedSquirrel on 2007-09-24
Strange. Maybe you're missing some font packages. You could try **xfontsel** to put together some sort of basic font. 

This [link]("http://web.mit.edu/answers/xwindows/xwindows_fonts.html") might help.


PS - It's fine with me if you carry on (but I am only one person ;)).

---

### Post by steveneddy on 2007-09-25
Fluxbox is so cool.......and fast.

:popcorn:

---

### Post by TeaSwigger on 2007-09-25
Ah not sure if it's worth posting or no, so I'll leave that to you ;) - but here's two simple screens of my simple fluxbox-ubuntu-themed desktop at this time. I guess it's fair to say it illustrates the refreshingly simple yet clean and colorful desktop one can have going with fluxbox in no time flat. Yet with a toolbar, desktop switcher with indicator, window switcher, clock, clipboard utility (Klipper via KDE) and right click for the menu - all you need to "go to it" GUI-style is there. What a nice setup :)

[ATTACH]44427[/ATTACH]

[ATTACH]44428[/ATTACH]

---

### Post by RedSquirrel on 2007-09-26
Those are nice. Here's a more updated one of mine...

---

### Post by RedSquirrel on 2007-09-26
@TeaSwigger:

I've been experimenting with urxvt again and it seems that it doesn't support the '-fa' and '-fs' options we were discussing above. I didn't realize it at the time because I didn't have rxvt installed and I thought it would use the same options as xterm. Sorry about that.

Here's what I'm using:

```
urxvt -tr -tint white -sh 15 +sb -geometry 107x47+20+20 [COLOR=Blue]-fn "xft:DejaVuSansMono:size=10"[/COLOR] -sl 1000 -title Terminal -cr orange
```

---

### Post by rjmdomingo2003 on 2007-09-27
> **slackmaGic said:**
> I'm not on Ubuntu, but it's fluxbox nonetheless :P

Let's see what we have here: we've got conky, a few mrxvt terms up one of which shows irssi which is being run through screen, rox-filer (barely use it but had to show it with those superb looking alienware icons)


[[IMG]http://www.slackmagic.com/uploads//files/thumbnail.png[/IMG]](http://www.slackmagic.com/uploads//files/06272007_2722_1680x1050.png)Hey slackmaGic, where did you get those alienware icons? They're really superb!

---

### Post by TeaSwigger on 2007-09-28
> **RedSquirrel said:**
> @TeaSwigger:

I've been experimenting with urxvt again and it seems that it doesn't support the '-fa' and '-fs' options we were discussing above. I didn't realize it at the time because I didn't have rxvt installed and I thought it would use the same options as xterm. Sorry about that.

Here's what I'm using:

```
urxvt -tr -tint white -sh 15 +sb -geometry 107x47+20+20 [COLOR=Blue]-fn "xft:DejaVuSansMono:size=10"[/COLOR] -sl 1000 -title Terminal -cr orange
```

Ah *-fn "xft:DejaVuSansMono:size=10"* method works like a charm, thanks :)

---

### Post by TeaSwigger on 2007-09-30
Well now it only looks like there's two things to "nail down" before I'm satisfied.

1) There are still a few WINE apps I can't seem to replace natively. When I close these apps, they "slip" down on screen and upon restarting will redraw at that lower point - say ~5-10 % lower each go. Like regular pants on a fashion model, ya have to drag 'em back up frequently. Doesn't happen in KDE or Gnome, just Fluxbox. Should I just chalk it up to some weird WINE thing and live with it or is this a known quirk with a known fix...?

2) Theme separation between Fluxbox & KDE sessions. yabbadabbadont's insightful solution a few pages back here does work for Gnome but not KDE. KDE still assumes control of Qt apps and colors & icons etc in the others. I'm hoping to dig into that in a bit and post here if I have success; but if I'm stumped I'll post here to nag about it ;)

---

### Post by yabbadabbadont on 2007-09-30
> **TeaSwigger said:**
> 2) Theme separation between Fluxbox & KDE sessions. yabbadabbadont's insightful solution a few pages back here does work for Gnome but not KDE. KDE still assumes control of Qt apps and colors & icons etc in the others. I'm hoping to dig into that in a bit and post here if I have success; but if I'm stumped I'll post here to nag about it ;)

You probably need to do something similar with your ~/.qt/qtrc file.  I don't have any KDE libs installed at the moment, but I use qtconfig to set the theme used by QT applications.

---

### Post by TeaSwigger on 2007-10-01
Thanks I'll test that suggestion :)

Question: you suggested swapping those gtk files by means of cp & rm commands at the start and finish of the fluxbox startup config; would it still be safe to use that method if there are several or more files to handle in the case of Flux/KDE? Or should one run a script instead...? I'm quite unfamiliar with these things yet.

update for anyone who may be interested in this stuff: I've rummaged through my home dir. There was neither a ~/.qt nor a ~/.qtrc in the home dir. What I did find which may be relevant are as follows:

A hidden sub-dir named ~/.qt in which reside:
kstylerc
phasestylerc
qt_plugins_3.3rc
qtrc
.kstylerc.lock  
.phasestylerc.lock  
.qt_plugins_3.3rc.lock  
.qtrc.lock

Alone in a hidden sub-dir named ~/.kde/env lay:
gtk-qt-engine.rc.sh

And shacking up in my home folder dir are:
.gtkrc-2.0-kde
.gtk_qt_engine_rc

Also there was neither ~/.gtkrc nor ~/gtkrc-2.0 nor ~/.gtkrc.mine nor ~/gtkrc-2.0.mine until I installed and used the GTK theme switch/switch2. 

This is a standard Kubuntu install to which I added fluxbox via apt-get from the repos, so this should be the same for all "stock" Kubuntus.

---

### Post by yabbadabbadont on 2007-10-01
The fluxbox startup file *is* a script.  ;)

But it would probably be easier to organize and swap them out if you put the commands into different scripts and then called the appropriate ones from the ~/.fluxbox/startup file.

---

### Post by TeaSwigger on 2007-10-01
Oh I knew *that* hehe :)

Didn't know if I needed qt3-config or qt4-config so I got 'em both... both work. They don't produce any new files that I could see like ~/.qtrc or such. I edited the startup file to swap all files listed in my relevant post above on startup and restore them on exit. The commands do the job; a simple enough thing to add. After logging in and out between Flux & KDE sessions and swapping styles like Madonna, I'm happy to relate that it does no harm at all.

There's just one problem. It doesn't work. KDE apps continue to blissfully ignore qtconfig's changes and can only be controlled in KDE's config center as far as I can figure. Yea I'm stumped now. 

You know I just tell myself it's all just that much more I didn't know before... ;)

---

### Post by yabbadabbadont on 2007-10-01
Try browsing through the files and directories in ~/.kde.  I would imagine that the settings are in there somewhere...  :)

---

### Post by TeaSwigger on 2007-10-04
If I may... any thoughts on the Fluxbuntu project's page? [http://www.fluxbuntu.org](http://www.fluxbuntu.org) As Ubuntu has the Human / orange-brown angle, and Kubuntu and Xubuntu are both into the slick blue angle, it looks like they're going to be dabbling in a more spring-like, organic nature angle of greens etc. It's an interesting choice and timely in hitting the conservation chord, as befitting the resource-conscious yet well, organic nature Fluxbox can offer. I sure wish the project well :)

---

### Post by mindtrick on 2007-10-04
Hi Fluxbox newbie here, 
I don't have the right click menu. I have to "sudo update-menus" but I can't figure any way to start a terminal?

---

### Post by mindtrick on 2007-10-04
OK, done it in GNOME and it worked.

---

### Post by RedSquirrel on 2007-10-04
> **TeaSwigger said:**
> If I may... any thoughts on the Fluxbuntu project's page? [http://www.fluxbuntu.org](http://www.fluxbuntu.org)

Several months ago, their screenshots seemed to have much darker tones. The new, lighter palette is nice.

Those shots are rather impressive. While I am content with my own custom setup, I can certainly appreciate the work they've done. I might give it a try when it comes out.

I imagine they will include some more choices of custom artwork with the distro (wallpapers, custom Fluxbox styles, etc.).

On my own system, most of the time I'm using a solid color background and solid color window decorations since they're a tiny bit faster, especially when I switch workspaces. I do enjoy fancy wallpapers, window decorations, and transparency from time to time. :)

---

### Post by TeaSwigger on 2007-10-08
Well folks I have a show-stoppin' problem here. Flux won't load. Session fails with a "lasted less than 10 sec" jazz. Here's the output of ~/.xsession-errors

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "teaswigger"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Teas:/tmp/.ICE-unix/5314
Initializing gnome-mount extension
```

And that's all she wrote. Too newbie to troubleshoot; no idea where to start looking or what could've caused it. Flux was working perfectly then no go. :(

---

### Post by mojoman on 2007-10-09
> **TeaSwigger said:**
> Well folks I have a show-stoppin' problem here. Flux won't load. Session fails with a "lasted less than 10 sec" jazz. Here's the output of ~/.xsession-errors

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "teaswigger"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Teas:/tmp/.ICE-unix/5314
Initializing gnome-mount extension
```

And that's all she wrote. Too newbie to troubleshoot; no idea where to start looking or what could've caused it. Flux was working perfectly then no go. :(

I had the same problem last week but it started after I had tried to upgrade fluxbox by installing a .deb of a later version (friday night, moonshine and root privileges, you know the drill...). Anyway, I fixed that by deinstalling the .deb and then installing it from source instead (the day after). However, to do that I had to start it in safe mode or whatever it's called. Is it just fluxbox or have you tried starting it with another DE/WM (if you have one installed)? That could help us narrowing down the problem to a general x-server-problem or just a fluxbox-related issue.

/mojoman

---

### Post by RedSquirrel on 2007-10-09
As mojoman said, it would help to know if this happens with other desktop environments / window managers or just Fluxbox.

Is this the exact same system you were using before, i.e., the 1.0rc2 Fluxbox from the Ubuntu repositories?

Can you recall anything that you changed?

You might try starting Fluxbox with default settings to see if it runs at all.

At the login screen, press Ctrl-Alt-F2. Login there.

Rename the .fluxbox directory:
```
mv ~/.fluxbox ~/old.fluxbox
```Type exit and press ENTER. Then press Ctrl-Alt-F7.

(You can also rename the .fluxbox directory using a terminal in another DE/WM.)

Then login to Fluxbox from the login screen and it should create a fresh .fluxbox directory and files.

Make sure you start Fluxbox with the startfluxbox script. In /usr/share/xsessions/fluxbox.desktop, the Exec line should be /usr/bin/startfluxbox.

---

### Post by TeaSwigger on 2007-10-09
Thank you, mojoman and RedSquirrel I appreciate the help. I'm back in Fluxbox after following the suggestion to rename ~/.fluxbox. Whew! No idea yet what happened. It does call /usr/bin/startfluxbox. I was able to log in to KDE via KDM, which are unaffected. However one odd thing, I have duplicate entries in that sessions selection list at log in. As it wasn't like that a while ago, and if I did anything it's completely by accident and unawares, I can only guess something happened in an update. Weird. Anyways I'll poke around in ~/old.fluxbox for clues as to what might've caused the Fluxbox no-go, so as to avoid that problem in future. 

@RedSquirrel, in thanks, a link to a wonderful photo of a, well, red squirrel:
[http://outdoors.webshots.com/photo/2144229160100088798MblqUq](http://outdoors.webshots.com/photo/2144229160100088798MblqUq) :D

@mojoman! Availing yourself of your root privileges to compile moonshine from source on Friday nights? lol :lol:

---

### Post by mojoman on 2007-10-10
> **TeaSwigger said:**
> @mojoman! Availing yourself of your root privileges to compile moonshine from source on Friday nights? lol :lol:

hehe, well, it's not the brightest thing I've done but probably not the stupidest either. Come to think of it, that would have been when I tried to get my ubuntu to play monkey audio (.ape) and ended up pulling the plug on my entire system. Alcohol was involved that time as well but, well, I'll leave it for another time. ;-)

Anyway, glad to hear you got it working.

---

### Post by RedSquirrel on 2007-10-10
> **TeaSwigger said:**
> Thank you, mojoman and RedSquirrel I appreciate the help. I'm back in Fluxbox after following the suggestion to rename ~/.fluxbox. Whew! No idea yet what happened. It does call /usr/bin/startfluxbox. I was able to log in to KDE via KDM, which are unaffected. However one odd thing, I have duplicate entries in that sessions selection list at log in. As it wasn't like that a while ago, and if I did anything it's completely by accident and unawares, I can only guess something happened in an update. Weird. Anyways I'll poke around in ~/old.fluxbox for clues as to what might've caused the Fluxbox no-go, so as to avoid that problem in future. 

@RedSquirrel, in thanks, a link to a wonderful photo of a, well, red squirrel:
[http://outdoors.webshots.com/photo/2144229160100088798MblqUq](http://outdoors.webshots.com/photo/2144229160100088798MblqUq) :D



Thanks for the photo. That's a nice one. I'd use it as a wallpaper but I think my cat would probably dig her claws into my monitor. :evil:

Duplicate entries? That's weird. I wonder if you have some duplicate files in /usr/share/xsessions (?). How many different DE/WM environments do you have installed? It's my understanding that installing too many can sometimes cause odd behavior.

As for Fluxbox not starting, it may have been an error in your ~/.fluxbox/startup file. Post it here if you like.

---

### Post by TeaSwigger on 2007-10-15
Hello everybody, 'nother day, 'nother question. :) 

In order to config my Logitech mouse, I used daou's superb 'btnx'. 
[http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

It's daemonic. Mbut it doesn't start with my Flux sessions. As noted before I use KDM to login to my Fluxbox sessions. I can't seem to put the code into ~/.fluxbox/start since it requires super duper sudo powers. My best guess as to how it would start is this command:

```
sudo /etc/init.d/btnx start
```

How might I run this utility in my Fluxbox sessions?

As for my prior no-start problem, there was nothing in my startup file at the time. The only "problem" I found was the previously used wallpaper had been unwittingly removed during a KDE session. If indeed that could account for it. Maybe a permissions goof slipped by me? Didn't see any that were off. Ah well at least I'm happy to say Fluxbox's been working perfectly since. The duplicate entries in KDM remain a puzzle. There are no duplicates in /usr/share/xsessions. But as it appears unrelated, so I'm poking into that at leasure. Appreciated all the help :)

---

### Post by urukrama on 2007-10-17
I'm not sure if this is the general fluxbox thread on here, but I have some questions. I've been using Openbox for a long time now, and wanted to give fluxbox another try. There are, however, a few 'issues' that I always run into. I'm sorry if they have been asked before (they probably have!), but I couldn't find an anwser and thought it wiser to ask the experts. :-)

* Is there an alt-tab on screen dialog, where you can see what apps you have running like in Openbox, icewm, metacity, etc? And if there isn't, is there one planned? This is a serious issue for me, as I like to work without a panel or taskbar, and this allows me to quickly see what is running.

* When I right click on the desktop to get the menu, and then do not click on any menu entry, but click on an open window, the menu does not dissapear (as it does in Openbox, Icewm and Xfce), and I have to click back on the desktop or on a menu entry. Sometimes only a submenu remains visible (with the main menu gone). I've had this several times when trying to switch themes/styles: the switch was succesful, but the styles submenu remains visible, separate from the main menu. Is there a setting somewhere that I can change to undo this behaviour?

---

### Post by TeaSwigger on 2007-10-17
> **urukrama said:**
> * Is there an alt-tab on screen dialog, where you can see what apps you have running like in Openbox, icewm, metacity, etc? And if there isn't, is there one planned? This is a serious issue for me, as I like to work without a panel or taskbar, and this allows me to quickly see what is running.

Would HTop in a terminal do? If you haven't try it, give it a go for a bit and see if it'll do. You could set this to open by a keyboard shortcut. For example, I use HTop in the urxvt terminal. To open it I have the following entry in my main menu under "Tasks":

```
[exec] (Task Manager (HTop\)) {urxvt +sb -fn xft:DejaVuSansMono:size=10 -fg black -bg white -e htop}
```

And have the following line in the ~/.fluxbox/keys file:

```
Mod4 t :Exec urxvt +sb -fn xft:DejaVuSansMono:size=10 -fg black -bg white -e htop
```

...which pops up HTop when I type windowskey (Mod4 in Flux's key config) + t. From there I can watch processes, basic resource use stat, and terminate etc any of the processes.

> * When I right click on the desktop to get the menu, and then do not click on any menu entry, but click on an open window, the menu does not dissapear (as it does in Openbox, Icewm and Xfce), and I have to click back on the desktop or on a menu entry. Sometimes only a submenu remains visible (with the main menu gone). I've had this several times when trying to switch themes/styles: the switch was succesful, but the styles submenu remains visible, separate from the main menu. Is there a setting somewhere that I can change to undo this behaviour?

Good question, I wonder too. It's happened to me too but hasn't been a problem; the one it used to stay open on was the backgrounds folder listing, and that I solved by making a series of small background lists, as the small lists behave ok.

---

### Post by yabbadabbadont on 2007-10-18
> **urukrama said:**
> * Is there an alt-tab on screen dialog, where you can see what apps you have running like in Openbox, icewm, metacity, etc? And if there isn't, is there one planned? This is a serious issue for me, as I like to work without a panel or taskbar, and this allows me to quickly see what is running.
Alt-tab will cycle through the open applications (on the current desktop by default) but there is no visual indicator.  However, you could set a hot-key to bring up the workspace menu to get something similar, but not as simple.  (Middle click the desktop to see the menu about which I'm speaking)  You would add something like the following to your ~/.fluxbox/keys file: ```
Mod4 w :WorkspaceMenu
```

> **urukrama said:**
> * When I right click on the desktop to get the menu, and then do not click on any menu entry, but click on an open window, the menu does not dissapear (as it does in Openbox, Icewm and Xfce), and I have to click back on the desktop or on a menu entry. Sometimes only a submenu remains visible (with the main menu gone). I've had this several times when trying to switch themes/styles: the switch was succesful, but the styles submenu remains visible, separate from the main menu. Is there a setting somewhere that I can change to undo this behaviour?
Many of these menu handling bugs have been fixed in the 1.0.0 release and the current SVN code.  If you have not already, you might consider building Fluxbox from source.  RedSquirrel has instructions for doing this as part of his Fluxbox menu customization HowTo thread here: [http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)

---

### Post by BoneSaw on 2007-10-18
so i recently had to install windows for some school stuff, and i put black box on it and loved it. if there was compiz-fusion support i would probably switch my gnome over to flux (it is the linux equivalent correct?)

anyway, what im saying is i love the minimalistic and configurable look, but i love wobbly windows more.

---

### Post by TeaSwigger on 2007-10-18
> **yabbadabbadont said:**
> Alt-tab will cycle through the open applications (on the current desktop by default) but there is no visual indicator.  However, you could set a hot-key to bring up the workspace menu to get something similar, but not as simple.  (Middle click the desktop to see the menu about which I'm speaking)  You would add something like the following to your ~/.fluxbox/keys file: ```
Mod4 w :WorkspaceMenu
```

Gracious! So that's what he meant :oops: Teach me to hold replies 'till after my tea has steeped and I've had my fix of camellia sinensis brew #-o

---

### Post by urukrama on 2007-10-18
Thank you all for the help.

> **yabbadabbadont said:**
> Many of these menu handling bugs have been fixed in the 1.0.0 release and the current SVN code.  If you have not already, you might consider building Fluxbox from source.  RedSquirrel has instructions for doing this as part of his Fluxbox menu customization HowTo thread here: [http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)

I did that first, but something went wrong post installation (I couldn't login without crashing fluxbox) so I went back to the outdated version in the dapper repos. Perhaps I'll give it another try.

The alt-tab issue is still a pity, though. I hope they add something like that in the near future, as it would make fluxbox a lot nicer to use (for me at least).

---

### Post by jviscosi on 2007-10-18
> **urukrama said:**
> The alt-tab issue is still a pity, though. I hope they add something like that in the near future, as it would make fluxbox a lot nicer to use (for me at least).

I agree; I used Openbox for a couple of weeks, mainly because it has the alt-tab dialog.  But I ended up back in Fluxbox.  (I always do.)

The other thing I was irritated about was Fluxbox's insistence on putting KDE tray icons in the slit even when compiled with KDE support disabled.  I finally decided to deal with that one myself, so I tracked down where in the code Flux checks to see if something has a KDE tray icon and hacked it to always return false.  Now my KDE icons are showing up in peksystray where I want them, and all is (almost) right with the world.

---

### Post by urukrama on 2007-10-18
> **jviscosi said:**
> I agree; I used Openbox for a couple of weeks, mainly because it has the alt-tab dialog.  But I ended up back in Fluxbox.  (I always do.)

For me it is always the opposite :p Fluxbox is nice, and has some great themes, but I never feel fully at home in it. Perhaps I should give it more (exclusive) time.

---

### Post by RedSquirrel on 2007-10-18
> **urukrama said:**
> I did that first, but something went wrong post installation (I couldn't login without crashing fluxbox) so I went back to the outdated version in the dapper repos. Perhaps I'll give it another try.

I'm not sure if you were following *my* instructions, but I recently added an extra step to make sure the ~/.fluxbox/startup file runs /usr/local/bin/fluxbox. The one from the repositories is set to run /usr/bin/fluxbox. If you had an old ~/.fluxbox/startup file, you might have to change that line.

Anyway, feel free to post (here or on my thread) if you have any trouble getting a compiled version to work properly.


> **urukrama said:**
>  The alt-tab issue is still a pity, though. I hope they add something like that in the near future, as it would make fluxbox a lot nicer to use (for me at least).

It's amazing what we all get used to. I find that alt-tab window mildly annoying when I see it in other WM/DE. I wouldn't mind this feature in Fluxbox, as long as I could turn it *off*. :grin:

---

### Post by yabbadabbadont on 2007-10-18
> **RedSquirrel said:**
> It's amazing what we all get used to. I find that alt-tab window mildly annoying when I see it in other WM/DE. I wouldn't mind this feature in Fluxbox, as long as I could turn it *off*. :grin:

++

---

### Post by urukrama on 2007-10-18
I got the latest stable version installed and running, using your howto RedSquirrel. Many thanks.

The menu thing is not entirely gone, though, at least not for the middle click (task list) menu...

And switching windows without dialog still feels very weird. :-)

---

### Post by jviscosi on 2007-10-19
> **urukrama said:**
> For me it is always the opposite :p Fluxbox is nice, and has some great themes

Yeah, I've been messing about with tenr's marzipan theme (adding rounded corners, changing the "shade" icon to bring it into line with the other decorations) ... theming is fun!  ;-)

> **urukrama said:**
> but I never feel fully at home in it. Perhaps I should give it more (exclusive) time.

LOL, yes, that's exactly how I feel when I'm using something other than Fluxbox, even OpenBox.  I can't explain it.  I don't even like using Fluxbox as the window manager for a desktop environment (e.g., XFCE) because the DE seems to sully Flux's purity somehow ...

---

### Post by urukrama on 2007-10-19
Is there a way to tie the desktop menu to some keys (Alt+F1)? 

EDIT: found it! Sorry about this. Just change the keys file in /home/USERNAME/.fluxbox and bind whatever keys you want to RootMenu.

---

### Post by TeaSwigger on 2007-10-19
> **urukrama said:**
> Is there a way to tie the desktop menu to some keys (Alt+F1)? 

EDIT: found it! Sorry about this.

Aw don't be sorry for asking any questions, but do post how you did it so others can find answers :)

---

### Post by raeb on 2007-10-19
Awesome thread  :D  Just moved back to ubuntu/fb after being on windows for WAY too long.  I don't even remember why I switched to windows in the first place.  Anyhow, needs more ss.

[[IMG]http://img140.imageshack.us/img140/640/screenytr2.th.png[/IMG]](http://img140.imageshack.us/my.php?image=screenytr2.png)

I'm a minimalist.

---

### Post by mojoman on 2007-10-19
> **raeb said:**
> Awesome thread  :D  Just moved back to ubuntu/fb after being on windows for WAY too long.  I don't even remember why I switched to windows in the first place.  Anyhow, needs more ss.

[[IMG]http://img140.imageshack.us/img140/640/screenytr2.th.png[/IMG]](http://img140.imageshack.us/my.php?image=screenytr2.png)

I'm a minimalist.

Nice theme! What is it? And welcome back...

/mojoman

---

### Post by raeb on 2007-10-19
> **mojoman said:**
> Nice theme! What is it? And welcome back...

/mojoman

Blue Black by endel ([http://endel.deviantart.com/art/Blue-Black-67038775](http://endel.deviantart.com/art/Blue-Black-67038775))
Also made a good orange/black one as well.

---

### Post by yabbadabbadont on 2007-10-19
> **TeaSwigger said:**
> Aw don't be sorry for asking any questions, but do post how you did it so others can find answers :)

I use Control-Escape for this.  It is configured in the ~/.fluxbox/keys file like this:
```
Control Escape :RootMenu
```
That was difficult, wasn't it?  ;)  :D

---

### Post by RedSquirrel on 2007-10-19
> **urukrama said:**
> I got the latest stable version installed and running, using your howto RedSquirrel. Many thanks.

You're welcome. Glad you got it up & running. :)

> **urukrama said:**
>  The menu thing is not entirely gone, though, at least not for the middle click (task list) menu...

I think the menu in Fluxbox just behaves like that. If you open the menu and then click on a window, the menu hangs around until you click on it again, at which point you can make the menu go away by clicking on the desktop or pressing Esc.


> **urukrama said:**
>  And switching windows without dialog still feels very weird. :-)

This has never been an issue for me. My work habits are such that I rarely have more than two windows open on a workspace, so I don't need an alt-tab window. That's just me, though. ;)

---

### Post by jviscosi on 2007-10-20
---- Gutsy Gibbon Upgrade Report ----

I upgraded Xubuntu to Gutsy overnight.  If anyone is interested, everything went pretty smoothly, although I had to tweak a few things:[LIST]
[*]The display came up 800x600.  Fixed by using envy (see below) to get the latest nVidia drivers, then updating the display settings in gnome-control-center.
[*]The version of envy in the repos doesn't work with Gutsy, so I had to get the latest version from the maintainer's website.  I could've installed the nVidia drivers manually but why bother when envy's available?  ;-)
[*][FONT=Courier New]  Option          "Render"          "Enable"
          Option          "Damage"        "Enable"[/FONT]
from Extensions and
    [FONT=Courier New]         Option          "DisableGLXRootClipping" "true"
  Option          "RenderAccel"            "true"
          Option          "AllowGLXWithComposite"  "true"
          Option          "DamageEvents"           "true"[/FONT]
from Screen were removed from xorg.conf by the upgrade.  I put them back.  Not sure if I really needed to do that or not but everything seems to be working fine.
[*]3ddesk (which I like to use to switch desktops) is no longer in the repositories and was removed by the upgrade, so I installed it from source to get it back.
[*]XGL was turned on by default, even in Fluxbox, which seemed to slow things down and also interfered with 3ddesk, so I disabled it by putting an empty file called "disable" in  ~/.config/xserver-xgl.
[*]Peksystray kept crashing.  A recompile fixed it.
[*]The repos contain fluxbox1.0.0, which is cool, except that it overwrote my hacked version of Fluxbox that keeps KDE tray icons out of the slit.  So I updated my hacked version to call itself 1.0.0.5098 and reinstalled it with checkinstall.[/LIST]Obviously a good deal of the above is because I like to do things in a nonstandard fashion, but even so, I only spent an hour or so tweaking after the upgrade itself was finished.  So far everything else is working fine, and Fluxbox is running without a hitch.   Ah, the beauty of Linux!  :-D

---

### Post by RedSquirrel on 2007-10-20
Just to update the menu situation, I installed SVN 5099 today and I noticed this line in the Changelog:

>  *07/10/15:
   * Added OnWindow modifier to keys file (Mark)So I added the following line to my ~/.fluxbox/keys file:
```
OnWindow   Mouse3   :hideMenus
```Seems to work fine. :)

EDIT: There is an issue with that binding. You will not get the menu when you right-click the titlebar. Depending on your usage patterns, setting it to Mouse2 or some other mouse button might be better. Note that if you set it to Mouse1, you won't be able to *move* the window with "click mouse button #1 and drag".

EDIT #2: I'm having some trouble getting fbpager to work with this SVN version as well. I'll have to see what that's all about... :neutral:

---

### Post by yabbadabbadont on 2007-10-20
I went ahead and installed Gutsy using the alternate CD last night.  Bad move on my part...  I knew I should have waited a month like I normally do.  I did the "command line system" install.  Much to my dismay, I discovered that the framebuffer is completely borked in the default kernel.  The only way that I was able to actually see text (instead of just a black screen) was to leave the display at the default 80x25 setting.  I fought it for a couple of hours trying different options and combinations of options.  Then I reinstalled and just did a default Ubuntu install.  X worked fine, good.  OK, hit Control-Alt-F1 to drop to the console.  Black screen.  :x  Allright, disable compiz, good.  Try the console again.  Still blank.  Switch to the nvidia drivers, good.  Still no text console.  Edit xorg.conf to get the monitor settings correct for the proper refresh rate.  I cut and pasted the settings from the backup I had made before the upgrade.  Logout.  Blank screen for 30 seconds or so, then the stupid failsafe crap comes up.  At this point I decide it's time to return to Gentoo for a while.  Anyway, sorry for the rant.

For an actual on-topic comment: Thanks for the info on the newest Fluxbox SVN RedSquirrel.  When I finally get to the point of installing Fluxbox, I'll see if I can remember how to pull an earlier version.

---

### Post by RedSquirrel on 2007-10-21
> **yabbadabbadont said:**
> For an actual on-topic comment: Thanks for the info on the newest Fluxbox SVN RedSquirrel.  When I finally get to the point of installing Fluxbox, I'll see if I can remember how to pull an earlier version.

```
svn checkout [COLOR=Blue]-r 5098 [/COLOR]svn://svn.berlios.de/fluxbox/trunk fluxbox

```

I'll play around with this some more today if I have time. fbpager works fine with my older version. I haven't built one on gutsy recently until I built 5099, so I have rolled all the way back to 5066! I'll do some reading and pull down some older, yet more recent versions and see how things go.

I'll have more to say about my gutsy + Fluxbox experiences a little later. ;)

---

### Post by D-EJ915 on 2007-10-21
> **yabbadabbadont said:**
> I went ahead and installed Gutsy using the alternate CD last night.  Bad move on my part...  I knew I should have waited a month like I normally do.  I did the "command line system" install.  Much to my dismay, I discovered that the framebuffer is completely borked in the default kernel.  The only way that I was able to actually see text (instead of just a black screen) was to leave the display at the default 80x25 setting.  I fought it for a couple of hours trying different options and combinations of options.  Then I reinstalled and just did a default Ubuntu install.  X worked fine, good.  OK, hit Control-Alt-F1 to drop to the console.  Black screen.  :x  Allright, disable compiz, good.  Try the console again.  Still blank.  Switch to the nvidia drivers, good.  Still no text console.  Edit xorg.conf to get the monitor settings correct for the proper refresh rate.  I cut and pasted the settings from the backup I had made before the upgrade.  Logout.  Blank screen for 30 seconds or so, then the stupid failsafe crap comes up.  At this point I decide it's time to return to Gentoo for a while.  Anyway, sorry for the rant.

For an actual on-topic comment: Thanks for the info on the newest Fluxbox SVN RedSquirrel.  When I finally get to the point of installing Fluxbox, I'll see if I can remember how to pull an earlier version.
see here: [http://ubuntuforums.org/showthread.php?t=258484&highlight=framebuffer+gutsy&page=6](http://ubuntuforums.org/showthread.php?t=258484&highlight=framebuffer+gutsy&page=6)

---

### Post by RedSquirrel on 2007-10-21
> **yabbadabbadont said:**
> I did the "command line system" install.  Much to my dismay, I discovered that the framebuffer is completely borked in the default kernel.

I finally got around to fixing the framebuffer issue on my system. I've known about this one for a while, but I only got around to it today. While I was looking up something else on Launchpad, I stumbled upon this lengthy discussion and figured I'd put the fix off long enough:

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910)

The instructions that D-EJ915 linked to are the same ones I used, except I used: 

```
sudo update-initramfs -u -k all -v
```because I have a number of kernels lying around and I wanted to see what was happening while it performed the update. ;)

I have been using gutsy on and off for about a month (installed Tribe5 server CD and I have been keeping up to date). Things are working reasonably well, except for the following:

1) Debian menu seems to be "in transition" and is missing some entries (Firefox, for example). I should probably look into this in more depth, but I don't really use the thing anyway. I have my own custom menu and my keyboard shortcuts to access my applications.

2) Fluxbox package: XShape extension support was left out. Not sure why. Icons in toolbar (iconbar) are surrounded by a black square, which looks ugly.

3) I'm seeing some strange artifacts in Firefox. For example, the outline around the location area sometimes has a break in it. On these forums, sometimes the lines around code boxes etc. disappear on the top and/or bottom. I have not seen this before.

---

### Post by yabbadabbadont on 2007-10-21
Good info, but if they are going to screw up something basic like framebuffer support in the kernel, then it's time to head to other pastures.  (Which I have already done. ;))  It had been so long since I had used Gentoo that I was surprised that I remembered all the tricks.  It wouldn't even have taken too long if it weren't for the glibc update that was waiting after the initial install.  I'm playing around with the latest and greatest Openbox at the moment. (It had the fewest build dependencies)  I'm working on modifying fluxbox-generate_menu so that it will output an Openbox xml submenu that can be included in the main OB menu.

---

### Post by RedSquirrel on 2007-10-21
> **yabbadabbadont said:**
> Good info, but if they are going to screw up something basic like framebuffer support in the kernel, then it's time to head to other pastures.  (Which I have already done. ;))  

Agreed. I have a feisty/gutsy dual boot right now. I wanted to keep feisty around in case gutsy didn't impress me. The only issue I have in feisty is the "Save As" dialog GTK+ bug. A month ago, I came very close to going with Gentoo or Arch, but settled on testing gutsy. Might be time for something new...


> **yabbadabbadont said:**
> It wouldn't even have take too long if it weren't for the glibc update that was waiting after the initial install.  

Which is one of the things holding me back from Gentoo. I don't want to push this old box too hard at the moment. (...but I could change my mind at any time... :)).

> **yabbadabbadont said:**
> I'm playing around with the latest and greatest Openbox at the moment. (It had the fewest build dependencies)  I'm working on modifying fluxbox-generate_menu so that it will output an Openbox xml submenu that can be included in the main OB menu.

Neat.

---

### Post by cknight on 2007-10-22
> **yabbadabbadont said:**
> Good info, but if they are going to screw up something basic like framebuffer support in the kernel, then it's time to head to other pastures.  

Pray tell, what is framebuffer support?  Is this only broken in the light-weight server install of Gutsy or the Ubuntu/Kubuntu/Xubuntu versions too?  What impact on fluxbox does this have?

On another tangent completely, what would you say are the differences between Openbox and Fluxbox?  How do the two compare?  I'm interested in trying Openbox one day, but haven't got any time at the moment to play around with it.

---

### Post by TeaSwigger on 2007-10-22
RedSquirrel, yabbadabbadont, are you two going to stick around? Might I find you elsewhere? Not many here to talk Fluxbox with elsewise. :| A shame they messed up that bad. Glad I'm sitting out the "upgrade." I keep getting this impression there's too much attention on "features" and not enough on fundamentals. Heck with the latest window wobble, I can't even use my old scanner yet. But it seems as much of a response to what people are clamboring about as anything from devs. At least that's the initial impressions I've had. Not sure I'm ready for Gentoo though, I've heard it's demanding of time and CPUs in a lot of compiling and recompiling etc?

---

### Post by RedSquirrel on 2007-10-22
> **cknight said:**
> Pray tell, what is framebuffer support?  Is this only broken in the light-weight server install of Gutsy or the Ubuntu/Kubuntu/Xubuntu versions too?  What impact on fluxbox does this have?

[http://en.wikipedia.org/wiki/Linux_framebuffer](http://en.wikipedia.org/wiki/Linux_framebuffer)

I have only installed the server edition, but yabbadabbadont wrote above that it was an issue in the full Ubuntu edition as well.

It has no effect on Fluxbox. (So, yes, we're off-topic. :evil:)


> **cknight said:**
> On another tangent completely, what would you say are the differences between Openbox and Fluxbox?  How do the two compare?  I'm interested in trying Openbox one day, but haven't got any time at the moment to play around with it.

Openbox has a little less eye candy and is slightly lighter than Fluxbox. It also has a different setup for configuration. The best way to evaluate it is, as always, to try it yourself. ;)

---

### Post by RedSquirrel on 2007-10-22
> **TeaSwigger said:**
> RedSquirrel, yabbadabbadont, are you two going to stick around? Might I find you elsewhere? Not many here to talk Fluxbox with elsewise. :| A shame they messed up that bad. Glad I'm sitting out the "upgrade." I keep getting this impression there's too much attention on "features" and not enough on fundamentals. Heck with the latest window wobble, I can't even use my old scanner yet. But it seems as much of a response to what people are clamboring about as anything from devs. At least that's the initial impressions I've had. Not sure I'm ready for Gentoo though, I've heard it's demanding of time and CPUs in a lot of compiling and recompiling etc?

I'll be around.

I think it's a good idea to wait a month before using gutsy. By then, the problems may be fixed or at least the workarounds will be well-known.

I agree with your impression of features vs. fundamentals, but it's still a nice distro IMO. I like that I can go from a blank hard drive to a functional system in less than half an hour. I'm just not impressed with the fluxbox package on gutsy and I'm glad I can build my own.  People who don't like to compile their own will be stuck with an inferior Fluxbox, which is a shame. The fact that the default (Debian) menu is incomplete doesn't help either. :(

Gentoo is extremely flexible but it does require a fair bit of compiling, especially at the beginning.

---

### Post by yabbadabbadont on 2007-10-22
> **RedSquirrel said:**
> Which is one of the things holding me back from Gentoo. I don't want to push this old box too hard at the moment. (...but I could change my mind at any time... :)).


Just wait until they release 2007.1 sometime in November.  At that point, all the stage files will be rebuilt with the current (at that time) stable packages.  I was planning on doing that myself, but decided that I might as well try out Gutsy in the mean time.  I would usually have waited a month to try Gutsy, but it seemed silly since I was going to switch back to Gentoo in a month anyway.  Gutsy just convinced me to do it sooner.  By the way, if you decide not to wait, it is best to upgrade glibc immediately after install, since you will need to rebuild the entire system afterwards.  (and that is when you have the fewest packages installed)  I just let my "emerge -e system && emerge -e world" run overnight.  It took six or seven hours.  I spend most of my time during the installation configuring my kernel and USE flags.  When stuff is building, I just walk away and watch a movie or something.  :D

---

### Post by yabbadabbadont on 2007-10-22
> **TeaSwigger said:**
> RedSquirrel, yabbadabbadont, are you two going to stick around? Might I find you elsewhere? Not many here to talk Fluxbox with elsewise. :| A shame they messed up that bad. Glad I'm sitting out the "upgrade." I keep getting this impression there's too much attention on "features" and not enough on fundamentals. Heck with the latest window wobble, I can't even use my old scanner yet. But it seems as much of a response to what people are clamboring about as anything from devs. At least that's the initial impressions I've had. Not sure I'm ready for Gentoo though, I've heard it's demanding of time and CPUs in a lot of compiling and recompiling etc?

I'll be around.  Especially in the Cafe Games forum.  :D

If you like to talk about fluxbox/openbox/e17/dwm and such, you might want to browse around the Gentoo forums.  For E17 especially, there are some massive threads.  They close them and start new ones whenever they get pretty long.  They are on part 5 now.  ;)
[E17 is coming? (part 5)](http://forums.gentoo.org/viewtopic-t-529895-highlight-.html)

---

### Post by TeaSwigger on 2007-10-22
Ah, just peeked in and saw there's life at Fluxbuntu.org! :D 

Maybe they delayed to bugfix gutsy a bit first...?

@ RedSquirrel & yabbadabbadont - glad to see you two are sticking around. It wouldn't be the same without you two. :) Same handle at gentoo, yabbadabbadont?

---

### Post by yabbadabbadont on 2007-10-23
> **TeaSwigger said:**
> Same handle at gentoo, yabbadabbadont?

Guilty as charged.  ;)

I've been yabbadabbadont there since March 13, 2003.  (strangely enough it was a Thursday and not a Friday...  :lol:)

---

### Post by mojoman on 2007-10-23
> **yabbadabbadont said:**
> Guilty as charged.  ;)

I've been yabbadabbadont there since March 13, 2003.  (strangely enough it was a Thursday and not a Friday...  :lol:)

I've been thinking about giving Gentoo a try. Right now I got four partitions I use for OS (Feisty, Lenny and XP) and one that I haven't decided what to do with yet but Gentoo is the likely candidate. If only I could get my girlfriend to switch from photoshop to gimp I'd have one more OS partition to play with...

/mojoman

---

### Post by TeaSwigger on 2007-10-23
> **mojoman said:**
> I've been thinking about giving Gentoo a try. Right now I got four partitions I use for OS (Feisty, Lenny and XP) and one that I haven't decided what to do with yet but Gentoo is the likely candidate. If only I could get my girlfriend to switch from photoshop to gimp I'd have one more OS partition to play with...

/mojoman

Oh Lenny's an OS! Right well that does make an earlier post read a bit different :redface:

Seriously, if I may, what version of Photoshoppy does she use / need? I'm running v7 in WINE as I distract- I mean, visit right now.

---

### Post by RedSquirrel on 2007-10-23
> **yabbadabbadont said:**
> Just wait until they release 2007.1 sometime in November. At that point, all the stage files will be rebuilt with the current (at that time) stable packages. ... 

That sounds like a good approach for me. I'll see if I can wait for it.


> **yabbadabbadont said:**
> By the way, if you decide not to wait, it is best to upgrade glibc immediately after install, since you will need to rebuild the entire system afterwards. (and that is when you have the fewest packages installed)

Thanks for the reminder. That's just the sort of thing that might have slipped my mind if I wasn't paying enough attention when putting the stuff together. ;)


On topic: I just pulled down the Fluxbox SVN 5109 source. Judging by the notes in the Changelog, development is going well. Some interesting stuff in there. I probably won't build it until tomorrow (by which time there may well be another update :grin:).

---

### Post by mojoman on 2007-10-24
> **TeaSwigger said:**
> Oh Lenny's an OS! Right well that does make an earlier post read a bit different :redface:

Seriously, if I may, what version of Photoshoppy does she use / need? I'm running v7 in WINE as I distract- I mean, visit right now.

I've never used Wine but I've been thinking about it. I might just have a look. As for Lenny, well, it's the Debian testing so I guess it's a version of an OS. 

On-topic: How come there are no system styles available when you compile fluxbox from source?  Now, I already had config-files and my own themes but what happens if there isn't any in the users directory?

/mojoman

---

### Post by crocd on 2007-10-24
My previous fluxbox desktop on feisty 64 bit with Noir theme. I am running gutsy at the moment but I am having keyboard issues it seems to start adding spaces for no reason and wont stop. On reboots my resolution goes belly up and I have to reinstall the nvidia driver.

I have some minor issues but I hope they get ironed out over the next couple of days. I reverted from 64 bit to 32 as a lot of flash etc wasn't working and I needed some stuff to work remotely from home.

My eterm isn't transparent which I hope to sort out soon.

---

### Post by yabbadabbadont on 2007-10-24
> **mojoman said:**
> On-topic: How come there are no system styles available when you compile fluxbox from source?

There are system styles installed when you build from source.  If they aren't showing up in your menu, then it is because you have your menu configured to look in the wrong place for them.  ;)

If you didn't specify the "--prefix" option when you ran configure, then the styles will be in /usr/local/share/fluxbox/styles.  Your menu probably is looking in /usr/share/fluxbox/styles.  Or it could be the other way around if you previously had it in /usr/local but have reconfigured a new version for /usr.  Check your ~/.fluxbox/menu for stylesdir entries and see where they are pointing.

---

### Post by yabbadabbadont on 2007-10-25
@RedSquirrel:

I you decide to try Gentoo at some point, let me know.  I created a SVN version of the fluxbox-1.0.0 ebuild.  (I used the traditional versioning for SVN/CVS ebuilds.  fluxbox-1.0.9999)  That way even the SVN version of fluxbox is built and installed using portage, complete with all dependency handling and USE flag configuration of the build options.  It was surprisingly easy since there already was  a subversion eclass file in the portage tree.

---

### Post by jviscosi on 2007-10-25
> **RedSquirrel said:**
> EDIT #2: I'm having some trouble getting fbpager to work with this SVN version as well. I'll have to see what that's all about... :neutral:

I actually filed a bug report about this and an issue with stale icons in the fbpanel and perlpanel taskbars that were hanging around after apps were closed or sent to the system tray.  The stale icons bug was fixed almost immediately (rev 5113 I think).  fbpager still doesn't work for me (it's not showing any windows) but bbpager does so I switched to that for now.

---

### Post by mojoman on 2007-10-25
> **yabbadabbadont said:**
> There are system styles installed when you build from source.  If they aren't showing up in your menu, then it is because you have your menu configured to look in the wrong place for them.  ;)

If you didn't specify the "--prefix" option when you ran configure, then the styles will be in /usr/local/share/fluxbox/styles.  Your menu probably is looking in /usr/share/fluxbox/styles.  Or it could be the other way around if you previously had it in /usr/local but have reconfigured a new version for /usr.  Check your ~/.fluxbox/menu for stylesdir entries and see where they are pointing.

Yup, that did it. Thanks!

---

### Post by RedSquirrel on 2007-10-25
> **yabbadabbadont said:**
> @RedSquirrel:

I you decide to try Gentoo at some point, let me know.  I created a SVN version of the fluxbox-1.0.0 ebuild.  (I used the traditional versioning for SVN/CVS ebuilds.  fluxbox-1.0.9999)  That way even the SVN version of fluxbox is built and installed using portage, complete with all dependency handling and USE flag configuration of the build options.  It was surprisingly easy since there already was  a subversion eclass file in the portage tree.

I'm probably going to hold off for a bit, but thanks for mentioning this.

I'm back to playing with gutsy. The newest firefox package seems better than the old one, but I'm still testing it out.

I went a bit nuts and installed IceWM, Openbox, and Xfce (and some of its goodies). It's kind of fun to play with other things once in a while. :)

---

### Post by RedSquirrel on 2007-10-25
> **jviscosi said:**
> I actually filed a bug report about this and an issue with stale icons in the fbpanel and perlpanel taskbars that were hanging around after apps were closed or sent to the system tray.  The stale icons bug was fixed almost immediately (rev 5113 I think).  fbpager still doesn't work for me (it's not showing any windows) but bbpager does so I switched to that for now.

I installed 5111 yesterday and it had some issues with the toolbar. The focus of the iconbar was messed up.

I just pulled down 5115, but I may hold off for a few days since I've acquired some new toys to play with. ;)

Thanks for the tip about bbpager. I might try that.

---

### Post by yabbadabbadont on 2007-10-25
5115 is working fine here with fbpanel.

---

### Post by TeaSwigger on 2007-10-25
I've a good friend who swears by gentoo and I am impressed with its sophistication, so who knows; when/if I get far enough "advanced" on things, we may all end up there lol

> **RedSquirrel said:**
> I went a bit nuts and installed IceWM, Openbox, and Xfce (and some of its goodies). It's kind of fun to play with other things once in a while. :)

Yeah! Same here. I haven't tried openbox, but I've been taking windowmaker, xfce, gnome and Icewm for periodic spins in addition to KDE and Fluxbox. No question that I'm continuing to be partial to Fluxbox - it's set as default - but it's a lot of fun seeing & experiencing the amazing choices. 

I'd installed IceWM for my sis and she likes it. I think it's a very solid feeling wm, and with a decent theme and options I'm sure it's a fine primary wm. One thing though, I'd compiled 1.3.1 and discovered the tray won't work reliably. The old 1.2.30 in the repos works fine though. The tradeoff: in 1.3.1, its own background setter icewmbg, actually scales a wallpaper in nice quality. On the older builds I have to use feh or something as a workaround 'cause the wallpaper would look terrible. Ah well. Otherwise rock solid. 

Good thing IceWM's app menu opens with a right click on the desktop, 'cause I find myself in a firm habit suddenly of clicking on that desktop for my "start menu." Uh oh. Maybe I'm getting hooked on Fluxbox... :p

---

### Post by yabbadabbadont on 2007-10-26
> **yabbadabbadont said:**
> 5115 is working fine here with fbpanel.

Spoke too soon.  It works fine with fbpanel, but I removed fbpanel and configured it to use the provided toolbar.  Mouse-wheeling on the iconbar no longer switches the workspace, while it still does on the desktop.  I filed a bug about it in the sourceforge fluxbox bug tracker.

Edit: Well, the bug was closed with the comment that "It is in the keys file now."  That's all, no explanation or anything.  So I read through the fluxbox manpage, very slowly and carefully.  Hmm.  OnDesktop is now a keys file modifier used with mouse# (# is button number).  So I check out my keys file.  fluxbox-update_configs has added OnDesktop entries so that the desktop mouse wheeling works.  It has also added two more lines using an undocumented option, OnWindow.  OK, now I dig into the source for fluxbox-update_configs.  It was supposed to add two more lines to my keys file that use the, of course, undocumented option, OnToolbar...  The code looks at session.configVersion in ~/.fluxbox/init to decide whether or not it should add entries to the keys file.  It didn't in my case.  I can only surmise that my configVersion was already at a level at which it assumes that the entries are already in the keys file.  It may have been because of using frequent svn updates.  My config got updated when OnDesktop and OnWindow were introduced, but before OnToolbar.  (or something strange like that)

Anyway, just in case someone else gets hit with this, here are the entries that are supposed to be in the keys file now.
```
OnDesktop Mouse1 :HideMenus
OnDesktop Mouse2 :WorkspaceMenu
OnDesktop Mouse3 :RootMenu
OnDesktop Mouse4 :PrevWorkspace
OnDesktop Mouse5 :NextWorkspace

OnToolbar Mouse4 :PrevWorkspace
OnToolbar Mouse5 :NextWorkspace

OnWindow Mod1 Mouse1 :StartMoving
OnWindow Mod1 Mouse3 :StartResizing BottomRight

```
NOTE: you may want to swap the mouse4 and mouse5 actions if you want the wheel to change the workspace in reverse order.

---

### Post by TeaSwigger on 2007-10-27
Presently downloading Fluxbuntu 7.10RC and hope to try & install it tomorrow :)

---

### Post by jviscosi on 2007-10-28
Has anyone else found that on the latest versions of Fluxbox from SVN, under ClickFocus, you have to click on the title bar of a window to focus it?  I can click anywhere in a window to raise it, but that window doesn't get focus unless I click in the title bar or on the tab (I use external tabs).  MouseFocus is working fine, and reverting to an older SVN version makes ClickFocus work as I'm accustomed.

I know they added those new OnWindow actions in keys so I'm wondering if I would need to add some additional OnWindow event in keys for Mouse1.  I haven't found any documentation though.

---

### Post by yabbadabbadont on 2007-10-28
Yes, I have the same behavior in svn 5115.  As for documentation on the OnWindow and OnToolbar keys file modifiers, there isn't any...  see my previous ranting post.  ;)

I can only suggest that you file a bug about it.  Hopefully, the devs will actually tell you how to fix it (assuming that it is a new config issue) instead of just saying, "It's in the keys file now", which is the response that I got.

---

### Post by jviscosi on 2007-10-28
Filed.  We'll see what happens.  Meanwhile it's not (quite) annoying enough to make me revert to an older SVN.

---

### Post by yabbadabbadont on 2007-10-28
They also appear to have broken the focused/unfocused style handling for the title text of entries in the iconbar.  Sometimes the focused entry uses the correct style element and sometimes it doesn't.  For the time being, I re-installed the latest and greatest Openbox and am playing with it again.

---

### Post by RedSquirrel on 2007-10-28
I noticed that focus issue with 5111 and like you said it's still present in 5115. fbpager still doesn't work (with 5115). If I run it normally, it doesn't even show up. If I run it in withdrawn state (-w), it shows up, but it doesn't show any windows. :( I'm using the stable tarball for now.

---

### Post by yabbadabbadont on 2007-10-28
Yeah.  There seem to be a lot more issues with the svn commits recently.  Used to be that they would pretty much work flawlessly.  I guess the pace of work on fluxbox has increased (a good thing) and these are the side effects.

Off-topic: You wouldn't happen to know of an LCD monitor that you could recommend for under $200 (US) would you?

---

### Post by jviscosi on 2007-10-29
Yeah, I've reverted to 5089 for now, before all the window stuff got broken.  I think most of the recent trouble is probably attributable to the addition of the OnWindow and OnTaskbar events, which are good from a customizability standpoint but seem to represent a fairly major architectural shift, the repercussions of which are still percolating through the rest of the code.  If I were doing the versioning, I would probably have branched this into a minor (1.1.x) rather than a revision (1.0.x).

Yabbadabbadont, I've been really happy with my HP w2207 monitor.  Amazon is selling the 19" version (w1907) for $214, which is not quite under $200, but is pretty close.

---

### Post by RedSquirrel on 2007-10-29
> **yabbadabbadont said:**
> Off-topic: You wouldn't happen to know of an LCD monitor that you could recommend for under $200 (US) would you?

Not really. Not for under $200. I would think for that price you would be looking at a non-brand-name monitor or maybe a 17", but you never know, there might be some deals out there...

About six months ago, I picked up a ViewSonic vx922, which is a 19" (5:4). I've been quite happy with it. It was in the "around $300" category, however. ;) (...and I'm not sure you can even find it now. Companies seem to be pushing mostly widescreen.)

I also tried the ViewSonic vx2235wm (22" widescreen). The screen size was nice, but the viewing angles didn't impress me. I've seen some ridiculous deals on this one here and there. You might want to check it out for yourself.

I also tried the w1907 that jviscosi mentioned (or one very similar to it), but I returned it after a couple of days. I didn't like the 19" widescreen. It feels too narrow for me.

I finally settled on the vx922. I didn't really want to spend a fortune on  a monitor, and this one suited me in terms of price and quality.

---

### Post by RedSquirrel on 2007-10-29
Does anyone have any thoughts on the new themes that are included with the installation? I wasn't overwhelmed by them at first, but I have been using a slightly modified zimek_green lately.

---

### Post by jviscosi on 2007-10-29
> **RedSquirrel said:**
> I also tried the w1907 that jviscosi mentioned (or one very similar to it), but I returned it after a couple of days. I didn't like the 19" widescreen. It feels too narrow for me.

Yeah, I actually never considered the w1907 when I was shopping.  I had planned to get the w2007 but a friend talked me into the w2207 and I'm glad he did.  The extra few inches are remembered long after the extra few (or not so few) dollars are forgotten.  ;-)

---

### Post by jviscosi on 2007-10-29
> **yabbadabbadont said:**
> Yes, I have the same behavior in svn 5115.  As for documentation on the OnWindow and OnToolbar keys file modifiers, there isn't any...  see my previous ranting post.  ;)

I can only suggest that you file a bug about it.  Hopefully, the devs will actually tell you how to fix it (assuming that it is a new config issue) instead of just saying, "It's in the keys file now", which is the response that I got.

I got the response "works for me" with a request for more information.  I thought I had provided a good deal of information in the initial bug report but I supplied what more I could think of.  We'll see what happens.  Yabba, do you use internal or external tabs?

---

### Post by jviscosi on 2007-10-29
> **RedSquirrel said:**
> Does anyone have any thoughts on the new themes that are included with the installation? I wasn't overwhelmed by them at first, but I have been using a slightly modified zimek_green lately.

That's a nice theme -- the color combination is easy on the eyes.  I'm still using my modded version of tenr's Marzipan theme, but I never keep a theme very long.  I'll check out some of the new themes when I start getting bored with Marzipan.

---

### Post by yabbadabbadont on 2007-10-30
> **jviscosi said:**
>  Yabba, do you use internal or external tabs?

Internal normally.  I'm using Openbox at the moment.

---

### Post by yabbadabbadont on 2007-10-30
> **RedSquirrel said:**
> Does anyone have any thoughts on the new themes that are included with the installation? I wasn't overwhelmed by them at first, but I have been using a slightly modified zimek_green lately.

I think my initial response was, meh.  ;)  I use tenr's Trivial theme when I'm in fluxbox.

---

### Post by yabbadabbadont on 2007-10-30
> **RedSquirrel said:**
> Not really. Not for under $200. I would think for that price you would be looking at a non-brand-name monitor or maybe a 17", but you never know, there might be some deals out there...

About six months ago, I picked up a ViewSonic vx922, which is a 19" (5:4). I've been quite happy with it. It was in the "around $300" category, however. ;) (...and I'm not sure you can even find it now. Companies seem to be pushing mostly widescreen.)

I also tried the ViewSonic vx2235wm (22" widescreen). The screen size was nice, but the viewing angles didn't impress me. I've seen some ridiculous deals on this one here and there. You might want to check it out for yourself.

I also tried the w1907 that jviscosi mentioned (or one very similar to it), but I returned it after a couple of days. I didn't like the 19" widescreen. It feels too narrow for me.

I finally settled on the vx922. I didn't really want to spend a fortune on  a monitor, and this one suited me in terms of price and quality.

My day started with my old monitor almost constantly flickering like the refresh rate was set to 60Hz.  (It was at 75Hz)  This is "usual" until it has had time to warm up a bit.  What wasn't usual, is that the flickering not only didn't stop, but became worse as time went on...  I guess 10 years is too much to ask of a CRT.  It sure was a workhorse though.  I looked around a bit, and found that I could get an eMachines 17" CRT for $120 at my local Circuit City.  It lasted about two hours.  It had a decent set of geometry controls, but nothing I did would remove a pronounced bowing of the top edge of the screen.  I could get the other three sides straight, just not the top.  :(  Back it went to the store.  I looked around a bit and finally decided on a 19" Samsung SyncMaster 932B.  $250 later (ouch), I'm playing with my new shiny.  :D  This thing sure is bright, even with the brightness and contrast both reduced to 30%.  I did some retroactive review research and it appears that I didn't make a bad choice for my needs.

Thanks to the both of you for your suggestions.  Now I just have to figure out the correct settings for my ~/.fonts.conf for this LCD.  (I just recently got them right for my old monitor.  :lol:)

Edit: OK, both of them at 20% looks good.  One thing down, a dozen to go.  ;)

---

### Post by jviscosi on 2007-10-30
FWIW, my research is indicating that (at least on my machine) the click-focus issue kicks in once a terminal has been loaded.  Before a terminal is open, it works the way it used to.  Once a terminal is loaded, clicking in the body of another window doesn't transfer focus.  This persists until all the windows are closed, at which point focus starts working normally, until the next time a terminal opens.  (I added all this to the bug report, of course.)

---

### Post by yabbadabbadont on 2007-10-30
> **jviscosi said:**
> FWIW, my research is indicating that (at least on my machine) the click-focus issue kicks in once a terminal has been loaded.  Before a terminal is open, it works the way it used to.  Once a terminal is loaded, clicking in the body of another window doesn't transfer focus.  This persists until all the windows are closed, at which point focus starts working normally, until the next time a terminal opens.  (I added all this to the bug report, of course.)

I hadn't really thought about it, but I believe that was the same thing I was seeing.

---

### Post by RedSquirrel on 2007-10-30
> **jviscosi said:**
> Yeah, I actually never considered the w1907 when I was shopping. I had planned to get the w2007 but a friend talked me into the w2207 and I'm glad he did. The extra few inches are remembered long after the extra few (or not so few) dollars are forgotten. ;-)

*Not so few* dollars. :) It was quite a big difference when I was shopping. I imagine they've come down somewhat.


> **jviscosi said:**
> That's a nice theme -- the color combination is easy on the eyes.  I'm still using my modded version of tenr's Marzipan theme, but I never keep a theme very long.  I'll check out some of the new themes when I start getting bored with Marzipan.

Nice screenshot. I do find the zimek-green is easy on the eyes. I'm even using its solid color backgound. I like wallpapers, but I find a solid color is less distracting.

---

### Post by RedSquirrel on 2007-10-30
> **yabbadabbadont said:**
> I use tenr's Trivial theme when I'm in fluxbox.

I like that one too. I normally use a blue or black style, but I'm enjoying the green for now. I used a modified Noir style for months.


> **yabbadabbadont said:**
> I looked around a bit and finally decided on a 19" Samsung SyncMaster 932B.  $250 later (ouch), I'm playing with my new shiny.  :D  This thing sure is bright, even with the brightness and contrast both reduced to 30%.  I did some retroactive review research and it appears that I didn't make a bad choice for my needs.

That looks like a nice one. I used a 15" CRT for almost seven years and it still  works. I just figured my eyes would appreciate something larger. Someday, I'll setup dual monitors but for now the 15" is taking a well-deserved break. ;)

I found it was quite an adjustment moving from CRT to LCD and I've read that this is quite common. I had an anti-glare screen attached to the old CRT which made the screen darker and added more contrast. That made the adjustment to LCD even more challenging. I managed to make the LCD look nice with a bit of fiddling with its settings.


> **yabbadabbadont said:**
> Now I just have to figure out the correct settings for my ~/.fonts.conf for this LCD.  (I just recently got them right for my old monitor.  :lol:)

Yeah, fonts can be a pain. On that subject, I solved the issue I was having with the weird graphical artifacts in gutsy's firefox. It was my fault, not gutsy's. I was playing with the DPI settings (I set mine in ~/.Xresources) and I had it set to 100 instead of the customary 96. I changed it back to 96 and all is well. :grin:

---

### Post by yabbadabbadont on 2007-10-30
> **RedSquirrel said:**
> Yeah, fonts can be a pain. On that subject, I solved the issue I was having with the weird graphical artifacts in gutsy's firefox. It was my fault, not gutsy's. I was playing with the DPI settings (I set mine in ~/.Xresources) and I had it set to 100 instead of the customary 96. I changed it back to 96 and all is well. :grin:

I knew enough to edit my xorg.conf and comment out all the CRT related settings so that the nvidia driver would auto-select from the EDID info in the LCD.  That worked out fairly nicely.  The logs show that the nvidia driver is calculating the DPI to be 85x86 for the native, 1280x1024, resolution.  I set it to 86x86 in the Monitor section of my xorg.conf to override this.  (fonts look better with square dpi settings)  I think I need to bump it up to 96 though, as the fonts are *tiny*...  and my eyes aren't getting any younger.  :lol:

I managed to get very nicely rendered fonts using a combination of custom patches for cairo and libXft and version 2.3.4 of freetype.  The new sub-pixel rendering code in cairo and libXft made for an amazing difference.

---

### Post by carlos1992 on 2007-10-30
hey how do i install fluxbox with Ubuntu 7.10 and i don't wanna loose ubuntu, how do you do that thing just install the enviroment

---

### Post by yabbadabbadont on 2007-10-30
> **carlos1992 said:**
> hey how do i install fluxbox with Ubuntu 7.10 and i don't wanna loose ubuntu, how do you do that thing just install the enviroment

If you just want the version from the official Ubuntu repositories: ```
sudo apt-get install fluxbox
```

Otherwise, follow the instructions linked to by RedSquirrel's signature.

---

### Post by carlos1992 on 2007-10-30
ok i did so know how do i use it (i feel stupid:confused::confused:) do i start terminal or control+alt+f1...f6
im'a give a try and see what happen:lolflag:

---

### Post by -grubby on 2007-10-31
log out. Under "session" in the login manager select "fluxbox"

---

### Post by b4d on 2007-11-02
Hi, I am new to Ubuntu but old at fluxbox, so I dropped by to post my screenie.

[[img]http://shrani.si/t/M/oj/2FVoGKxg/snapshot21.jpg[/img]](http://shrani.si/?M/oj/2FVoGKxg/snapshot21.png)

Conky, aterm, ...

---

### Post by carlos1992 on 2007-11-09
hey the last screenshot was fluxbox how do you get that desktop the borders look really cool

---

### Post by b4d on 2007-11-10
Depends which borders do you mean. If you mean pure window decoration, there is none, i've mapped this in keys file:
```
Mod1 d                    :ToggleDecor
```
so pressing alt+d toggles window decoration on/off.

The other thing is the terminal decoration, that blue line, that's achieved with the use of zsh shell instead of bash, if you need .zshrc, I can post it.

Oh, the flux theme is sepiroth, form the official page, a little modified though.

---

### Post by semperfiguy on 2007-11-10
I have a couple questions about compiling the svn.  I followed the steps on the fluxbox page to pull the svn down, then ./configure make and checkinstall.  That all worked fine.

I had a little difficulty getting it to work with GDM and that brings me to my first question. 

In the /usr/share/xsessions folder I made a fluxbox.desktop file but in it it always will run from /home/semperfiguy/.fluxbox/startup  Is there a way I can change it to make it run from which ever user signs in .fluxbox/startup file?

And the second question.  It messes up all the fonts and everything from when it was running the ubuntu repo version of fluxbox.  Since I backed up the .fluxbox directory before I did the install All the settings should be the same as before right?  So is there something I was supposed to compile in?

and finally the package manager is telling me there is a new version of fluxbox out 1.0.0.  How do I turn that off.  Thanks in advance

Edit:  Answered the first question.. should of looked first.

---

### Post by RedSquirrel on 2007-11-10
> **semperfiguy said:**
>  In the /usr/share/xsessions folder I made a fluxbox.desktop file but in it it always will run from /home/semperfiguy/.fluxbox/startup  Is there a way I can change it to make it run from which ever user signs in .fluxbox/startup file?

You need to use /usr/local/bin/startfluxbox in the Exec line in the fluxbox.desktop file.


> **semperfiguy said:**
>  And the second question.  It messes up all the fonts and everything from when it was running the ubuntu repo version of fluxbox.  Since I backed up the .fluxbox directory before I did the install All the settings should be the same as before right?  So is there something I was supposed to compile in?

That's odd. 

The default ./configure should be sufficient. I haven't seen any font issues related to the SVN version. I'm currently using the stable version (1.0.0) on Arch and I haven't built an SVN version since 5115 since there were some focus issues. It's possible something may have changed with SVN version. Not sure.


> **semperfiguy said:**
>  and finally the package manager is telling me there is a new version of fluxbox out 1.0.0.  How do I turn that off.  

There might be a better way, but I made the SVN deb version 1.0.999 instead of 1.0.0.

---

### Post by semperfiguy on 2007-11-10
Yup I got the first part right after I posted. I was following a different guide at first and they used the wrong way.  

The fonts I was trying to use are the artwiz fonts, I dont know if that has anything to do with it.  The fonts from the system styles are fine.  Its just the other fonts I guess that have trouble. 

Thank you for your help.

---

### Post by RedSquirrel on 2007-11-10
> **semperfiguy said:**
> The fonts I was trying to use are the artwiz fonts, I dont know if that has anything to do with it.  The fonts from the system styles are fine.  Its just the other fonts I guess that have trouble.

Yeah, someone on another thread commented about the artwiz fonts not working properly. I don't use them, so I can't help with this. Sorry.

---

### Post by semperfiguy on 2007-11-10
I figured it out. the fonts are declared differently in the them files for 1.0.0 and SVN.  In the repos ver.  they are like this
```
*font:                              - *-fontname-*-*-*-*-*-*-*-*-*-*-*
```

In SVN it's
```
*font:                              fontname
```

so heres my desktop now:
[ATTACH]49813[/ATTACH]

---

### Post by rjmdomingo2003 on 2007-11-11
> **semperfiguy said:**
> I figured it out. the fonts are declared differently in the them files for 1.0.0 and SVN.  In the repos ver.  they are like this
```
*font:                              - *-fontname-*-*-*-*-*-*-*-*-*-*-*
```

In SVN it's
```
*font:                              fontname
```

so heres my desktop now:
[ATTACH]49813[/ATTACH]
Reminiscin' about black glass borderless..:-| Yes, that was once my fave theme.. Nova lime's the current.

Suggest you change the theme font to Market Deco (dafont.com), and observe..

---

### Post by semperfiguy on 2007-11-11
Show me how to install new fonts and I'll give it a try.  I downloaded the font and unzipped it to my ~/.fonts directory.  I then ran ```
mkfontdir
``` and ```
mkfontscale
```
And in my .fluxbox/startup file there is a line ```
xset +fp "/home/semperfiguy/.fonts"
```

But it doesn't show up in xfontsel.  What else do I need to do to make it show up?

---

### Post by rjmdomingo2003 on 2007-11-11
> **semperfiguy said:**
> Show me how to install new fonts and I'll give it a try.  I downloaded the font and unzipped it to my ~/.fonts directory.  I then ran ```
mkfontdir
``` and ```
mkfontscale
```
And in my .fluxbox/startup file there is a line ```
xset +fp "/home/semperfiguy/.fonts"
```

But it doesn't show up in xfontsel.  What else do I need to do to make it show up?
What I usually do is:

1. Place the (unzipped) font file to /usr/share/fonts/truetype (This step may not be necessary).
2. Open the fluxbox style file.
3. Change the font(s) to your desired font name.

This works for me all the time. Hope it does for you too.

Note that the font name isn't necessarily the same as the font filename. To check what is the font name, just double-click the file, and check the font name.

---

### Post by jviscosi on 2007-11-12
> **jviscosi said:**
> FWIW, my research is indicating that (at least on my machine) the click-focus issue kicks in once a terminal has been loaded.  Before a terminal is open, it works the way it used to.  Once a terminal is loaded, clicking in the body of another window doesn't transfer focus.  This persists until all the windows are closed, at which point focus starts working normally, until the next time a terminal opens.  (I added all this to the bug report, of course.)

The Fluxbox programmers figured out the problem ... here is Mark's explanation:

> O.K., I've figured out how to reproduce this. Whenever you use an
emacs-style keychain, change your keymode, change your keyboard
layout/modifier map (with xmodmap), or reload the configuration, all open
windows will begin to exhibit this behavior. New windows will be fine. I'm
working on a somewhat significant patch right now, but I'll try to get this
fixed in the next few days.[FONT=Tahoma,Sans,Arial,Helvetica,sans-serif]
So I was seeing this happen when I opened a terminal because my .bashrc (I don't use dash as my shell) runs an xmodmap script to apply extra keys from my multimedia keyboard.  Commenting out the call to xmodmap causes the terminals to stop causing this problem.
[/FONT]

---

### Post by yabbadabbadont on 2007-11-14
That doesn't fit with what I saw though.  I never use xmodmap, and it isn't used by any of the profiles that are run when opening a terminal on my system.  But opening a terminal did seem to cause the issue though.  Oh well.  It sounds like they found and fixed a bug that needed fixing anyway.

---

### Post by RedSquirrel on 2007-11-14
I just installed SVN 5130. The issue I was seeing with the iconbar focus seems to be fixed, which is a relief. That was really annoying!

By the way, I setup a nifty PKGBUILD file on Arch for Fluxbox SVN and I use the versionpkg script which automatically pulls down the latest source (if there is a new SVN version) and builds a package. It's almost too easy. :)

---

### Post by rjmdomingo2003 on 2007-11-14
Hey fluxters! I enjoy flux a lot, and have configured the repo version of feisty like crazy.

Upon upgrading to gutsy, I was convinced through this thread to try out the latest subversion release of flux. I installed SVN 5127, if I'm not mistaken, 2 days ago. All went well (including customizing my menu, conky, idesk, backgrounds), except for theming. 

All window title bars have the correct theme buttons (accdg. to their pixmaps), but the bar itself is colored grey, where it should be black (or hex color 222222). It stands out like a sore thumb. Using switch2 & gnome-appearance properties don't help.

Any help would be great.

---

### Post by jviscosi on 2007-11-15
> **rjmdomingo2003 said:**
> All window title bars have the correct theme buttons (accdg. to their pixmaps), but the bar itself is colored grey, where it should be black (or hex color 222222). It stands out like a sore thumb. Using switch2 & gnome-appearance properties don't help.

Hmm, that's one I haven't seen.  What theme are you using?  Or is this in any theme?

---

### Post by rjmdomingo2003 on 2007-11-15
> **jviscosi said:**
> Hmm, that's one I haven't seen.  What theme are you using?  Or is this in any theme?
I'm using the Nova theme. 

I noticed that unlike feisty's gnome-theme-manager, gutsy's gnome-appearance-properties doesn't list the Nova theme in the window border tab, despite being installed. It's only listed in the Controls tab.

---

### Post by semperfiguy on 2007-11-16
I had this problem too when I tried out that theme.  You have to add the line
```
window.label.focus:                                             flat
```
to the theme.cfg file

---

### Post by urukrama on 2007-11-16
> **rjmdomingo2003 said:**
> I noticed that unlike feisty's gnome-theme-manager, gutsy's gnome-appearance-properties doesn't list the Nova theme in the window border tab, despite being installed. It's only listed in the Controls tab.

Doesn't the gnome-theme-manager only manage Metacity's themes, and not Fluxbox's (or any other window manager)?

---

### Post by rjmdomingo2003 on 2007-11-17
> **urukrama said:**
> Doesn't the gnome-theme-manager only manage Metacity's themes, and not Fluxbox's (or any other window manager)?
Correct! However, for you to have the theme's controls &/or borders, style change (from the flux menu) & switch2 ain't enough.

---

### Post by rjmdomingo2003 on 2007-11-17
> **semperfiguy said:**
> I had this problem too when I tried out that theme.  You have to add the line
```
window.label.focus:                                             flat
```
to the theme.cfg file
That worked! :guitar:
Thanks a lot! Cheers!

---

### Post by RedSquirrel on 2007-11-21
I'm seeing a weird graphical issue with the iconbar on SVN 5133. This may have been present with other versions and I just didn't notice. :)

When I move to a workspace that has applications on it, the iconbar displays some weird graphics before stabilizing and showing the titles of the applications I have running in that workspace.

I was just wondering if anyone else has seen this. I've gone back to the stable version for now and this issue is not present in that version.

---

### Post by rjmdomingo2003 on 2007-11-22
> **RedSquirrel said:**
> I'm seeing a weird graphical issue with the iconbar on SVN 5133. This may have been present with other versions and I just didn't notice. :)

When I move to a workspace that has applications on it, the iconbar displays some weird graphics before stabilizing and showing the titles of the applications I have running in that workspace.

I was just wondering if anyone else has seen this. I've gone back to the stable version for now and this issue is not present in that version.
I installed svn 5127, and I don't see what you observe. I don't have the toolbar visible. To check what you're seeing, I tried having it visible, changed workspaces, and checked window labels. I didn't notice any graphical weirdness on icons.

---

### Post by TeaSwigger on 2007-11-23
Hello folks, about... fbdesk. Tried the version from the repos. Set it up to use ~/.fluxbox/fbdesk & ~/.fluxbox/fbdesk.icons. Then tried to set its config. Black text, gray text background, lousy font by default. After config... It ah... well it likes what it likes text and text background wise, and refuses to change it on account of some pithy type in some config file. Should I be using another version or...?

---

### Post by rjmdomingo2003 on 2007-11-23
> **TeaSwigger said:**
> Hello folks, about... fbdesk. Tried the version from the repos. Set it up to use ~/.fluxbox/fbdesk & ~/.fluxbox/fbdesk.icons. Then tried to set its config. Black text, gray text background, lousy font by default. After config... It ah... well it likes what it likes text and text background wise, and refuses to change it on account of some pithy type in some config file. Should I be using another version or...?
You could try idesk. I found it "easier" to configure than fbdesk. Icons are easier to manager using the idesktool.

Here's my latest desktop using idesk: [http://ubuntuforums.org/attachment.php?attachmentid=51115&d=1195823367](http://ubuntuforums.org/attachment.php?attachmentid=51115&d=1195823367)

---

### Post by TeaSwigger on 2007-11-23
> **rjmdomingo2003 said:**
> You could try idesk. I found it "easier" to configure than fbdesk. Icons are easier to manager using the idesktool.

Here's my latest desktop using idesk: [http://ubuntuforums.org/attachment.php?attachmentid=51115&d=1195823367](http://ubuntuforums.org/attachment.php?attachmentid=51115&d=1195823367)

Ah a very elegant layout you have there, rjm :) Superb synergy.

Yeah I was sort of suspecting I'd be directed to idesk; for some reason I keep wanting to use fbdesk with fluxbox, or perhaps ROX (when ROX isn't baffling me). Unless anyone has anything to add on fbdesk's behalf I'll take the suggestion and go back to idesk then. :)

---

### Post by rjmdomingo2003 on 2007-11-24
> **TeaSwigger said:**
> Ah a very elegant layout you have there, rjm :) Superb synergy.

Yeah I was sort of suspecting I'd be directed to idesk; for some reason I keep wanting to use fbdesk with fluxbox, or perhaps ROX (when ROX isn't baffling me). Unless anyone has anything to add on fbdesk's behalf I'll take the suggestion and go back to idesk then. :)
Thanks! I'm already working on "enhancing" my desktop setup. My suggestion: stick to idesk.

---

### Post by RedSquirrel on 2007-11-24
> **rjmdomingo2003 said:**
> I installed svn 5127, and I don't see what you observe. I don't have the toolbar visible. To check what you're seeing, I tried having it visible, changed workspaces, and checked window labels. I didn't notice any graphical weirdness on icons.

OK, thanks for the input. I wonder why it happens with the SVN version and not the stable version... Strange.

I'll continue to install newer versions and see if it gets better in the near future...

Edit: I neglected to mention earlier that I'm seeing this with themes that use _pixmaps_ in the toolbar (iconbar). Themes that use colours or simple gradients don't have a problem.

---

### Post by cknight on 2007-11-28
Just a quick shout to let folks know about [a new Fluxbox how-to covering the power and flexibility of fluxbox key bindings]("http://ubuntuforums.org/showthread.php?t=617812").  My experiences seem to suggest that few people bother to setup custom key bindings, which is a shame since they can really enhance your user experience without taking away from Fluxbox being fast and light.  So, here's a call to all you Fluxbox users out there to add something new and interesting to your keys file, especially those who have never done so :)

---

### Post by rjmdomingo2003 on 2007-11-28
> **cknight said:**
> Just a quick shout to let folks know about [a new Fluxbox how-to covering the power and flexibility of fluxbox key bindings]("http://ubuntuforums.org/showthread.php?t=617812").  My experiences seem to suggest that few people bother to setup custom key bindings, which is a shame since they can really enhance your user experience without taking away from Fluxbox being fast and light.  So, here's a call to all you Fluxbox users out there to add something new and interesting to your keys file, especially those who have never done so :)

Thanks for the heads-up!

---

### Post by -grubby on 2007-12-15
me being so ignorant, I couldn't find this thread by searching, so I made a new one [http://ubuntuforums.org/showthread.php?p=3959777#post3959777](http://ubuntuforums.org/showthread.php?p=3959777#post3959777)

---

### Post by steveneddy on 2008-02-17
I should re-install Fluxbox again.

It was erased in the last reinstall.

I miss Flux.

---

### Post by eriqjaffe on 2008-03-05
Just wanted to share this information - I have found a simple volume control called VolWheel that resides in the tray (panel) on a post in the Arch forums.

```
$ mkdir .volwheel
$ cd .volwheel
$ wget http://olwtools.googlecode.com/svn/trunk/volwheel/volwheel
$ sudo apt-get install alsa-utils gnome-icon-theme libgtk2-perl libgtk2-trayicon-perl
$ sudo chmod a+x volwheel
$ ./volwheel &
```

Then just add ~/.volwheel/volwheel & to your startup file and you're good to go.  It'll interface fine with the osdsh, if you use that.

...and you should have a nifty little icon for controlling your mixer via the scroll wheel of your mouse (scroll up & down to change the volume, click the scroll wheel to toggle mute):
[IMG]http://img.photobucket.com/albums/v71/fizzjob/36.png[/IMG]

...right-click to bring up the properties (allows you to set what the tray app is controlling, as well as the command to bring up your default mixer):
[IMG]http://img.photobucket.com/albums/v71/fizzjob/49.png[/IMG]

...and here's a shot of it controlling alsamixer (the mixer you set in the preferences comes up if you left-click on the icon):
[IMG]http://img.photobucket.com/albums/v71/fizzjob/58.png[/IMG]

---

### Post by yabbadabbadont on 2008-03-05
That looks interesting.  I might have to give it a try.  Currently, I use either the gkrellm-volume plugin, or keyboard shortcuts for amixer.
From my keys file:
```
Mod4 bracketleft :Execute amixer -q set PCM playback 1-
Mod4 bracketright :Execute amixer -q set PCM playback 1+

```

---

### Post by kerry_s on 2008-03-05
there's also this 1, very light-> [http://www.pcbypaul.com/software/absvolume.html](http://www.pcbypaul.com/software/absvolume.html)
the deb works in ubuntu 7, my friend uses it.
he use keyboard shortcut for mute-> amixer set PCM toggle
wait, it's not a tray icon though, i think he use a keyboard shortcut to launch it to. 
nothing like alternatives. :)

---

### Post by eriqjaffe on 2008-03-05
> **kerry_s said:**
> there's also this 1, very light-> [http://www.pcbypaul.com/software/absvolume.html](http://www.pcbypaul.com/software/absvolume.html)
the deb works in ubuntu 7, my friend uses it.
he use keyboard shortcut for mute-> amixer set PCM toggle
wait, it's not a tray icon though, i think he use a keyboard shortcut to launch it to. 
nothing like alternatives. :)
I have keys for mine, too, but since my ancient Vaio's Fn keys don't work with Ubuntu, they're a little awkward - I'm constantly trying to use Fn-F4 to change the volume, but that doesn't work since I ditched Windows.  ;)

---

### Post by kerry_s on 2008-03-06
> **eriqjaffe said:**
> I have keys for mine, too, but since my ancient Vaio's Fn keys don't work with Ubuntu, they're a little awkward - I'm constantly trying to use Fn-F4 to change the volume, but that doesn't work since I ditched Windows.  ;)

yeah, you have to jump through hoops on these vaio's to use that fn key, not worth it. i simply have 3 click buttons on my tool bar and and ctrl+f3 is lower, ctrl+f4 is higher.
mines vaio pcg-f430
:lolflag:

---

### Post by markjensen on 2008-03-06
> **eriqjaffe said:**
> I have keys for mine, too, but since my ancient Vaio's Fn keys don't work with Ubuntu, they're a little awkward - I'm constantly trying to use Fn-F4 to change the volume, but that doesn't work since I ditched Windows.  ;)
If those keys generate keycodes in **xev**, then you can add them into your fluxbox keys file to have actions taken on them.

---

### Post by kerry_s on 2008-03-06
> **markjensen said:**
> If those keys generate keycodes in **xev**, then you can add them into your fluxbox keys file to have actions taken on them.

no they don't, vaio proprietary crap.
normally you would use the "sonypi" driver.

---

### Post by eriqjaffe on 2008-03-06
Yeah, there's something going on with them, because Fn-Left and Fn-Right work for "Home" and "End".  I've considered messing with it, but I never really thought it was worth the effort - the only one of those special keys I ever used when I ran Windows was the volume control anyways.

---

### Post by steveneddy on 2008-03-07
Not complaining, but i can't believe this thread is still alive.

Keep up the good work, fellas.

---

### Post by ittiam on 2008-03-07
> **yabbadabbadont said:**
> It isn't very exciting.  I've found a setup that I like and I pretty much stick with it.

Hey i have just started using fluxbox, could someone let me know how could i get those transparent widgets which shows mem usage and about hda details. Thanks

---

### Post by steveneddy on 2008-03-07
> **ittiam said:**
> Hey i have just started using fluxbox, could someone let me know how could i get those transparent widgets which shows mem usage and about hda details. Thanks

I think that is called conky.

It's in the repos.

---

### Post by RedSquirrel on 2008-03-07
Yeah, conky is one of them. The program in yabbadabbadont's screenshots is **gkrellm**. It is in the repositories.

---

### Post by Bruce M. on 2008-03-08
Hi Folks,

I've read the first three or fours pages of this thread and have been thinking of Fluxbox or (dare I say it) Openbox for a while now. I still have my doubts. I've never tried Fluxbox, but recently installed Xubuntu because I have an OLD computer (see Sig) and XFCE 7.10 is better here than GNOME. ( I miss GNOME, but getting used to X ).

> Fluxbox (from Synaptic)

Highly configurable and low resource X11 Window manager
Fairly similar to blackbox, from which it is derived, but has been
extended with features such as pwm-style window tabs, configurable
key bindings, toolbar, and an iconbar. It also includes some cosmetic
fixes over blackbox.

This package contains support for Gnome and KDE.


The Iconbar is a good thing as my wife insists on Icons for her stuff.

So here's a few questions:

[LIST=1]
[*] Will it install in Xubuntu?
[*] Is it faster than XFCE ( if it will install )?
[*] Is it lighter in resources?
[*] Is it lighter with processes running?
[/LIST]

 What I'm looking for, *without leaving Ubuntu*, is to lower my CPU stress.  :)
 Of course getting rid of FireFox will do that to a great degree as well, but what to use? That's for another thread though.

Thanks
Bruce

---

### Post by RedSquirrel on 2008-03-08
> **Bruce M. said:**
> So here's a few questions:[LIST=1]
[*] Will it install in Xubuntu?
[*] Is it faster than XFCE ( if it will install )?
[*] Is it lighter in resources?
[*] Is it lighter with processes running?[/LIST] What I'm looking for, *without leaving Ubuntu*, is to lower my CPU stress.  :)
 Of course getting rid of FireFox will do that to a great degree as well, but what to use? That's for another thread though.

Thanks
Bruce

It will install no matter what you're using right now. Just install the fluxbox package and then run the following command to generate the menu:

```
sudo update-menus
```If that menu isn't complete enough for you, see the link in my signature to get a better menu. I also have a "links and information" section in that tutorial.

To get into Fluxbox: Logout. At the login screen go to Sessions and select Fluxbox and then login.

Fluxbox is lighter than Xfce. It leaves more resources for your applications (e.g., Firefox) so that things don't bog down so much.

To be honest, with your specs, I don't know if you will notice that much of a speed improvement over Xfce. Your specs are pretty good, actually. Try it and see.

And try Openbox too. It's very nice.

If you're looking for a really light system, install a minimal system and build up from there, e.g.,

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by Bruce M. on 2008-03-08
> **RedSquirrel said:**
> It will install no matter what you're using right now. Just install the fluxbox package and then run the following command to generate the menu:

```
sudo update-menus
```If that menu isn't complete enough for you, see the link in my signature to get a better menu. I also have a "links and information" section in that tutorial.

Bookmarked your signature link earlier today  :)

> **RedSquirrel said:**
> To get into Fluxbox: Logout. At the login screen go to Sessions and select Fluxbox and then login.

Fluxbox is lighter than Xfce. It leaves more resources for your applications (e.g., Firefox) so that things don't bog down so much.

To be honest, with your specs, I don't know if you will notice that much of a speed improvement over Xfce. Your specs are pretty good, actually. Try it and see.

And try Openbox too. It's very nice.

later maybe, but for now I'll look at FB.  My wife will kill me  :)

> **RedSquirrel said:**
> If you're looking for a really light system, install a minimal system and build up from there, e.g.,

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

I saw "server" ( a while back ) and backed away.

And while I was wondering about speed it's not a biggie, I know 800Mhz isn't going to blitz anything.  Well, a turtle or snail maybe.  :)

Thanks
Bruce

---

### Post by markjensen on 2008-03-08
I guess the short, quick answer is that *box _is_ "faster" than XFCE (which is my second favorite Linux DE).  There is next to nothing to load up once X is loaded and you log in.

However, if you run big heavy apps on top of it, you are going to consume a lot of resources.   *box won't be consuming them, but OO.o is a huge app.  And if you run KDE apps, you need to load in the KDE libraries.  And if you also run Gnome apps, then the Gnome libraries are likewise loaded.

Think of it as a very light-weight *foundation* (which is really just what a Window Manager is) in which you run apps.  Choose well, and you keep light.  You can look at distros like DamnSmallLinux to see some light app choices.

---

### Post by Bruce M. on 2008-03-08
> **markjensen said:**
> I guess the short, quick answer is that *box _is_ "faster" than XFCE (which is my second favorite Linux DE).  There is next to nothing to load up once X is loaded and you log in.

However, if you run big heavy apps on top of it, you are going to consume a lot of resources.   *box won't be consuming them, but OO.o is a huge app.  And if you run KDE apps, you need to load in the KDE libraries.  And if you also run Gnome apps, then the Gnome libraries are likewise loaded.

Think of it as a very light-weight *foundation* (which is really just what a Window Manager is) in which you run apps.  Choose well, and you keep light.  You can look at distros like DamnSmallLinux to see some light app choices.

Yup, realize that, some GNOME stuff gets loaded by default in XFCE, but I use NO K stuff.  :)

---

### Post by steveneddy on 2008-07-05
I miss yabbadabbadont.

---

### Post by yabbadabbadont on 2008-07-05
> **steveneddy said:**
> I miss yabbadabbadont.

Albatross!

---

### Post by steveneddy on 2008-07-06
> **yabbadabbadont said:**
> Albatross!

Good to see you old friend.

Hope things are going well for you.

You're in Gentoo land, isn't that right?

---

### Post by markjensen on 2008-07-07
> **Bruce M. said:**
> Yup, realize that, some GNOME stuff gets loaded by default in XFCE, but I use NO K stuff.  :)
Yes.  My point was perhaps less than clear.

I stated that open|black|fluxbox was faster to boot than XFCE because *boxes don't have much to load at all.   I didn't mean to be so unclear that some might think I said XFCE didn't have anything to load beyond X.

---

### Post by mojoman on 2008-07-18
Hi guys,

Glad to see that there's still life in this thread. 

I seldom check in these days as I'm mostly running Debian but lately I've been fooling around with Arch on the side. Arch is quite nice and it has some excellent documentation as well. Naturally, I started off with my favourite WM and found some very good documentation on fluxbox styles. Maybe this is old news for the crowd who lurks around in this thread but nevertheless, here it is:

[_http://wiki.archlinux.org/index.php/Fluxbox_Style_Guide_]("http://wiki.archlinux.org/index.php/Fluxbox_Style_Guide")

all the best
mojoman

---

