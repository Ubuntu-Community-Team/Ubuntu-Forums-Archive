---
title: "suspend your sambaserver/XBMC machine"
date: 2010-03-06
forum: Desktop Environments
---

### Post by koekiemonster on 2010-03-06
Situation:
You've got an HTPC, running XBMC and sharing it's files through samba, and you want to be able to put it in suspend (S3), when it's not in use.
the normal idle check of ubuntu ignores the use of samba shares, so using the default standby after x minutes in gnome was no option, since it suspends the machine even if you're sending/downloading files from it, or using it to stream media from.

the python script i wrote checks if there are samba file locks (streaming media, or down/uploads), important samba shares in use, if the machine is idle (keyboard/mouse activity) and if XBMC is playing media. it also has a lockfile function, so you can keep the machine awake (during upgrades, or if you're accessing it through ssh/ftp)

how to use it is in the comments of the script, read this because the script will need some aditional files/info from you.

comments/tips/ideas are welcome, future plans are to include checks for ftp server activity and torrent downloading activity.


```
#!/usr/bin/python

###########################
# HTPC suspend script     #
# author: Hans van Schoot #
###########################

# The purpose of this script is to suspend the machine if it's idle.
# the script checks:
# - if a lockfile is present (this way the script can be bypassed when needed)
# - if XBMC is running, and if it's playing
# - if there is keyboard or mouse activity
# - if there are samba shares in use (READ ON FOR THIS!)

# To function properly this script needs a couple things:
# - from apt-get: xprintidle
# - the gnome-power-control script (installed in /usr/bin) from AgenT: http://ubuntuforums.org/showpost.php?p=8309702&postcount=16
# - xbmc web server enabled without a password (can be found in xmbc settings under network) 
#     (if you don't need xbmc, you can comment out the xbmc section or put the xbmcDelay on 0)
# - to be able to use "sudo smbstatus" (so rootaccess, or if you run the script on userlevel this can be fixed by adding
#     "your_username ALL=(ALL) NOPASSWD: /usr/bin/smbstatus" visudo (run "sudo visudo" in terminal))


#############################
# Settings and delay values #
#############################
# the system suspends only if all the different items are idle for a longer time than specified for it
# the values are in minutes, unless you change the sleep command at the start of the loop
xbmcDelay = 15
sambafileDelay = 30
xDelay = 30
# this is the path to the lockfile you can use.
# to lock the system, just use the touchcommand: "touch /home/media/.suspendlockfile" (or create a starter to it)
# to unlock the system, just use rmcommand "rm /home/media/.suspendlockfile" (or create a starter to it)
lockfilePath = "/home/media/.suspendlockfile.txt"
# the path to the xmbc webserver, edit this if you use another port for instance
xbmcAdress = "http://127.0.0.1:8080/xbmcCmds/xbmcHttp?command=getcurrentlyplaying"

##### SAMBACHECK SETTINGS #######
# the script checks the output of sudo smbstatus to see if there are locked files 
# (usualy someone downloading or playing media from the system)
# if no locked files are found, it checks if there are folders in use that should keep the system awake
# 
# smbimportantlist is a list of strings the sambashare should check if they are in use (for instance a documents folder)
# to find out what to put here: 
# 1. connect to the share with another computer
# 2. use "sudo smbstatus" in console
# 3. check for the name of the share, it's printed out under "Service"
#
# makeup of the list is: [ 'item1' , 'item2' , 'item3' ]
smbimportantlist = [
'documents',
'muziek'
]

# change this to False if you want the script to run silent
debugmode = True




### the script starts here
from os import *
from urllib2 import *
from time import sleep

xbmcIdletime = 0
sambaIdletime = 0
noLockfile = True
keeponrunnin = True

# this is the loop that keeps the script running. the sleep command makes it wait one minute
# if you want to increase/decrease the frequencies of the checks, change the sleeptimer.
# keep in mind that this wil change the Delay times for xbmc and samba
while keeponrunnin:
    sleep(60)
# this checks when the mouse and keyboard were touched, and converts the time to minutes
    try: xIdletime = int(popen('xprintidle').read())/60000
    except IOError, e:
        if debugmode:
            print "xprintidle is not installed? use sudo apt-get install xprintidle"
        

# check XBMC for activity:
    xbmcRequest = Request(xbmcAdress)
    try: handle = urlopen(xbmcRequest)
    except IOError, e:
        if debugmode:
            print "XBMC draait niet"
        xbmcIdletime += 1 
    else:
        page = handle.read()
        if page.find('Filename:[Nothing Playing]') >= 0:
            if debugmode:
                print "Nothing Playing\n"
            xbmcIdletime += 1 
        elif page.find('PlayStatus:Playing') >= 0:
            if debugmode:
                print "XBMC is playing"
            xbmcIdletime = 0
        elif page.find('PlayStatus:Paused') >= 0:
            if debugmode:
                print "XBMC is paused"
            xbmcIdletime += 1


# check if the lockfile is present
    if path.exists("/home/media/.suspendlockfile"):
        noLockfile = False
    else:
        noLockfile = True

#######################################
# next section is the samba checkpart #
#######################################
    try: sambainfo = popen('sudo smbstatus').read()
    except IOError, e:
        if debugmode:
            print "No Sambaserver found, or no sudorights for smbstatus"
        sambaIdletime += 1 
    else:
        # first we check for file-locks
        if sambainfo.find('Locked files:\n') >= 0:
            sambaIdletime = 0
            if debugmode:
                print "a locked samba file has been found"
        # if no locked files, strip the info and look for keywords, if found reset idletime
        else:
            sambaIdletime += 1
            sambasplit = sambainfo.split('\n')[4:-4]
            sambasplit.reverse()
            for i in sambasplit:
                if i == '-------------------------------------------------------':
                    break
                for j in smbimportantlist:
                    # check to filter out crashes on empty lines
                    if len(i.split()) >= 1:
                        if i.split()[0].find(j) >= 0:
                            sambaIdletime = 0
                            if debugmode:
                                print "an important samba share is in use"


# this is the final check to see if the system can suspend. 
# uncomment the print statements and run in terminal if you want to debug/test the script
    if xbmcIdletime >= xbmcDelay and xIdletime >= xDelay and sambaIdletime >= sambafileDelay and noLockfile:
        if debugmode:
            print "suspend allowed"
        system('gnome-power-control suspend')
        xbmcIdletime = 0
        sambaIdletime = 0
    else:
        if debugmode:
            print "system is active, not suspending"
            print "xsystem is idle for ", xIdletime, " minutes"
            print "xbmc is idle for ", xbmcIdletime, " minutes"
            print "samba is idle for ", sambaIdletime, " minutes"
            if noLockfile:
                print "er is geen lockfile gevonden"
            else:
                print "er is een lockfile gevonden"
```


aditional tip: i'm using this in combination with wake on lan

---

### Post by dinozzo on 2010-03-31
Hi [koekiemonster]("http://ubuntuforums.org/member.php?u=967406"), this script is exactly what im after. I have done a minimal install of ubuntu and installed xbmc using this guide [http://wiki.xbmc.org/index.php?title=XBMCbuntu#Method_1a:_add_NVIDIA_repository](http://wiki.xbmc.org/index.php?title=XBMCbuntu#Method_1a:_add_NVIDIA_repository)

I have installed everything needed as the instructions say in your script and I executed it to test it and it returned an error after a while:

root@ubuntu:/home/xbmc/Media# /home/xbmc/Media/suspend.py
couldn't open display
Traceback (most recent call last):
  File "/home/xbmc/Media/suspend.py", line 78, in <module>
    try: xIdletime = int(popen('xprintidle').read())/60000
ValueError: invalid literal for int() with base 10: ''

Any ideas how to fix?

---

### Post by koekiemonster on 2010-04-01
Hi dinozzo,

if you're running a minimal install of ubuntu and XBMC, you can remove the part that checks for xprintidle. (since you're not using a gnome/kde desktop to work on the machine i guess?) that might also be the source of the error. xprintidle checks for mouse or keyboard activity in an X session and you don't have that with a minimal install.
just remember to halt the script or put a lockfile in place when you're working on the machine outside of xbmc ;)

comment out (or remove) this part:
```

    try: xIdletime = int(popen('xprintidle').read())/60000
    except IOError, e:
        if debugmode:
            print "xprintidle is not installed? use sudo apt-get install xprintidle"
```and change the line following the "final check" by removing this: "xIdletime >= xDelay and"


i've also upgraded my own script with a check for transmission torrent activity, i'll upload it when i've time to clean up and comment my code :)

---

### Post by koekiemonster on 2010-04-01
decided i could make some time to put v2 on the forum ;)

