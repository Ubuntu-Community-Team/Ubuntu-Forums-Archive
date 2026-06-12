---
title: "Determine last used or prefered Desktop Enviorment from TTY"
date: 2014-04-15
forum: Desktop Environments
---

### Post by octius4u on 2014-04-15
Greetings everybody.

I have searched (googled) quite a bit for an solution to determine what the last DE of choice was while in TTY.
Because the usual variable such as $DESKTOP_SESSION were not available. I need your help please.

After quite a bit of searching the only solution I found was:
```
 cat /etc/lightdm/lightdm.conf | grep user-session= | colrm 1 13 
```

The file lightdm.conf shows the user session and with "grep"ing a line and then with "column remove" I managed to get the exact result.
The reason I wanted this is because I wish to install some tweaks with a bash script on a minimal system.

For example

```
#!/bin/bash
$MySession='cat /etc/lightdm/lightdm.conf | grep user-session= | colrm 1 13'

if [ $MySession = "xubuntu" ] then
   apt-add-repository $MyXfceApp
elif [ $MySession = "ubuntu" ] then
   add-apt-repository $MyUnityApp
else
   echo "Desktop session not recognized. " 
fi
```

My Question:
I'd imagine that looking into a file is not the best way to choose. Therefor I'm wandering if this can be accomplished in a more definitive or reliable way from the TTY. Any help will be appreciated. Thanks in advanced.

---

### Post by steeldriver on 2014-04-15
If you mean where lightdm looks to know what each *individual* user's last desktop session was, I think that's in /var/lib/AccountsService/users/

```

$ sudo cat /var/lib/AccountsService/users/steeldriver 
[User]
XSession=Lubuntu
XKeyboardLayouts=

```

AFAIK this is essentially the same information as in each user's ~/.dmrc file (but potentially available to the lightdm greeter before the home directory is accessible)

```

cat /home/steeldriver/.dmrc 

[Desktop]
Session=Lubuntu

```

---

### Post by octius4u on 2014-04-15
Thank you for your response. I didn't know about this location. I will look at it from within other Desktop Environments as well. 

I would have preferred a variable of sorts or a command or any other way to choose what Desktop Environment was/is used while I am in a TTY. I would prefer an alternative means of determining DE's other then looking into a file for the answer, because files are modified for various reasons, and I don't believe they are the most stable method. Or am I wrong?

Basically I'm saying the reading a file feels like cheating and was hoping that the OS would be able to tell me the installed DE's trough a variable, or by use of a command.
Or simply put how would a pro go about determining what DE is installed from within a bash script, while in TTY in order to install the corresponding PPAs and APPs.

---

