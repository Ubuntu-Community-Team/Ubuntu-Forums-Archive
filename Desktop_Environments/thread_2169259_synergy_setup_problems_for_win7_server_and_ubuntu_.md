---
title: "synergy setup problems for win7 server and ubuntu client"
date: 2013-08-21
forum: Desktop Environments
---

### Post by wendallsan on 2013-08-21
Hi, I've been encouraged to use synergy with my development setup, which includes a win7 laptop and ubuntu server at my desk.  I have to use Windows to work with my business partner, but have used Ubuntu on the desktop for 10+ years.  I primarily use the laptop and would like to configure it as the synergy server and configure the ubuntu desktop as the client. I have tried configuring this several times using the documentation and information around the web, but have never succeeded in getting a connection to work. I have tried using various versions of the windows install (1.3.1), as there is some discussion of problems with the most recent version.

I go through the windows install's documentation to set up the laptop as the server, add my 2 screens, and link the two screens with the following details. Please note that 'RUXED' is the computer name for my windows 7 laptop and 'grapefruitsky' is the hostname of my ubuntu desktop, so I am using screen names below that are identical to the systems' names.

screens:
1: grapefruitsky with alias set to that system's local ip address (192.168.1.103)
2: RUXED with alias set to the laptop's local ip address (192.168.1.104)

links:
RUXED is below grapefruitsky
grapefruitsky is above RUXED

Once this is configured, clicking the 'test' button I get a log window with the message:

INFO: Synergy server 1.3.1 on Microsoft Windows 6.1
NOTE: started server
INFO: screen "RUXED" shape changed

There are no error messages, so it seems to be working. I end the test and start the server normally, bring up the server log viewer from the system tray, and move to the client.

on the ubuntu desktop, I configure it as a client, synergy identifies the system with the screen name 'grapefruitsky', and I set the Server IP field to either RUXED, RUXED.local, or 192.168.1.104 (trying different suggestions from the internet). I can start the client, and receive no error messages.

So at this point it appears that both the client and server are running, and to the best of my understanding they are configured to work together, but I receive no messages on the server indicating that a connection from the client has been made, and most importantly no one-mouse-on-two computers goodness.

The first thing I checked at this point was the windows firewall, but allowances for synergy were put in place with the app was installed. I also checked my ubuntu system to see if I have a firewall installed there (it is a fresh install of ubuntu, as I have not used it since I can't get synergy working).  Running 'sudo ufw status' reports that the firewall is inactive, so I don't think there are any problems there, either.  What can I do to begin to troubleshoot this beyond what I have already done? Thanks for any assistance.

---

