---
title: "a feeling like in Unity"
date: 2015-10-16
forum: Desktop Environments
---

### Post by oui on 2015-10-16
I did install Unity 14.04 64 bit from DVD first yesterday morning.

And after that Lubuntu 14.04 64 bit from CD a few hours later to compare both.

My decision is that Lubuntu does perfectly the work and is more comprehensive to use.

But

the look on Unity did persuade me.

How to do that und make it better?

I did find an easy way:

- install xli
- install menu
- install jwm (theoretically, jwm does not need some xli or feh, xli is very small compared with feh, but usually jwm is rarely compiled with the option to manage itself background pictures)
- install rox-filer (real unity refuses to manage rox: no way found to place an icon in the unity toolbar for it and divers other extra installed app's!): Why rox-filer? Rox manages itself in ~/.config/rox.sourceforge.net/SendTo in all Linuxes and all Window managers the standard app's you love and wish to use: nothing new to learn! No depleasant surprise like in unity ):P ! Unpleasant: for ex. that Unity refuse to take in consideration some of my added app's and that I  have to learn a lot to change it: no help function to see directly, same thing in the top bar of application windows: you read some translations in you language and can't recognise which app were preinstalled and preselected for the function and which man page you can look to better you comprehension!)
- install xfce4-appfinder
- install grun
- install xxxterm, working well, as the xombrero package prefered by lubuntu for ubuntu minimal is not present in the depository
- copy the directory /usr/share/backgrounds from the ubuntu unity installation at the same place into the partition where you did install lubuntu, and link one of them as "default.jpg"

So, it's the principal adaptation.