```

#!/usr/bin/python

###########################
# HTPC suspend script     #
# author: Hans van Schoot #
###########################
# TODO list: build in a check for ftp server activity

# The purpose of this script is to suspend the machine if it's idle.
# the script checks:
# - if a lockfile is present (this way the script can be bypassed when needed)
# - if XBMC is running, and if it's playing
# - if there is keyboard or mouse activity
# - if transmission download speed is too low to be keeping the system awake
# - if there are samba shares in use (READ ON FOR THIS!)

# To function properly this script needs a couple things:
# - from apt-get: xprintidle
# - from apt-get: transmissioncli
# - the gnome-power-control script (installed in /usr/bin) from AgenT: http://ubuntuforums.org/showpost.php?p=8309702&postcount=16
# - xbmc web server enabled without a password (can be found in xmbc settings under network) 
#     (if you don't need xbmc, you can comment out the xbmc section or put the xbmcDelay on 0)
# - to be able to use "sudo smbstatus" (so rootaccess, or if you run the script on userlevel this can be fixed by adding
#     "your_username ALL=(ALL) NOPASSWD: /usr/bin/smbstatus" visudo (run "sudo visudo" in terminal))

# if you're running a minimal ubuntu install (without a x session, like gnome or kde) you can't use/don't need
# the xprintidle stuff. you can remove this from the script, or just don't install xprintidle and put the xDelay on 0


#############################
# Settings and delay values #
#############################
# the system suspends only if all the different items are idle for a longer time than specified for it
# the values are in minutes, unless you change the sleep command at the start of the loop
xbmcDelay = 15
sambafileDelay = 30
xDelay = 30
transmissionDelay = 10
# this is the path to the lockfile you can use.
# to lock the system, just use the touchcommand: "touch /home/media/.suspendlockfile" (or create a starter to it)
# to unlock the system, just use rmcommand "rm /home/media/.suspendlockfile" (or create a starter to it)
lockfilePath = "/home/media/.suspendlockfile.txt"
# the path to the xmbc webserver, edit this if you use another port for instance
xbmcAdress = "http://127.0.0.1:8080/xbmcCmds/xbmcHttp?command=getcurrentlyplaying"
# logindata for the transmission server (this is the same data you need to enter when contacting the demon through the web interface
transmissionlogin = "enter your login here"
transmissionpass = "enter your password here"
# command to contact the transmission server
transmissionAdress = "transmission-remote -n %s:%s " %(transmissionlogin,transmissionpass)
# minimal download speed required to keep the system awake (in kb/s)
transmissionSpeed = 10.0


##### SAMBACHECK SETTINGS #######
# the script checks the output of sudo smbstatus to see if there are locked files 
# (usualy someone downloading or playing media from the system)
# if no locked files are found, it checks if there are folders in use that should keep the system awake
# 
# smbimportantlist is a list of strings the sambashare should check if they are in use (for instance a documents folder)
# to find out what to put here: 
# 1. connect to the share with another computer
# 2. use "sudo smbstatus" in console
# 3. check for the name of the share, it's printed out under "Service"
#
# makeup of the list is: [ 'item1' , 'item2' , 'item3' ]
smbimportantlist = [
'documents',
'muziek'
]

# this list checks for lockfiles in specified home directories, makeup is the same as the smblist, but with pathnames to possible lockfiles
# add/change (or remove) as many lockfile locations as you like
lockfilelist = [
'/home/user1/.suspendlockfile',
'/home/user2/.suspendlockfile',
'/home/user3/.suspendlockfile'
]

# change this to False if you want the script to run silent
debugmode = True




### the script starts here
from os import *
from urllib2 import *
from time import sleep

xIdletime = 0
xbmcIdletime = 0
sambaIdletime = 0
transmissionIdletime = 0
Lockfile = 0
keeponrunnin = True

# this is the loop that keeps the script running. the sleep command makes it wait one minute
# if you want to increase/decrease the frequencies of the checks, change the sleeptimer.
# keep in mind that this wil change the Delay times for xbmc and samba
while keeponrunnin:
    print "\n !!! Niet dichtdoen!!!\n Dit schermpje moet de pc in slaapstand zetten!\n"
    sleep(60)
# this checks when the mouse and keyboard were touched, and converts the time to minutes
    try: xIdletime = int(popen('xprintidle').read())/60000
    except IOError, e:
        if debugmode:
            print "xprintidle is not installed? use sudo apt-get install xprintidle"
        

# check XBMC for activity:
    xbmcRequest = Request(xbmcAdress)
    try: handle = urlopen(xbmcRequest)
    except IOError, e:
        if debugmode:
            print "XBMC draait niet"
        xbmcIdletime += 1
    except httplib.HTTPException:
        if debugmode:
            print "XBMC pagina httpexception error, better luck next round..."
    else:
        page = handle.read()
        if page.find('Filename:[Nothing Playing]') >= 0:
            if debugmode:
                print "Nothing Playing\n"
            xbmcIdletime += 1 
        elif page.find('PlayStatus:Playing') >= 0:
            if debugmode:
                print "XBMC is playing"
            xbmcIdletime = 0
        elif page.find('PlayStatus:Paused') >= 0:
            if debugmode:
                print "XBMC is paused"
            xbmcIdletime += 1


# counting the number of lockfiles
    Lockfile = 0
    for i in lockfilelist:
        if path.exists(i):
            Lockfile += 1

#######################################
# next section is the samba checkpart #
#######################################
    try: sambainfo = popen('sudo smbstatus').read()
    except IOError, e:
        if debugmode:
            print "No Sambaserver found, or no sudorights for smbstatus"
        sambaIdletime += 1 
    else:
        # first we check for file-locks
        if sambainfo.find('Locked files:\n') >= 0:
            sambaIdletime = 0
            if debugmode:
                print "a locked samba file has been found"
        # if no locked files, strip the info and look for keywords, if found reset idletime
        else:
            sambaIdletime += 1
            sambasplit = sambainfo.split('\n')[4:-4]
            sambasplit.reverse()
            for i in sambasplit:
                if i == '-------------------------------------------------------':
                    break
                for j in smbimportantlist:
                    # check to filter out crashes on empty lines
                    if len(i.split()) >= 1:
                        if i.split()[0].find(j) >= 0:
                            sambaIdletime = 0
                            if debugmode:
                                print "an important samba share is in use"


# this is the check for torrent activity. it checks the last value in the last line
# from the transmission-remote command, which is the downloadspeed in kb/s
    try: transmissioninfo = popen(transmissionAdress + "-l").read()
    except IOError, e:
        if debugmode:
            print "transmissioncli not installed"
        transmissionIdletime += 1
    else: 
        if transmissioninfo.find('Couldn\'t connect to server') >= 0:
            transmissionIdletime += 1
            if debugmode:
                print "transmission draait niet"
        elif float(transmissioninfo.split()[-1]) >= transmissionSpeed:
                transmissionIdletime = 0
                if debugmode:
                    print "transmission is downloading @ %s kb/s" %(transmissioninfo.split()[-1])
        else:
            transmissionIdletime += 1


# this is the final check to see if the system can suspend. 
# uncomment the print statements and run in terminal if you want to debug/test the script
    if xbmcIdletime >= xbmcDelay and xIdletime >= xDelay and sambaIdletime >= sambafileDelay and transmissionIdletime >= transmissionDelay and Lockfile == 0:
        if debugmode:
            print "suspend allowed"
        system('gnome-power-control suspend')
        xbmcIdletime = 0
        sambaIdletime = 0
        transmissionIdletime = 0
    else:
        if debugmode:
            print "system is active, not suspending"
            print "xsystem is idle for ", xIdletime, " minutes"
            print "xbmc is idle for ", xbmcIdletime, " minutes"
            print "samba is idle for ", sambaIdletime, " minutes"
            print "transmission is idle for ", transmissionIdletime, " minutes"
            if Lockfile == 0:
                print "er is geen lockfile gevonden"
            else:
                print "er is/zijn %i lockfile gevonden" %(Lockfile)

```

