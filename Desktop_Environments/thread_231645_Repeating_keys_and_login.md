---
title: "Repeating keys and login"
date: 2006-08-07
forum: Desktop Environments
---

### Post by Dors on 2006-08-07
most of the times when i boot my pc, when i start pressing keys to login in the login screen, each key i press start to repeat 2,3,4,5 or more times and i cant login, when i go to the command line i have no problems at all.
What can i do to solve the repeating key problem?
TY!:confused:

---

### Post by fourchannel on 2006-08-07
have you tried using another keyboard? most of the time repeating keys are a fault in the keyboard.

EDIT:
sorry I misread what you had said, and kinda overlooked that you said the CLI was fine.

Can you post your /etc/X11/xorg.conf file so we can see if the problem lies in there?

can you also post your /etc/gdm/gdm.conf aswell?

remember to put the output inside of [code] tags  =D

---

### Post by Dors on 2006-08-08
Well i still have the same problem, keys keep repeating them self.Hope somebody can help, im still new dont know anything about this files, i just changed once the xorg.conf to enable my serial mouse, thats all.[-o< 
here are my files:
1)xorg.conf
```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/ttyS0"
	Option		"Protocol"		"Microsoft"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Silicon Integrated Systems (SiS) 530/620 PCI/AGP VGA Display Adapter"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-57
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems (SiS) 530/620 PCI/AGP VGA Display Adapter"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Dors on 2006-08-08
And...
its a bit too much dont know what to erase to make it less
2)gdm.conf
```

[daemon]
# Automatic login, if true the first local screen will automatically logged in
# as user as set with AutomaticLogin key.
AutomaticLoginEnable=false
AutomaticLogin=

# Timed login, useful for kiosks.  Log in a certain user after a certain amount
# of time.
TimedLoginEnable=false
TimedLogin=
TimedLoginDelay=30

# The GDM configuration program that is run from the login screen, you should
# probably leave this alone.
#Configurator=/usr/sbin/gdmsetup --disable-sound --disable-crash-dialog

# The chooser program.  Must output the chosen host on stdout, probably you
# should leave this alone.
#Chooser=/usr/lib/gdm/gdmchooser

# The greeter for local (non-xdmcp) logins.  Change gdmlogin to gdmgreeter to
# get the new graphical greeter.
Greeter=/usr/lib/gdm/gdmgreeter

# The greeter for xdmcp logins, usually you want a less graphically intensive
# greeter here so it's better to leave this with gdmlogin
#RemoteGreeter=/usr/lib/gdm/gdmlogin

# Launch the greeter with an additional list of colon separated GTK+ modules.
# This is useful for enabling additional feature support e.g. GNOME
# accessibility framework. Only "trusted" modules should be allowed to minimize
# security holes
#AddGtkModules=false
# By default, these are the accessibility modules.
#GtkModulesList=gail:atk-bridge:/usr/lib/gtk-2.0/modules/libdwellmouselistener:/usr/lib/gtk-2.0/modules/libkeymouselistener

# Default path to set.  The profile scripts will likely override this value.
# This value will be overridden with the value from /etc/default/login if it
# contains "ROOT=<pathvalue>".
#DefaultPath=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
# Default path for root.  The profile scripts will likely override this value.
# This value will be overridden with the value from /etc/default/login if it
# contains "SUROOT=<pathvalue>".
#RootPath=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

# If you are having trouble with using a single server for a long time and want
# GDM to kill/restart the server, turn this on.  On Solaris, this value is
# always true and this configuration setting is ignored.
#AlwaysRestartServer=false

# User and group used for running GDM GUI applicaitons.  By default this is set
# to user "gdm" and group "gdm".  This user/group should have very limited
# permissions and access to ony the gdm directories and files.
User=gdm
Group=gdm

# To try to kill all clients started at greeter time or in the Init script.
# does not always work, only if those clients have a window of their own.
#KillInitClients=true
LogDir=/var/log/gdm
# You should probably never change this value unless you have a weird setup.
PidFile=/var/run/gdm.pid

