---
title: "Problems with shell script launching GUI pwd prompt"
date: 2012-03-06
forum: Desktop Environments
---

### Post by ekidmose on 2012-03-06
I'm using AFS under ubuntu 10.04 to access files and it works ok, but I want to improve it.. :-)
In order to access the files on the AFS filessystem I must obtain a token by executing a "klog" command and input my password. The token expires every 24 hrs, requiring the klog to be executed again. 

What I want to do: 
When a network connection is established it should check if I have a token, and prompt me for password and obtain a new one if required. 

What I've got: 
The attached script which is executed by NetworkManager whenever a network device changes state. 
By monitoring the file testupdown.txt I've verified that the script and the desired if-condition is executed, when I've got no tokens and plug in the Ethernet cable in. 

The problem:
When executing the script from a terminal it works perfectly fine, 
but when the script is called by NetworkManager the GUI prompt(the line with "pwd=$(zenity..." doesn't show on my screen. 
As mentioned, line just above is executed as the script writes to testupdown.txt. 
I've tried replacing the line "pwd=$(zenity..." with "xterm klog" which would also be fine, but this doesn't show on the screen either. 

Does anyone have any suggestions as to why the script is executed but anything GUI related seems to disappear?
Any suggestions to further troubleshooting?

Thanks a bunch  :-)

---

### Post by ekidmose on 2012-03-13
Any suggestions as to where help can be found?
Am I posting to the wrong forum section?

---

