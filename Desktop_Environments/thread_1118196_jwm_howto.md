---
title: "jwm howto?"
date: 2009-04-06
forum: Desktop Environments
---

### Post by pgo on 2009-04-06
I have installed Ubuntu 8.04 LTS via alternate installer, and did a console/text (f4) install on an old laptop.

I've installed xorg, jwm and slim (sudo apt-get install xorg jwm slim).

Now I need a few things:

- a graphical way to shutdown the computer
- "sudo for x" so that I can run things like synaptics, etc. from the GUI.
- some sort of graphical network manager, so I can set up the network interface from the GUI (must support wireless).

Any ideas on what packages to install, or other ways (configuration steps), inorder to achive this? 

Thanks,
Per

---

### Post by andrea000 on 2009-04-06
for a lightweight gui i would go with [Fluxbox]("http://smallboxadmin.blogspot.com/2008/10/adding-lightweight-gui-to-ubuntu-server.html")

---

### Post by pgo on 2009-04-06
> **andrea000 said:**
> for a lightweight gui i would go with [Fluxbox]("http://smallboxadmin.blogspot.com/2008/10/adding-lightweight-gui-to-ubuntu-server.html")

Thank you for the suggestion (and link). I am considering Fluxbox; but will installing Fluxbox in itself take care of my "requirements"? (If not, I'd like to know how to take care of those three things under Fluxbox as well)

Regards,
Per

---

### Post by kerry_s on 2009-04-06
> - a graphical way to shutdown the computer

2 ways you can go about it, just do it by adding to the menu or via script. any which way make sure you add the "NOPASSWD:" to visudo for the commands.
example:
you ALL=(ALL) NOPASSWD: /sbin/shutdown, /sbin/reboot, /sbin/halt, /sbin/poweroff

menu:
```
<Program label="Reboot">exec sudo reboot</Program>
<Program label="Shutdown">exec sudo halt</Program>
<Exit label="Exit-X" confirm="false"/>
```

script:
```
#!/bin/sh
XMESSAGE=$(which gxmessage) || XMESSAGE=xmessage

$XMESSAGE " Logout Selections " -center -buttons "Cancel":1,"Reboot":2,"Shutdown":3,"Exit X":4  
case $? in
1) exit 0 ;;
2) sudo reboot ;;
3) sudo halt ;;
4) jwm -exit ;;
esac

```


> - "sudo for x" so that I can run things like synaptics, etc. from the GUI.


**sudo apt-get install gksu**
then for those programs that need a password use gksudo.
example:
```
<Program label="Package Manager">exec gksudo synaptic</Program>
```

> - some sort of graphical network manager, so I can set up the network interface from the GUI (must support wireless).


**sudo apt-get install network-manager**
add "nm-applet" to your startup.
example:
```
<StartupCommand>
nm-applet
</StartupCommand>
```

---

### Post by kerry_s on 2009-04-06
oops, i meant to put a copy of my .jwmrc for your pickings. :lolflag:
it's really modified, i was practising my vi and went to town on it.
there's also another version on the forums somewhere that has icons and looks like gnome if you want to search for that.
here 1: [http://ubuntuforums.org/showthread.php?t=1079677&highlight=.jwmrc&page=5](http://ubuntuforums.org/showthread.php?t=1079677&highlight=.jwmrc&page=5)

mind you i change all the time, so you can fine several different 1's, most of the time i like simple.

```
<?xml version="1.0"?>

<JWM>

	<!-- Startup commands -->
<StartupCommand>
</StartupCommand>

	<!-- Group settings -->
<Group>
<Name>xmessage</Name>
<Name>xpad</Name>
<Option>noborder</Option>
<Option>nolist</Option>
<Option>notitle</Option>
</Group>

<Group>
<Name>pidgin</Name>
<Name>orage</Name>
<Option>nolist</Option>
</Group>

	<!-- Logout menu -->
<RootMenu height="0" onroot="0" labeled="true" label="Logout Options">
<Separator/><Separator/>
<Program label="Suspend">exec sudo pm-suspend</Program>
<Program label="Reboot">exec sudo reboot</Program>
<Program label="Shutdown">exec sudo halt</Program>
<Exit label="Exit-X" confirm="false"/>
</RootMenu>

<RootMenu height="0" onroot="12">
</RootMenu>

	<!-- Main menu / Right click -->
<RootMenu height="0" onroot="3" labeled="true" label="Main Menu">
<Separator/><Separator/>
<Menu label="Accessories">
<Program label="Edit Menu">exec mousepad ~/.jwmrc</Program>
<Program label="Terminal">exec xterm</Program>
<Program label="Calculator">exec xcalc</Program>
<Program label="Notes">exec xpad</Program>
</Menu>
<Menu label="Graphics">
<Program label="Paint">exec mtpaint</Program>
</Menu>
<Menu label="Internet">
<Program label="WWW-Browser">exec epiphany | xmessage " Loading " -center -timeout 10 &amp;</Program>
<Program label="Messenger">exec pidgin</Program>
</Menu>
<Menu label="Office">
<Program label="Docs">exec abiword</Program>
</Menu>
<Menu label="Sound + Video">
<Program label="Media Player">exec gnome-mplayer</Program>
<Program label="Alsa">exec xterm -e alsamixer</Program>
</Menu>
<Menu label="System Tools">
<Program label="Htop">exec xterm -e htop</Program>
<Program label="Gparted">exec gksudo gparted</Program>
<Program label="Configuration Editor">exec gconf-editor</Program>
</Menu>
<Separator/>
<Menu label="Places">
<Program label="Home Folder">exec Thunar</Program>
<Program label="Desktop">exec Thunar ~/Desktop</Program>
<Program label="Scripts">exec Thunar ~/Scripts</Program>
</Menu>
<Separator/>
<Menu label="Preferences">
<Program label="Appearance">exec lxappearance</Program>
</Menu>
<Menu label="Administration">
<Program label="Root File Manager">exec gksudo "Thunar /"</Program>
<Program label="Root Terminal">exec gksudo "xterm -rv -fn 9x15"</Program>
</Menu>
<Separator/>
<Program label="Logout">exec $HOME/Scripts/logout</Program>
<Separator/>
<Restart label="Restart JWM"/>
</RootMenu>

<RootMenu height="0" onroot="45">
</RootMenu>

	<!-- Volume menu -->
<RootMenu height="0" onroot="6" labeled="true" label="Volume">
<Separator/><Separator/>
<Program label="100">exec amixer set Master 100% unmute</Program>
<Program label="75">exec amixer set Master 75% unmute</Program>
<Program label="50">exec amixer set Master 50% unmute</Program>
<Program label="25">exec amixer set Master 25% unmute</Program>
<Program label="Mute">exec amixer set Master toggle</Program>
</RootMenu>

	<!-- Quicklaunch menu -->
<RootMenu height="0" onroot="7" labeled="true" label="Quick Launcher">
<Separator/><Separator/>
<Program label="Terminal">exec xterm</Program>
<Program label="File Manager">exec Thunar</Program>
<Program label="Web Browser">exec epiphany | xmessage " Loading " -center -timeout 10 &amp;</Program>
</RootMenu>

<RootMenu height="0" onroot="89">
</RootMenu>

	<!-- Bottom panel -->
<Tray x="0" y="-1" height="0">
<TrayButton label="  JWM   ">root: 3</TrayButton>
<TrayButton label="_">showdesktop</TrayButton>
<TrayButton label=" +  ">root: 7</TrayButton>
<TaskList/>
<Dock/>
<TrayButton label=" V  ">root: 6</TrayButton>
<Clock format=" %l:%M   ">exec orage</Clock>
<!--<Pager/>-->
</Tray>

	<!-- Top panel -->
<Tray valign="top" halign="center" height="0" layer="0">
<Clock format="   %A   |   %B   |   %D   "/>
</Tray>

<Tray x="-30" y="-50" height="0" layer="0">
<TrayButton icon="logout.png">root: 0</TrayButton>
</Tray>

	<!-- Styles -->
<WindowStyle>
<Font>Verdana-7</Font>
<Width>4</Width>
<Height>18</Height>
<Active>
<Text>white</Text>
<Title>gray20</Title>
<Corner>gray20</Corner>
<Outline>gray20</Outline>
</Active>
<Inactive>
<Text>white</Text>
<Title>gray20</Title>
<Corner>gray20</Corner>
<Outline>gray20</Outline>
</Inactive>
</WindowStyle>

<TaskListStyle>
<Font>Verdana-7</Font>
<ActiveForeground>white</ActiveForeground>
<ActiveBackground>gray30</ActiveBackground>
<Foreground>white</Foreground>
<Background>gray20</Background>
</TaskListStyle>

<TrayStyle>
<Font>Verdana-12</Font>
<Background>gray20</Background>
<Foreground>white</Foreground>
</TrayStyle>

<PagerStyle>
<Outline>black</Outline>
<Foreground>white</Foreground>
<Background>gray20</Background>
<ActiveForeground>white</ActiveForeground>
<ActiveBackground>gray30</ActiveBackground>
</PagerStyle>

<MenuStyle>
<Font>Verdana-12</Font>
<Foreground>white</Foreground>
<Background>gray20</Background>
<ActiveForeground>white</ActiveForeground>
<ActiveBackground>gray30</ActiveBackground>
</MenuStyle>

<PopupStyle enabled="false"/>

	<!-- Icon paths -->
<IconPath>
$HOME/.icons
</IconPath>

	<!-- Desktops -->
<Desktops count="1">
<!--<Background type="command">exec eval `cat $HOME/.fehbg`</Background>-->
</Desktops>

	<!-- Actions -->
<DoubleClickSpeed>400</DoubleClickSpeed>
<DoubleClickDelta>2</DoubleClickDelta>
<FocusModel>click</FocusModel>
<SnapMode>screen</SnapMode>
<MoveMode>outline</MoveMode>
<ResizeMode>outline</ResizeMode>

	<!-- Keyboard shortcuts  -->
<Key mask="A"  key="F2">exec: gmrun</Key>
<Key mask=""   key="Print">exec: scrot %T.png -e 'mv $f ~/Desktop';xmessage " Screenshot Done! " -center</Key>
<Key mask="A"  key="Print">exec: xterm -g 35x0+0+0 -e scrot -cd 5 %T.png -e 'mv $f ~/Desktop'</Key>
<Key mask=""   key="Super_L">exec: xset dpms force off</Key>
<Key mask="CA" key="Delete">exec: sudo reboot</Key>

</JWM>


```

---

### Post by pgo on 2009-04-07
> **kerry_s said:**
> oops, i meant to put a copy of my .jwmrc for your pickings. :lolflag:
it's really modified, i was practising my vi and went to town on it.
there's also another version on the forums somewhere that has icons and looks like gnome if you want to search for that.
here 1: [http://ubuntuforums.org/showthread.php?t=1079677&highlight=.jwmrc&page=5](http://ubuntuforums.org/showthread.php?t=1079677&highlight=.jwmrc&page=5)
[--&<---8<--]


Awesome, thanks a lot! Vi rules :) (The Gnome look sounds kewl, I'll have a look once I get the stuff working)

Regards,
Per

---

### Post by pgo on 2009-04-07
Great! Thank you so much!

> **kerry_s said:**
> 
**sudo apt-get install network-manager**
add "nm-applet" to your startup.
example:
```
<StartupCommand>
nm-applet
</StartupCommand>
```

I can't get this one working though; nm-applet seems to not be part of network-manager??? Do I need network-manager-gnome, or something like that as well? (I was hopeing to avoid as many Gnome deps as possible)

Are there any alternative packages?

Regards,
Per

---

### Post by kerry_s on 2009-04-07
> **pgo said:**
> Great! Thank you so much!



I can't get this one working though; nm-applet seems to not be part of network-manager??? Do I need network-manager-gnome, or something like that as well? (I was hopeing to avoid as many Gnome deps as possible)

Are there any alternative packages?

Regards,
Per

you might, i'm not sure. have you tried rebooting first to make sure network manager has control of the network devices? try running nm-applet from the terminal see what it says.

yes, there is others. i'm not sure what is in the repo though i use arch linux now.
i hear wicd is pretty good, try> **sudo apt-get install wicd**
for the tray: **wicd-client**

don't worry about libaries they don't affect performance, i have lots of gnome and xfce4  in mine and i'm running on a low spec laptop 450mhz 256mb ram.

---

### Post by pgo on 2009-04-07
> **kerry_s said:**
> you might, i'm not sure. have you tried rebooting first to make sure network manager has control of the network devices? try running nm-applet from the terminal see what it says.

Yeah, I think I tried rebooting. And I couldn't find nm-applet from the shell. So I assume the applet is part of network-manager-gnome and network-manager-kde(?).

> **kerry_s said:**
> yes, there is others. i'm not sure what is in the repo though i use arch linux now.
i hear wicd is pretty good, try> **sudo apt-get install wicd**
for the tray: **wicd-client**

Wicd is working out fine for me, thanks again :) It will be the universe repository for Ubuntu Jaunty. For hardy I had to add **deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras** to */etc/apt/sources.list*. And then run: **wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add -** followed by: **sudo apt-get install wicd**.

> **kerry_s said:**
> don't worry about libaries they don't affect performance, i have lots of gnome and xfce4  in mine and i'm running on a low spec laptop 450mhz 256mb ram.

OK, it's just that I was hopeing to make a nice, lean, clean, absolute minimal desktop install. And, it's seems I've made it now thanks to you. (I'll make a small howto and put on the web somewhere)

Regards,
Per

---

### Post by kerry_s on 2009-04-07
i just came back to tell you to grab wicd if you could. :lolflag:
i was just trying it another machine, i couldn't even get networkmanager working, but wicd worked right away.

minimal and something you really want to use kinda clash.
for example: 
pcmanfm is small does the job, but thunar is way better, never crashes, slows down or has thumbnail problems. thunar comes with other xfce4 junk.

firefox is great, but it's a pig on resources, epiphany on the other hand can do the same thing firefox does, but is heavily simplified. epiphany comes with gnome junk

etc...

it's just a matter of what you want, i got mine to setup to work in as little as 122mb ram(minus vid) which is what my test laptop has. this laptop has 256mb so it has no problems running the same apps that work good on the 122mb laptop.
i can go days without ever dipping into swap on 256mb.

---

### Post by mister_playboy on 2009-04-07
I have a simple question.  How do I get jmw to appear as a choice on the session menu?  I'm testing desktops on my old laptop with 160MB RAM.  Xfce is good, although Firefox and Synaptic are pokey.  LDXE looks sharp, but seems slower than Xfce.  Fluxbox is fast, but a little ugly.  I was wanting a more old school look... jmw looks like just what I want.

What do I need to edit?  LDXE and Fluxbox did that work for me, so I didn't learn anything...

---

### Post by pgo on 2009-04-07
> **mister_playboy said:**
> I have a simple question.  How do I get jmw to appear as a choice on the session menu?  I'm testing desktops on my old laptop with 160MB RAM.  Xfce is good, although Firefox and Synaptic are pokey.  LDXE looks sharp, but seems slower than Xfce.  Fluxbox is fast, but a little ugly.  I was wanting a more old school look... jmw looks like just what I want.

What do I need to edit?  LDXE and Fluxbox did that work for me, so I didn't learn anything...

Yeah, JWM is good if you want an old school (or, Windows inspired) look. And it's probably the most lightweight of the ones you mentioned. 

The answer is; it depends :) What login manager are you using?