# Note that a post login script is run before a PreSession script.  It is run
# after the login is successful and before any setup is run on behalf of the
# user.
PostLoginScriptDir=/etc/gdm/PostLogin/
PreSessionScriptDir=/etc/gdm/PreSession/
PostSessionScriptDir=/etc/gdm/PostSession/
DisplayInitDir=/etc/gdm/Init
# Distributions:  If you have some script that runs an X server in say VGA
# mode, allowing a login, could you please send it to me?
#FailsafeXServer=
# if X keeps crashing on us we run this script.  The default one does a bunch
# of cool stuff to figure out what to tell the user and such and can run an X
# configuration program.
XKeepsCrashing=/etc/gdm/XKeepsCrashing
# Reboot, Halt and suspend commands, you can add different commands separated
# by a semicolon.  GDM will use the first one it can find.
RebootCommand=/sbin/shutdown -r now "Rebooted from gdm menu."
HaltCommand=/sbin/shutdown -h now "Halted from gdm menu."
SuspendCommand=/usr/sbin/pmi action sleep
HibernateCommand=/usr/sbin/pmi action hibernate
# Probably should not touch the below this is the standard setup.
ServAuthDir=/var/lib/gdm
# This is our standard startup script.  A bit different from a normal X
# session, but it shares a lot of stuff with that.  See the provided default
# for more information.
BaseXsession=/etc/gdm/Xsession
# This is a directory where .desktop files describing the sessions live.  It is
# really a PATH style variable since 2.4.4.2 to allow actual interoperability
# with KDM.  Note that <dmconfdir>/Sessions is there for backwards
# compatibility reasons with 2.4.4.x.
SessionDesktopDir=/etc/X11/sessions/:/etc/dm/Sessions/:/usr/share/gdm/BuiltInSessions/:/usr/share/xsessions/
# This is the default .desktop session.  One of the ones in SessionDesktopDir
DefaultSession=default.desktop
# Better leave this blank and HOME will be used.  You can use syntax ~/ below
# to indicate home directory of the user.  You can also set this to something
# like /tmp if you don't want the authorizations to be in home directories.
# This is useful if you have NFS mounted home directories.  Note that if this
# is the home directory the UserAuthFBDir will still be used in case the home
# directory is NFS, see security/NeverPlaceCookiesOnNFS to override this
# behavior.
UserAuthDir=
# Fallback directory for writing authorization file if user's home directory
# is not writable.
UserAuthFBDir=/tmp
UserAuthFile=.Xauthority
# The X server to use if we can't figure out what else to run.
StandardXServer=/usr/bin/X
# The maximum number of flexible X servers to run.
#FlexibleXServers=5
# And after how many minutes should we reap the flexible server if there is no
# activity and no one logged on.  Set to 0 to turn off the reaping.  Does not
# affect Xnest flexiservers.
#FlexiReapDelayMinutes=5
# The X nest command.
Xnest=/usr/bin/Xnest -br -br -audit 0 -name Xnest
# Automatic VT allocation.  Right now only works on Linux.  This way we force
# X to use specific vts.  turn VTAllocation to false if this is causing
# problems.
FirstVT=7
VTAllocation=true
# Should double login be treated with a warning (and possibility to change VT's
# on Linux and FreeBSD systems for console logins)
#DoubleLoginWarning=true
# Should a second login always resume the current session and switch VT's on
# Linux and FreeBSD systems for console logins
#AlwaysLoginCurrentSession=true

# If true then the last login information is printed to the user before being
# prompted for password.  While this gives away some info on what users are on
# a system, it on the other hand should give the user an idea of when they
# logged in and if it doesn't seem kosher to them, they can just abort the
# login and contact the sysadmin (avoids running malicious startup scripts).
#DisplayLastLogin=false

# Program used to play sounds.  Should not require any 'daemon' or anything
# like that as it will be run when no one is logged in yet.
SoundProgram=/usr/lib/gdmplay

# These are the languages that the console cannot handle because of font
# issues.  Here we mean the text console, not X.  This is only used when there
# are errors to report and we cannot start X.
# This is the default:
#ConsoleCannotHandle=am,ar,az,bn,el,fa,gu,hi,ja,ko,ml,mr,pa,ta,zh

# This determines whether GDM will honor requests DYNAMIC requests from the
# gdmdynamic command.
#DynamicXServers=false

# This determines whether GDM will send notifications to the console.
#ConsoleNotify=true

# How long gdm should wait before it assumes a started Xserver is defunct and
# kills it.  10 seconds should be long enough for X, but Xgl may need 20 or 25. 
GdmXserverTimeout=10

[security]
# Allow root to login.  It makes sense to turn this off for kiosk use, when
# you want to minimize the possibility of break in.
AllowRoot=false
# Allow login as root via XDMCP.  This value will be overridden and set to
# false if the /etc/default/login file exists and contains
# "CONSOLE=/dev/login", and set to true if the /etc/default/login file exists
# and contains any other value or no value for CONSOLE.
AllowRemoteRoot=false
# This will allow remote timed login.
AllowRemoteAutoLogin=false
# 0 is the most restrictive, 1 allows group write permissions, 2 allows all
# write permissions.
RelaxPermissions=0
# Check if directories are owned by logon user.  Set to false, if you have, for
# example, home directories owned by some other user.
CheckDirOwner=true
# Number of seconds to wait after a failed login
#RetryDelay=1
# Maximum size of a file we wish to read.  This makes it hard for a user to DoS
# us by using a large file.
#UserMaxFile=65536
# If true this will basically append -nolisten tcp to every X command line, a
# good default to have (why is this a "negative" setting? because if it is
# false, you could still not allow it by setting command line of any particular
# server).  It's probably better to ship with this on since most users will not
# need this and it's more of a security risk then anything else.
# Note: Anytime we find a -query or -indirect on the command line we do not add
# a "-nolisten tcp", as then the query just wouldn't work, so this setting only
# affects truly local sessions.
DisallowTCP=true
# By default never place cookies if we "detect" NFS.  We detect NFS by
# detecting "root-squashing".  It seems bad practice to place cookies on things
# that go over the network by default and thus we do not do it by default.
# Sometimes you can however use safe remote filesystems where this is OK and
# you may want to have the cookie in your home directory.
#NeverPlaceCookiesOnNFS=true
# Will cause PAM_DISALLOW_NULL_AUTHTOK to be passed as a flag to
# pam_authenticate and pam_acct_mgmt, disallowing NULL password.  This setting
# will only take effect if PAM is being used by GDM.  This value will be
# overridden with the value from /etc/default/login if it contains
# "PASSREQ=[YES|NO]"
#PasswordRequired=false
# Specifies the PAM Stack to use, "gdm" by default.
PamStack=gdm

