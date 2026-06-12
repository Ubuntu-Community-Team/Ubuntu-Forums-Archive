---
title: "Remote Desktop and automation scripts - advise"
date: 2011-05-09
forum: Desktop Environments
---

### Post by MugOTea on 2011-05-09
Hi all,

I am preparing a support server in the typical format, client calls for support, they are instructed to visit a public webpage and enter a pre-negotiated session ID. Using SSH to a separate server which is also in contact with the public hosted database, the support technician receives details about the clients system via javascript (OS, Browser etc.) and generates a file / link for the client to click on (on the fly).

I have already configured the Windows client download which is a self extracting single click VNC server which fully uninstalls when the job is done. The on the fly compilation covers use of predetermined ports that MY server has allowed through a firewall, and OS specific instructions such as UAC control / disabled. Once installed on the clients PC the VNC server is preconfigured to connect to my server using the VNC reverse protocol making life easy for the client.

MY QUESTION(S):
I want to include this functionality for supporting various flavours of linux and mac - and in future any other device that supports X or vnc protocols. But I need help with how to automate a connection to Linux / Ubuntu and make the clients life as easy as possible.

I presume I will need a command/script that will do the following with as little involvement from the client (preferably a single click):
 - Check for compatible VNC / X Sharing server capability
 - Confirm actions with client / user
 - Finally reverse connect to client hosted on ADDRESS/PORT specified in a generated conf file

I considering researching the DEB install format / automation under ubuntu but I need the client to understand it is a safe connection (using VNC passwords) and reversed so they are not exposed, and will not be left open once the support session is over. Deb always seems to require sudo when theoretically this service shouldn't (for the connection anyway). 

What do you guys think?

1/ Is my post in the right category?
2/ Would anyone be interested in the scripts and a tutorial for what I have sofar?
3/ Any suggestions on how to package a connection and automatic script under linux (or mac)?

As I say, the windoze download works already and the client is faced with a webpage, which is populated by the technician in real time with links and files to download/run. The executable download appears and they are asked to run it and the connection begins shortly afterwards.

The code is pretty crude at the moment, I'd call it prototype some other developers I know call it - well something we shouldn't say in front of children, but I'm just getting into the modular scripting that Linux lends itself to and it gets things working quickly! :)

ps I'm not deliberately poaching for information on MAC on this forum but thought someone might have an idea whilst I was typing this epic message lol

---

