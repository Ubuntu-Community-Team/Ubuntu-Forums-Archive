---
title: "Fluxbox vs Openbox vs Blackbox"
date: 2008-06-05
forum: Desktop Environments
---

### Post by Inxsible on 2008-06-05
I have been trying out different WMs lately and I have a question.

Can someone tell me what the differences or nuances are between the three?

Now I know, that Fluxbox and Openbox are based on Blackbox and that the new Openbox is a complete re-write. But what else apart from that?

I mean - why did they create Fluxbox, when they had Blackbox- there has to be some differences apart from the Look & Feel, right?

---

### Post by kerry_s on 2008-06-05
yes, they all started from blackbox.
the main reason for the forks was to add features not in blackbox.
openbox, brings more compliance to the desktop specs as well as cleaning of old legacy code.
fluxbox was the next step up, i'm pretty sure you can see the added features right away.

basically, there where they want to be, most changes now are, cleaning of old code and/or keeping up with specs. they have for the most part stayed the same visually, most of the changes have been under the hood.

specs = [http://www.freedesktop.org/wiki/](http://www.freedesktop.org/wiki/)

---

### Post by Inxsible on 2008-06-05
Now I read somewhere that the config files for Openbox was XML based and those for Fluxbox was text based.

Is that true? and what about Blackbox?

If I want to install one of those WMs, what should my choice be based on? Or rather, why should I choose one over the other?


And kerry -- my Xubuntu install went kaput - it just hangs all the time - don't know what I did.

So I am finally going to install Debian Xfce that I had downloaded such a long time ago. Just to see if the debian xfce is faster and better than xubuntu like you said. But eventually I plan to install Debian netinst + WM(flux/black/open?) OR Ubuntu minimal + WM

---

### Post by kerry_s on 2008-06-05
if i remember correctly i think it's xml, but you can edit it with a standard text editor just like you would in fluxbox. jwm uses xml to, it's very easy to get the hang of.

openbox is more of you want to pick everything yourself, it has nothing on the desktop, just a blank slate.

fluxbox you get a toolbar of sorts. :)

some would say openbox is faster, others would say fluxbox has more features, the war go's on and on.
:lolflag:

it all depends on what you use, 
do you use a toolbar?
then icewm or jwm might be more fitting.

you know you can have several wm's installed at once and try them all out.

don't fear xml, it's easy, just looks like this->