You will exit you lubuntu using the function logoff user (I don't know the exact English text: my installation is on French...).
You will find an usual login field. But you also will find little icons on the top right corner. The most central one of them is the icon permitting to accede to new window manager JWM

login now.

JWM appears. you find it uggly, black screen, bar? we will remedy immediately

hit on the main menu key named «JWM»! The poor menu appears. terminal / Debian / lock / restart / exit.

rename system.jwmrc as root in /etc/jwm into system.jwmrc0

and copy the following new version at it's place! with «exit« (name above) re-login and show the changes!

full screen availability!

the tool bar is (hidden) at the left bord (you can change it easily in system.jwmrc if you prefer an other position, for ex. exactly like in unity! You also add pictural icon's where I did use only text only icons,, or both, or add more app's in the bar! But try the text icon «app's» before you do that! it is probably enough ):P . «grun» is also avaible! And under «Debian» you can accede to a lot of app's of your installation! Please don't adapt the file Debian in /etc/jwm: it is a system file managed by the system itself to actualise the Debian menu each time you add or remove app's: You would work for nothing ;) ...

A perfect touch of presentation: adapt the background and text colors from «terminal» (right click on it after it is open, the select «preferences»).

As music lover, I did link the picture partitura_etc (ubuntu DVD 14.04) to default.jpg to define it as background. If the desktop is empty, the effect is fantastic as no rand bar covers the picture!

I wish fun days with that very simple, economix (JWM is a very small app especially if no xli is used!) different desktop (somewhat for «lubuntu minimal»?) :guitar: !

```
<?xml version="1.0"?>

<JWM>

   <!-- The root menu, if this is undefined you will not get a menu. -->
   <!-- Additional RootMenu attributes: onroot, labeled, label -->
   <RootMenu height="15" onroot="12">
      <Program icon="terminal.png" label="terminal">x-terminal-emulator</Program>
      <Separator/>
     <Program icon="rox.png" label="rox">rox</Program>
     <Program icon="leafpad.png" label="editeur">leafpad</Program>
     <Program icon="pcmanfm.png" label="navigateur de fichier">pcmanfm</Program>
      <Separator/>
      <Include>/etc/jwm/debian-menu</Include>
      <Separator/>
      <Program icon="lock.png" label="Lock">
         xscreensaver-command -activate
      </Program>
      <Separator/>
      <Restart label="Restart" icon="restart.png"/>
      <Exit label="Exit" confirm="true" icon="quit.png"/>
   </RootMenu>

   <Group>
      <Class>Pidgin</Class>
      <Option>sticky</Option>
   </Group>

   <Group>
      <Name>gkrellm</Name>
      <Option>nolist</Option>
      <Option>sticky</Option>
   </Group>

   <Group>
      <Name>xterm</Name>
      <Option>vmax</Option>
      <Option>icon:terminal.png</Option>
   </Group>

   <!-- Additional tray attributes: autohide, width, border, layer, layout -->
   <!-- Tray  x="0" y="-1" height="32" autohide="false" -->
   <Tray autohide="true" layout="vertical" insert="left" valign="center">
      <!-- Additional TrayButton attribute: label -->
      <TrayButton label="menu">root:1</TrayButton>
       <TrayButton label="app's">exec:xfce4-appfinder</TrayButton>
      <TrayButton label="grun">exec:grun</TrayButton>
      <TrayButton label="paint">exec:mtpaint</TrayButton>
      <TrayButton label="rox">exec:rox</TrayButton>
      <TrayButton label="web">exec:xxxterm</TrayButton>
      <!-- Additional Pager attribute: labeled -->
      <Pager labeled="true"/>
      <TaskList maxwidth="256"/>
      <Dock/>
      <!-- Additional Swallow attribute: height -->
      <Swallow name="xload" width="64">
         xload -nolabel -bg black -fg red -hl white
      </Swallow>
      <Clock format="%H:%M">xclock</Clock>
   </Tray>

   <!-- Visual Styles -->

   <WindowStyle>

      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Width>4</Width>
      <Height>20</Height>

      <Active>
         <Text>white</Text>
         <Title>gray30:gray60</Title>
         <Outline>black</Outline>
         <Opacity>1.0</Opacity>
      </Active>

      <Inactive>
         <Text>#aaaaaa</Text>
         <Title>#808488:#303438</Title>
         <Outline>black</Outline>
         <Opacity>0.5:0.9:0.1</Opacity>
      </Inactive>

   </WindowStyle>

   <TaskListStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <ActiveForeground>black</ActiveForeground>
      <ActiveBackground>gray80:gray90</ActiveBackground>
      <Foreground>black</Foreground>
      <Background>gray90:gray80</Background>
   </TaskListStyle>

   <!-- Additional TrayStyle attribute: insert -->
   <TrayStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Background>gray90</Background>
      <Foreground>black</Foreground>
      <Opacity>0.75</Opacity>
   </TrayStyle>

   <PagerStyle>
      <Outline>black</Outline>
      <Foreground>gray90</Foreground>
      <Background>#808488</Background>
      <ActiveForeground>#70849d</ActiveForeground>
      <ActiveBackground>#2e3a67</ActiveBackground>
   </PagerStyle>

   <MenuStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Foreground>black</Foreground>
      <Background>gray90</Background>
      <ActiveForeground>white</ActiveForeground>
      <ActiveBackground>#70849d:#2e3a67</ActiveBackground>
      <Opacity>0.85</Opacity>
   </MenuStyle>

   <PopupStyle>
      <Font>-*-fixed-*-r-*-*-10-*-*-*-*-*-*-*</Font>
      <Outline>black</Outline>
      <Foreground>black</Foreground>
      <Background>yellow</Background>
   </PopupStyle>

   <IconPath>
      /usr/share/icons/wm-icons/32x32-gant
   </IconPath>

   <!-- Virtual Desktops -->
   <!-- Desktop tags can be contained within Desktops for desktop names. -->
   <Desktops width="4" height="2">
      <!-- Default background. Note that a Background tag can be
           contained within a Desktop tag to give a specific background
           for that desktop.
       -->
      <!-- Background type="image">/usr/share/backgrounds/default.jpg </Background -->
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

   <StartupCommand>
     <!-- gkrellm &
      exec ~/.browserVorbereitung &
      setxkbmap us intl -->
      xli -onroot -fillscreen /usr/share/backgrounds/default.jpg &
	  exec ~/.mystart &
</StartupCommand>

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

   <Key mask="A" key="Tab">next</Key>
   <Key mask="A" key="F4">close</Key>
   <Key mask="A" key="#">desktop#</Key>
   <Key mask="A" key="F1">root:1</Key>
   <Key mask="A" key="F2">window</Key>
   <Key mask="A" key="F10">maximize</Key>
   <Key mask="A" key="Right">rdesktop</Key>
   <Key mask="A" key="Left">ldesktop</Key>
   <Key mask="A" key="Up">udesktop</Key>
   <Key mask="A" key="Down">ddesktop</Key>

</JWM>
```

to be happy in xxxterm (xombrero) you need in you home a file .xxxterm.conf: my one follow here. please adapt the choices (home page, dictionaries, standard app's to open to) to you needs...

after that, enter once and quit immediately (that create the subdir ~/.xxxterm)! then enter the url of you first favorite and register it with

Esc + :favadd

you see your favorites with

Alt+f

and

create a new tab with

Ctrl+T

You quit with

Esc + :q

More: read in the following .xxxterm.conf ;)

```

##
## GENERAL SETTINGS
##

# NOTE: browser_mode and gui_mode MUST be the first entries in this
# file!

# Normal browser operation (default).
# browser_mode		= normal

# Prevent tracking operation.
# browser_mode		= whitelist

# Classic GUI (default).
# gui_mode		= classic

# Minimalistic GUI.
# gui_mode		= minimal

home			= file:///home/f/.big/my/links/forum.html
download_dir		= ~
# window_maximize	= 1
window_width		= 1024
window_height		= 768
enable_spell_checking	= 1
spell_check_languages	= de_DE, fr_FR, en_GB
default_zoom_level	= 1.0
encoding		= UTF-8
search_string		= [https://encrypted.google.com/search?q=%external_editor](https://encrypted.google.com/search?q=%external_editor)		= gedit -f <file>

# "default_script" points to a script executed by the run_script
# command. The only argument passed to this script is the current URI.
#
# xdefault_script	= ~/playflash.sh

##
## MIME TYPES
##

# PDF, note that xpdf can't load a URI directly; use "@" in front of
# mime_type to indicate to download the file first.

mime_type		= application/pdf,evince

# Specific MIME type for video.
#mime_type		= video/x-ms-wmv,mplayer
#mime_type		= video/quicktime,mplayer

# Default MIME type for video.
#mime_type		= video/*,mplayer

# Default MIME type for audio.
#mime_type		= audio/*,vlc

# Word documents.
# mime_type		= application/calligrawords,soffice

# Ignoring flash can be done by using a non-existent binary name.
# mime_type		= application/x-shockwave-flash,donothing


##
## ADVANCED SETTINGS
##

resource_dir		= /usr/share/xxxterm

##
## ADVANCED COOKIE AND JAVASCRIPT SETTINGS
##

# The following low-level settings are set by the high-level setting
# "browser_mode", and shouldn't be tweaked manually unless you know what
# you are doing.

# The settings for "browser_mode = normal" are as follows:

# allow_volatile_cookies	= 0
# cookie_policy			= allow
# cookies_enabled		= 1
# enable_cookie_whitelist	= 0
# read_only_cookies		= 0
# save_rejected_cookies		= 0
# session_timeout		= 3600
# enable_scripts		= 1
# enable_js_whitelist		= 0
# enable_localstorage		= 1
# enable_plugins		= 1
# enable_plugin_whitelist	= 0

# The settings for "browser_mode = whitelist" are as follows:

# allow_volatile_cookies	= 0
# cookie_policy			= no3rdparty
# cookies_enabled		= 1
# enable_cookie_whitelist	= 1
# read_only_cookies		= 0
# save_rejected_cookies		= 0
# session_timeout		= 3600
# enable_scripts		= 0
# enable_js_whitelist		= 1
# enable_localstorage		= 0
# enable_plugins		= 0
# enable_plugin_whitelist	= 1


##
## KEY BINDINGS
##

# To delete all default keybindings use "keybinding = clearall".
#
# keybinding	= clearall
#
# Key names can be found at:
#
#   [http://git.gnome.org/browse/gtk+/tree/gdk/gdkkeysyms-compat.h](http://git.gnome.org/browse/gtk+/tree/gdk/gdkkeysyms-compat.h)
#
# Just chop off the "GDK_" part and you have the keyname. Or look at:
#
#   [http://git.gnome.org/browse/gtk+/tree/gdk/gdkkeysyms.h](http://git.gnome.org/browse/gtk+/tree/gdk/gdkkeysyms.h)
#
# and chop off "GDK_KEY_".
#
# Be aware that the names are case sensitive!
#
# The default keybindings are the following:
#
# keybinding	= command,colon
# keybinding	= search,slash
# keybinding	= searchb,question
# keybinding	= command_mode,Escape
# keybinding	= insert_mode,i
# keybinding	= cookiejar,M1-j
# keybinding	= downloadmgr,M1-d
# keybinding	= history,M1-h
# keybinding	= print,C-p
# keybinding	= quitall,C-q
# keybinding	= restart,M1-q
# keybinding	= run_script,M1-r
# keybinding	= js toggle,C-j
# keybinding	= cookie toggle,M1-c
# keybinding	= togglesrc,C-s
# keybinding	= yankuri,y
# keybinding	= pasteuricur,p
# keybinding	= pasteurinew,P
# keybinding	= toplevel toggle,F4
# keybinding	= help,F1
# keybinding	= proxy toggle,F2
# keybinding	= searchnext,n
# keybinding	= searchprevious,N
# keybinding	= focusaddress,F6
# keybinding	= focussearch,F7
# keybinding	= promptopen,F9
# keybinding	= promptopencurrent,F10
# keybinding	= prompttabnew,F11
# keybinding	= prompttabnewcurrent,F12
# keybinding	= hinting,f
# keybinding	= hinting,period
# keybinding	= hinting_newtab,S-F
# keybinding	= hinting_newtab,comma
# keybinding	= userstyle,s
# keybinding	= userstyle_global,S
# keybinding	= goback,BackSpace
# keybinding	= goback,M1-Left
# keybinding	= goforward,S-BackSpace
# keybinding	= goforward,M1-Right
# keybinding	= reload,F5
# keybinding	= reload,C-r
# keybinding	= reload,C-l
# keybinding	= favorites,!M1-f
# keybinding	= scrolldown,j
# keybinding	= scrolldown,Down
# keybinding	= scrollup,k
# keybinding	= scrollup,Up
# keybinding	= scrollbottom,G
# keybinding	= scrollbottom,End
# keybinding	= scrolltop,Home
# keybinding	= scrollpagedown,space
# keybinding	= scrollpagedown,C-f
# keybinding	= scrollpagedown,Page_Down
# keybinding	= scrollhalfdown,C-d
# keybinding	= scrollpageup,Page_Up
# keybinding	= scrollpageup,C-b
# keybinding	= scrollhalfup,C-u
# keybinding	= scrollright,l
# keybinding	= scrollright,Right
# keybinding	= scrollfarright,dollar
# keybinding	= scrollleft,h
# keybinding	= scrollleft,Left
# keybinding	= scrollfarleft,0
# keybinding	= statustoggle,C-n
# keybinding	= tabnew,C-t
# keybinding	= tabclose,!C-w
# keybinding	= tabundoclose,U
# keybinding	= tabnext 1,C-1
# keybinding	= tabnext 2,C-2
# keybinding	= tabnext 3,C-3
# keybinding	= tabnext 4,C-4
# keybinding	= tabnext 5,C-5
# keybinding	= tabnext 6,C-6
# keybinding	= tabnext 7,C-7
# keybinding	= tabnext 8,C-8
# keybinding	= tabnext 9,C-9
# keybinding	= tabfirst,C-less
# keybinding	= tablast,C-greater
# keybinding	= tabprevious,C-Left
# keybinding	= tabnext,C-Right
# keybinding	= focusout,C-minus
# keybinding	= focusin,C-equal
# keybinding	= focusin,C-plus
# keybinding	= focusreset,C-0
# keybinding	= editelement,!C-i

```

you can build yourself such a system from each Debian / Ubuntu base (MinimalUbuntu? Mubuntu? OwnMubuntu?)

I install the base and only the base.

The I did do that, it was the day before yesterday in Debian SID. The procedere in Ubuntu would be the same with non important differences. I did use the mini CD to install and in taksel use only the marked option. Not more.

After that, I did reboot to an other Linux, open the new partition and remplace ~/.bash_history. See later my new one!

And after reboot to the new installation, hitting on the key Cursor_up, enough time,+Enter

do the rest ):P .

