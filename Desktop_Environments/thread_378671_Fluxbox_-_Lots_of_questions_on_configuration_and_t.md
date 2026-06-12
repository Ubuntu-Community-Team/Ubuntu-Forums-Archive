---
title: "Fluxbox - Lots of questions on configuration and tweaking."
date: 2007-03-07
forum: Desktop Environments
---

### Post by Raavea on 2007-03-07
I've got Fluxbox on my machine with GNOME doing the other bits - the inner bits of windows etc, you know what I mean? 

 My main question is: If I completely remove GNOME, can flux do these parts itself?
 Questions branching off of that are: Will this make my flux transparent? If I have to have GNOME or somesuch thing to do the inner bits, what do you recommend for speed and appeal and preferably integration with flux itself? Is fbdesk a decent choice for my desktop manager or should I go for something else? I would like widgets and such, as well as icons. Is there a file manager similar to Nautilus but with less of the weight? (I really like Nautilus, and have found Thunar to not be what I want.)

I really need the opinion of a well-versed fluxer.. I don't know much about anything but how to make GNOME look up to my standards...


 Basically, I want this machine to hum, I want it fast, pretty, and integrated. I'm just trying to find out if this can be done. :)

---

### Post by RedSquirrel on 2007-03-08
> **Raavea said:**
> I've got Fluxbox on my machine with GNOME doing the other bits - the inner bits of windows etc, you know what I mean? 

 My main question is: If I completely remove GNOME, can flux do these parts itself?

You don't need GNOME. There is gtk-theme-switch to choose a theme for Fluxbox. It's in the repos. 

You still have to choose a Fluxbox style which applies to the window title bar and the Fluxbox menu and so on. I'm using the *Human* theme with the *Vista Black* style right now. (See screenshot.) 

> 
 Questions branching off of that are: Will this make my flux transparent? 


If you don't choose a theme, then you'll get the default Fluxbox one which is a fairly bland looking grey. You'll want to change that, almost certainly. :)

> 
If I have to have GNOME or somesuch thing to do the inner bits, what do you recommend for speed and appeal and preferably integration with flux itself? Is fbdesk a decent choice for my desktop manager or should I go for something else? I would like widgets and such, as well as icons. Is there a file manager similar to Nautilus but with less of the weight? (I really like Nautilus, and have found Thunar to not be what I want.)I'll have to leave it to someone else to answer most of your questions about desktop integration. I tend to use the command line for file manipulation, but I use Thunar once in a while. I haven't used fbdesk. 

There is something called Rox filer which is pretty lightweight and you can configure it to add icons to your desktop. The forums at the [fluxbuntu]("http://www.fluxbuntu.org") site discuss this. I have never used it myself, though, because I don't like desktop icons and I'm content with Thunar.

