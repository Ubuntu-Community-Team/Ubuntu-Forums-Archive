---
title: "A question about installing openbox and fluxbox on xubuntu."
date: 2009-03-16
forum: Desktop Environments
---

### Post by reprobus on 2009-03-16
I want to try a really light weight window manager such as openbox or fluxbox. If I install these with apt-get will it add them to the login screen under the choose session thingy so I can choose which one to use like it does when you are running regular ubuntu with gnome and install xubuntu desktop or kde desktop. Also is there anything I should know about, any problems or whatnot or do they both just work without any hitches after installation? Also which one would you guys recommend, openbox or fluxbox? Thanks...

---

### Post by kerry_s on 2009-03-16
yes, the will be selectable.

try both:
sudo apt-get install fluxbox openbox

you might also want to try lxde instead of just plain openbox, lxde is the openbox desktop setup. it's lighter then xfce4.

sudo apt-get install lxde

---

### Post by Anzan on 2009-03-16
Fluxbox is easily modified using flat files while Openbox uses XML so I prefer Fluxbox. As well, I don't think that Openbox has the ability to tab diffrent windows together.

You can add anything that you need such as nm-applet to the Startup file.

---

### Post by RedSquirrel on 2009-03-16
> **reprobus said:**
> Also is there anything I should know about, any problems or whatnot or do they both just work without any hitches after installation?

They work fine, but you'll most likely want to customize them. For that, you have to read, read, read. :D

