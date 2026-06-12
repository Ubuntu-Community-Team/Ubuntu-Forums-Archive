---
title: "jwm desktop config help needed"
date: 2009-01-03
forum: Debian
---

### Post by cmay on 2009-01-03
hi
i  installed  64studio (,debian derivative for audio recording. ) and wants to use a really light windows manager for it as i uuse it for audio production so as little load on running desktop is a good thing. i have icewm and jwm (looks the same ? ) and the troble i have is to get font size bigger on my jwm desktop. i would also like to know how one sets icons and use those on the desktop. i never use icons other than on my studio setup since it is supposed to not look pretty as such but be very handy and practical to start up applications and find the way around the setup. 
i been trying to locate the config files but i cant see the stuff in the terminal since it is too small and i have my eyes operated a few years ago so i do not see that well if gets too small. 

thanks for the time.

---

### Post by cmay on 2009-01-04
i posted the jwmrc i started to work on.
[PHP]<?xml version="1.0"?>

<JWM>

        <!-- The root menu, if this is undefined you will not get a menu. -->
        <!-- Additional RootMenu attributes: onroot, labeled, label height="32" -->
        <RootMenu label="Apps">
                <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>

                <Program icon="rxvt.xpm" label="Terminal">xterm</Program>

                <!-- Addititional Menu attributes: height, labeled -->
                <Menu icon="folder.xpm" label="Applications">
                        <Program icon="firefox.xpm" label="Firefox">firefox</Program>
                        <Program icon="fm.xpm" label="File Manager">xfe</Program>
                        <Program icon="gaim.xpm" label="Gaim">gaim</Program>
                        <Program icon="gxine.png" label="gxine">gxine</Program>
                        <Program icon="xmms.xpm" label="XMMS">xmms</Program>
                       
                </Menu>

                <Menu icon="folder.png" label="Utilities">
                        <Program icon="xcalc.png">xcalc</Program>
                        <Program icon="xfontsel.png">xfontsel</Program>
                        <Program icon="xmag.png">xmag</Program>
                        <Program icon="xprop.png" label="xprop">
                                xprop | xmessage -file -
                        </Program>
                </Menu>

                <Menu icon="folder.xpm" label="grafik">
                        <Program label="gimp">gimp</Program>


                <Menu icon="folder.png" label="sound">
                      <Program label="audacity">audacity</Program>
                              
                </Menu>

                <Separator/> 
            
                <Restart label="Restart" icon="restart.png"/>
                <Exit label="Exit" confirm="true" icon="exit.png"/>

        </RootMenu>

        <Group>
                <Class>Gaim</Class>
                <Option>sticky</Option>
        </Group>

        <Group>
                <Class>xmms</Class>
                <Option>icon:xmms.xpm</Option>
        </Group>

        <!-- Additional tray attributes: autohide, width, border, layer, layout -->
        <Tray  x="0" y="-1" height="32">

                <!-- Additional TrayButton attribute: label -->
                <TrayButton label="cmay_studio"/>

                <!-- Additional Pager attributes; width, height -->
                <Pager/>

                <!-- Additional TaskList attribute: maxwidth -->
                <TaskList/>

                <!-- Additional Swallow attribute: height -->
                <Swallow name="xload" width="64">
                        xload -nolabel -bg black -fg red -hl white
                </Swallow>
                <Clock>xclock</Clock>
        </Tray>

        <!-- Visual Styles -->

        <BorderStyle>
                <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
                <Width>1</Width>
                <Height>15</Height>
                <Foreground>black</Foreground>
                <Background>gray90</Background>
                <ActiveForeground>white</ActiveForeground>
                <!--  <ActiveBackground>#4A5966</ActiveBackground> -->