Easy, or not :D :

After that, I install above files.

Good luck

```

## Please, use following .bash_history instead the original one! Actually my SID graphic base has about 2550 MB size and before did have 1510 MB.
## So that I did install a little more than 1 GB in SID 64 bit as before! 
##
# finish! good luck! you can reboot and fill up after that (or now) the installation as you want with gnome- or libre-office, flashplayer plugin, java-jre, or the free equivalents of both, dictionaries for hunspell, aspell, ispell as you need / create user and add that user in /etc/sudoers, add partitions in /etc/fstab, etc. apt-get remove systemd nano
apt-get autoclean
# you can now copy your /etc/jwm/system-jwmrc as well as your /root/.xombrero.conf or .xxxterm.conf (if you have created no user) or /home/myHome/.xombrero.conf if the simple already exists and place your background picture "default.jpg" into the dir (create it if not available) /usr/share/backgrounds!
apt-get remove systemd nano && apt-get install xorg ratpoison jwm xli xombrero xfce4-appfinder rox-filer leafpad vim-athena mtpaint mplayer2 xsane gocr ispell hunspell
# you can use now the graphic mode! If you do that, you will find a new .bash_history file and continue if you copy the actual one f.ex. cp .bash_history bash_history you can look at the copy using cat! Or continue the installation in CLI mode, is more easy ;-) !
apt-get remove systemd nano && apt-get install xorg ratpoison sudo
# First step, installation without graphic mode is now done! You can use it, be happy, or continue with graphic mode, next line above!
apt-get autoclean
# try now event. to setup your printer before complications appear!
apt-get remove systemd nano && apt-get install gpm clex vim vim-scripts wordgrinder sc alpine aspell alsa-utils alsaplayer-common libasound2-plugins pulseaudio links didiwiki cups cups-filters original-awk gprolog yap gforth ucblogo
# check if you want links or better links2 and if you want some CLI app's like wordgrinder, alpine, etc.
# next line above check if you need the app's at the line end! Probably you don't want to install them...
reboot
apt-get upgrade
apt-get update
apt-get autoclean
# inspect your sources.list file ! you can change it now...
cd /etc/apt
# you did now entry in your fresh installed debian / ubuntu base

```

