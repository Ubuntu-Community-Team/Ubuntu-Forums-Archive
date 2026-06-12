---
title: "Everything with KDE is somehow corrupt with a white screen and red &quot;X&quot;es"
date: 2012-10-29
forum: Desktop Environments
---

### Post by Stonecold1995 on 2012-10-29
Randomly, KDE started refusing to open programs through the normal menu, giving an error saying something like "KDEInit could not launch /usr/bin/application" (something like that).  I thought nothing of it because every once in a while that will happen and logging out or rebooting fixed it.  Some hours later, Dolphin stopped working (saying "invalid protocol" in every directory).  After that, I decided to log out and back in, but everything was f*cked up!  Pressing "Alt+F1" to get me to the console worked, and its working fine there, but KDE is completely broken.  I'm on a laptop so I'm using Intel's integrated graphics btw.

[Here's a screenshot of my desktop.]("http://i49.tinypic.com/j6q104.png")  Everything is completely unusable!

Help??

The login manager works fine though, but after the splash screen it does this.  Could this be the "white screen of death" I'm reading about?  I don't know much about that though.

**EDIT:** I renamed .kde and logged in again, and it worked (but without all my settings of course).  Then I put the original .kde back and it's working again (I can log in and everything), but now a new problem arose.  I seem to have the default wallpaper, so I tried right-clicking to change the wallpaper location, but I couldn't right-click.  Right-clicking simply does nothing.  How do I get this back??  I have access to a backup I made of /home about 10 days ago but that was before I upgraded to 12.10, so I don't know what folder in .kde is the culprit.  [B]So now my main problem is getting right-click functionality for plasma-desktop back so I can edit my desktop settings again.

EDIT2:[/B]  I may have found the specific file that's giving me trouble.  It's ~/.kde/share/config/plasma-desktop-appletsrc that might have something wrong with it.  The contents of my plasma-desktop-appletsrc is currently this:
```
[$Version]
update_info=plasma_popupapplet_fix_groups.upd:PlasmaPopupAppletFixGroups1

[ActionPlugins][RightButton;NoModifier]
_add panel=false
_context=true
_lock_screen=false
_logout=false
_run_command=false
_sep1=false
_sep2=false
_sep3=true
_wallpaper=true
add sibling containment=false
add widgets=false
configure=true
configure shortcuts=false
lock widgets=false
manage activities=false
remove=true

[AppletGlobals][plasma_applet_launcher]
SwitchTabsOnHover=false
askBeforeRemoval=true

[AppletGlobals][plasma_applet_pager]
rows=2

[AppletGlobals][plasma_applet_simplelauncher]
SwitchTabsOnHover=false
askBeforeRemoval=true

[AppletGlobals][plasma_applet_sm_temperature]
acpi/Thermal_Zone/0/Temperature=Temperature
acpi/Thermal_Zone/0/Temperature_offset=0.0
lmsensors/acpitz-virtual-0/temp1=temp1
lmsensors/acpitz-virtual-0/temp1_offset=0.0
lmsensors/radeon-pci-0100/temp1=temp1
lmsensors/radeon-pci-0100/temp1_offset=0.0

[Containments][101][Applets][106][Configuration][Applets][110][Configuration][ExtenderItems][2]
extenderItemPosition=0

[Containments][101][Applets][107][Configuration][ExtenderItems][1]
extenderItemPosition=0

[Containments][113]
ActionPluginsSource=Global
activity=New Activity
activityId=2f68d25b-36f2-4d76-984f-badd1d7c7100
desktop=-1
formfactor=0
geometry=0,0,1366,768
immutability=1
lastDesktop=-1
lastScreen=0
location=0
plugin=desktop
screen=-1
wallpaperplugin=image
wallpaperpluginmode=SingleImage
zvalue=0

[Containments][113][Wallpaper][image]
slideTimer=10
slidepaths=/usr/share/wallpapers/
userswallpapers=
wallpaper=/usr/share/wallpapers/Ariya
wallpapercolor=0,0,0
wallpaperposition=0

[Containments][115]
ActionPluginsSource=Global
activity=New Activity
activityId=49c89cb1-9a65-43fa-ba72-c9fad003c229
desktop=-1
formfactor=0
geometry=1372,0,640,480
immutability=1
lastDesktop=-1
lastScreen=1
location=0
plugin=desktop
screen=1
wallpaperplugin=image
wallpaperpluginmode=SingleImage
zvalue=0

[Containments][115][Wallpaper][image]
slideTimer=10
slidepaths=/usr/share/wallpapers/
userswallpapers=
wallpaper=/usr/share/wallpapers/Ariya
wallpapercolor=0,0,0
wallpaperposition=0

[Containments][116][Applets][121][Configuration][Applets][125][Configuration][ExtenderItems][6]
extenderItemPosition=0

[Containments][116][Applets][122][Configuration][ExtenderItems][5]
extenderItemPosition=0

[Containments][129]
ActionPluginsSource=Global
activity=Desktop Icons
activityId=7d663b7b-3408-48b3-92fb-abe83300c935
desktop=-1
formfactor=0
geometry=0,924,1366,768
immutability=1
lastDesktop=-1
lastScreen=0
location=0
plugin=folderview
screen=-1
wallpaperplugin=image
wallpaperpluginmode=SingleImage
zvalue=0

[Containments][129][Wallpaper][image]
slideTimer=10
slidepaths=/usr/share/wallpapers/
userswallpapers=
wallpaper=/usr/share/wallpapers/Horos
wallpapercolor=0,0,0
wallpaperposition=0

[Containments][130]
ActionPluginsSource=Global
activity=Desktop Icons
activityId=7d663b7b-3408-48b3-92fb-abe83300c935
desktop=-1
formfactor=0
geometry=1372,924,1366,768
immutability=1
lastDesktop=-1
lastScreen=1
location=0
plugin=desktop
screen=-1
wallpaperplugin=image
wallpaperpluginmode=SingleImage
zvalue=0

[Containments][130][Wallpaper][image]
slideTimer=10
slidepaths=/usr/share/wallpapers/
userswallpapers=
wallpaper=/usr/share/wallpapers/Horos
wallpapercolor=0,0,0
wallpaperposition=0

[Containments][140][Applets][145][Configuration][Applets][149][Configuration][ExtenderItems][4]
extenderItemPosition=0

[Containments][140][Applets][146][Configuration][ExtenderItems][1]
extenderItemPosition=0

[Containments][156][Applets][161][Configuration][Applets][165][Configuration][ExtenderItems][11]
extenderItemPosition=134

[Containments][156][Applets][162][Configuration][ExtenderItems][10]
extenderItemPosition=0

[Containments][169]
ActionPluginsSource=Global
EnabledEntries=plasma-sal-bookmarks.desktop,plasma-sal-contacts.desktop,plasma-sal-multimedia.desktop,plasma-sal-internet.desktop,plasma-sal-graphics.desktop,plasma-sal-games.desktop,plasma-sal-office.desktop
activity=New Activity
activityId=eab13aa9-653b-4a24-a242-d9acc4c12819
desktop=-1
formfactor=0
geometry=0,1848,800,600
immutability=1
lastDesktop=-1
lastScreen=-1
location=0
plugin=desktop
screen=-1
wallpaperplugin=image
wallpaperpluginmode=SingleImage
zvalue=0

[Containments][210]
ActionPluginsSource=Global
EnabledEntries=plasma-sal-bookmarks.desktop,plasma-sal-contacts.desktop,plasma-sal-multimedia.desktop,plasma-sal-internet.desktop,plasma-sal-graphics.desktop,plasma-sal-games.desktop,plasma-sal-office.desktop
activity=New Activity
activityId=0427d8b7-589e-467d-93c8-0849fa175aba
desktop=-1
formfactor=0
geometry=806,1848,800,600
immutability=1
lastDesktop=-1
lastScreen=-1
location=0
plugin=desktop
screen=-1
wallpaperplugin=image
wallpaperpluginmode=SingleImage
zvalue=0

[Containments][215][Applets][220][Configuration][Applets][224][Configuration][ExtenderItems][1]
extenderItemPosition=0

[Containments][231][Applets][236][Configuration][Applets][240][Configuration][ExtenderItems][72]
extenderItemPosition=0

[Containments][292][Applets][297][Configuration][Applets][301][Configuration][ExtenderItems][77]
extenderItemPosition=0

[Containments][3][Applets][6]
geometry=105,3,1498,32

[Containments][3][Applets][7]
geometry=1607,3,32,32

[Containments][3][Applets][8]
geometry=1643,3,185,32

[Containments][3][Applets][8][Configuration][Applets][10]
geometry=4,88,24,24

[Containments][3][Applets][8][Configuration][Applets][10][Configuration][ExtenderItems][1]
extenderItemPosition=0

[Containments][3][Applets][8][Configuration][Applets][2]
geometry=4,60,24,24

[Containments][3][Applets][8][Configuration][Applets][3]
geometry=140,4,24,24

[Containments][3][Applets][8][Configuration][Applets][4]
geometry=4,32,24,24

[Containments][3][Applets][8][PopupApplet]
DialogHeight=172
DialogWidth=219

[Containments][325][Applets][330][Configuration][Applets][334][Configuration][ExtenderItems][89]
extenderItemPosition=0

[Containments][420]
ActionPluginsSource=Global
activity=New Activity
activityId=49c89cb1-9a65-43fa-ba72-c9fad003c229
alignToGrid=false
blankLabel=false
clickForFolderPreviews=true
customIconSize=48
customLabel=
desktop=-1
drawShadows=true
filter=0
filterFiles=*
flow=1
formfactor=0
geometry=0,2604,1920,1080
iconsLocked=false
immutability=1
lastDesktop=-1
lastScreen=0
location=0
mimeFilter=
numTextLines=2
plugin=desktop
screen=-1
showPreviews=true
sortColumn=0
url=desktop:/
wallpaperplugin=image
wallpaperpluginmode=SingleImage
zvalue=0

[Containments][420][ToolBox]
corner=1
offset=0

[Containments][420][Wallpaper][color]
backgroundMode=0
color1=255,255,255
color2=0,0,0

[Containments][420][Wallpaper][image]
slideTimer=1810
slidepaths=/usr/share/wallpapers/,/home/alex/Pictures/Wallpapers/,/home/alex/Pictures/Wallpapers
userswallpapers=/home/alex/Pictures/Anonymous 6.jpg,/home/alex/Pictures/Anonymous.jpg,/home/alex/Pictures/Wallpapers/Expect us (red).jpg,/home/alex/Elfen Lied.jpg,/home/alex/Miku Hatsune.jpg,/home/alex/Linux-tan.jpg,/home/alex/Downloads/1333516587723.png,/home/alex/1324237445268.jpg,/home/alex/1324237445268 (3).jpg,/home/alex/Yume Nikki (cropped).jpg,/home/alex/341179.jpg,/home/alex/moe-99624-fixed-flower-kowarekake_no_orgel-pop (2).jpg,/home/alex/nevada-tan-desk-lrg.jpg,/home/alex/Anonymous 17.jpg,/home/alex/Touhou Project 183.jpg,/home/alex/35.jpg,/home/alex/Painful decapitation.jpg,/home/alex/Remove the eye.png,/home/alex/rustle-cropped2.jpg,/home/alex/rustle-cropped.jpg,/home/alex/1.jpg,/home/alex/40.jpg,/home/alex/19.jpg,/home/alex/38.jpg,/home/alex/AAAAAAAA.jpg,/home/alex/theme_ntp_background.png
wallpaper=/home/alex/Pictures/Wallpapers/Touhou Project/Touhou Project 350.png
wallpapercolor=0,0,0
wallpaperposition=0

[Containments][420][Wallpaper][mandelbrot]
mandelbrotcenter=-0.366666666666666,0.245833333333333
mandelbrotcolor1=0,0,0
mandelbrotcolor2=255,255,255
mandelbrotcolor3=0,0,255
mandelbrotlock=0
mandelbrotquality=1
mandelbrotzoom=4

[Containments][420][Wallpaper][marble]
mapTheme=moon/clementine/clementine.dgml
movement=0
positionLatitude=25.9406816786297
positionLongitude=-113.440571878522
projection=0
quality=4
rotateLatitude=0
rotateLongitude=0.025
rotationTimeout=10000
showPlacemarks=false
zoom=1200

[Containments][420][Wallpaper][org.kde.potd]
provider=wcpotd

[Containments][420][Wallpaper][pattern]
BackgroundColor=0,0,0
ForegroundColor=255,255,255
Pattern=

[Containments][420][Wallpaper][virus]
maxcells=2000
showcells=true
updateinterval=200
userswallpapers=
wallpaper=/home/alex/Pictures/Wallpapers/Shinryaku! Ika Musume/Shinryaku! Ika Musume 7.jpg
wallpapercolor=56,111,150
wallpaperposition=0

[Containments][420][Wallpaper][weather]
clearNightPaper=/usr/share/wallpapers/City_at_Night/
clearPaper=/usr/share/wallpapers/Fields_of_Peace/
cloudyNightPaper=/usr/share/wallpapers/JK_Bridge_at_Night/
cloudyPaper=/usr/share/wallpapers/Colorado_Farm/
freezingRainPaper=/usr/share/wallpapers/Icy_Tree/
hailPaper=/usr/share/wallpapers/Storm/
manyCloudsPaper=/usr/share/wallpapers/Beach_Reflecting_Clouds/
mistPaper=/usr/share/wallpapers/Fresh_Morning/
partlyCloudyNightPaper=/usr/share/wallpapers/JK_Bridge_at_Night/
partlyCloudyPaper=/usr/share/wallpapers/Evening/
rainPaper=/usr/share/wallpapers/There_is_Rain_on_the_Table/
showersPaper=/usr/share/wallpapers/There_is_Rain_on_the_Table/
showersScatteredPaper=/usr/share/wallpapers/There_is_Rain_on_the_Table/
snowPaper=/usr/share/wallpapers/Winter_Track/
snowRainPaper=/usr/share/wallpapers/Icy_Tree/
snowScatteredPaper=/usr/share/wallpapers/Winter_Track/
source=
stormPaper=/usr/share/wallpapers/Storm/
updateWeather=30
userswallpapers=
wallpapercolor=56,111,150
wallpaperposition=0

[Containments][435]
ActionPluginsSource=Global
activity=
activityId=
desktop=-1
formfactor=2
geometry=0,-50,1920,44
immutability=1
lastDesktop=-1
lastScreen=0
location=4
plugin=panel
screen=0
zvalue=0

[Containments][435][ActionPlugins]
RightButton;NoModifier=contextmenu

[Containments][435][Applets][438]
geometry=44,4,70,40
immutability=0
plugin=pager
zvalue=0

[Containments][435][Applets][438][Configuration]
Share=false
currentDesktopSelected=0
displayedText=2
showWindowIcons=false

[Containments][435][Applets][438][LayoutInformation]
Order=1

[Containments][435][Applets][439]
geometry=118,4,1281,40
immutability=0
plugin=tasks
zvalue=1

[Containments][435][Applets][439][Configuration]
Share=false
forceRows=true
groupWhenFull=true
groupingStrategy=1
highlightWindows=false
maxRows=1
showOnlyCurrentActivity=true
showOnlyCurrentDesktop=true
showOnlyCurrentScreen=false
showOnlyMinimized=false
showTooltip=true
sortingStrategy=1

[Containments][435][Applets][439][Configuration][Launchers]
Items=

[Containments][435][Applets][439][LayoutInformation]
Order=2

[Containments][435][Applets][440]
geometry=1535,4,226,40
immutability=0
plugin=systemtray
zvalue=1

[Containments][435][Applets][440][Configuration]
DefaultAppletsAdded=true
Share=false
ShowApplicationStatus=true
ShowCommunications=true
ShowHardware=true
ShowSystemServices=true
ShowUnknown=true
alwaysShown=
hidden=

[Containments][435][Applets][440][Configuration][Applets][442]
geometry=166,3,24,24
immutability=1
plugin=org.kde.networkmanagement
zvalue=0

[Containments][435][Applets][440][Configuration][Applets][442][PopupApplet]
DialogHeight=332
DialogWidth=650

[Containments][435][Applets][440][Configuration][Applets][442][Shortcuts]
global=

[Containments][435][Applets][440][Configuration][Applets][443]
geometry=4,60,24,24
immutability=1
plugin=notifier
zvalue=0

[Containments][435][Applets][440][Configuration][Applets][443][PopupApplet]
DialogHeight=356
DialogWidth=306

[Containments][435][Applets][440][Configuration][Applets][443][Shortcuts]
global=

[Containments][435][Applets][440][Configuration][Applets][444]
geometry=4,88,24,24
immutability=1
plugin=notifications
zvalue=0

[Containments][435][Applets][440][Configuration][Applets][444][Configuration]
AutoHidePopup=false
Share=false
ShowJobs=false
ShowNotifications=true
customPosition=-2,-7
customPositionAffinityHoriz=r
customPositionAffinityVert=b

[Containments][435][Applets][440][Configuration][Applets][444][Configuration][ExtenderItems][122]
extenderIconName=dialog-information
extenderItemName=jobGroup
extenderItemPosition=0
extenderTitle=Jobs
isCollapsed=true
isGroup=true
sourceAppletId=444
sourceAppletPluginName=notifications

[Containments][435][Applets][440][Configuration][Applets][444][PopupApplet]
DialogHeight=77
DialogWidth=175

[Containments][435][Applets][440][Configuration][Applets][444][Shortcuts]
global=

[Containments][435][Applets][440][Configuration][Applets][445]
geometry=4,4,24,24
immutability=1
plugin=battery
zvalue=0

[Containments][435][Applets][440][Configuration][Applets][445][PopupApplet]
DialogHeight=188
DialogWidth=413

[Containments][435][Applets][440][Configuration][Applets][445][Shortcuts]
global=

[Containments][435][Applets][440][Configuration][Applets][476]
geometry=0,3,24,24
immutability=1
plugin=weather
zvalue=0

[Containments][435][Applets][440][Configuration][Applets][476][Configuration]
Share=false
pressureUnit=5008
<snip>
speedUnit=9000
temperatureUnit=6001
updateInterval=30
visibilityUnit=2007

[Containments][435][Applets][440][Configuration][Applets][476][PopupApplet]
DialogHeight=180
DialogWidth=255

[Containments][435][Applets][440][Configuration][Shortcuts]
Systemtray-Klipper-440=Ctrl+Alt+V

[Containments][435][Applets][440][LayoutInformation]
Order=6

[Containments][435][Applets][440][PopupApplet]
DialogHeight=160
DialogWidth=211

[Containments][435][Applets][441]
geometry=1765,4,155,40
immutability=0
plugin=digital-clock
zvalue=0

[Containments][435][Applets][441][Configuration]
Share=false
announceInterval=0
calendarType=locale
dateStyle=3
defaultTimezone=Local
displayEvents=true
displayHolidays=true
holidaysRegions=us_en-us
holidaysRegionsDaysOff=us_en-us
plainClockDrawShadow=true
plainClockFont=Ubuntu,28,-1,5,50,0,0,0,0,0
showSeconds=true
showTimezone=true
timeZones=America/Los_Angeles
timezone=Local
useCustomColor=false
useCustomShadowColor=false

[Containments][435][Applets][441][LayoutInformation]
Order=7

[Containments][435][Applets][441][PopupApplet]
DialogHeight=236
DialogWidth=266

[Containments][435][Applets][447]
geometry=1491,4,40,40
immutability=0
plugin=icon
zvalue=0

[Containments][435][Applets][447][Configuration]
Url=file:///usr/share/applications/kde4/dolphin.desktop

[Containments][435][Applets][447][LayoutInformation]
Order=5

[Containments][435][Applets][448]
geometry=1447,4,40,40
immutability=0
plugin=icon
zvalue=0

[Containments][435][Applets][448][Configuration]
Url=file:///home/alex/.local/share/applications/chromium-browser.desktop

[Containments][435][Applets][448][LayoutInformation]
Order=4

[Containments][435][Applets][450]
geometry=1403,4,40,40
immutability=0
plugin=icon
zvalue=0

[Containments][435][Applets][450][Configuration]
Url=file:///usr/share/applications/kde4/konsole.desktop

[Containments][435][Applets][450][LayoutInformation]
Order=3

[Containments][435][Applets][478]
geometry=0,4,40,40
immutability=0
plugin=launcher
zvalue=0

[Containments][435][Applets][478][Configuration]
Share=false
ShowAppsByName=true

[Containments][435][Applets][478][LayoutInformation]
Order=0

[Containments][435][Applets][478][Shortcuts]
global=

[Containments][435][Configuration]
maximumSize=1920,44
minimumSize=1920,44

[Containments][457]
ActionPluginsSource=Global
activity=
activityId=49c89cb1-9a65-43fa-ba72-c9fad003c229
desktop=-1
formfactor=0
geometry=1926,2604,1920,1080
immutability=1
lastDesktop=0
lastScreen=0
location=0
plugin=desktop
screen=-1
wallpaperplugin=image
wallpaperpluginmode=SingleImage
zvalue=0

[Containments][457][Wallpaper][image]
slideTimer=10
slidepaths=/usr/share/wallpapers/
userswallpapers=
wallpaper=/usr/share/wallpapers/Ariya
wallpapercolor=0,0,0
wallpaperposition=0

[Containments][458]
ActionPluginsSource=Global
activity=
activityId=49c89cb1-9a65-43fa-ba72-c9fad003c229
desktop=-1
formfactor=0
geometry=0,3840,1920,1080
immutability=1
lastDesktop=1
lastScreen=0
location=0
plugin=desktop
screen=-1
wallpaperplugin=image
wallpaperpluginmode=SingleImage
zvalue=0

[Containments][458][Wallpaper][image]
slideTimer=10
slidepaths=/usr/share/wallpapers/,/home/alex/Pictures/Wallpapers/,/home/alex/Pictures/Wallpapers
userswallpapers=
wallpaper=/usr/share/wallpapers/Ariya
wallpapercolor=0,0,0
wallpaperposition=0

[Containments][459]
ActionPluginsSource=Global
activity=
activityId=49c89cb1-9a65-43fa-ba72-c9fad003c229
desktop=-1
formfactor=0
geometry=1926,3840,1920,1080
immutability=1
lastDesktop=2
lastScreen=0
location=0
plugin=desktop
screen=-1
wallpaperplugin=image
wallpaperpluginmode=SingleImage
zvalue=0

[Containments][459][Wallpaper][image]
slideTimer=10
slidepaths=/usr/share/wallpapers/
userswallpapers=
wallpaper=/usr/share/wallpapers/Ariya
wallpapercolor=0,0,0
wallpaperposition=0

[Containments][460]
ActionPluginsSource=Global
activity=
activityId=49c89cb1-9a65-43fa-ba72-c9fad003c229
desktop=-1
formfactor=0
geometry=0,5076,1920,1080
immutability=1
lastDesktop=3
lastScreen=0
location=0
plugin=desktop
screen=-1
wallpaperplugin=image
wallpaperpluginmode=SingleImage
zvalue=0

[Containments][460][Wallpaper][image]
slideTimer=10
slidepaths=/usr/share/wallpapers/
userswallpapers=
wallpaper=/usr/share/wallpapers/Ariya
wallpapercolor=0,0,0
wallpaperposition=0

[Containments][472]
ActionPluginsSource=Global
EnabledEntries=plasma-sal-bookmarks.desktop,plasma-sal-contacts.desktop,plasma-sal-multimedia.desktop,plasma-sal-internet.desktop,plasma-sal-graphics.desktop,plasma-sal-games.desktop,plasma-sal-office.desktop
activity=New Activity
activityId=711f5772-b26e-4127-abbf-6b7615f2f9f4
desktop=-1
formfactor=0
geometry=1926,5076,800,600
immutability=1
lastDesktop=-1
lastScreen=-1
location=0
plugin=desktop
screen=-1
wallpaperplugin=image
wallpaperpluginmode=SingleImage
zvalue=0

[Containments][474]
ActionPluginsSource=Global
EnabledEntries=plasma-sal-bookmarks.desktop,plasma-sal-contacts.desktop,plasma-sal-multimedia.desktop,plasma-sal-internet.desktop,plasma-sal-graphics.desktop,plasma-sal-games.desktop,plasma-sal-office.desktop
activity=New Activity
activityId=258b1b1a-1d19-43db-9001-6bebb7e2ea4d
alignToGrid=false
blankLabel=false
clickForFolderPreviews=true
customIconSize=48
customLabel=
desktop=-1
drawShadows=true
filter=0
filterFiles=*
flow=1
formfactor=0
geometry=0,6312,1920,1080
iconsLocked=false
immutability=1
lastDesktop=-1
lastScreen=0
location=0
mainGroup=3
mimeFilter=
numTextLines=2
plugin=desktop
screen=0
showPreviews=true
sortColumn=0
url=desktop:/
wallpaperplugin=image
wallpaperpluginmode=SingleImage
zvalue=0

[Containments][474][Groups][3]
geometry=0,0,1920,1080
plugin=floating
zvalue=0

[Containments][474][ToolBox]
corner=1
offset=0

[Containments][474][Wallpaper][image]
slideTimer=1810
slidepaths=/usr/share/wallpapers/,/home/alex/Pictures/Wallpapers/,/home/alex/Pictures/Wallpapers
userswallpapers=
wallpaper=/usr/share/wallpapers/Air/
wallpapercolor=0,0,0
wallpaperposition=0

[Containments][474][Wallpaper][marble]
mapTheme=earth/bluemarble/bluemarble.dgml
movement=0
positionLatitude=147.90729526519
positionLongitude=-151.536354399512
projection=0
quality=2
rotateLatitude=0
rotateLongitude=0.025
rotationTimeout=10000
showPlacemarks=false
zoom=1250

[General]
immutability=1

```

Could that be the file that's causing the right-click context menu not to open on the desktop?  When I delete (or rename) that file and restart plasma-desktop, it seems to work but it looses all the settings, which I don't want.

---

### Post by Stonecold1995 on 2012-10-29
OK, I fixed everything.  I just had to add this to plasma-desktop-appletsrc:
```
[ActionPlugins]
MidButton;NoModifier=applauncher
RightButton;NoModifier=contextmenu
```
I killed and restarted plasma-desktop and it's all working now.

Now does anyone know what caused this in the first place?  I haven't edited any configuration files or done any upgrades or anything around that time that I remember that could have caused this...

---

### Post by Zorael on 2012-10-30
Corrupt cache, maybe? I have never had this happen myself.
```
$ rm -rf ~/.kde/cache-${HOSTNAME}/*  # caveat emptor, naturally
$ kbuildsycoca4 --noincremental
```

If it strikes again; get to a terminal. Try enabling debug output, then kill and restart plasma-desktop from there. Maybe kded too.
```
$ kdebugdialog  # untick Disable and hit Select All
$ kquitapp plasma-desktop
$ kquitapp **kded**
$ **kded_4_**
$ plasma-desktop
```
If no graphical terminal will open (maybe krunner died too), remember that you can just hop to a tty and **export DISPLAY=:0** to have programs you run there pop up in your X session (at tty7 or where ever). Screen-likes such as [**tmux**](apt://tmux) and [**byobu**](apt://byobu) are great here.

As for the right-button desktop click thing, I got that once after fiddling about too much with the settings. The graphical way to re-add the context menu functionality is to click the cashew, pick Desktop Settings, then Mouse Actions.

---

