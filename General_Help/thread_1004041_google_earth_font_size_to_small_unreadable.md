---
title: "google earth font size to small unreadable"
date: 2008-12-06
forum: General Help
---

### Post by alwayshere on 2008-12-06
google earth font size to small unreadable in ubuntu 8.10 

how do I sort this ??

---

### Post by eBoxNet on 2008-12-06
Check this thread. 
[http://ubuntuforums.org/showthread.php?t=758247](http://ubuntuforums.org/showthread.php?t=758247)

---

### Post by alwayshere on 2008-12-06
sudo  gedit ~/.config/Google/GoogleEarthPlus.conf

show this 


> [General]
AnimSpeed=1
CachePath=/root/.googleearth/Cache
ClampBegin=false
ControllerEnabled=false
ControllerMode=2
InvertMouseWheel=false
KMLPath=/root/.googleearth
Key="yaUtgEwD7bE="
LogoutClean=true
NavigatorShow=0
PolyEditXPos=75
PolyEditYPos=72
RepeatMode=1
ReverseControls=false
SMode=true
SwoopEnabled=true
TimeFolderRestrict=false
TimeShow=1
TimeZoneHours=13
TimeZoneMinutes=0
TimeZoneMode=1
TimeZoneName=Local
UID="VovpqYWLqz/NzQu08HS0QQ=="
VID="AAAADTQuMy43Mjg0LjM5MTY="
currentVersion=4.3.7284.3916
defaultBrowser=true
hiddenWindows-4_3=@Invalid()
lastHeight=640
lastLeft=15
lastTip=2
lastTop=33
lastWidth=960
layersOpen=true
mouseWheelSpeed=1
osName=Linux
placesOpen=true
renderWarning-OGLsoftwareEmulated=false
searchOpen=true
shown_GPS=false
shown_LeftPanel=true
shown_RenderFrame=true
shown_Ruler=false
visibleWindows-4_3=RenderWindow, ServerWindow
wasFullScreen=false
wasMaximized=false

[Layer]
FlySpeed=0.171
drivingDirectionsRange=1000
drivingDirectionsSpeed=150
drivingDirectionsTilt=45
pauseTime=1.6
tourBalloonShow=false
tourCycles=1
tourSpeed=0.171

[Render]
CompassVisible=true

[UsageStatistics]
firstRun\day=7
firstRun\hour=13
firstRun\minute=24
firstRun\month=12
firstRun\second=48
firstRun\year=2008
loginHistory=0
numRuns=1
numRunsThisVersion=1
prevRun\day=7
prevRun\hour=13
prevRun\minute=24
prevRun\month=12
prevRun\second=48
prevRun\year=2008

[autoupdate]
InstalledVersion=4.3.7284.3916

---

### Post by eBoxNet on 2008-12-06
try adding this : GuiFontSize=12
on [render] section

---

### Post by alwayshere on 2008-12-07
Thanks for the help but it did not work I think that line is for an older version .

---

### Post by alwayshere on 2008-12-07
wow am I the only one using google earth is there a better option or something ???

if your goggle earth is working could you please post the result of the below command thanks .

sudo  gedit ~/.config/Google/GoogleEarthPlus.conf

---