---

### Post by sudodus on 2015-10-17
Have you seen ToriOS, which also uses jwm?

[http://torios.net](http://torios.net)

---

### Post by TREESofRIGHTEOUSNESS on 2015-10-17
If you want the most recent JWM (with SVG/PNG/JPEG support compiled in) you can use:
[B]ppa:israeldahl/jwm
[/B]If you want a nicer menu and a graphical configuration for jwm
**ppa:torios-dev/torios-core**
And install:
[B]jwm-settings-manager jwm-menu
[/B]There are a lot of other apps you might find useful as well in the torios-core PPA...
But @sudodus is right, check out ToriOS!  You can install ToriOS on top of your current OS (of from a mini iso)
:D

---

### Post by vasa1 on 2015-10-17
I think OP's initial intent was to make Lubuntu feel like "Unity" ;)

@TREEof..., we have a ToriOS thread somewhere around. I'll paste that link here, if I find it. Do you have a list of apps in the torios-core ppa that aren't in Lubuntu or that can't be installed from *buntu standard repos?

Here we are: [http://ubuntuforums.org/showthread.php?t=2200017&highlight=torios](http://ubuntuforums.org/showthread.php?t=2200017&highlight=torios)

Edit: never mind. I was being lazy. The list is here: [https://launchpad.net/~torios-dev/+archive/ubuntu/torios-core](https://launchpad.net/~torios-dev/+archive/ubuntu/torios-core)

---

### Post by oui on 2015-10-17
Thank you very much! I will check willing your links in the next time; they will help me to complete above installations schema!

[COLOR="#FF0000"]I did now publish, now (yesterday, it was to late to check again it before publishing) the new .bash_history used to install the graphic base of my Mubuntu or DebianMiGra (DebianMinimalGraphic!).[/COLOR]

You can, of course, preserve **systemd**, which I did remove with insistance at all the steps as it is now a dependence in a lot of package being often reinstalled by apt-get!

I hoppe that the idea to use a special adapted .bash_history will help more people to manage her installations jobs ;-) !

---

### Post by vasa1 on 2015-10-17
> **oui said:**
>  ... my Mubuntu or DebianMiGra (DebianMinimalGraphic!).
...
IANAL, but I think you shouldn't call your version M**ubuntu**.

What do the mods think?

---

### Post by sudodus on 2015-10-17
> **vasa1 said:**
> IANAL, but I think you shouldn't call your version M**ubuntu**.

What do the mods think?

I agree. I think the names with a letter or two followed by **buntu** are trademarked by Canonical, the company behind Ubuntu.

---

### Post by oui on 2015-10-18
> **sudodus said:**
> I agree. I think the names with a letter or two followed by **buntu** are trademarked by Canonical, the company behind Ubuntu.

ok, I renounce willing (all the more that it is rather a drawback for Ubuntu is: I do not think the same thing happened with Debian! Maybe my method is sometimes known as a good Debian variante and the community where the idea did be born, Ubuntu Lubuntu, die say "no"  ):P !!! The Debian world is really bigger as the Ubuntu world. It includes more distros like Mint, etc...) :D .

---