# XDMCP is the protocol that allows remote login.  If you want to log into GDM
# remotely (I'd never turn this on on open network, use ssh for such remote
# usage that).  You can then run X with -query <thishost> to log in, or
# -indirect <thishost> to run a chooser.  Look for the 'Terminal' server type
# at the bottom of this config file.
[xdmcp]
# Distributions: Ship with this off.  It is never a safe thing to leave out on
# the net.  Setting up /etc/hosts.allow and /etc/hosts.deny to only allow local
# access is another alternative but not the safest.  Firewalling port 177 is
# the safest if you wish to have xdmcp on.  Read the manual for more notes on
# the security of XDMCP.
Enable=false
# Honor indirect queries, we run a chooser for these, and then redirect the
# user to the chosen host.  Otherwise we just log the user in locally.
#HonorIndirect=true
# Maximum pending requests.
#MaxPending=4
#MaxPendingIndirect=4
# Maximum open XDMCP sessions at any point in time.
#MaxSessions=16
# Maximum wait times.
#MaxWait=15
#MaxWaitIndirect=15
# How many times can a person log in from a single host.  Usually better to
# keep low to fend off DoS attacks by running many logins from a single host.
# This is now set at 2 since if the server crashes then GDM doesn't know for
# some time and wouldn't allow another session.
#DisplaysPerHost=2
# The number of seconds after which a non-responsive session is logged off.
# Better keep this low.
#PingIntervalSeconds=15
# The port.  177 is the standard port so better keep it that way.
#Port=177
# Willing script, none is shipped and by default we'll send hostname system id.
# But if you supply something here, the output of this script will be sent as
# status of this host so that the chooser can display it.  You could for
# example send load, or mail details for some user, or some such.
#Willing=/etc/gdm/Xwilling

[gui]
# The specific gtkrc file we use.  It should be the full path to the gtkrc that
# we need.  Unless you need a specific gtkrc that doesn't correspond to a
# specific theme, then just use the GtkTheme key.
#GtkRC=/usr/share/themes/Default/gtk-2.0/gtkrc

# The GTK+ theme to use for the GUI.
GtkTheme=Human
# If to allow changing the GTK+ (widget) theme from the greeter.  Currently
# this only affects the standard greeter as the graphical greeter does not yet
# have this ability.
AllowGtkThemeChange=true
# Comma separated list of themes to allow.  These must be the names of the
# themes installed in the standard locations for gtk themes.  You can also
# specify 'all' to allow all installed themes.  These should be just the
# basenames of the themes such as 'Thinice' or 'LowContrast'.
GtkThemesToAllow=Human,HighContrast,HighContrastInverse,LowContrast

# Maximum size of an icon, larger icons are scaled down.
#MaxIconWidth=128
#MaxIconHeight=128

[greeter]
# The following options for setting titlebar and setting window position are
# only useful for the standard login (gdmlogin) and are not used by the
# themed login (gdmgreeter).
#
# The standard login has a title bar that the user can move.
#TitleBar=true
# Don't allow user to move the standard login window.  Only makes sense if
# TitleBar is on.
#LockPosition=false
# Set a position for the standard login window rather then just centering the
# window.  If you enter negative values for the position it is taken as an
# offset from the right or bottom edge.
#SetPosition=false
#PositionX=0
#PositionY=0

# Enable the Face browser.  Note that the Browser key is only used by the
# standard login (gdmlogin) program.  The Face Browser is enabled in 
# the Graphical greeter by selecting a theme that includes the Face
# Browser, such as happygnome-list.  The other configuration values that
# affect the Face Browser (MinimalUID, DefaultFace, Include, Exclude,
# IncludeAll, GlobalFaceDir) are used by both the Standard and Themed
# greeter.
Browser=false
# The default picture in the browser.
#DefaultFace=/usr/share/pixmaps/nobody.png
# User ID's less than the MinimalUID value will not be included in the face
# browser or in the gdmselection list for Automatic/Timed login.  They will not
# be displayed regardless of the settings for Include and Exclude.
MinimalUID=1000
# Users listed in Include will be included in the face browser and in the
# gdmsetup selection list for Automatic/Timed login.  Users should be separated
# by commas.
#Include=
# Users listed in Exclude are excluded from the face browser and from the
# gdmsetup selection list for Automatic/Timed login.  Excluded users will still
# be able to log in, but will have to type their username.  Users should be
# separated by commas.  
Exclude=bin,daemon,adm,lp,sync,shutdown,halt,mail,news,uucp,operator,nobody,gdm,postgres,pvm,rpm
# By default, an empty include list means display no users.  By setting
# IncludeAll to true, the password file will be scanned and all users will be
# displayed except users excluded via the Exclude setting and user ID's less
# than MinimalUID.  Scanning the password file can be slow on systems with
# large numbers of users and this feature should not be used in such
# environments.  The setting of IncludeAll does nothing if Include is set to a
# non-empty value.
IncludeAll=true
# If user or user.png exists in this dir it will be used as his picture.
#GlobalFaceDir=/usr/share/pixmaps/faces/

