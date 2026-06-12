---
title: "Load an app AS a work space"
date: 2007-09-17
forum: Desktop Environments
---

### Post by Felson on 2007-09-17
I am trying to see if I can find a way to load an app as a works space. The objective is generally for emulation of windows, but could be desired for any number of applications. 

Am currently using Ubuntu 7.x (not Kbuntu), so gnome...

A for example.
Load qemu in Workspace 6. maximize/full-screen. Remove all (or some) of the gnome panels from workspace 6, but leave them on all other work spaces.

Anyone know if this can be done, or know where to point me to, to find info on some or all of this?
I will post an answer if I figure it out as well, in case I am not the only crazy person that wants to do this.

---

### Post by weblordpepe on 2007-09-18
Damn dude I've been trying to do the exact same thing. Blimmin vmware doesn't let me prevent the 'next workspace' and 'previous workspace' buttons from being passed to the virutal machine.

because i know just what you mean. flick - windows. flick, ubuntu again. flick, windows, flick ubuntu. etc.

---

### Post by Felson on 2007-09-18
Ok, I have come up with a "hack" way to accomplish this. There are some aspects of it I don't really care for/trust, but it works.... I use VNC as my screen, but depending on your Virtual server, you may not need it. I use it so I can still copy/past between Guest and Host.

Here is a quick how to. With VNC.

Install the following
```

sudo apt-get install wmctrl xtightvncviewer zenity

```

Then you are going to need vncpasswd from tight VNC as well. The default one from RealVNC is useless...
```

wget http://www.myte.ca/vnc/xtightvncpasswd
sudo cp xtightvncpasswd /usr/bin
sudo chmod 755 /usr/bin/xtightvncpasswd
rm xtightvncpasswd

```
Note, I just extracted this binary from the tight VNC server RPM from there website. For some reason, the tighvncserver that is in the repository doesn't have the vncpasswd from tightVNC. If you don't trust me as the source, be my guest, and get it from [http://www.tightvnc.com/download.html]("http://www.tightvnc.com/download.html")
The reason that we need this one, is because the default one won't take a password from STDIN.

Finally, copy the following into a script, and make it executable.
```

#!/bin/bash

VNCHOST=`zenity --title="Host Name" --entry --text="Host Name"`;
VNCPORT=`zenity --title="Port Number" --entry --entry-text="5900" --text="Port Number"`;
PASSWORD=`zenity --title="Password" --entry --text="Password" --hide-text`;
WINDOW=`zenity --title="Window" --entry --text="Window (first is 0)"`;

echo $PASSWORD | /usr/bin/xtightvncpasswd -f > /tmp/vncpass

echo "/usr/bin/xtightvncviewer -passwd /tmp/vncpass -encoding \"tight hextile copyrect zlib corre rre raw\" -compresslevel 9 -quality 5 $VNCHOST::$VNCPORT\
 &"
/usr/bin/xtightvncviewer -passwd /tmp/vncpass -encoding "tight hextile copyrect zlib corre rre raw" -compresslevel 9 -quality 5 $VNCHOST::$VNCPORT &

sleep 5

rm /tmp/vncpass
NewWinID=`wmctrl -l | tail -n 1 | awk '{print $1}'`
echo "windwoID: " $NewWinID

wmctrl -iR $NewWinID -t $WINDOW
wmctrl -iR $NewWinID -b toggle,fullscreen

```
Any place where you see "zenity" you can replace with a fixed string. For my Virtual Server, I use them all as fixed values so I don't have to fill in any boxes.

Now for known "bugs" :)
1) I didn't make the cancel button on the inputs work, and there is no crash detection. If you cancel of enter bad values, it will move some random window to the work space of your choosing, and make it full screen.
2) The script is making an assumption that no other windows are going to open in the 5 seconds after you call VNC. If a window opens after the VNC window, and before the 5 seconds is up, it will move to the work space of your choosing, and make it full screen.
3) There is a /tmp/vncpass file that contains the password to the server that you just connected too. If someone knows it's there, and grabs it in the 5 seconds before it's deleted, and knows the host/port of your VNC Server, they can use it to connect.
4) You need to have the Guest set to the same screen res as the host to have the full "Work Space" effect.

Anyone who has any ideas on how to solve some of these issues, please feel free to post fixes in this thread.

---