```

<?xml version="1.0"?>

<JWM>
<StartupCommand>
conky
</StartupCommand>

<RootMenu height="15" onroot="3">
      <Program label="Terminal">x-terminal-emulator</Program>
      <Program label="WWW Browser">x-www-broser</Program>
      <Program label="Synaptic">sudo synaptic</Program>
      <Separator/>
      <Restart label="Restart"/>
      <Menu label="Exit">
      <Exit label="Exit WM" confirm="false"/>
      <Program label="Reboot">sudo reboot</Program>
      <Program label="Shutdown">sudo halt</Program>
      </Menu>
</RootMenu>

   <Tray  x="0" y="-1" height="28">
      <TrayButton label="Debian  ">root:3</TrayButton>
      <TrayButton label="_">showdesktop</TrayButton>
      <TrayButton label=" T  ">exec:rxvt</TrayButton>
      <TrayButton label=" FM  ">exec:rxvt -g 110x45+0+0 -e clex</TrayButton>
      <TrayButton label="WWW">exec:iceweasel</TrayButton>
      <TaskList/>
      <Dock/>
      <Clock format="  %H:%M  ">asmix -g +1050+670</Clock>
      <Pager/>
      <TrayButton label=" X  ">exec:xset dpms force off</TrayButton>
   </Tray>

   <Group>
      <Name>abiword</Name>
      <Name>soffice</Name>
      <Name>xedit</Name>
      <Option>maximized</Option>
   </Group>

   <WindowStyle>
      <Font>-misc-*-*-*-*-*-*-140-*-*-*-*-*-*</Font>
      <Width>4</Width>
      <Height>20</Height>

      <Active>
        <Text>yellow</Text>
        <Title>#6B6D6B:#4A494A</Title>
        <Corner>yellow</Corner>
        <Outline>black</Outline>
      </Active>

      <Inactive>
        <Text>white</Text>
        <Title>#4A494A:#6B6D6B</Title>
        <Corner>yellow</Corner>
        <Outline>black</Outline>
      </Inactive>
   </WindowStyle>

   <TaskListStyle>
      <Font>-misc-*-*-*-*-*-*-140-*-*-*-*-*-*</Font>
      <ActiveForeground>yellow</ActiveForeground>
      <ActiveBackground>#303438:black</ActiveBackground>
      <Foreground>white</Foreground>
      <Background>#303438:black</Background>
   </TaskListStyle>

   <TrayStyle>
      <Font>-misc-*-*-*-*-*-*-140-*-*-*-*-*-*</Font>
      <Background>black</Background>
      <Foreground>white</Foreground>
   </TrayStyle>

   <PagerStyle>
     <Outline>black</Outline>
     <Foreground>yellow</Foreground>
     <Background>black</Background>
     <ActiveForeground>white</ActiveForeground>
     <ActiveBackground>#303438</ActiveBackground>
   </PagerStyle>

   <MenuStyle>
      <Font>-misc-*-*-*-*-*-*-140-*-*-*-*-*-*</Font>
      <Foreground>white</Foreground>
      <Background>#303438</Background>
      <ActiveForeground>yellow</ActiveForeground>
      <ActiveBackground>#303438:black</ActiveBackground>
   </MenuStyle>

   <PopupStyle enabled="false">
      <Font>-misc-*-*-*-*-*-*-140-*-*-*-*-*-*</Font>
      <Outline>black</Outline>
      <Foreground>black</Foreground>
      <Background>yellow</Background>
   </PopupStyle>

   <IconPath>
      $HOME/.icons
   </IconPath>
   <Desktops count="3">
   <Background type="solid">black</Background>
   </Desktops>

   <DoubleClickSpeed>400</DoubleClickSpeed>
   <DoubleClickDelta>2</DoubleClickDelta>
   <FocusModel>click</FocusModel>
   <SnapMode distance="10">border</SnapMode>
   <MoveMode>outline</MoveMode>
   <ResizeMode>outline</ResizeMode>
   <Key key="Up">up</Key>
   <Key key="Down">down</Key>
   <Key key="Right">right</Key>
   <Key key="Left">left</Key>
   <Key key="h">left</Key>
   <Key key="j">down</Key>
   <Key key="k">up</Key>
   <Key key="l">right</Key>
   <Key key="Return">select</Key>
   <Key key="Escape">escape</Key>
   <Key mask="A" key="Tab">nextstacked</Key>
   <Key mask="A" key="F4">close</Key>
   <Key mask="A" key="#">desktop#</Key>
   <Key mask="A" key="F1">root:3</Key>
   <Key mask="A" key="F2">exec:grun</Key>
   <Key mask="" key="Print">exec:scrot %T.png -e 'gpicview $f'</Key>
   <Key mask="A" key="Print">exec:rxvt -g 40x1+0+0 -e scrot -cd 5 %T.png -e 'gpicview $f'</Key>
   <Key mask="C" key="Print">exec:rxvt -g 15x1+0+0 -e scrot -sb %T.png -e 'gpicview $f'</Key>

</JWM>


```

---

### Post by kerry_s on 2008-06-05
i forgot to mention, most wm's now honor the menu, so if you install "menu" all you have to do is run " update-menus " and the menu will be done for you.

for example here's what the the original jwmrc looks like when i installed and used update-menus:

```

 <?xml version="1.0"?>
 
 <JWM>
 
    <!-- The root menu, if this is undefined you will not get a menu. -->
    <!-- Additional RootMenu attributes: onroot, labeled, label -->
    <RootMenu height="15" onroot="123">
       <Program icon="rxvt.png" label="Terminal">x-terminal-emulator</Program>
          <Program icon="firefox.png" label="Www Browser">x-www-browser</Program>
 
 <!-- #DEBIAN
       <Menu icon="folder.png" label="Applications">
          <Program icon="firefox.png" label="Iceweasel">iceweasel</Program>
 
          <Program icon="audacious.png" label="Audacious">audacious</Program>
          <Program icon="dia.png" label="Dia">dia</Program>
          <Program icon="pidgin.png" label="Pidgin">pidgin</Program>
          <Program icon="gimp.png" label="Gimp">gimp</Program>
          <Program icon="gtk-gnutella.png" label="gtk-gnutella">
             gtk-gnutella
          </Program>
          <Program icon="gxine.png" label="gxine">gxine</Program>
          <Program icon="ooffice.png" label="Open Office">ooffice</Program>
       </Menu>
       <Menu icon="folder.png" label="Utilities">
          <Program icon="xcalc.png">xcalc</Program>
          <Program icon="xfontsel.png">xfontsel</Program>
          <Program icon="xmag.png">xmag</Program>
          <Program icon="xprop.png" label="xprop">
             xprop | xmessage -file -
          </Program>
       </Menu>
 -->
     <Menu label="Debian">
      <Menu label="Applications">
        <Menu label="Accessibility">
          <Program label="Xmag" confirm="false">xmag</Program>
        </Menu>
        <Menu label="Editors">
          <Program label="Xedit" confirm="false">xedit</Program>
        </Menu>
        <Menu label="File Management">
          <Program label="grun" confirm="false">/usr/bin/grun</Program>
        </Menu>
        <Menu label="Graphics">
          <Program label="mtPaint" confirm="false">/usr/bin/mtpaint</Program>
          <Program label="OpenOffice.org Draw" confirm="false">/usr/bin/oodraw</Program>
          <Program label="X Window Snapshot" confirm="false">xwd | xwud</Program>
        </Menu>
        <Menu label="Net">
          <Menu label="Iceape Components">
            <Program label="Iceape Browser" confirm="false">/usr/bin/iceape</Program>
            <Program label="Iceape Composer" confirm="false">/usr/bin/iceape -edit</Program>
          </Menu>
        </Menu>
        <Menu label="Network">
          <Menu label="Communication">
            <Program label="Xbiff" confirm="false">xbiff</Program>
          </Menu>
          <Program label="Iceape Navigator" confirm="false">/usr/bin/iceape</Program>
        </Menu>
        <Menu label="Office">
          <Program label="AbiWord Word Processor" confirm="false">/usr/bin/abiword</Program>
          <Program label="OpenOffice.org Impress" confirm="false">/usr/bin/ooimpress</Program>
          <Program label="OpenOffice.org Writer" confirm="false">/usr/bin/oowriter</Program>
        </Menu>
        <Menu label="Programming">
          <Program label="Python (v2.5)" confirm="false">x-terminal-emulator  -T "Python (v2.5)" -e sh -c "/usr/bin/python2.5"</Program>
        </Menu>
        <Menu label="Science">
          <Menu label="Mathematics">
            <Program label="Xcalc" confirm="false">xcalc</Program>
          </Menu>
        </Menu>
        <Menu label="Shells">
          <Program label="Bash" confirm="false">x-terminal-emulator  -T "Bash" -e sh -c "/bin/bash --login"</Program>
          <Program label="Dash" confirm="false">x-terminal-emulator  -T "Dash" -e sh -c "/bin/dash -i"</Program>
          <Program label="Sh" confirm="false">x-terminal-emulator  -T "Sh" -e sh -c "/bin/sh --login"</Program>
        </Menu>
        <Menu label="System">
          <Menu label="Administration">
            <Program label="alsaconf" confirm="false">x-terminal-emulator  -T "alsaconf" -e sh -c "su-to-root -p root -c /usr/sbin/alsaconf"</Program>
            <Program label="Editres" confirm="false">editres</Program>
            <Program label="Orphaner (all)" confirm="false">x-terminal-emulator  -T "Orphaner (all)" -e sh -c "su-to-root -c '/usr/sbin/orphaner -a'"</Program>
            <Program label="Orphaner (libs)" confirm="false">x-terminal-emulator  -T "Orphaner (libs)" -e sh -c "su-to-root -c /usr/sbin/orphaner"</Program>
            <Program label="Orphaner - editkeep" confirm="false">x-terminal-emulator  -T "Orphaner - editkeep" -e sh -c "su-to-root -c '/usr/sbin/editkeep'"</Program>
            <Program label="Xclipboard" confirm="false">xclipboard</Program>
            <Program label="Xfontsel" confirm="false">xfontsel</Program>
            <Program label="Xkill" confirm="false">xkill</Program>
            <Program label="Xrefresh" confirm="false">xrefresh</Program>
          </Menu>
          <Program label="clex" confirm="false">x-terminal-emulator  -T "clex" -e sh -c "/usr/bin/clex"</Program>
          <Menu label="Hardware">
            <Program label="Xvidtune" confirm="false">xvidtune</Program>
          </Menu>
          <Menu label="Monitoring">
            <Program label="Conky" confirm="false">x-terminal-emulator  -T "Conky" -e sh -c "/usr/bin/conky"</Program>
            <Program label="Pstree" confirm="false">x-terminal-emulator  -T "Pstree" -e sh -c "/usr/bin/pstree.x11"</Program>
            <Program label="Top" confirm="false">x-terminal-emulator  -T "Top" -e sh -c "/usr/bin/top"</Program>
            <Program label="Xconsole" confirm="false">xconsole -file /dev/xconsole</Program>
            <Program label="Xev" confirm="false">x-terminal-emulator -e xev</Program>
            <Program label="Xload" confirm="false">xload</Program>
          </Menu>
          <Menu label="Package Management">
            <Program label="Synaptic Package Manager" confirm="false">/usr/bin/su-to-root -X -c /usr/sbin/synaptic</Program>
          </Menu>
        </Menu>
        <Menu label="Terminal Emulators">
          <Program label="Rxvt" confirm="false">/usr/bin/rxvt-xterm</Program>
        </Menu>
        <Menu label="Tools">
          <Program label="xcal" confirm="false">/usr/bin/xcal</Program>
        </Menu>
        <Menu label="Viewers">
          <Program label="VLC media player" confirm="false">/usr/bin/wxvlc</Program>
          <Program label="Xditview" confirm="false">xditview</Program>
        </Menu>
      </Menu>
      <Menu label="Games">
        <Menu label="Tools">
          <Program label="Rclock" confirm="false">/usr/bin/rclock</Program>
        </Menu>
        <Menu label="Toys">
          <Program label="Oclock" confirm="false">oclock</Program>
          <Program label="Xclock (analog)" confirm="false">xclock -analog</Program>
          <Program label="Xclock (digital)" confirm="false">xclock -digital -update 1</Program>
          <Program label="Xeyes" confirm="false">xeyes</Program>
          <Program label="Xlogo" confirm="false">xlogo</Program>
        </Menu>
      </Menu>
      <Menu label="Help">
        <Program label="Info" confirm="false">x-terminal-emulator  -T "Info" -e sh -c "info"</Program>
        <Program label="Xman" confirm="false">xman</Program>
      </Menu>
    </Menu>

         <Separator/>
       <Restart label="Restart" icon="restart.png"/>
       <Exit label="Exit" confirm="true" icon="exit.png"/>
    </RootMenu>
 
    <Group>
       <Class>Pidgin</Class>
       <Option>sticky</Option>
    </Group>
 
    <Group>
       <Name>gkrellm2</Name>
       <Option>nolist</Option>
    </Group>
 
    <Group>
       <Name>rxvt</Name>
       <Option>vmax</Option>
    </Group>
 
    <!-- Additional tray attributes: autohide, width, border, layer, layout -->
    <Tray  x="0" y="-1" height="32">
 
       <!-- Additional TrayButton attribute: label -->
       <TrayButton label="JWM">root:1</TrayButton>
 
       <TrayButton label="_">showdesktop</TrayButton>
 
       <!-- Additional Pager attributes; width, height -->
       <Pager/>
 
       <!-- Additional TaskList attribute: maxwidth -->
       <TaskList/>
 
       <Dock/>
 
       <!-- Additional Swallow attribute: height -->
       <Swallow name="xload" width="64">
          xload -nolabel -bg black -fg red -hl white
       </Swallow>
 
       <Clock format="%H:%M">xclock</Clock>
 
    </Tray>
 
    <!-- Visual Styles -->
 
    <WindowStyle>
 
       <Font>-*-fixed-*-r-*-*-9-*-*-*-*-*-*-*</Font>
       <Width>4</Width>
       <Height>20</Height>
 
       <Active>
          <Text>white</Text>
          <Title>#70849d:#2e3a67</Title>
          <Corner>white</Corner>
          <Outline>black</Outline>
       </Active>
 
       <Inactive>
          <Text>#aaaaaa</Text>
          <Title>#808488:#303438</Title>
          <Corner>#aaaaaa</Corner>
          <Outline>black</Outline>
       </Inactive>
 
    </WindowStyle>
 
    <TaskListStyle>
       <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
       <ActiveForeground>black</ActiveForeground>
       <ActiveBackground>gray90:gray70</ActiveBackground>
       <Foreground>black</Foreground>
       <Background>gray70:gray90</Background>
    </TaskListStyle>
 
    <!-- Additional TrayStyle attribute: insert -->
    <TrayStyle>
       <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
       <Background>gray90</Background>
       <Foreground>black</Foreground>
    </TrayStyle>
 
    <PagerStyle>
       <Outline>black</Outline>
       <Foreground>gray90</Foreground>
       <Background>#808488</Background>
       <ActiveForeground>#70849d</ActiveForeground>
       <ActiveBackground>#2e3a67</ActiveBackground>
    </PagerStyle>
 
    <MenuStyle>
       <Font>-*-fixed-*-r-*-*-9-*-*-*-*-*-*-*</Font>
       <Foreground>black</Foreground>
       <Background>gray90</Background>
       <ActiveForeground>white</ActiveForeground>
       <ActiveBackground>#70849d:#2e3a67</ActiveBackground>
    </MenuStyle>
 
    <PopupStyle>
       <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
       <Outline>black</Outline>
       <Foreground>black</Foreground>
       <Background>yellow</Background>
    </PopupStyle>
 
    <IconPath>
       $HOME/.icons
    </IconPath>
 
    <!-- Virtual Desktops -->
    <!-- Desktop tags can be contained within Desktops for desktop names. -->
    <Desktops count="4">
 
       <!-- Default background. Note that a Background tag can be
            contained within a Desktop tag to give a specific background
            for that desktop.
        -->
       <Background type="tile">$HOME/bg.xpm</Background>
 
    </Desktops>
 
    <!-- Double click speed (in milliseconds) -->
    <DoubleClickSpeed>400</DoubleClickSpeed>
 
    <!-- Double click delta (in pixels) -->
    <DoubleClickDelta>2</DoubleClickDelta>
 
    <!-- The focus model (sloppy or click) -->
    <FocusModel>sloppy</FocusModel>
 
    <!-- The snap mode (none, screen, or border) -->
    <SnapMode distance="10">border</SnapMode>
 
    <!-- The move mode (outline or opaque) -->
    <MoveMode>opaque</MoveMode>
 
    <!-- The resize mode (outline or opaque) -->
    <ResizeMode>opaque</ResizeMode>
 
    <!-- Key bindings -->
    <Key key="Up">up</Key>
    <Key key="Down">down</Key>
    <Key key="Right">right</Key>
    <Key key="Left">left</Key>
    <Key key="h">left</Key>
    <Key key="j">down</Key>
    <Key key="k">up</Key>
    <Key key="l">right</Key>
    <Key key="Return">select</Key>
    <Key key="Escape">escape</Key>
 
    <Key mask="A" key="Tab">nextstacked</Key>
    <Key mask="A" key="F4">close</Key>
    <Key mask="A" key="#">desktop#</Key>
    <Key mask="A" key="F1">root:1</Key>
    <Key mask="A" key="F2">window</Key>
 
 </JWM>
 

```