# File which contains the locale we show to the user.  Likely you want to use
# the one shipped with GDM and edit it.  It is not a standard locale.alias
# file, although GDM will be able to read a standard locale.alias file as well.
LocaleFile=/etc/gdm/locale.conf
# Logo shown in the standard greeter.
#Logo=/usr/share/pixmaps/gdm-foot-logo.png
# Logo shown on file chooser button in gdmsetup (do not modify this value).
#ChooserButtonLogo=/usr/share/pixmaps/gdm-foot-logo.png
# The standard greeter should shake if a user entered the wrong username or
# password.  Kind of cool looking
#Quiver=true

# The Actions menu (formerly system menu) is shown in the greeter, this is the
# menu that contains reboot, shutdown, suspend, config and chooser.  None of
# these is available if this is off.  They can be turned off individually
# however.
#SystemMenu=true
# Configuration is available from the system menu of the greeter.
ConfigAvailable=false
# Should the chooser button be shown.  If this is shown, GDM can drop into
# chooser mode which will run the xdmcp chooser locally and allow the user to
# connect to some remote host.  Local XDMCP does not need to be enabled,
# however.
#ChooserButton=true

# Welcome is for all console logins and RemoteWelcome is for remote logins
# (through XDMCP).
# DefaultWelcome and DefaultRemoteWelcome set the string for Welcome to
# "Welcome" and for DefaultWelcome to "Welcome to %n", and properly translate
# the message to the appropriate language.  Note that %n gets translated to the
# hostname of the machine.  These default values can be overridden by setting
# DefaultWelcome and/or DefaultRemoteWelcome to false, and setting the Welcome
# and DefaultWelcome values as desired.  Just make sure the strings are in
# utf-8 Note to distributors, if you wish to have a different Welcome string
# and wish to have this translated you can have entries such as
# "Welcome[cs]=Vitejte na %n".
DefaultWelcome=true
DefaultRemoteWelcome=true
#Welcome=Welcome
#RemoteWelcome=Welcome to %n

# Xinerama screen we use to display the greeter on.  Not for true multihead,
# currently only works for Xinerama.
#XineramaScreen=0
# Background settings for the standard greeter:
# Type can be 0=None, 1=Image & Color, 2=Color, 3=Image
#BackgroundType=2
#BackgroundImage=
#BackgroundScaleToFit=true
# The Standard greeter (gdmlogin) uses BackgroundColor as the background
# color, while the themed greeter (gdmgreeter) uses GraphicalThemedColor
# as the background color.
BackgroundColor=#2b0600
GraphicalThemedColor=#2b0600
# XDMCP session should only get a color, this is the sanest setting since you
# don't want to take up too much bandwidth
#BackgroundRemoteOnlyColor=true

# Program to run to draw the background in the standard greeter.  Perhaps
# something like an xscreensaver hack or some such.
#BackgroundProgram=
# If this is true then the background program is run always, otherwise it is
# only run when the BackgroundType is 0 (None).
#RunBackgroundProgramAlways=false
# Delay before starting background program
#BackgroundProgramInitialDelay=30
# Should the background program be restarted if it is exited.
#RestartBackgroundProgram=true
# Delay before restarting background program
#BackgroundProgramRestartDelay=30

# Show the Failsafe sessions.  These are much MUCH nicer (focus for xterm for
# example) and more failsafe then those supplied by scripts so distros should
# use this rather then just running an xterm from a script.
#ShowGnomeFailsafeSession=true
#ShowXtermFailsafeSession=true
# Normally there is a session type called 'Last' that is shown which refers to
# the last session the user used.  If off, we will be in 'switchdesk' mode
# where the session saving stuff is disabled in GDM
#ShowLastSession=true
# Always use 24 hour clock no matter what the locale.
#Use24Clock=auto
# Use circles in the password field.  Looks kind of cool actually, but only
# works with certain fonts.
UseCirclesInEntry=true
# Do not show any visible feedback in the password field. This is standard for
# instance in console, xdm and ssh.
#UseInvisibleInEntry=false

# These two keys are for the themed greeter (gdmgreeter).  Circles is the
# standard shipped theme.  If you want GDM to select a random theme from a
# list then provide a list that is delimited by /: to the GraphicalThemes
# key and set GraphicalThemeRand to true.  Otherwise use GraphicalTheme
# and specify just one theme.
GraphicalTheme=Human
#GraphicalThemes=circles/:happygnome
GraphicalThemeDir=/usr/share/gdm/themes/
GraphicalThemeRand=false