<Background type="command">eval ‘cat $HOME/.fehbg‘</Background>
        </BorderStyle>

        <TaskListStyle>
                <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
                <ActiveForeground>white</ActiveForeground>
                <ActiveBackground>#8899A6</ActiveBackground>
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
                <Background>#888888</Background>
                <ActiveForeground>#8899AA</ActiveForeground>
                <ActiveBackground>#3A4956</ActiveBackground>
        </PagerStyle>

        <MenuStyle>
                <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
                <Foreground>black</Foreground>
                <Background>gray90</Background>
                <ActiveForeground>white</ActiveForeground>
                <ActiveBackground>#3A4956</ActiveBackground>
        </MenuStyle>

        <Clock>
                <Program>xclock</Program>
        </Clock>

        <PopupStyle>
                <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
                <Outline>black</Outline>
                <Foreground>black</Foreground>
                <Background>yellow</Background>
        </PopupStyle>

        <Menu>
                <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
                <Foreground>black</Foreground>
                <Background>#DCDAD5</Background>
                <ActiveForeground>white</ActiveForeground>
                <ActiveBackground>#3A4956</ActiveBackground>
        </Menu>

        <Icons>
                <IconPath>$HOME/.icons</IconPath>
        </Icons>

        <StartupCommand>
                xli -onroot /usr/share/backgrounds/default.jpg
        </StartupCommand>

        <!-- Virtual Desktops -->
        <!-- Name tags can be contained within Desktops for desktop names. -->
        <Desktops count="4"/>

        <!-- Double click speed (in milliseconds) -->
        <DoubleClickSpeed>400</DoubleClickSpeed>

        <!-- Double click delta (in pixels) -->
        <DoubleClickDelta>2</DoubleClickDelta>

        <!-- The focus model (sloppy or click) -->
        <FocusModel>sloppy</FocusModel>

        <!-- The snap mode (none, screen, or border) -->
        <SnapMode distance="2">border</SnapMode>

        <!-- The move mode (outline or opaque) -->
        <MoveMode>opaque</MoveMode>

        <!-- The resize mode (outline or opaque) -->
        <ResizeMode>opaque</ResizeMode>

        <!-- Key bindings -->
        <Key key="Up">up</Key>
        <Key key="Down">down</Key>
        <Key key="Right">right</Key>
        <Key key="Left">left</Key>
        <Key key="Return">select</Key>
        <Key key="Escape">escape</Key>

        <Key mask="A" key="Tab">next</Key>
        <Key mask="A" key="F4">close</Key>
        <Key mask="A" key="#">desktop#</Key>
        <Key mask="A" key="F1">root</Key>
        <Key mask="A" key="F2">window</Key>

</JWM>[/PHP]

---

### Post by kerry_s on 2009-01-04
that's a old jwmrc config file, what version is the jwm your using.

is that 1 from your /etc/jwm/jwmrc ?

anyways what you do is copy it:

**cp /etc/jwm/jwmrc ~/.jwmrc**

then you can modify it.

stock it uses fixed fonts but you can use smooth fonts, example:
```
<Font>-*-fixed-*-r-*-*-9-*-*-*-*-*-*-*</Font>
can be:
<Font>sans-14</Font>
or if want bold:
<Font>sans-12:bold</Font>
```

i use a mix of font sizes:

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


    <!-- The root menu's -->
    <RootMenu height="15" onroot="3">
       <Program label="Terminal">exec xterm</Program>
       <Program label="File Manager">exec pcmanfm</Program>
       <Program label="Web Browser">exec iceweasel 2>/dev/null | xmessage "Loading....." -center  -timeout 5 -button , </Program>
    <Separator/>
       <Menu label="Office">
       <Program label="Calculator">exec xcalc</Program>
       <Program label="Sticky Note">exec xpad</Program>
       <Program label="Todo">exec gtodo</Program>
       <Program label="Documents">exec oowriter</Program>
       <Program label="Spread sheets">exec oocalc</Program>
       </Menu>
    <Separator/>
       <Menu label="Administration">
       <Program label="Root File Manager">exec gksu pcmanfm /</Program>
       <Program label="Manage Programs">exec gksu synaptic</Program>
       <Program label="Edit jwmrc">exec nedit ~/.jwmrc</Program>
       <Program label="Edit xorg.conf">exec gksu nedit /etc/X11/xorg.conf</Program>
       <Program label="Gparted">exec gksu gparted</Program>
       <Program label="Sound settings">exec xterm -e alsamixer</Program>
       </Menu>
    <Separator/>
       <Menu label="Suspend">
       <Program label="Standby">exec sudo s2ram -f</Program>
       <Program label="Hibernate">exec sudo s2disk --force</Program>
       <Program label="Both">exec sudo s2both --force</Program>
       </Menu>
       <Menu label="Logout">
       <Exit label="Exit X" confirm="false"/>
       <Program label="Reboot">exec sudo shutdown -rf now</Program>
       <Program label="Shutdown">exec sudo shutdown -hf now</Program>
       </Menu>
       <Restart label="Restart JWM"/>
    </RootMenu>


    <RootMenu height="15" onroot="6">
       <Program label="Standby">exec sudo s2ram -f</Program>
       <Program label="Hibernate">exec sudo s2disk</Program>
       <Program label="Both">exec sudo s2both --force</Program>
    </RootMenu>


    <!-- Tray's -->
    <Tray  x="0" y="-1" height="32">
       <TrayButton icon="logo.png" label="JWM  ">root:3</TrayButton>
       <TrayButton label="_">showdesktop</TrayButton>
       <TaskList/>
       <Dock/>
       <Clock format="%l:%M  ">xclock -digital -strftime "(%m)%B %e,%Y  %A" -g -10-35</Clock>
    </Tray>


    <Tray  x="-50" y="50" height="32" layer="0">
       <TrayButton label="Suspend">root:6</TrayButton>
    </Tray>


    <Tray  x="-1" y="-100" width="68" autohide="true">
        <Pager/>
        <Swallow name="wmix">exec wmix</Swallow>
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
       <Font>sans-10</Font>
       <ActiveForeground>white</ActiveForeground>
       <ActiveBackground>#2e3a67:#303438</ActiveBackground>
       <Foreground>black</Foreground>
       <Background>gray70:gray90</Background>
    </TaskListStyle>
 
    <TrayStyle>
       <Font>sans-14</Font>
       <Background>gray</Background>
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
       <Font>sans-12:bold</Font>
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

       <Background type="command">exec xsetroot -solid black</Background>
 
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