i like to do my own menu of course, but at 1 time i did use the stock menu.

---

### Post by Inxsible on 2008-06-05
Oh..I am not worried about XML at all. I use it everyday at work. I just wanted to know the differences that's all.

Since all of them honor "menu" - I guess that gives an easy way to get the programs that you install in the menu quickly without having to remember to manually create an entry each time you install something.

---

### Post by urukrama on 2008-06-05
I made [a comparison]("http://urukrama.wordpress.com/2008/04/26/a-comparison-of-four-window-managers/") of Fluxbox, Openbox, Pekwm and Icewm. You might like it.

---

### Post by Inxsible on 2008-06-05
> **urukrama said:**
> I made [a comparison]("http://urukrama.wordpress.com/2008/04/26/a-comparison-of-four-window-managers/") of Fluxbox, Openbox, Pekwm and Icewm. You might like it.Hey urukrama..

wonderful link....

I guess at the moment I will go for Fluxbox as my WM. Lets see how things work out :)

---

### Post by Nythain on 2008-06-06
if only one of the *boxes would get around to adding a tiling feature, id be in heaven... the efficiency of tiling, the power of a root menu, phenomenal cosmic power, itty bitty resource footprint :P

---

### Post by RedSquirrel on 2008-06-06
Blackbox is no longer in active development.

