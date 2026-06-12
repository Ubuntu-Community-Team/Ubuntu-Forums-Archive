---
title: "Cannot get jwm to show icons"
date: 2008-12-19
forum: Desktop Environments
---

### Post by lykwydchykyn on 2008-12-19
I have jwm installed from the repositories on Intrepid.  I am trying to configure it to use the tango icons.

I set up several IconPath tags, per the documentation, pointing to the tango directories.

Then I added "icon=" parameters to a couple of TrayButton tags..

No matter how many times I restart and try different things, it doesn't work.  The icons are no-show.  It does not give me any errors in ~/.xsession-errors (initially, before setting the iconpath tags, it did; now it doesn't).

Very strangely, if I start a Xephyr window and run jwm in the zephyr window, the icons work fine.

Below is the jwmrc (minus the root menu section, which is tediously long):

```

 <?xml version="1.0"?>
 
 <JWM>
    <IconPath>
	/usr/share/icons/Tango/32x32/places/
    </IconPath>
    <IconPath>
	/usr/share/icons/Tango/32x32/apps/
    </IconPath>
    <IconPath>
	/usr/share/icons/Tango/32x32/actions/
    </IconPath>
    <IconPath>
       $HOME/.icons
    </IconPath>
#Root menu here -- SNIP! 
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
 
       <TrayButton icon="user-desktop.png" popup="Desktop">showdesktop</TrayButton>
       <TrayButton icon="user-home.png" popup="Home Folder">exec:thunar $HOME</TrayButton>

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
 
 
    <!-- Virtual Desktops -->
    <!-- Desktop tags can be contained within Desktops for desktop names. -->
    <Desktops count="4">
 
       <!-- Default background. Note that a Background tag can be
            contained within a Desktop tag to give a specific background
            for that desktop.
        -->
       <Background type="image">$HOME/Wallpapers/astral_cloud.png</Background>
 
    </Desktops>
 
    <!-- Double click speed (in milliseconds) -->
    <DoubleClickSpeed>400</DoubleClickSpeed>
 
    <!-- Double click delta (in pixels) -->
    <DoubleClickDelta>2</DoubleClickDelta>
 
    <!-- The focus model (sloppy or click) -->
    <FocusModel>click</FocusModel>
 
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
    <Key mask="A" key="R">exec:krunner</Key> 
    <Key mask="A" key="T">exec:x-terminal-emulator</Key>
    <StartupCommand>bash $HOME/.jwm/autostart</StartupCommand> 

</JWM>

```

---

### Post by kerry_s on 2008-12-19
remove the "/" on the end.
also using feh to set the background you won't get that long pause on jwm startup.
```
       <Background type="command">eval `cat $HOME/.fehbg`</Background>
or
       <Background type="command">feh --bg-scale /path/to/pic</Background>
```

mine for you pickings:

```
<?xml version="1.0"?>
 
 <JWM>
 
<StartupCommand>
xrdb -load ~/.Xdefaults
</StartupCommand>

<RestartCommand>
xrdb -load ~/.Xdefaults
</RestartCommand>

<Group>
<Name>xmessage</Name>
<Name>gtodo</Name>
<Name>xpad</Name>
<Option>nolist</Option>
<Option>noborder</Option>
<Option>notitle</Option>
</Group>


    <!-- The root menu, if this is undefined you will not get a menu. -->
    <!-- Additional RootMenu attributes: onroot, labeled, label -->
    <RootMenu height="15" onroot="3">
       <Program label="Terminal">xterm</Program>
       <Program label="File Manager">xplorer --directory ~/</Program>
       <Program label="Web Browser">iceweasel 2>/dev/null | xmessage "Loading....." -center  -timeout 5 -button , </Program>
    <Separator/>
       <Menu label="Office">
       <Program label="Calculator">xcalc</Program>
       <Program label="Sticky Note">xpad</Program>
       <Program label="Todo">gtodo</Program>
       <Program label="Documents">oowriter</Program>
       <Program label="Spread sheets">oocalc</Program>
       </Menu>
    <Separator/>
       <Menu label="Administration">
       <Program label="Root File Manager">gksu xplorer</Program>
       <Program label="Manage Programs">gksu synaptic</Program>
       <Program label="Edit jwmrc">leafpad ~/.jwmrc</Program>
       <Program label="Edit xorg.conf">gksu leafpad /etc/X11/xorg.conf</Program>
       <Program label="Gparted">gksu gparted</Program>
       <Program label="Sound settings">xterm -e alsamixer</Program>
       </Menu>
    <Separator/>
       <Menu label="Suspend">
       <Program label="Standby">sudo s2ram -f</Program>
       <Program label="Hibernate">sudo s2disk</Program>
       <Program label="Both">sudo s2both --force</Program>
       </Menu>
       <Menu label="Logout">
       <Exit label="Exit X" confirm="false"/>
       <Program label="Reboot">sudo shutdown -rf now</Program>
       <Program label="Shutdown">sudo shutdown -hf now</Program>
       </Menu>
       <Restart label="Restart JWM"/>
    </RootMenu>


    <RootMenu height="15" onroot="6">
       <Program label="Standby">sudo s2ram -f</Program>
       <Program label="Hibernate">sudo s2disk</Program>
       <Program label="Both">sudo s2both --force</Program>
    </RootMenu>


    <!-- Additional tray attributes: autohide, width, border, layer, layout -->
    <Tray  x="0" y="-1" height="32">
       <!-- Additional TrayButton attribute: label -->
       <TrayButton icon="logo.png" label="JWM  ">root:3</TrayButton>
       <TrayButton label="_">showdesktop</TrayButton>
       <TrayButton icon="home.png">exec: xplorer --directory ~/Desktop</TrayButton>
       <TrayButton icon="firefox.png">exec: iceweasel 2>/dev/null | xmessage "Loading....." -center  -timeout 5 -button , </TrayButton>

       <!-- Additional TaskList attribute: maxwidth -->
       <TaskList/>
       <Dock/>
       <Clock format="%l:%M " width="65">xclock -digital -strftime "%B %e,%Y  %A" -g -10-35</Clock>
    </Tray>


    <Tray  x="-50" y="50" height="32" layer="0">
       <TrayButton label=" Suspend  ">root:6</TrayButton>
    </Tray>


    <Tray  x="-1" y="-100" width="68" autohide="true">
        <Pager/>
        <Swallow name="wmix">wmix</Swallow>
     </Tray>


    <!-- Visual Styles -->
    <WindowStyle>
        <Font>sans-7</Font>
       <Width>4</Width>
       <Height>20</Height>
       <Active>
          <Text>white</Text>
          <Title>#2e3a67:#303438</Title>
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
       <Font>sans-9</Font>
       <ActiveForeground>white</ActiveForeground>
       <ActiveBackground>#2e3a67:#303438</ActiveBackground>
       <Foreground>black</Foreground>
       <Background>gray70:gray90</Background>
    </TaskListStyle>
 
    <!-- Additional TrayStyle attribute: insert -->
    <TrayStyle>
       <Font>sans-14</Font>
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
       <Font>sans-10:bold</Font>
       <Foreground>black</Foreground>
       <Background>gray90</Background>
       <ActiveForeground>white</ActiveForeground>
       <ActiveBackground>#2e3a67:#303438</ActiveBackground>
    </MenuStyle>
 
    <PopupStyle enabled="false"/>
 
    <IconPath>
       $HOME/.icons
    </IconPath>
 
    <!-- Virtual Desktops -->
    <!-- Desktop tags can be contained within Desktops for desktop names. -->
    <Desktops count="3">
 
       <!-- Default background. Note that a Background tag can be
            contained within a Desktop tag to give a specific background
            for that desktop.
       <Background type="command">eval `cat $HOME/.fehbg`</Background>
       <Background type="solid">black</Background>
        -->

       <Background type="solid">black</Background>
 
    </Desktops>
 
    <!-- Double click speed (in milliseconds) -->
    <DoubleClickSpeed>400</DoubleClickSpeed>
 
    <!-- Double click delta (in pixels) -->
    <DoubleClickDelta>2</DoubleClickDelta>
 
    <!-- The focus model (sloppy or click) -->
    <FocusModel>click</FocusModel>
 
    <!-- The snap mode (none, screen, or border) -->
    <SnapMode distance="10">border</SnapMode>
 
    <!-- The move mode (outline or opaque) -->
    <MoveMode>outline</MoveMode>
 
    <!-- The resize mode (outline or opaque) -->
    <ResizeMode>outline</ResizeMode>
 
    <!-- Key bindings -->
    <Key key="Up">up</Key>
    <Key key="Down">down</Key>
    <Key key="Right">right</Key>
    <Key key="Left">left</Key>
    <Key key="Return">select</Key>
    <Key key="Escape">escape</Key>
  
    <Key mask="A" key="Tab">nextstacked</Key>
    <Key mask="" key="F8">close</Key>
    <Key mask="C" key="#">desktop#</Key>
    <Key mask="C" key="Menu">root:3</Key>
    <Key mask="A" key="F2">exec: grun</Key>
    <Key mask="" key="Print">exec: scrot %T.png -e 'mv $f ~/Desktop'; xmessage "Done" -center -timeout 1 -button , </Key>
    <Key mask="A" key="Print">exec: xmessage "Select" -center -timeout 2 -button , ;scrot -sb %T.png -e 'mv $f ~/Desktop'; xmessage "Done" -center -timeout 1 -button , </Key>
    <Key mask="CA" key="Print">exec: xterm -fn 10x20 -g 40x1+300+0 -e scrot -cd 5 %T.png -e 'mv $f ~/Desktop'; xmessage "Done" -center -timeout 1 -button , </Key>
    <Key mask="C" key="Super_L">exec: sleep 1;xset dpms force off</Key>
    <Key mask="C" key="Up">exec: amixer set Master 3+ unmute</Key>
    <Key mask="C" key="Down">exec: amixer set Master 3- unmute</Key>
 </JWM>

```