# If InfoMsgFile points to a file, the greeter will display the contents of the
# file in a modal dialog box before the user is allowed to log in.
#InfoMsgFile=
# If InfoMsgFile is present then InfoMsgFont can be used to specify the font to
# be used when displaying the contents of the file.
#InfoMsgFont=Sans 24

# If SoundOnLogin is true, then the greeter will beep when login is ready for
# user input.  If SoundOnLogin is a file and the greeter finds the 'play'
# executable (see daemon/SoundProgram) it will play that file instead of just
# beeping.
SoundOnLogin=true
SoundOnLoginFile=/usr/share/sounds/question.wav
# If SoundOnLoginSuccess, then the greeter will play a sound (as above) when a
# user successfully logs in.
#SoundOnLoginSuccess=false
#SoundOnLoginSuccessFile=
# If SoundOnLoginFailure, then the greeter will play a sound (as above) when a
# user fails to log in.
#SoundOnLoginFailure=false
#SoundOnLoginFailureFile=

# Specifies a program to be called by the greeter/login program when the
# initial screen is displayed.  The purpose is to provide a hook where files
# used after login can be preloaded to speed performance for the user. The
# program will only be called once only, the first time a greeter is displayed.
# The gdmprefetch command may be used.  This utility will load any libraries
# passed in on the command line, or if the argument starts with a "@"
# character, it will process the file assuming it is an ASCII file containing a
# list of libraries, one per line, and load each library in the file.
#PreFetchProgram=/usr/lib/gdm/gdmprefetch /etc/gdm/gdmprefetchlist

# The chooser is what's displayed when a user wants an indirect XDMCP session,
# or selects Run XDMCP chooser from the system menu
[chooser]
# Default image for hosts.
#DefaultHostImg=/usr/share/pixmaps/nohost.png
# Directory with host images, they are named by the hosts: host or host.png.
HostImageDir=/usr/share/hosts/
# Time we scan for hosts (well only the time we tell the user we are scanning
# actually, we continue to listen even after this has expired).
#ScanTime=4
# A comma separated lists of hosts to automatically add (if they answer to a
# query of course).  You can use this to reach hosts that broadcast cannot
# reach.
Hosts=
# Broadcast a query to get all hosts on the current network that answer.
Broadcast=true
# Set it to true if you want to send a multicast query to hosts.
Multicast=false
# It is an IPv6 multicast address.It is hardcoded here and will be replaced
# when officially registered xdmcp multicast address of TBD will be available.
#Multicast_Addr=ff02::1
# Allow adding random hosts to the list by typing in their names.
#AllowAdd=true

[debug]
# This will cause GDM to send debugging information to the system log, which 
# will create a LOT of output.  It is not recommended to turn this on for
# normal use, but it can be useful to determine the cause when GDM is not
# working properly.
Enable=false
# This will enable debug messages for accessibilty gesture listeners into the
# syslog.  This includes output about key events, mouse button events, and
# pointer motion events.  This is useful for figuring out the cause of why the
# gesture listeners may not be working, but is too verbose for general debug.
Gestures=false

[servers]
# These are the standard servers.  You can add as many you want here and they
# will always be started.  Each line must start with a unique number and that
# will be the display number of that server.  Usually just the 0 server is
# used.
0=Standard
#1=Standard
# Note the VTAllocation and FirstVT keys on Linux and FreeBSD.  Don't add any
# vt<number> arguments if VTAllocation is on, and set FirstVT to be the first
# vt available that your gettys don't grab (gettys are usually dumb and grab
# even a vt that has already been taken).  Using 7 will work pretty much for
# all Linux distributions.  VTAllocation is not currently implemented on
# anything but Linux and FreeBSD.  Feel free to send patches.  X servers will
# just not get any extra arguments then.
#
# If you want to run an X terminal you could add an X server such as this:
#0=Terminal -query serverhostname
# or for a chooser (optionally serverhostname could be localhost):
#0=Terminal -indirect serverhostname
#
# If you wish to run the XDMCP chooser on the local display use the following
# line
#0=Chooser

## Note:
# is your X server not listening to TCP requests?  Perhaps you should look at
# the security/DisallowTCP setting!

