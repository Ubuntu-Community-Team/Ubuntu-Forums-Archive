---
title: "XDCMP setup for idiots ..."
date: 2016-03-14
forum: Desktop Environments
---

### Post by David_Partridge on 2016-03-14
OK I'm obviously being dense.  I want to be able to login to my Ubuntu LTS Server (14.04.4) from a Windows PC using XDCMP.

I have MobaXterm installed on the PC.

I have installed lubuntu desktop on the server.

I tried putting a lightdm.conf into /etc/lightdm and setting:

[XDMCPServer]
enabled=true
port=177

but that doesn't seem to have worked.

Please can someone take me by the hand and guide me to get the greeter displayed on my Windows box? Simple steps please :)

Thanks
Dave

---

### Post by David_Partridge on 2016-03-15
Looking at /var/log/lightdm/lightdm.log, I see:

```
[+791.74s] DEBUG: Got BroadcastQuery(authentication_names=[]) from 192.168.129.83:65237
[+791.74s] DEBUG: Send Willing(authentication_name='' hostname='' status='') to 192.168.129.83:65237
[+791.74s] DEBUG: Got BroadcastQuery(authentication_names=[]) from 192.168.129.83:65237
[+791.74s] DEBUG: Send Willing(authentication_name='' hostname='' status='') to 192.168.129.83:65237
[+792.06s] DEBUG: Got Request(display_number=1 connections=[] authentication_name='' authentication_data= authorization_names=['MIT-MAGIC-COOKIE-1' 'XDM-AUTHORIZATION-1'] manufacturer_display_id='') from 192.168.129.83:65237
[+792.06s] DEBUG: Send Decline(status='No valid address found' authentication_name='' authentication_data=) to 192.168.129.83:65237

```

Connection attempts using Open Text Exceed on another system I see only:

```
[+1475.97s] DEBUG: Got BroadcastQuery(authentication_names=[]) from 192.168.129.66:63111
[+1475.97s] DEBUG: Send Willing(authentication_name='' hostname='' status='') to 192.168.129.66:63111
[+1475.97s] DEBUG: Got BroadcastQuery(authentication_names=[]) from 192.168.129.66:63111
[+1475.97s] DEBUG: Send Willing(authentication_name='' hostname='' status='') to 192.168.129.66:63111

```

Does that help you to help me?

Thanks
Dave

---

### Post by QDR06VV9 on 2016-03-15
This was a couple of years ago I had the need to do the same as you.. Now bear in mind this was few years ago(2 to maybe 3 years)
But Long story short i pulled out some old notes on this and came up with this...

Turn on the XDMCP feature on the server

To turn on the XDMCP feature on the server computer:

    Select the menu: System -> Administration -> Login Window
    In the Login Window Preferences dialog window, select: Remote Tab -> Style: Same as Local
    Then close the dialog window and restart the server computer.

Login from a client PC running Ubuntu

There is more than one way to login from a client PC

Connect from the login screen

    Logout from your current session
    Select Actions on the login screen
    Choose "Run XDMCP Chooser"
    Add the host name or the ip address of computer you want to login to.

Connect from the current X session

To login to a remote X server from the current session you need to install the xnest package.

Then you can use tsclient program or run the Xnest command like this:

Example:
```
$ Xnest -ac -kb -query 192.168.1.1 :1 -geometry 1024x768
```
Hope this was helpful
Kind Regards

---

### Post by gordintoronto on 2016-03-15
Note that the software is actually "XDMCP".

---