some cleanups and it's now also capable of reading the transmission download speed and keeping the system alive above a set speed. (i don't think it's usefull to keep the system running for torrents downloading with very low speed).
i also changed a small thing with the xprintidle and added a comment about running a minimal installation (thanks to the head's up from dinozzo) with this script

---

### Post by dinozzo on 2010-04-01
Awesome stuff [koekiemonster]("http://ubuntuforums.org/member.php?u=967406")! I now have it working and it works a treat!

root@ubuntu:/home/xbmc# /home/xbmc/suspend
Nothing Playing
a locked samba file has been found
system is active, not suspending
xbmc is idle for  1  minutes
samba is idle for  0  minutes
no lockfile has been found

All I need now is to get it to run on system startup. What would you suggest is the best way of doing this?

TIA

---

### Post by koekiemonster on 2010-04-01
good to hear it's working. on my server it gets started by gnome, but that's not an option with a minimal install. i think a bit of google work with terms like "ubuntu minimal run script on startup" should do the trick for you ;o)

---

### Post by koekiemonster on 2010-10-02
I moved to XBMC Dharma beta 2, and updated the script a few times since my last post. it's now also capable of making recursive backups (rsync and linked files, to minimize disk space used)
I'm working on a complete remake with a lot of cleaning up in the code, but for those of you who are interested, this is the version i'm currently running:

```

#!/usr/bin/python

###########################
# HTPC suspend script     #
# author: Hans van Schoot #
###########################
# TODO list: build in a check for ftp server activity
# turn the script into nice program with modules

# The purpose of this script is to suspend the machine if it's idle.
# the script checks:
# - if a lockfile is present (this way the script can be bypassed when needed)
# - if XBMC is running, and if it's playing
# - if there is keyboard or mouse activity
# - if transmission download speed is too low to keep the system awake for
# - if there are samba shares in use (READ ON FOR THIS!)

# To function properly this script needs a couple things:
# - from apt-get: xprintidle
# - from apt-get: transmissioncli
# - the gnome-power-control script (installed in /usr/bin) from AgenT: http://ubuntuforums.org/showpost.php?p=8309702&postcount=16
# - xbmc web server enabled without a password (can be found in xmbc settings under network) 
#     (if you don't need xbmc, you can comment out the xbmc section or put the xbmcDelay on 0)
# - to be able to use "sudo smbstatus" (so rootaccess, or if you run the script on userlevel this can be fixed by adding
#     "your_username ALL=(ALL) NOPASSWD: /usr/bin/smbstatus" visudo (run "sudo visudo" in terminal))
# the same goes for sudo /usr/sbin/pm-suspend !!!!! the suspend command!


#############################
# Settings and delay values #
#############################
# the system suspends only if all the different items are idle for a longer time than specified for it
# the values are in minutes, unless you change the sleep command at the start of the loop
xbmcDelay = 30
sambafileDelay = 30
xDelay = 0 #currently broken, XBMC Dharma beta 2 generates X events...
transmissionDelay = 10
# these deltas are the minimum time between 2 backups, or the running of flexget
# flexget automaticly runs on wakeup of the machine
# do not remove datetime import line!
from datetime import *
backupDelta = timedelta(hours=24)
flexgetDelta = timedelta(hours=2)

# this is the path to the lockfile you can use.
# to lock the system, just use the touchcommand: "touch /home/media/.suspendlockfile" (or create a starter to it)
# to unlock the system, just use rmcommand "rm /home/media/.suspendlockfile" (or create a starter to it)
lockfilelist = [
'/home/USERNAMEHERE/.suspendlockfile'
]
# the path to the xmbc webserver, edit this if you use another port for instance
xbmcAdressJSON = "http://127.0.0.1:8080/jsonrpc"

# command to contact the transmission server, -n is user/pass
transmissionAdress = "transmission-remote -n USERNAME:PASSWORD "
# minimal download speed required to keep the system awake
transmissionSpeed = 10.0


##### SAMBACHECK SETTINGS #######
# the script checks the output of sudo smbstatus to see if there are locked files 
# (usualy someone downloading or playing media from the system)
# if no locked files are found, it checks if there are folders in use that should keep the system awake
# 
# smbimportantlist is a list of strings the sambashare should check if they are in use (for instance a documents folder)
# to find out what to put here: 
# 1. connect to the share with another computer
# 2. use "sudo smbstatus" in console
# 3. check for the name of the share, it's printed out under "Service"
#
# makeup of the list is: [ 'item1' , 'item2' , 'item3' ]
smbimportantlist = [
'documents',
'muziek'
]


# change this to False if you want the script to run silent
debugmode = True




### the script starts here
from os import *
from urllib2 import *
from time import sleep
import json
import httplib
import sys


xbmcIdletime = 0
sambaIdletime = 0
transmissionIdletime = 0
Lockfile = 0
keeponrunnin = True
startup = True
newfiles = False
backupDate = datetime.now()
flexgetDate = datetime.now()


# this is the loop that keeps the script running. the sleep command makes it wait one minute
# if you want to increase/decrease the frequencies of the checks, change the sleeptimer.
# keep in mind that this wil change the Delay times for xbmc and samba
while keeponrunnin:
    print "\n !!! Niet dichtdoen!!!\n Dit schermpje moet de pc in slaapstand zetten!\n"

# aditional lines to make flexget run directly after a suspend, even if the last flexget was less than 2 hours ago
    if startup:
        sleep(10)
        print popen('flexget').read()
        flexgetDate = datetime.now()
        startup = False

    sleep(60) # this is the delay that runs the script every minute, lower this value for testing!


# this part checks if transmission and xbmc are idle. if there are new files (newfiles gets activated when transmission is downloading, so if transmission is idle again the torrents should be finished. another trick would be to check the transmission-remote output for torrents that are completed and move them)
    if transmissionIdletime >= 3 and xbmcIdletime >= 3 and newfiles:
        print popen('/home/media/showmover.py').read() #this is a script i'm using to move downloaded files into the right TV show directory
        print "updating the xbmc video Library"
        try: handle = urlopen(xbmcAdressJSON, '{"jsonrpc": "2.0", "method": "VideoLibrary.ScanForContent", "id": "1"}')
        except IOError, e:
            print "jsonrpc is not responding..."
        else:
            newfiles = False


# this checks when the mouse and keyboard were touched, and converts the time to minutes
    try: xIdletime = int(popen('xprintidle').read())/60000
    except IOError, e:
        if debugmode:
            print "xprintidle is not installed? use sudo apt-get install xprintidle"
        

# check XBMC for activity:
    try: handle = urlopen(xbmcAdressJSON, '{"jsonrpc": "2.0", "method": "Player.GetActivePlayers", "id": "1"}')
    except IOError, e:
        print "XBMC webinterface (jsonRPC) is not responding, checking if xbmc is running"
        psgrepxbmc = popen("ps -e | grep xbmc").read()
        if len(psgrepxbmc) == 0:
            print "XBMC not found using grep, most likely not running! starting XBMC..."
            system("xbmc &")
        else:
            print "XBMC is running, but jsonrpc is not responding"
# i need to come up with something smart here. something like xbmcActive boolean & xbmc not responsive timer. if timer >5 & boolean false (so not to kill during playback): kill all xbmc proccesses, sleep 15 seconds and start xbmc?
#            psgreplines = psgrepxbmc.split("\n")
#            for psline in psgreplines:
#                pid = psline.split()[0]
#                system("kill %i",pid)
#            sleep(15)
#            system("xbmc &")
            xbmcIdletime += 1
    else:
# dit moet eleganter kunnen!
        if debugmode:
            print "contact with the JSONRPC page"
        page = handle.read()
        if page.find('"audio" : true') >= 0 or page.find('"video" : true') >= 0 or page.find('"picture" : true') >= 0:
            if debugmode:
                print "XBMC is playing or paused"
# we need to filter out paused here!
            xbmcIdletime = 0 
        elif page.find('"audio" : false') >= 0 and page.find('"video" : false') >= 0 and page.find('"picture" : false') >= 0:
            if debugmode:
                print "XBMC is not playing or paused"
            xbmcIdletime += 1
        else:
            print "Something strange is going on, or we messed up the search patterns!"
            if debugmode:
                print page


# counting the number of lockfiles
    Lockfile = 0
    for i in lockfilelist:
        if path.exists(i):
            Lockfile += 1

#######################################
# next section is the samba checkpart #
#######################################
    try: sambainfo = popen('sudo smbstatus').read()
    except IOError, e:
        if debugmode:
            print "No Sambaserver found, or no sudorights for smbstatus"
        sambaIdletime += 1 
    else:
        # first we check for file-locks
        if sambainfo.find('Locked files:\n') >= 0:
            sambaIdletime = 0
            if debugmode:
                print "a locked samba file has been found"
        # if no locked files, strip the info and look for keywords, if found reset idletime
        else:
            sambaIdletime += 1
            sambasplit = sambainfo.split('\n')[4:-4]
            sambasplit.reverse()
            for i in sambasplit:
                if i == '-------------------------------------------------------':
                    break
                for j in smbimportantlist:
                    # check to filter out crashes on empty lines
                    if len(i.split()) >= 1:
                        if i.split()[0].find(j) >= 0:
                            sambaIdletime = 0
                            if debugmode:
                                print "an important samba share is in use"


# this is the check for torrent activity. it checks the last value in the last line
# from the transmission-remote command, which is the downloadspeed in kb/s
    try: transmissioninfo = popen(transmissionAdress + "-l").read()
    except IOError, e:
        if debugmode:
            print "transmissioncli not installed"
        transmissionIdletime += 1
    else: 
        if transmissioninfo == '':
            transmissionIdletime += 1
            if debugmode:
                print "transmission draait niet"
        elif float(transmissioninfo.split()[-1]) >= transmissionSpeed:
                transmissionIdletime = 0
                newfiles = True
                if debugmode:
                    print "transmission is downloading @ %s kb/s" %(transmissioninfo.split()[-1])
        else:
            transmissionIdletime += 1



# a check to see if we can run backup scripts
    if xbmcIdletime >=3 and xIdletime >=3 and sambaIdletime >=3 and Lockfile == 0:
        currenttime = datetime.now()
        if (currenttime - backupDate) >= backupDelta:
            # backup the files using linkcopy, combined with Rsyncing to the original backup location gives recursives backups
            print "backing up the system now..."
            system('cp -al /media/drive2/Backups /media/drive2/Backups-old/backup-%i-%i-%i'%(currenttime.year,currenttime.month,currenttime.day))
            backupDate = datetime.now()
            print "rsyncing the current Backupfolder to the other harddisk, this should be fast if not too much has changed"
            system('rsync -a /media/drive2/Backups /media/drive1/Backup-mirror')


# this part runs flexget if xbmc is idle and the flexget hasn't been run in the last 2 hours 
    if xbmcIdletime >=3:
        currenttime = datetime.now()
        if (currenttime - flexgetDate) >= flexgetDelta:
            print popen('flexget').read()
            flexgetDate = datetime.now()



# this is the final check to see if the system can suspend. 
# uncomment the print statements and run in terminal if you want to debug/test the script
    if xbmcIdletime >= xbmcDelay and xIdletime >= xDelay and sambaIdletime >= sambafileDelay and transmissionIdletime >= transmissionDelay and Lockfile == 0:
        if debugmode:
            print "suspend allowed"
        system('sudo /usr/sbin/pm-suspend')
        xbmcIdletime = 0
        startup = True
    else:
        if debugmode:
            print "the time is", datetime.now()
            print "system is active, not suspending"
            print "xsystem is idle for ", xIdletime, " minutes"
            print "xbmc is idle for ", xbmcIdletime, " minutes"
            print "samba is idle for ", sambaIdletime, " minutes"
            print "transmission is idle for ", transmissionIdletime, " minutes"
            if Lockfile == 0:
                print "er is geen lockfile gevonden"
            else:
                print "er is/zijn %i lockfile gevonden" %(Lockfile)

```

---