Yes, Openbox uses XML for its configuration files. Fluxbox uses a custom syntax. Both are easy to follow. 

Fluxbox splits the key bindings configuration into a separate file (~/.fluxbox/keys) whereas Openbox puts that in its massive rc.xml file.

I thought I read somewhere that the Openbox devs were thinking of adding a tiling feature (but maybe that's just the heat gettin' to me :D).

---

### Post by Nythain on 2008-06-06
yeah, i've read in a few places they are considering adding it to openbox, and im hoping, till then ill remain an avid flux fan...

a few people i've mentioned it to bring up the impracticality of it, due to the tiling windows "maximized" nature and not being able to click on the "desktop" for the root menu... keybindings i say to them!!! :P

---

### Post by RedSquirrel on 2008-06-07
> **Nythain said:**
> yeah, i've read in a few places they are considering adding it to openbox, and im hoping, till then ill remain an avid flux fan...

As you probably know, there are a couple of separate applications you can use to achieve some sort of tiling. A brief search on Google turned up this thread on the Arch forums:

[http://bbs.archlinux.org/viewtopic.php?id=48048](http://bbs.archlinux.org/viewtopic.php?id=48048)

I would research the matter further but I'm not a big fan of tiling. I think I'd need a huge monitor or a TV. For my standard 19" (1280x1024), using a tiled layout makes the windows too small for my taste.



> **Nythain said:**
> a few people i've mentioned it to bring up the impracticality of it, due to the tiling windows "maximized" nature and not being able to click on the "desktop" for the root menu... keybindings i say to them!!! :P

Yep. I disabled the mouse bindings for the menus. The only way to get the menus on my system is through **key** bindings. :)

