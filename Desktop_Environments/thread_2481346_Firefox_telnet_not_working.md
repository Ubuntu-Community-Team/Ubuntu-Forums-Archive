---
title: "Firefox telnet not working"
date: 2022-11-26
forum: Desktop Environments
---

### Post by rpra006 on 2022-11-26
Hi there,
I am using Firefox to access eve-ng server. 

Basically each node is exposed as a telnet link such as following:
[FONT=monospace][COLOR=#000000]telent://192.168.1.168:36323
I have made sure that I have enabled the following in Firefox and restarted Firefox:
[/COLOR][/FONT]“network.protocol-handler.expose.telnet” and set the value “false"[FONT=monospace][COLOR=#000000]

When click on the link that is a telnet link I get to select the system handler option, which when I select just launches Konsole but no telnet to the end point. 

After searching I found the following script that I have now located in /usr/bin directory and from Firefox I point to this script but nothing happens:
The script is as follows:

[/COLOR][/FONT]```
[FONT=monospace]
#!/bin/sh 
#address=`echo ${*##telnet://} | sed 's/:/ /g'` 

**address**=`echo $1 | cut -d : -f 2 | sed 's;/;;g'` 
**port**=`echo $1 | cut -d : -f 3` 
exec /usr/bin/konsole -e telnet $address $port 
#exec /usr/bin/xterm -e telnet $address $port 
[/FONT]
```[FONT=monospace][COLOR=#000000]
[/COLOR]
The above script works when I execute from the CLI such as following:

[/FONT]```
[FONT=monospace][COLOR=#000000]fftelnet telent://192.168.1.168:58129[/COLOR][/FONT]
```[FONT=monospace]

But it does not work when I select this from Firefox.

Please help. [/FONT][FONT=monospace]


[/FONT]

---

### Post by TheFu on 2022-11-28
Is Firefox installed using the snap package or from a PPA/Repo?

```
$ snap list
```
will show the list of snaps on your system.  Snap packages run in a constrained environment that doesn't allow any workflows that aren't approved, in advance, by the snap package team.  I suspect that's the problem.

Firefox has a method to install through a PPA. [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

---