---

### Post by lykwydchykyn on 2008-12-19
> **kerry_s said:**
> remove the "/" on the end.

Tried that.  Still no joy.
> 
also using feh to set the background you won't get that long pause on jwm startup.
```
       <Background type="command">eval `cat $HOME/.fehbg`</Background>
or
       <Background type="command">feh --bg-scale /path/to/pic</Background>
```

Thanks!  I'll give it a shot.

Are you running yours on Ubuntu or on Debian?  I'm just wondering if this might be a bug in the Ubuntu package.  I'm going to try it on another computer, and then maybe on a debian box to compare.

---

### Post by lykwydchykyn on 2008-12-19
just tried it on a machine running hardy and it works fine there.
Tried it on another Intrepid machine and got the same error.  Looks like maybe a bug in the Intrepid package?

I put a bug report on Launchpad, we'll see what happens.

---

### Post by kerry_s on 2008-12-19
it figures. i only use debian now.
does any icons work?
have you tried linking or copying the icons to ~/.icons?

---

### Post by lykwydchykyn on 2008-12-19
> **kerry_s said:**
> it figures. i only use debian now.
does any icons work?
have you tried linking or copying the icons to ~/.icons?

none of them work.  Not in the menu or anywhere else.

I've tried copying them to ~/.icons, that doesn't change anything.

I'm trying to compile from source now but running into problems building a .deb.

What's interesting is that it is making space for the icon, it's just not displaying it.  If I give it a bad icon path or something, it doesn't make space for the icon.  So it's clearly finding the icon file, it's just not displaying for some reason.

EDIT: trying to attach the screenshot I sent in with the bug report.  It shows how running jwm in Xephyr shows the icons, but normal sessions don't show them.

---

### Post by kerry_s on 2008-12-19
that sucks, have you tried xpm images?
makes me wonder, what version is in intrepid?

---

### Post by lykwydchykyn on 2008-12-19
It's also v2.0.1.  I tried .xpm icons and it didn't work either.  Interestingly, the button sizes changed a bit since the .xpm files were smaller.  Which tells me that it knows how big the images are.  Weird, eh?

EDIT: btw, I compiled from source as well, and it's no different.  I'm beginning to wonder if the problem is with something deeper, like an xlib or something.  But I haven't the first idea of how to sort that out.

---

