---
title: "quick question about small desktop enviroments"
date: 2008-12-09
forum: Desktop Environments
---

### Post by cmay on 2008-12-09
hi.
i have now gotten my older computers up and runnning and i can not use ubuntu since it takes too much ram. so i figure i will try ubuntu with fluxbox black box or jwm. i need to ask what are the most easy to configure minmial desktop and the thing i want the most is to have nice wallpapers and a singel menu since i never use desktop icons but always put my own wall paper like the one in my avatar on my desktop. the blackbox desktop i found last night and been configuring as extra desktop choice on my newer computer runnning 64studio and i switch between gnome and blackbox on that. the two ohter computes i need only a minimal destop on. tehy have been runnning freedos and minix but i need to run jaunty on them so i can help testing a bit. jaunty takes too much ram than i got on any ohter comp than my soundstudio which i do not want to reinstall for that purpose. 
links or how to guides will also make me very happy. 
thanks for the time.

---

### Post by snowpine on 2008-12-09
Hi Cmay,

I am a big fan of Openbox personally. Here is a good guide to configuring it: [http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

My main OS these days is Crunchbang, which is based on Openbox. It uses Nitrogen for managing wallpaper, that is one possible solution for you. I know it's also possible to manage wallpaper using PCManFM.

Fluxbox is cool too; I used Fluxbuntu as my main OS for a few months. 

Good luck!

---

### Post by kerry_s on 2008-12-09
i use jwm, so if you go that way i can help you there.

jwm can set a background, but i use solid black.
images take up resources, memory and there covered 90% of the time, if your trying to save, images are a waste.

i use a lenny custom install on 450mhz 256mb ram, nothing is slow on mine.

---

### Post by imag1narynumber on 2008-12-09
Fluxbox was often my choice, since it's so very easy to configure.  If you can get a light tiling WM going, like dwm, that's good and usually somewhat lightweight.  I personally love e17 and I've been running that for years.  Very light on resources while still giving you some eye-candy.

---

### Post by cmay on 2008-12-09
thanks all of you. i found the xfce desktop and the blackbox enviroment is the ones  will choose from on one of the computers and installed jwm on the ohter of the computers. 
i think your right kery_s about the jwm being fast and with out the wall paper which i will be sad to miss it runs less ram hungry. i must say jaunty needs a lot of ressurses and i may have to switch completely from ubuntu to debian when lenny is coming out as stable. 
i have also bookmarked the openbox link. but i found blackbox and its easy to configure (i did with out a manual so its easy) and i like the desktop look and feel of that one. i edited the blackbox-menu so it shows the programs i will use for just internet and the terminal and restart and exit so have a sort of internet only box standing. its an old computer and i will just use it to run jaunty on right now. 
thanks for the time.

---

### Post by kerry_s on 2008-12-09
you can use a background if you want, i'm not saying you shouldn't if that's what you like. however you would be better off going with feh, just change the jwmrc background command to this:

```
<Background type="command">eval &#8216;cat $HOME/.fehbg&#8216;</Background>
```

then just open any image you want with feh and use the right click set background in feh.

feh is my default image viewer, if you find that a little complicated you can also do it the old fashion way(feh /path/to/pic), you'll just have to change the of the pic name manually for different pics.

there's no reason you can't use lenny now, it will be exactly the same when it go's stable.
net installer:
[http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso)

for custom at package selection uncheck everything.
example after install:
log in as root
apt-get install xorg jwm pcmanfm leafpad
exit
log in as user
startx

---

### Post by mikjp on 2008-12-09
Just changing the desktop environment to a lightweight window manager is not enough to make Ubuntu comfortably run on an old computer. You also have to disable as many services as possible.

I would suggest you to use Debian instead. Do a minimal install of Debian and add only applications you really need. Add xorg and some lightweight window manager. 

See my blog for more info and links...

Greetings,

Mikko

---

### Post by cmay on 2008-12-10
@kerry_s
thanks a lot. i just apt-got feh and it works great. this is something like the most easy way to make a simple setup for a older computer that should look nice and have just a simple menu with firefox and a editor so people do not have all the choices of programs which they do not use and i been thinking about how to make such simple setups when i repair and install linux on older computers for ohters. so this is really useful. thanks that helped a lot.

---

### Post by handydan918 on 2008-12-10
cmay ellucidated mankind with the following;

> i may have to switch completely from ubuntu to debian when lenny is coming out as stable. 

Just so ya understand.

With the Debian development cycle, "stable" doesn't mean it is less crash-prone. 
It means the packages are NOT UPDATED except for security patches.
Ergo, the software is "stable".

"Testing" is the last phase before "stable", and has more up-to-date packages than "stable". In my experience, it is still very  {stable}. Meaning not crash prone.

The most cutting edge packages are found in Sid/Unstable.

Unstable is where things may be what they sound like. Packages in unstable may very well break your toy, just like the kid in Toystory. 

hpe this helps. The whole stable-testing-unstable thing causes a ton of confusion. 

BTW, Ubu is more or less unstable. Think on that.

---

### Post by kerry_s on 2008-12-10
hey cmay, i use a few tricks so i'll put my whole .jwmrc and you just grab what ever you want. let me know if you want something in particular like having jwm swallow xterm to the desktop, more than 1 menu(you can have from 0->9) or anything like that.

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
    <RootMenu height="25" onroot="3">
       <Program label="Terminal">xterm</Program>
       <Program label="File Manager">pcmanfm</Program>
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
       <Program label="Root File Manager">gksu pcmanfm /</Program>
       <Program label="Manage Programs">gksu synaptic</Program>
       <Menu label="Files">
       <Program label="Edit jwmrc">leafpad ~/.jwmrc</Program>
       <Program label="Edit xorg.conf">gksu leafpad /etc/X11/xorg.conf</Program>
       </Menu>
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


    <!-- Additional tray attributes: autohide, width, border, layer, layout -->
    <Tray  x="0" y="-1" height="32">
       <!-- Additional TrayButton attribute: label -->
       <TrayButton icon="logo.png" label="JWM  ">root:3</TrayButton>
       <TrayButton label="_">showdesktop</TrayButton>
       <!-- Additional TaskList attribute: maxwidth -->
       <TaskList/>
       <Dock/>
       <Clock format="%l:%M " width="65">xclock -digital -strftime "%B %e,%Y  %A" -g -10-35</Clock>
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
       <Font>sans-10</Font>
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
       <Font>sans-12</Font>
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
       <Background type="command">eval &#8216;cat $HOME/.fehbg&#8216;</Background>
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
    <Key mask="A" key="F4">close</Key>
    <Key mask="A" key="#">desktop#</Key>
    <Key mask="A" key="F1">root:3</Key>
    <Key mask="A" key="F2">exec: grun</Key>
    <Key mask="CA" key="Escape">exec: xkill</Key>
    <Key mask="" key="Print">exec: scrot %T.png; xmessage "Done" -center -timeout 1 -button , </Key>
    <Key mask="A" key="Print">exec: xmessage "Select" -center -timeout 2 -button , ;scrot -sb %T.png; xmessage "Done" -center -timeout 1 -button , </Key>
    <Key mask="CA" key="Print">exec: xterm -fn 10x20 -g 40x1+300+0 -e scrot -cd 5 %T.png; xmessage "Done" -center -timeout 1 -button , </Key>
    <Key mask="C" key="Super_L">exec: sleep 1;xset dpms force off</Key>
    <Key mask="C" key="Up">exec: amixer set Master 3+ unmute</Key>
    <Key mask="C" key="Down">exec: amixer set Master 3- unmute</Key>
 </JWM>

```

---

### Post by urukrama on 2008-12-10
> **cmay said:**
> i have also bookmarked the openbox link. but i found blackbox and its easy to configure (i did with out a manual so its easy) and i like the desktop look and feel of that one.

I strongly recommend Openbox over Blackbox. Blackbox hasn't been developed for quite a while now, and Openbox is probably the most polished window manager of its kind. Openbox is very easy to configure, especially with obconf and obmenu. It is very light as well, and you'll find plenty of themes to make it look pretty. Openbox was originally based on Blackbox code (it is now entirely rewritten), so its look and feel are very similar to Blackbox. As Openbox is very popular, you'll also find more support for any problems that you might run into than you would with Blackbox, which is not so widely used these days.

The Openbox guide linked to earlier might also be useful if you don't use Openbox. It covers a lot of things that are also applicable to other window managers (such as setting the Gtk theme, icons on the desktop, panels, wallpapers, and so on.)

---

### Post by cmay on 2008-12-10
@kerry_s thanks a lot. i am installing a base install and i copied this post of yours . i also found the jwm homepage and i am going to drink some coffee and set it up tonight. thanks a lot. it means a lot to me.

---

### Post by kerry_s on 2008-12-10
> **cmay said:**
> @kerry_s thanks a lot. i am installing a base install and i copied this post of yours . i also found the jwm homepage and i am going to drink some coffee and set it up tonight. thanks a lot. it means a lot to me.

your welcome, let me know if you get stuck or need help setting up autologin or anything.

---

### Post by cmay on 2008-12-10
thanks . :)

---

### Post by cmay on 2008-12-18
done . i fixed a old computer and  i got the jwm desktop installed and set background and it looks nice. i think i am going to start using this look and feel on old computers i repair find and fix and the older ones i almost just  can fish out of the dumpsters and fix and bring back to life i will give away looking something like this. its debian testing one of the unstable builds i used this time buit for others that needs a littel extra pc for theiir kids i think this could go with a stable etch or lenny .
thanks for the help all of you .

---

### Post by kerry_s on 2008-12-18
looks good, i like that debian swirl, might just have to steal it. :lolflag:

centered or scaled?

---

### Post by cmay on 2008-12-18
scaled. iits actually pretty niice i think. there are much more artwork in lenny than there is in etch. the blue swirls are also many more versions of. and there is a splash image of this picture i used here.

---

### Post by kerry_s on 2008-12-18
> **cmay said:**
> scaled. iits actually pretty niice i think. there are much more artwork in lenny than there is in etch. the blue swirls are also many more versions of. and there is a splash image of this picture i used here.

i'm just joking, i prefer just plain black, no images. :lolflag:

i'm 1 of those who prefer not to waste any extra resources on anything that is not actually doing something, other than looking good.

---

### Post by cmay on 2008-12-18
i seen some of your other screenshots. its actually pretty impressive desktop even that i like to use my homemade minix bsd and linux image like my avatar on black background. but i was impressed enough to start looking at jwm  :)

---

### Post by kerry_s on 2008-12-18
yeah, jwm is really underrated sure it doesn't have some features, but it has enough if not more. i think it's mostly due to the lack of how to's and how young it is compared to other wm's. but a lot more people are starting to see some of the advantages and it's staring to become the wm for most mini distro's. 

i had a heck of a time learning it when i started using it and trust me, i've read the man pages hundreds of times, trying all kinds of things, using the "jwm -p" to check if your settings is okay before you restart will save your butt.

---

### Post by mikjp on 2008-12-20
JWM is really cool, but so are some other window managers like pekwm and windowmaker. At the moment I'm using JWM on my openSUSE box.

---