### Post by cmay on 2009-01-04
thanks for the reply. 
i use the jwm package in etch but i just updated the menus so all programs in the debian menu are shown. the only trouble  have is the fonts in the terminal i cant figure out how to change. the others are nice to know about as well. do you know how to change font sizes in the terminal. i use terminal pretty much for starting programs i do not have listed in the menu. 
thanks for the time.

---

### Post by kerry_s on 2009-01-04
> **cmay said:**
> thanks for the reply. 
i use the jwm package in etch but i just updated the menus so all programs in the debian menu are shown. the only trouble  have is the fonts in the terminal i cant figure out how to change. the others are nice to know about as well. do you know how to change font sizes in the terminal. i use terminal pretty much for starting programs i do not have listed in the menu. 
thanks for the time.

oh okay, etch uses a older version.

what terminal?
if it's xterm you can press ctrl+right click for the menu.

i use xterm, normally i use fixed fonts "xterm -fn 9x15" but right now i'm using smooth fonts set in my .Xdefaults file.

so just change your line:
[B]<Program icon="rxvt.xpm" label="Terminal">xterm</Program>
to
<Program icon="rxvt.xpm" label="Terminal">xterm -fn 9x15</Program>
[/B]

so in your .Xdefauls file put:

**Xterm*font: 9x15**

or

[B]XTerm*faceName: mono
XTerm*faceSize: 10[/B]

an of course you need to run:

**xrdb -load ~/.Xdefaults**

for it to take effect, i run that in my startup and restart to load.

sorry, if it don't make sence i have a cold and blurry/watery eyes.

---

### Post by cmay on 2009-01-04
i use xterm so its perfect. thanks you. 
 do you know how to put icons on the desktop then i have already used the good stuff from the jwmrc you posted a while ago. i almost never use icons but in case of recording studio its nice to have the most used programs as icons on the desktop. 
thanks for the time.

---

### Post by kerry_s on 2009-01-04
> **cmay said:**
> i use xterm so its perfect. thanks you. 
 do you know how to put icons on the desktop then i have already used the good stuff from the jwmrc you posted a while ago. i almost never use icons but in case of recording studio its nice to have the most used programs as icons on the desktop. 
thanks for the time.

sorry, for getting back late, i had the internet on another laptop i'm working on. trying to install arch linux on a ibm t20, arch just takes ton's of time to configure. :(

i assume your using 1 of the lite weight file managers.
if your using pcmanfm> click edit> preferences> desktop, check manage the desktop...
if your using rox> rox -p=1 (i think)

if your using a filemanager that doesn't do desktops, then install idesk.

---

### Post by cmay on 2009-01-04
i think i will try to install idesk then. thanks a lot and good luck with your arch configuration.

---

### Post by kerry_s on 2009-01-04
> **cmay said:**
> i think i will try to install idesk then. thanks a lot and good luck with your arch configuration.

idesk is a little tricky at first, but once you get the hang of it, its easy.

---

### Post by cmay on 2009-01-15
i have a simple question about jwm. in puppy linux which i use a lot at times jwm is used as desktop enviroment and it looks good and is very easy to work with. but there is a desktop theme chooser that i been trying to find in debian etch respotories and same with a obmenu (gui for menu editing in openbox) for openbox which i use on crunch bang linux since i have a bit poor eyesigth  menu editing with xml files is not always so funny for me.where can i find these program and can obmenu be used for jwm as well as fluxbox and openbox. 
thanks for the time.

---

### Post by cmay on 2009-01-17
i upgraded to lenny. using a lenny xfce and lxde image i found a link to in anohter tread. thanks kerry_s for that post since i got it from there. i also just installed the obmeny since it is in lenny respotories. so is nitrogen. sad thing is that i have to configure jwmrc once more. i had it just great. it showed only two items . terminal and applications. which again showed just firefox and then under text it showed nano mousepad and abiword. and geany. that was really great. but i am still blown away by the speed i got from the lxde desktop on this lenny install. its great. i should have known about this iso image before. thanks for the time. tread solved as i am very very happy. :)

---