---

### Post by urukrama on 2008-06-07
> **RedSquirrel said:**
> I would research the matter further but I'm not a big fan of tiling. I think I'd need a huge monitor or a TV. For my standard 19" (1280x1024), using a tiled layout makes the windows too small for my taste.

I'm not fond of tiling either (small screen), but it is sometimes handy, especially if you want to view two or three windows side by side. For that purpose, I use [whaw]("http://repetae.net/computer/whaw/"). With just a few mouse movements you can tile (either vertically or horizontally; not both unfortunately) only those windows you want to tile.

---

### Post by Nythain on 2008-06-07
i have a huge monitor (well not huge, 21") and run at 1600x1200, usually with 4 or more terminals and a few other apps open... i love the appeal of tiling, i just hate the configuration and look and specifically, lack of a customizable root menu with other tiling wm's

thanks for the link to the arch forums... i've heard of the app from googling, but just like some of the posters, i couldnt actuall FIND the file, now i can :)

---

### Post by urukrama on 2008-06-07
**Nythain**, have you tried dzen? See [this thread]("http://bbs.archlinux.org/viewtopic.php?id=45364") on the Arch forums.

You could also experiment with 9menu. I tried that in the past, and it looked somewhat promising. I just didn't pursue it.

---

### Post by Nythain on 2008-06-07
thanks, looking into both, though dzen appears to be a lot more effort than the benefit is worth, 9menu is looking pretty simple and snazzy though

---

### Post by InTheFlatField on 2008-06-07
Well as a long time user of fluxbox I guess I'll weigh in on some it's advantages.

**Workspaces**
Virtual desktops.  The other ones have this too.

**Tabs**
This one is fairly obvious.  If you've ever used firefox or any other tabbed application then you know the advantages of them.  Fluxbox has them for applications.

**Easy and powerful customization**
All the configuration in fluxbox is done through simple text based files that can be opened with any text editor.  These include:
-menu:  Menu is entirely decided by the user and can have icons.
-apps:  Define custom behavior for applications.  You can have applications start in certain places, as certain dimensions, in certain workspaces, on every workspace, etc and define those for as many applications as you choose.  Very powerful.
-startup:  Have fluxbox start up whatever you want when it starts.
-keys:  Define anything to any key combination.
-init:  Various options for fluxbox including themes and fonts.

Oh and nifty fake transparency.

For more information head over to: [Fluxbox Wiki]("http://fluxbox-wiki.org/index.php/Fluxbox-wiki")

---

### Post by orengolan on 2008-06-08
I switched to [awesome window manager]("http://awesome.naquadah.org/") after trying gnome, xfce, icewm, fluxbox and openbox.

If you like tiling, hate your mouse and want save time - awesome is for you.
it's very efficient and save space on the screen and there is no desktop or icons (you can add them if you want).
There is one config file (~/.awesomerc) and it's easy to use and extend.

the community is active and friendly.  
there is irc channel, mailing list and wiki.

---

### Post by TenPlus1 on 2008-06-08
OpenBox seems to work a lot faster than Fluxbox to me, and the added bonus of having obconf and obmenu means you can customise it without having to edit text files...

FbPanel is a very good panel add-in that's very fast, low in memory and already has the ebian menu's added...

---

### Post by Dave_Connor on 2009-03-29
I am really liking Fluxbox on my EEE PC. With my window combinations up it short of acts like tiling. The automount feature I loose out on compared to gnome but I already have a script for that. The customize menu and config really add power to the users side. So Fluxbox + 1.

---

### Post by kerry_s on 2009-03-29
> **Dave_Connor said:**
> I am really liking Fluxbox on my EEE PC. With my window combinations up it short of acts like tiling. The automount feature I loose out on compared to gnome but I already have a script for that. The customize menu and config really add power to the users side. So Fluxbox + 1.

try installing ivman for automount.
sudo apt-get install ivman

you can customize the menu's in all wm's, the only thing i miss from fluxbox is the tab grouping thing.

---

### Post by sheshdd on 2009-03-29
that's a very cool box desktop,i started using blackbox on ubuntu the other day,but i did have some problems when i opened nautilus.don't know how to explain it,but when i opened it i got the wallpaper from gnome...and if i remember correctly i even got the gnome upper bar,so there was kind of a mess,i just gave up on it.

but one thing's for sure,blackbox(and all similars) are very cool,i was using bblean(bb for windows) for over 2 o 3 years,it really got my machine running more stable since it replaces the explorer shell.very very cool,too bad i haven't learned enough of this for ubuntu.

---

### Post by snowpine on 2009-03-29
> **sheshdd said:**
> that's a very cool box desktop,i started using blackbox on ubuntu the other day,but i did have some problems when i opened nautilus.don't know how to explain it,but when i opened it i got the wallpaper from gnome...and if i remember correctly i even got the gnome upper bar,so there was kind of a mess,i just gave up on it.


You need to launch Nautilus with the following command:

```
nautilus --no-desktop
```

That should solve the wallpaper problem. 

I highly recommend using a "lite" file manager (pcmanfm, rox, thunar, etc) to experience the full performance benefits of a *box windows manager.

---

### Post by RedSquirrel on 2009-03-29
> **kerry_s said:**
> try installing ivman for automount.
sudo apt-get install ivman

you can customize the menu's in all wm's, the only thing i miss from fluxbox is the tab grouping thing.

This thread was about *box. Where did all these jwm pics come from? :P :D

jwm is nice. One thing I missed when I was tinkering with it is to be able to go the previous workspace via a key binding. There is only "next workspace", which is fine if you only have two workspaces, but I almost always have four. I might look at the code someday, but for now I'm too busy studying fvwm. 

I ran a custom jwm from one of his svn tarballs. There were a couple of bug fixes and I could turn off the confirmation support (*Are you sure you want to exit?* Ugh. I _really_ dislike those things! :mad: :))