Regards,
Per

---

### Post by kerry_s on 2009-04-07
> **mister_playboy said:**
> I have a simple question.  How do I get jmw to appear as a choice on the session menu?  I'm testing desktops on my old laptop with 160MB RAM.  Xfce is good, although Firefox and Synaptic are pokey.  LDXE looks sharp, but seems slower than Xfce.  Fluxbox is fast, but a little ugly.  I was wanting a more old school look... jmw looks like just what I want.

What do I need to edit?  LDXE and Fluxbox did that work for me, so I didn't learn anything...

it should be there just like the others.
to create go's something like this:

**sudo your-editor /usr/share/xsession/jwm.desktop**

```

[Desktop Entry]
Name=JWM
Exec=/usr/bin/jwm
Type=Application

```

i doubt you will like jwm if you didn't like fluxbox or lxde.
try icewm it is the closes thing to the windows look and feel.
**sudo apt-get install icewm icemc**

---

### Post by mister_playboy on 2009-04-08
I retract my statement about LXDE... something weird was going on during that first usage that was thrashing the HDD.  It's definitely faster than Xfce.  Very nice!

My networking won't start up in any session other than Xfce.  Ndiswrapper shows the driver is loaded, but I have to start an Xfce session and then logout and back in to get an internet connection in the other sessions.

Thanks for the help.

---

### Post by kerry_s on 2009-04-08
hmmm, xfce uses the wavelan plugin, it's only for xfce4-panel, so you'll need to have a different network manager for wm's. try wicd or wifi-radar, see whats in the repo.

---

### Post by mister_playboy on 2009-04-08
That's what I was guessing... thanks for pointing me towards a compatiable manager.

One last question... earlier, you posted the config file you use in jwm, and I think it looks great.  Where should that xml config file be placed in the directory?  I just visited the site for jwm, but it's pretty sparse.  :)

---

### Post by kerry_s on 2009-04-08
it goes in your home folder. just open your filemanger and press ctrl+h to see the hidden, hidden files/folders have a "." in front.

i just switched to rox-filer.

---

