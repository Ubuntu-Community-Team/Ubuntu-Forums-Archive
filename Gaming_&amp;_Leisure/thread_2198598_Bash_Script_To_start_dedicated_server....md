---
title: "Bash Script To start dedicated server..."
date: 2014-01-09
forum: Gaming &amp; Leisure
---

### Post by wgladue on 2014-01-09
So I am trying to convert bat file into a bash script.  The Game Was originally for Windows, but the native linux build is coming "soon".  I have been pulling out my hair trying to get a dedicated server bash file to work.  The original Bat goes as follows:
*********************************************************************************************************************
rem
rem Starts a dedicated server
rem
rem -quit, -batchmode, -nographics: Unity commands
rem -configfile              : Allows server settings to be set up in an xml config file. Use no path if in same dir or full path.
rem -dedicated                    : Has to be the last option to start the dedicated server.

start 7daystodie -quit -batchmode -nographics -configfile=serverconfig.xml -dedicated

REM wait until game started
timeout 10

REM connect to the service interface. use 'shutdown' to stop the server
if exist "Tools/bin/putty.exe" (
     "Tools/bin/putty.exe" -telnet localhost 8081
) else (
     telnet localhost 8081
)

pause


*****************************************************************************


So far, I have come up with this

********************************************************************

#! /bin/bash
# script to start dedicated server
./7DaysToDie.x86_64 -quit -batchmode -nogui -configfile=serverconfig.xml -dedicated


**********************************************************************************

but it isn't working right...

Any Suggetions would be appreciated...

---

### Post by papibe on 2014-01-09
Hi wgladue. Welcome to the forum ):P

The line:
```
./7DaysToDie.x86_64... 
```
only would start the program if 'DaysToDie.x86_64' is located on the current directory where you are executing the script, and have execution permissions.

It would be interesting to see what errors are you getting so we can help you debug it.

Here's a few ideas:
[LIST]
[*]Use the absolute path to the program, and
[*]make sure that the program has execution permissions.
[/LIST]
Let's assume that the 7DaysToDie.x86_64 is in /usr/bin/7DaysToDie.x86_64. Then to add execution permissions:
```
sudo chmod a+x /usr/bin/7DaysToDie.x86_64
```
(it will ask for your user password).

Then the script should be:
```
#! /bin/bash
# script to start dedicated server
/usr/bin/7DaysToDie.x86_64 -quit -batchmode -nogui -configfile=serverconfig.xml -dedicated
```
Finally, the script itself has to be executable so make sure it is:
```
chmod a+x yourscript.sh
```
(assuming your script is called yourscript.sh)

Hope it helps. Let us know how it goes.
Regards.

---

### Post by wgladue on 2014-01-09
yeah, the script is located in the same directory as the executable... 
When I run it via terminal, things seem to go okay without errors.  After about a minute, I get a "loading screen" pop-up for the game 
I had to change the "bat: -nographics" to "bash: -nogui" to avoid any errors and it accesses my xml file properly.
 
The thing that bugs me is that screen that comes up... its not a great dedicated server script if there is a gui :D

Any suggestions? and thank you very much for the warm welcome ):P

---

### Post by wgladue on 2014-01-09
I also have an update, I shared the file with a fellow tester, and he does not have the pop-up display on his VM.  I am using Ubuntu 13.10, and the only main difference we have found was that he has a Virtual Machine, and I run Ubuntu as an OS

---