---

### Post by kerry_s on 2009-03-30
:lolflag:

i'm just saying it don't have to be *box to do custom menus.

>                      desktop#
                            Switch  to  a specific desktop. To use this, "#" must be specified in
                            the key section. The number 1 to the number  of  desktops  configured
                            are then substituted for "#". Grabbed.


the confirmation is a simple true/false easily disabled.
example:

```
<Exit icon="application-exit.png" label="Exit-X" confirm="false"/>
```

---

### Post by tonytraductor on 2009-05-21
I like dwm, a tiling wm, but it doesn't render java swing guis properly (a java but more than a dwm bug).  
I have experimented with Ion3, which is tiling and tabbed, and does render the java swing guis well, but is far more complicated to navigate, because of the tabbing, in addition to tiling.
So, I've tried the app tile to tile in ob and flux.
It works fine in tux, to a degree.
It tiles full screen, horizontally or vertically, but what it doen't to is tile the focused window left, full height, and tile others right, half/half, heightwise, but rather tiles all windows full height, so if you have three windows, they are all full height next to each other.  But it mostly works.  Same applies to horizontal tiling.

I also tried it in openbox, and it's a bit off.  It always tiles as if there is yet one more window.  Ie., if you have two terminals open and tile, it acts as if there is a third, and leaves that space empty.  Not useful, really.