[http://www.fluxbuntu.org](http://www.fluxbuntu.org)

> 
I really need the opinion of a well-versed fluxer.. I don't know much about anything but how to make GNOME look up to my standards...

 Basically, I want this machine to hum, I want it fast, pretty, and integrated. I'm just trying to find out if this can be done. :)Yes, it can be done. Fluxbox is highly configurable and you can add all sorts of eye candy if you want. I personally don't use any of it, but that's just me. I like to keep things uncluttered.

There are some links in my sig that you might find useful.

---

### Post by kerry_s on 2007-03-08
I think you got the wrong idea on what fluxbox is, it's not a desktop, there are no applications that come with it. It is a WM(window manager) meaning it provides the thing that the apps you select work in. Usually if you want speed you want to go pure fluxbox and select your applications carefully. If your asking i don't think your ready to do your own fluxbox build yet, so try->

  -> [http://modzer0.cs.uaf.edu/~hardwarehank/fluxbuntu/rev2/fluxbuntu-nbuild1-rev2-desktop-i386.iso](http://modzer0.cs.uaf.edu/~hardwarehank/fluxbuntu/rev2/fluxbuntu-nbuild1-rev2-desktop-i386.iso)
Pics= [http://fluxbuntu.org/](http://fluxbuntu.org/)

-> [ftp://ftp.oss.cc.gatech.edu/pub/linux/distributions/damnsmall/current/current.iso](ftp://ftp.oss.cc.gatech.edu/pub/linux/distributions/damnsmall/current/current.iso)
Best small fluxbox= [http://damnsmalllinux.org/](http://damnsmalllinux.org/)


-> [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)
This one will install any of the supported ubuntu versions straight from the net(net installer). With this you can also build your own fluxbox setup using the server(base) install.

---

### Post by kerry_s on 2007-03-08
RedSquirrel, you need some menu help. :lolflag: 

Here's mine for you to play with->

---

### Post by RedSquirrel on 2007-03-08
> **kerry_s said:**
> RedSquirrel, you need some menu help. :lolflag: 

Here's mine for you to play with->


LOL *indeed*! Did it ever occur to you that I like it that way? I like having only three entries to begin with. :)

I almost never use the menu anyway. I setup keyboard shortcuts for the programs I use most often and I tend to use the terminal a fair bit as well. But thanks for your suggestion in any case.

---

### Post by kerry_s on 2007-03-08
> **RedSquirrel said:**
> LOL *indeed*! Did it ever occur to you that I like it that way? I like having only three entries to begin with. :)

I almost never use the menu anyway. I setup keyboard shortcuts for the programs I use most often and I tend to use the terminal a fair bit as well. But thanks for your suggestion in any case.


I thought you just didn't get around to it yet, so i was trying to give you a head start. I'm more of a mouse person, the keyboards to far when i'm relaxed in the chair. I only got 2 entries in my keys file, for when i know i have my keyboard in my hands.

```
Mod1 Tab :NextWindow
Mod1 Shift Tab :PrevWindow
None F1 :ExecCommand xterm
Mod1 F2 :ExecCommand fbrun -w 600 -h 50 -nearmouse -font Sans-16
Mod1 F3 :Workspace 3
Mod1 F4 :Workspace 4
Mod1 F5 :Workspace 5
Mod1 F6 :Workspace 6
Mod1 F7 :Workspace 7
Mod1 F8 :Workspace 8
Mod1 F9 :Workspace 9
Mod1 F10 :Workspace 10
Mod1 F11 :Workspace 11
Mod1 F12 :Workspace 12

```

:lolflag:

---

### Post by RedSquirrel on 2007-03-08
> **kerry_s said:**
> I thought you just didn't get around to it yet, so i was trying to give you a head start. 

Thanks. You have some neat tricks in there. :guitar:

> 
* I'm more of a mouse person, the keyboards to far when i'm relaxed in the chair. I only got 2 entries in my keys file, for when i know i have my keyboard in my hands.*My keys file:

```
Control Mod1 Left :PrevWorkspace
Control Mod1 Right :NextWorkspace
Mod1 Tab :MacroCmd {Deiconify LastWorkspace} {NextWindow 0}
Mod1 F1 :ExecCommand 
Mod1 F2 :ExecCommand 
Mod1 F3 :ExecCommand leafpad
Mod1 F4 :ExecCommand xfce4-terminal
Mod1 F5 :ExecCommand abiword 
Mod1 F6 :ExecCommand gksudo synaptic
Mod1 F7 :ExecCommand thunar
Mod1 F8 :Workspace 8
Mod1 F9 :Workspace 9
Mod1 F10 :Workspace 10
Mod1 F11 :Workspace 11
Mod1 F12 :Workspace 12
None XF86HomePage :ExecCommand firefox
None XF86Mail     :ExecCommand mozilla-thunderbird
None XF86Search   :ExecCommand 

```... and the spartan menu file:

```
[begin] (Fluxbox)
[submenu] (Debian Menu)
[include] (/etc/X11/fluxbox/menudefs.hook)
[end]
[include] (~/.fluxbox/custom-menu-entries)
[submenu] (Fluxbox Menu)
[include] (/etc/X11/fluxbox/system.fluxbox-menu)
[end]
[end]

```


PS - OK, this is a bit of *thread drift*, but kerry_s, that's a huge screenshot. Which monitor are you using (if you don't mind me asking)?

---

### Post by kerry_s on 2007-03-08
LOL, i'm running dual monitors. I've got my small 1 set for panning because i was doing something and needed more space side by side.
Left= 15" HP M70 max=1280x1024
Right= 18" Gateway vx920 max=1600x1200
I've got it set a little bigger than earlier right now, i needed even more space. :)

Option         "MetaModes" "1280x1024 @2000x1024, 1280x1024"
giving me->
(II) NVIDIA(0): Virtual screen size determined to be 3280 x 1024
so roughly a 32" wide screen.

---

### Post by Raavea on 2007-03-09
> **kerry_s said:**
> I think you got the wrong idea on what fluxbox is, it's not a desktop, there are no applications that come with it. It is a WM(window manager) meaning it provides the thing that the apps you select work in. Usually if you want speed you want to go pure fluxbox and select your applications carefully. Oh, I know. You seem to have misunderstood my query. Basically, I have compiled (and been using) the latest Fluxbox from the source. It's all dandy and fast, but Gnome is still handling the insides of the windows - I think this because unless I open gnome-theme-manager and pick a theme, the insides of my windows (everything but the edges and the titlebar) are a manky grey that reminds me of '98 before I began playing with the colours for it. 

There is no transparency for my menus or titlebars etc, though I have tried to set it. This can wait until I am a bit more familiar with flux and it's setup.

 I have fbdesk with an icon on it, and am considering trying ROX instead.. I have my wallpaper load on startup, I have fluxStyles installed along with some styles, I have the artwiz fonts working, and I have altered my menu to suit my needs. I have figured out how to use nautilus without it taking over the desktop, and I have been tinkering about with making my own theme for flux.

 As you can probably guess by now... I prefer to leap in at the deep end. :3


 All I need to know now is how to get rid of the gnomey parts of my install so flux will draw all parts of my window itself. Any hints? 



...Wanna see my menu? :D


PS: Your sig got me where I am now. And your screen makes mine feel inadquate. Shame on you, showing off your largesse! :lol:

---

### Post by kerry_s on 2007-03-09
> All I need to know now is how to get rid of the gnomey parts of my install so flux will draw all parts of my window itself. Any hints?

Install> gtk-theme-switch

It does the installing and setting of themes in fluxbox. It will be under tools in your menu.

I use feh for the background setter and as my image viewer, dual purpose. :) 

```
 [submenu] (Backgrounds)
  [exec] (Black) {fbsetroot -solid black}
  [wallpapers] (/usr/share/fluxbox/backgrounds)
  [wallpapers] (~/.fluxbox/backgrounds)
 [end]
```
 
Put this part in your menu and in init change

```
session.screen0.rootCommand:	
to
session.screen0.rootCommand:	fbsetbg -l

```

Then you can just click to set your bg on the fly and it will always use the last background on startup.

Once you have that setup fluxbox should be handling it and you should have transparency.

Yes! Of course i want to see your menu. :)  Just in case you have something i haven't found/thought of.