# Definition of the standard X server.
[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0 
flexible=true
# Indicates that the X server should be started at a different process
# priority.  Values can be any integer value accepted by the setpriority C
# library function (normally between -20 and 20) with 0 being the default. For
# highly interactive applications, -5 yields good responsiveness. The default
# value is 0 and the setpriority function is not called if the value is 0.

#priority=0

# To use this server type you should add -query host or -indirect host to the
# command line.
[server-Terminal]
name=Terminal server
# Add -terminate to make things behave more nicely
command=/usr/bin/X -br -audit 0 -terminate
# Make this not appear in the flexible servers (we need extra params anyway,
# and terminate would be bad for xdmcp choosing).  You can make a terminal
# server flexible, but not with an indirect query.  If you need flexible
# indirect query server, then you must get rid of the -terminate and the only
# way to kill the flexible server will then be by Ctrl-Alt-Backspace.
flexible=false
# Not local, we do not handle the logins for this X server.
handled=false

# To use this server type you should add -query host or -indirect host to the
# command line.
[server-Chooser]
name=Chooser server
command=/usr/bin/X -br -audit 0
# Make this not appear in the flexible servers for now, but if you wish to
# allow a chooser server then make this true.  This is the only way to make a
# flexible chooser server that behaves nicely.
flexible=false
# Run the chooser instead of the greeter.  When the user chooses a machine they
# will get this same server but run with "-terminate -query hostname".
chooser=true

```

---

### Post by Dors on 2006-08-09
well the problem is getting worst, in the beggining rebooting 3 times solved the problem, but now more than 5 and the last time even 10 couldnt solve it:confused: 
Dont know what to do with this keyboard, can anybody tell me what to do plz?

---

### Post by fourchannel on 2006-08-09
the only thing I can think of is to reconfigure your xserver.

```
sudo dpkg-reconfigure xserver-xorg
``` 
I looked through both your xorg.conf and gdm.conf files and could find nothing that would lead to have crazy repeating keys.

Go ahead and run the reconfigure command, cause this next bit is not as good of a fix as  a properly setup X file.


Well, halfway through typing this reply I found a command to set the keyboard repeat rate in X.  the 400 is the initial delay (i presume to be miliseconds) and the 30 is the repeat rate (you need to tinker with that until you find a setting you like)
 ```
sudo xset r rate 400 30
``` 
Post back with what you find out.

---

### Post by Dors on 2006-08-11
Well i tried reconfiguring xserver, i just could change my monitor settings, no more...
im going to try with the repeat delay but dont think that will helps, i think it has something to do with the update.
i reinstall everything and after rebooting(after ubuntu update) i cant type, so im going to try that if not reinstall again... :S
Is there another way to fix this?is driving me crazy!

---

### Post by Patrick Cosmos on 2006-08-13
I am having the exact same issue.  All keys repeat, all the time - in GDM, and in Gnome.

Somehow, however, if I ctrl-shift-F1 over to the console from GDM, everything is cool.  No repeated keystrokes; I can pointlessly edit my xorg.conf to my heart's content.

So, anyways, after basically a weekend of Googling and trying everything I could find, I am stuck.  I will be bummed out if I have to reinstall and even *more* bummed if I have to jump distros.

For the record, I am using a MS Wireless Desktop keyboard/mouse, and the problem is the same whether I use PS/2 or USB.

Any more help, anyone?  This is the oddest computer problem I have ever come across.

---

### Post by Dors on 2006-08-15
I still have the same problem, when i isntall everything is fine, but after i update buntu 6.06 it start repeating everything, plz any help out there?

---

### Post by gdlx on 2006-08-18
I installed Dapper 6.06 and went thru update. After reboot I am getting the repeat keys on login screen. There must be a way to set the keyboard rate from the console. Does anyone know which file to edit???:confused:

---

### Post by Dors on 2006-08-19
Exactly after the update the problem begins, i dont know if this problem have something to do with my serial mouse, any idea?

---

### Post by Dors on 2006-08-20
come on guys plz help, any idea, need to solve this or at least guys will there be a new update soon.
need to know what update do this to my keyboard, at least i'll reinstall everything and wont update

---

### Post by gdlx on 2006-08-21
having same problem trying to login. Login to terminal mode no problem.
Went to /usr/lib/X11/xkb/compat/ 
Opened "default" and commented out the last entry for japan. This seemed to correct the problem and I have been able to login to gnome several times with no keys repeating.
If you are not familiar with VIM, you may want to apt-get install jed. It is an editor that is similar to a dos full screen editor. It may be easier to work with until you learn one of the Linux console editors.

I'm still a beginner so take this with caution and make backups of any files before you edit them.:D

---

### Post by gdlx on 2006-08-21
having same problem trying to login. Login to terminal mode no problem.
Went to /usr/lib/X11/xkb/compat/ 
Opened "default" and commented out the last entry for japan. 

// $XKeyboardConfig: xkbdesc/compat/default,v 1.3 2005/10/17 00:42:11 svu Exp $
// $Xorg: default,v 1.3 2000/08/17 19:54:34 cpqbld Exp $
default xkb_compatibility "default"  {
    include "basic"
    augment "mousekeys"
    augment "accessx(basic)"
    augment "misc"
    augment "iso9995"
    augment "level5"
// ??should be changed/renamed/removed
//    augment "xfree86"
//    augment "japan"
};

This seemed to correct the problem and I have been able to login to gnome several times with no keys repeating.
If you are not familiar with VIM, you may want to apt-get install jed. It is an editor that is similar to a dos full screen editor. It may be easier to work with until you learn one of the Linux console editors.

I'm still a beginner so take this with caution and make backups of any files before you edit them.:D

Well, the problem returned after 5 0r 6 reboots.:confused:

---

### Post by munku on 2006-08-22
I had the same problems and found a solution. When Grub loads up, edit the initial boot up params and add clock=tsc to the end. It worked for me. No more repeating keys.

---

### Post by Dors on 2006-08-22
:o well 2 ways to solve it, ill try the easy one 1st
Munku can u tell me how can i edit grub?
hope than will solve evertyhing :P

---

### Post by Dors on 2006-08-24
how can i edit grub munku, itried editing the first boot, adding after boot
clock=tsc
but nothign happened, i even think it didnt even do it, just when i put it before boot i got an error command
maybe im editing the wrong place, really dont know
any idea?

---

### Post by helmet on 2006-08-25
i had that problem with logitech wireless through kvm. the only reason i used that keyboard was to switch the kvm. my only suggestion is buy a wired keyboard, since wireless ones suck anyway (not very helpful i know...but..)

---

### Post by Dors on 2006-08-26
well i use a wired keyboard and a serial mouse, dunno if the problem is my serial mouse :S:cry:

---

### Post by fvgm on 2006-09-14
Hi, i´m having the same problems on K6-2 450mhz processor. It´s occur when X starts. In text mode, everything works fine. And it´s have occurred with others linux distributions. Someone can help me?? it´s annoying...

---

### Post by superboss on 2006-09-30
I have this error on a AMD K6-2 500MHz with ubuntu and xubuntu. Adding clock=tsc to grub did nothing for me. When will this very annoying problem be fixed?! Should get a pretty high priority given that the system is rendered useless with it present (I can't even login).

---

### Post by superboss on 2006-10-03
Why is this issue left unsolved? I want to use ubuntu, help me.

---

### Post by ozonblue on 2006-10-30
Same problem here.

I have an old HP Vectra which used to work beautifully with Slackware/KDE.

Changed to Ubuntu Dapper - and the weirdest things happens - on some reboots everything is stable - but on some reboots I get key repeat problem on gdm login screen - in fact even when you do login somehow - the x system is just plain unstable.

I have no problems in console mode.

I have tried everyting under the sun - differnet keyborads, trying different versions of the avaible kernels, upgrading to edgy etc.etc. playing with BIOS settings and passing all kinds of weird parameters like noacpi to the kernel.

No luck. I must emphasise that sometimes the machine boots and there is no problem - which means it is sort of intermittant and more diificult to fault find.

Any help would be much appreciated.

---

### Post by talbain on 2006-12-05
Yeah plase help on this topic, i'm having the same issue and i really want to use xubunto in my other computer.

---

### Post by talbain on 2006-12-08
Okay, how i solved my problem:

The computer i installed edgy on was so old that i even forgot it has no acpi support in its chipset.

(Im using a USB mouse and a PS/2 keyboard)

So what i did was:

Let the machine boot and show the login screen, since i couldnt login, i pressed "Ctrl+Alt+F1" to show the console and log in.

Then:
```
sudo nano /boot/grub/menu.lst
```

and added the text in red to this line:

```
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hda1 ro quiet splash [COLOR="Red"]acpi=off noacpi[/COLOR]
```

things were still kinda crazy so i went into the BIOS and changed an option (that you might or might not have) that says "USB Legacy Mode" from "Enabled" to "Disabled" and everything went smooth as silk...

But just to be ultra super sure i decided to reinstall edgy, let the cd boot (i used the alternative disk, not the live one) and press "F6" then add "acpi=off noacpi" to the end of the line so this option gets preinstalled.

I noticed that if my BIOS has "USB Legacy Mode" set to "Enable" the comp would instantly restart after pressing "Enter", so i had to disble that first and then again the installation went smoothly.

Kudos to [bsherman]("http://www.ubuntuforums.org/member.php?u=1327") for [this]("http://www.ubuntuforums.org/showpost.php?p=9953&postcount=3") post on diabling ACPI, thread [here]("http://www.ubuntuforums.org/showthread.php?t=2620&highlight=acpi").

Later on i also added the apm module as indicated in his post.

Hope this helps anyone.
Good luck.

---

### Post by haz2a on 2007-02-05
I had this problem in Xubuntu 6.06 LTS (XFCE) on an old AMD K6-2/500 with SiS 530/5595 chipset. Very difficult to login at the login window.

Adding the kernel parameter 'clock=tsc' in GRUB (ie: to the 'kernel' line of the top kernel entry in /boot/grub/menu.lst) worked for me.

---

### Post by ansicplusplus on 2007-10-27
Hy,

i have the same problem with repeating keys on a Quadcore with 4G ram. After about 10 reboots the repeating starts and stays until i reboot up to 3 times. I don't have to tell you that it's quite annoying -- especially if i'm in a hurry and fsck decides it's time to have a good look at my 750G. :-|

I will try the clock=tsc solution. Hopefully this will work.

Does anyone know what clock=tsc ist supposed to do ?

Greetings,
ansicplusplus

---

### Post by crypticmystic on 2007-10-29
I have also seen this, albiet more sublty since I upgraded to 7.10... I've had ubuntu on my thinkpad x31 for years and just upgraded to 7.10  (gutsy) a week ago.. Since then I occasionally experience a key that will not "unstick" in shell, firefox, or whatever application I am in (indication a driver keyboard issue)... I couldn't rule out that my keyboard itself is old and possibly flakey, so I tried using an external USB keyboard, which has worked fine before... But it was giving me the same issue.. And it's very irregular for me... sometimes it doesn't happen for hours, other times it happens quick and a reboot fixes it....  I did an apt-get upgrade to 7.10 from 7.04 so possibly a clean install would work better...  I don't hae the time and energy to try that right now...  But just another note that there does seem to be something different going on between 7.04 and 7.10 keyboard wise... fwiw...

---

### Post by hermesrules on 2007-10-30
Hi, guys! This has troubled me for a very, very long time without success. I feel elated to have found this thread. In my case, however, the issue occurs in Linux (using OpenSuse 10.3 at the moment, but it happened in every version of Kubuntu/Ubuntu I've used), Windows, and even in my BIOS setup. I could tell of the latter since everytime unknown key is pressed, the PC speaker makes a sound. So I hear these beeps quite frequently.

I have tracked down which key is causing the problem for me - the PrintScr. In KDE suddenly I would get tens and hundreds of ksnapshot instances, which would render my computer absolutely unusable. I had to disable any PrintScr occurence in the shortcuts, and also erase ksnapshot from the menu. Now, if I am lucky to boot, it no longer happens. Same in Gnome - had to completely disable gnome-screenshot. In XP I get copies of my screen into the clipboard, which makes it impossible for me to do any reasonable copy/paste. The cursors flickers on the screen, and it seems to be causing some problems to playing videos.

However, if I press Esc, the repeating stops for a while, and soon afterwards it resumes. In XP, sometimes pressing Shift-Insert (the shortcut for paste) also seems to stop it for a while.

I will try the clock=tsc solution, hopefully it would work. I have a laptop, the keyboard has never been spilled onto, and everything on that key seems normal. I wonder if it would go away if I connect a different keyboard...

Cheers!

PS. Well, I just tried out the clock=tsc solution. Other than slowing down my computer and a few "tsc clock unstable" messages, nothing happened. No improvement. I also disabled legacy USB support in my BIOS as suggested in some of the previous posts, but no go there either. I can't boot into Linux, and am starting to suspect a more serious damage. It seems that runlevel 5 is reached too soon, and gdm starts up way early. If I switch to the console (Ctrl-Alt-1), and it does not spew the "Init 1 respawning too fast" message, I can see some of the services are still being started. It's kinda like runlevel 3 has been skipped. When trying to log into gdm it tells me my /home partition is not mounted (I have it on an external HDD)... More often though gdm fails to start the X server and I only see a blinking cursor in the top left corner, but no graphics... :(

Yet Windoze boots alright...

If anyone has any ideas, please share! Thanks!

---

### Post by ansicplusplus on 2007-11-04
> **ansicplusplus said:**
> 
I will try the clock=tsc solution. Hopefully this will work.


Hy,

clock= is deprecated and shopuld be changed to clocksource=. Unfortunately clocksource=tsc doesn't solve my problem. My next try will be clocksource=acpi_pm.

Greetings,
ansicplusplus

---

### Post by hermesrules on 2007-11-05
In my case I solved the problem by disconnecting the laptop's keyboard and attaching an external PS/2 one. I guess the repeating key problem was due to a fault in the keyboard. The computer is 4 years old already, so probably it should not be such a big surprise...

Has anyone else tried with a different keyboard?

---

### Post by spamgoat on 2007-11-06
Is this bug the same as the one explained in [http://ubuntuforums.org/showthread.php?t=599978](http://ubuntuforums.org/showthread.php?t=599978) ? If so, it seems to be a fairly widespread bug.

---

### Post by Xeom on 2008-02-13
Has annnnnnnnnnnnybody found a way to solve this problem yet its so annoying and makes theeeeeeeee OS allllllllllmost unusable. There has to be a way to solve this.

Its does let me log in but as you can see very annoying when typing.Its even worse when it happens with a backspace andddddddddd it makes fps gaming hard.

I've seen a few reports on bugs like this but non of themmmmmmmmmmmm have even been looked at and a year has already past from their orginalllllllll post date.

---

### Post by Paul S on 2008-04-28
> **Xeom said:**
> Has annnnnnnnnnnnybody found a way to solve this problem yet its so annoying and makes theeeeeeeee OS allllllllllmost unusable. There has to be a way to solve this.

Its does let me log in but as you can see very annoying when typing.Its even worse when it happens with a backspace andddddddddd it makes fps gaming hard.

I've seen a few reports on bugs like this but non of themmmmmmmmmmmm have even been looked at and a year has already past from their orginalllllllll post date.

I think this is launchpad 124406 which is still a problem here on a fresh install of kubuntu hardy.  Suggest you subscribe to it too.

---