Both flux and ob make adding your own keybinding quite simple (especially flux).  I used flux as my default wm for quite a while, but recently have been using openbox.
At this juncture, however, I am considering a move to ion3.
I just wish it were a bit simply to control/navigate, more like dwm.
If dwm would render my java guis (one of my main work apps uses java swing), I would be there.  I also wish the documentation were more complete.  I had to use a Spanish manual to learn how to do stuff that was missing from the English one (thankfully I am multilingual).
I tried awm and xmonad, too, but no difference in terms of the java guis.
So, if I want to do my work, and want tiling, my options are using tile with flux or ob (works better with flux), or ion3.

---

### Post by RedSquirrel on 2009-05-21
> **kerry_s said:**
> :lolflag:

i'm just saying it don't have to be *box to do custom menus.



the confirmation is a simple true/false easily disabled.
example:

```
<Exit icon="application-exit.png" label="Exit-X" confirm="false"/>
```

I didn't see your edit until now. tonytraductor's post brought the thread back to life. :)

I exit via a keybinding, 

```
<Key mask="CA" key="q">exit</Key>
```so I think for that it is necessary to compile with the '--disable-confirm' option.

By the way, I'm mostly using jwm these days and I took the time to look through some of the code. It turns out there is a command to go the previous desktop. It's 'pdesktop'. Example:

```
   <Key mask="CA" key="Left">pdesktop</Key>
   <Key mask="CA" key="Right">desktop</Key>

```

---

### Post by stanca on 2009-08-23
Fluxbox!...;)

---

### Post by Rodney9 on 2010-01-16
+ FluxBox

---