---

### Post by Raavea on 2007-03-09
Installing gtk-theme-switch now. Thanks. I didn't want to risk just removing gnome completely only to find I am stuck using bash and links2. This laptop seems to have some issues with the screen and the bash terminal *(not a terminal like xterm, but like the virtual terminal or the section of shutdown where it goes 'Closing this [ok]' etc)* that make it impossible to use. 


So, my menu. It's still in early stages... I think I have a few more modifications to make to be happy with where things are. And I will be reviewing my installed apps soonish.Thanks for that bg hint, I use the command fbgset to change the bg anyhow, and have added my own wallpapers dir into the menu snippet you gave me - it all works beautifully, thanks bundles. ^_^ ```
[begin] (In Flux)
 [exec] (Terminal) {xterm}
 [exec] (Firefox) {firefox}
 [exec] (Thunderbird) {mozilla-thunderbird}
 [exec] (Gaim) {gaim}
 [exec] (Skype) {skype}
 [exec] (X-Chat) {xchat}
 [submenu] (Coding Stuff)
  [exec]   (G-Edit) {gedit}
  [exec]   (Nano) {xterm -e nano}
  [exec]   (Vim) {xterm -e vim}
  [exec]   (Vi) {xterm -e vi}
  [exec]   (G-Ftp) {gftp}
 [end]
 [submenu] (Utils)
  [exec] (Nautilus) {nautilus --no-desktop --browser}
  [exec] (Calculator) {xcalc}
  [exec] (Gimp) {gimp}
  [exec] (Beep) {beep-media-player}
  [exec] (Blender) {blender -w}
  [exec] (Rhythmbox) {rhythmbox}
  [exec] (Alsa mixer) {xterm -e alsamixer}
  [exec] (Open Office)      {ooffice}
  [exec] (OO Calc)          {oocalc}
  [exec] (OO Writer)        {oowriter}
  [exec] (OO Impress)       {ooimpress}
  [exec] (OO Draw)          {oodraw}
  [exec] (OO Math)          {oomath}
  [exec] (Acroread) {acroread}
  [submenu] (X Utils)
   [exec]   (Xfontsel) {xfontsel}
   [exec]   (Xman) {xman}
   [exec]   (Xload) {xload}
   [exec]   (Xbiff) {xbiff}
   [exec]   (Editres) {editres}
   [exec]   (Viewres) {viewres}
   [exec]   (Xclock) {xclock}
   [exec]   (Xmag) {xmag}
   [exec]   (Xeyes) {xeyes}
   [exec] (Reload .Xdefaults) {xrdb -load /home/raavea/.Xdefaults}
  [end]
 [end]
 [submenu] (Games)
  [exec]   (Gnome MUD) {gnome-mud}
  [exec]   (Gnibbles) {gnibbles}
  [exec]   (GNU-Robots) {gnobots2}
  [exec]   (G-Ataxx) {gataxx}
  [exec]   (G-Lines) {glines}
  [exec]   (G-Nect) {gnect}
  [exec]   (Mahjongg) {mahjongg}
  [exec]   (Mines) {gnomine}
  [exec]   (Gnometris) {gnometris}
  [exec]   (Tetravex) {gnotravex}
  [exec]   (Gnotski) {gnotski}
  [exec]   (Iagno) {iagno}
  [exec]   (Gtali) {gtali}
  [exec]   (Same-Gnome) {same-gnome}
  [exec]   (Klondike) {sol}
  [exec]   (Frozen Bubble) {frozen-bubble}
  [exec]   (Wesnoth) {wesnoth}
  [exec]   (Blackjack) {blackjack}
 [end]
 [submenu] (System Tools)
  [exec]   (Firestarter) {firestarter}
  [exec]   (Top) {xterm -e top}
 [end]
 [submenu] (Fluxbox Tools)
  [config] (Configure)
  [submenu] (Backgrounds)
   [exec] (Black) {fbsetroot -solid black}
   [wallpapers] (/usr/share/fluxbox/backgrounds)
   [wallpapers] (~/.fluxbox/backgrounds)
   [wallpapers] (~/.wallpaper)
  [end]
  [submenu] (System Styles) {Choose a style...}
   [stylesdir] (/usr/local/share/fluxbox/styles)
  [end]
  [submenu] (User Styles) {Choose a style...}
   [stylesdir] (~/.fluxbox/styles)
  [end]
  [workspaces] (Workspace List)
   [submenu] (Tools)
    [exec] (Window name) {xprop WM_CLASS|cut -d \" -f 2|xmessage -file - -center}
   [end]
  [submenu] (Window)
   [restart] (Gnome) {gnome-session}
  [end]
  [commanddialog] (Fluxbox Command)
  [reconfig] (Reload Config)
  [restart] (Restart)
  [exec] (About) {(fluxbox -v; fluxbox -info | sed 1d) 2> /dev/null | xmessage -file - -center}
  [separator]
  [exit] (Exit)
 [end]
[end]
```


EDIT: Hmm, transparency still isn't working. But switch2 is uber, thanks~

---

### Post by kerry_s on 2007-03-09
You got a very nice menu, i snagged your alsa-mixer line and dumped my wmix app, saves me 152kb. I'm trying to keep a full setup under 1 gig, it's for my next project i want to use a cf card and adapter in place of the hd. I'm at 670mb now, still trimming work in progress. :) 



When you set transparency, are you clicking on the restart button?

---

### Post by RedSquirrel on 2007-03-09
Have a look at this for the things you need to have transparency:

[http://fluxbox.sourceforge.net/docs/en/faq.php#transparent](http://fluxbox.sourceforge.net/docs/en/faq.php#transparent)

Be sure to restart Fluxbox (from the Fluxbox menu) to show the changes you made to the transparency values. They can be changed (if you didn't know) from the Fluxbox menu:

Fluxbox Menu -> Configuration -> Transparency

You can change the toolbar transparency by right-clicking on the toolbar.

You can also change the transparency values by editing your ~/.fluxbox/init file directly.


EDIT: I removed some lines from my post that were probably more *confusing* than helpful. :)

---

### Post by Raavea on 2007-03-10
I don't have that option in my menu. I have;
>  Fluxbox Menu> Configure>
 - Focus model
 - Tab options
 - Slit
 - Toolbar
 - Image Dithering
 - Opaque Window Moving
 - Full Maximisation
 - Focus New Windows
 - Focus Last Window on Workspace
 - Workspace Warping
 - Desktop MouseWheel Switching
 - Decorate Transient Windows
 - Click RaisesI'm looking at that link and my init file now, so I'll edit this post if I get it sorted. :)


 Oh,I've looked at that before. it says -RENDER for the first command, and RENDER for the xdpy one, but I don't know how to fix it - I'm using 1.0rc2

---

### Post by kerry_s on 2007-03-10
So i'm guessing you might have forgot to compile it in? I'm using fiesty so i have the latest.

---

### Post by Raavea on 2007-03-10
That'd be it then. I've seen mention of compiling with it incluided, but it wasn't mentioned in the guide I used that that was neccessary... Does this mean I need to recompile? There's no way to enable it now? If I do need to recompile, what do I need to do? I mean, do I need to reove what I have? How? Or can I sort of, alter a config file to make it work...? Or...? I've never really had to recompile something so big and important so I don't want to do something wrong!

---

### Post by kerry_s on 2007-03-10
It's up to you, i would have stayed with the one in the repos. There has been very little change from that and the newest version. I know when i used dapper that version was solid, with fantastic twinview support, after that it went down hill from there, in my opinion, the twinview support is not that good on the newer versions.

---

### Post by Raavea on 2007-03-10
Hmm. I followed what the website said - that the old 'stable' version isn't as good as the new one. So I got the new one. 

I don't know what to do.. I will have to try and find out if anyone else has had the same thing.

---

### Post by kerry_s on 2007-03-10
You sound like your a very competent user, Have you given any thought to doing a custom install and building your system to you? It's not as hard as it sounds, i'll give you a quick rundown.

fiesty net installer-> [http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso](http://mirror.linux.org.mt/mirror/ubuntu/dists/feisty/main/installer-i386/current/images/netboot/mini.iso)

type "server" to do the server install
skip selecting anything when it  comes to that,your going to apt-get your own, just tab and continue.

after it's complete and you reboot, it looks like it gets stuck, but if you can see your host name, that means it's done and it's just waiting for you to login, the new parallel booting makes the cursor look like it's still loading.

after you login, type> sudo su
that will make you root

type> apt-get install x-window-system-core gdm fluxbox synaptic

That's it the hard parts done, just type> reboot

Now select fluxbox from the session menu and login, it will be a completely barebones fluxbox install, just open synaptic and start installing all the parts you want to complete your personal build.

---

### Post by Raavea on 2007-03-10
I will try that, and thanks, that's the nicest thing anyone's said to me all day. Most of it is logic-fuelled guesswork, though. :lol:

 Fiesty is safe to use? I am still on Dapper...
 You referred to that as the net installer. Does this mean I can use it straight off the net? o.O If so, how~?
 Well, it seems I can't boot from the cd or I did something wrong, as I burned it to disc and set to boot and it didn't... Maybe I should fiddle with it a bit more. :D

 And hopefully this doesn't require me using the virtual terminal, as that thing just doesn't work on my monitor. It flickers at the top inch of the monitor so it's real hard to read as it seems to cycle and scroll too....


EDIT: Ahh, burned it as an image now, seems to be more successful. Now to try booting... hehe

---

### Post by kerry_s on 2007-03-10
Sorry, it's are shopping day, got to get that food.

Dapper mini-> [http://sk.archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/mini.iso](http://sk.archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/netboot/mini.iso)

I have edgy to-> [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)

Yes, fiesty is pretty steady now that there pretty far along, just don't upgrade things right away and check the forums, if there's problems you'll see them and can hold off on updates till there fixed.

The net installer installs straight from the net, so it is always up to date, you can also use that 1 disk to install any of the supported *buntu versions or as i do build my own setup.

---

### Post by kerry_s on 2007-03-10
Almost forgot, with dapper and edgy there's an extra step, you'll need to turn all the repos on, in fiesty there all on by default.

dapper and edgy->

server install
login
sudo su
nano /ect/apt/sources.list
uncomment the repos
ctrl and x and y and enter to save
apt-get update
apt-get install x-window-system-core gdm fluxbox synaptic
or
apt-get install x-window-system-core gdm icewm icemc(or iceconf) icewm-themes synaptic
or
apt-get install x-window-system-core gdm whateveryoudesire
reboot
select session, login and build away.

Just have fun. :)

---

### Post by Raavea on 2007-03-10
Hehe, I am having fun. I've already done it and am currently playing about choosing apps. 

 Thanks bundles!


I just have to choose a file manager now..

---

### Post by kerry_s on 2007-03-10
LOL, It feels good building the system to your needs, doesn't it? You will know exactly what is installed and how it all works to complete your system.

Thunar makes a good file manager, if you like the icon based type, an included bonus with thunar you can use the xfce4-panel and have icons and launchers.

Rox is also good and can be used as the background and will let you put icons on the desktop.

I use emelfm, it's just a dirt simple file manger, no icons, but it really provides all you need in a file manger. 

Let me know if you need any help, You can grab firefox to look around with google and install the applications you need as you go along. That's what i usually do, i just install the applications as i need them, instead of trying to guess what i might need/use.

---

### Post by Raavea on 2007-03-12
I have one more query... How would I set my menu button for Puzzle Pirates to work? To get PP to work, I have to open a terminal, cd to ~/.yohoho and then ./yohoho
I tried a few different combinations of things in the menu EXEC but it didn't work.

---

### Post by BLTicklemonster on 2007-03-16
> **kerry_s said:**
> Install> gtk-theme-switch

It does the installing and setting of themes in fluxbox. It will be under tools in your menu.

I use feh for the background setter and as my image viewer, dual purpose. :) 

```
 [submenu] (Backgrounds)
  [exec] (Black) {fbsetroot -solid black}
  [wallpapers] (/usr/share/fluxbox/backgrounds)
  [wallpapers] (~/.fluxbox/backgrounds)
 [end]
```
 
Put this part in your menu and in init change

```
session.screen0.rootCommand:	
to
session.screen0.rootCommand:	fbsetbg -l

```

Then you can just click to set your bg on the fly and it will always use the last background on startup.

Once you have that setup fluxbox should be handling it and you should have transparency.

Yes! Of course i want to see your menu. :)  Just in case you have something i haven't found/thought of.

Wow. Thanks!!! That sizes it and everything!

---