[http://fluxbox.org](http://fluxbox.org)
[http://fluxbox-wiki.org](http://fluxbox-wiki.org)

[http://icculus.org/openbox/index.php/Main_Page](http://icculus.org/openbox/index.php/Main_Page)


> **reprobus said:**
> Also which one would you guys recommend, openbox or fluxbox?

Try both, as kerry_s suggested. Both are tiny and have excellent documentation, so it's just a matter of seeing which one you prefer.

---

### Post by reprobus on 2009-03-16
I tried both. Fluxbox is alright, I didn't like Openbox. I think I will stick with XFCE. Fluxbox would probably be great for older machines that can't handle anything else though.

---

### Post by Anzan on 2009-03-17
Yes, it is. But I use it on everything. 

Once you have it configured exactly as you wish it's so easy to just copy all of your settings.

Enjoy Xfce. It's a nice DE.

---

### Post by kerry_s on 2009-03-17
> **reprobus said:**
> I tried both. Fluxbox is alright, I didn't like Openbox. I think I will stick with XFCE. Fluxbox would probably be great for older machines that can't handle anything else though.

did you try lxde? it's more of a desktop like xfce, but uses light programs, it's a good place to start when your just learning. it will give you a idea what a small setup can be like. it's up to you to get it the way you want.

pics:
[http://images.google.com/images?hl=en&q=lxde&btnG=Search+Images&gbv=2](http://images.google.com/images?hl=en&q=lxde&btnG=Search+Images&gbv=2)

i use jwm on 450mhz 256mb ram, i have it setup to look like gnome.

---

### Post by Anzan on 2009-03-17
kerry_s, that's a very interesting joe's setup.

---

### Post by kerry_s on 2009-03-17
> **Anzan said:**
> kerry_s, that's a very interesting joe's setup.

thanks, i did it on a bet for beer. :lolflag:
my friend thought just because it's a light window manager you can only use it like it is stock, i told him it's up to you to make it what you want, he said he wanted the gnome look but really light, so the bet was on. ;)
i went the whole nine yards, even have the gnome icons in the menus. i since made some changes like splitting the top bar, i don't use a background but still have it.
jwm uses 1.5mb, fresh boot i'm only using a total 24mb.

here's the .jwmrc:
```
<?xml version="1.0"?>

<JWM>

<StartupCommand>
</StartupCommand>

<Group>
 <Name>xmessage</Name>
 <Name>xpad</Name>
 <Option>noborder</Option>
 <Option>nolist</Option>
 <Option>notitle</Option>
</Group>

   <RootMenu height="0" onroot="0">
      	<Program icon="gnome-session-suspend.png" label="Suspend">exec sudo pm-suspend</Program>
      	<Program icon="gnome-session-reboot.png" label="Reboot">exec sudo reboot</Program>
      	<Program icon="gnome-session-halt.png" label="Shutdown">exec sudo poweroff</Program>
      	<Exit icon="application-exit.png" label="Exit-X" confirm="false"/>
   </RootMenu>

   <RootMenu height="0" onroot="12">
   </RootMenu>

   <RootMenu height="0" onroot="3">
      <Menu icon="applications-accessories.png" label="Accessories">
	<Program icon="utilities-terminal.png" label="Terminal">exec xterm</Program>
	<Program icon="accessories-calculator.png" label="Calculator">exec xcalc</Program>
	<Program icon="task-due.png" label="Notes">exec xpad</Program>
      </Menu>
      <Menu icon="applications-graphics.png" label="Graphics">
	<Program icon="applications-graphics.png" label="Paint">exec mtpaint</Program>
      </Menu>
      <Menu icon="applications-internet.png" label="Internet">
	<Program icon="web-browser.png" label="WWW-Browser">exec xmessage " Loading... " -center -timeout 10 -buttons , | firefox &amp;</Program>
      </Menu>
      <Menu icon="applications-office.png" label="Office">
	  <Program icon="applications-office.png" label="Docs">exec abiword</Program>
	  <Program icon="beta-base.png" label="Office">exec soffice-beta</Program>
      </Menu>
      <Menu icon="applications-multimedia.png" label="Sound + Video">
	  <Program icon="applications-multimedia.png" label="Media Player">exec gnome-mplayer</Program>
	  <Program icon="preferences-desktop.png" label="Alsa">exec xterm -e alsamixer</Program>
      </Menu>
      <Menu icon="applications-system.png" label="System Tools">
          <Program icon="gtk-edit.png" label="Edit Menu">exec leafpad ~/.jwmrc</Program>
          <Program icon="utilities-system-monitor.png" label="Htop">exec xterm -e htop</Program>
          <Program label="Gparted">exec gksudo gparted</Program>
      </Menu>
   </RootMenu>

   <RootMenu height="0" onroot="6">
	<Program icon="user-home.png" label="Home Folder">exec thunar</Program>
	<Program icon="user-desktop.png" label="Desktop">exec thunar ~/Desktop</Program>
   </RootMenu>

   <RootMenu height="0" onroot="7">
      <Menu icon="preferences-system.png" label="Administration">
        <Program icon="dialog-warning.png" label="Root File Manager">exec gksudo "thunar /"</Program>
	<Program icon="dialog-warning.png" label="Root Terminal">exec gksudo "xterm -rv -fn 9x15"</Program>
      </Menu>
      <Menu icon="preferences-desktop.png" label="Preferences">
          <Program icon="preferences-desktop-theme.png" label="Appearance">exec lxappearance</Program>
      </Menu>
	<Separator/>
      	<Program icon="system-log-out.png" label="Logout">exec ~/.logout</Program>
	<Separator/>
        <Restart icon="view-refresh.png" label="Restart JWM"/>
   </RootMenu>


   <Tray  x="0" y="0" height="0">
      <TrayButton label=" Applications  ">root: 3</TrayButton>
      <TrayButton label=" Places  ">root: 6</TrayButton>
      <TrayButton label=" System  ">root: 7</TrayButton>
   </Tray>

   <Tray  x="-1" y="0" height="0">
      <TrayButton icon="audio-volume-low.png">exec: amixer set Master 5-</TrayButton>
      <TrayButton icon="audio-volume-high.png">exec: amixer set Master 5+</TrayButton>
      <Clock format="   %a %b %d - %l:%M   ">exec cal | xmessage -g -1+32 -file "-"</Clock>
      <TrayButton icon="system-log-out.png">root: 0</TrayButton>
   </Tray>

   <Tray  halign="center" valign="bottom" height="0">
      <TrayButton icon="go-bottom.png">showdesktop</TrayButton>
      <TaskList/>
      <Dock/>
      <Pager/>
   </Tray>

   <Tray  x="50" y="50" layer="0" layout="vertical" width="0">
      <TrayButton icon="xterm.png">exec: xterm</TrayButton>
      <TrayButton icon="filemanager.png">exec: thunar</TrayButton>
      <TrayButton icon="www.png">exec: xmessage " Loading... " -center -timeout 10 -buttons , | firefox &amp;</TrayButton>
   </Tray>

<!-- Visual Styles -->

   <WindowStyle>

      <Font>Sans-7</Font>
      <Width>4</Width>
      <Height>18</Height>

      <Active>
         <Text>white</Text>
         <Title>gray30:gray20</Title>
         <Corner>gray20</Corner>
         <Outline>black</Outline>
      </Active>

      <Inactive>
         <Text>white</Text>
         <Title>gray20:gray30</Title>
         <Corner>gray30</Corner>
         <Outline>black</Outline>
      </Inactive>

   </WindowStyle>

   <TaskListStyle>
      <Font>Sans-7</Font>
      <ActiveForeground>white</ActiveForeground>
      <ActiveBackground>gray30</ActiveBackground>
      <Foreground>white</Foreground>
      <Background>gray20</Background>
   </TaskListStyle>

   <TrayStyle>
      <Font>Sans-10</Font>
      <Background>black</Background>
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
      <Font>Sans-12</Font>
      <Foreground>white</Foreground>
      <Background>gray20</Background>
      <ActiveForeground>white</ActiveForeground>
      <ActiveBackground>gray30</ActiveBackground>
   </MenuStyle>

   <PopupStyle enabled="false"/>

   <IconPath>
      $HOME/.icons
   </IconPath>
   <IconPath>
      /usr/share/pixmaps
   </IconPath>
   <IconPath>
      /usr/share/icons/gnome/16x16/categories
   </IconPath>
   <IconPath>
      /usr/share/icons/gnome/16x16/actions
   </IconPath>
   <IconPath>
      /usr/share/icons/gnome/16x16/apps
   </IconPath>
   <IconPath>
      /usr/share/icons/gnome/16x16/places
   </IconPath>
   <IconPath>
      /usr/share/icons/gnome/16x16/status
   </IconPath>
   <IconPath>
      /usr/share/icons/hicolor/16x16/apps
   </IconPath>

<!-- Desktops -->
   <Desktops count="3">
	<!--<Background type="command">exec eval `cat  $HOME/.fehbg`</Background>-->
	<Background type="command">exec xsetroot -solid black</Background>
   </Desktops>

   <DoubleClickSpeed>400</DoubleClickSpeed>
   <DoubleClickDelta>2</DoubleClickDelta>
   <FocusModel>click</FocusModel>
   <SnapMode distance="10">border</SnapMode>
   <MoveMode>outline</MoveMode>
   <ResizeMode>outline</ResizeMode>

<!-- Key bindings -->
   <Key mask="A" key="F2">exec: gmrun</Key>
   <Key mask=""  key="Print">exec: scrot %T.png -e 'mv $f ~/Desktop';xmessage " Screenshot Done! " -center</Key>
   <Key mask="A"  key="Print">exec: xterm -g 35x0-1-40 -e scrot -cd 5 %T.png -e 'mv $f ~/Desktop'</Key>
   <Key mask=""  key="Super_L">exec: xset dpms force off</Key>
   <Key mask="CA" key="Delete">exec: xterm -e htop</Key>
</JWM>


```

---

### Post by Anzan on 2009-03-19
Good job. Congratulations.

---

