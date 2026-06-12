---
title: "Can't use clipboard between client and VNC server"
date: 2015-09-02
forum: Desktop Environments
---

### Post by dan12345 on 2015-09-02
Hi,

I've ubuntu 14.04 running on a Thinkpad T60, which I'm using as a server, and access remotely with x11vnc. The problem is that I can't cut and paste between x11vnc sessions and VNC clients. I have this consistently with different VNC clients on PC/ios/Linux and Mac systems and those clients have no problem cutting and pasting from other ubuntu systems). I've tried replacing x11vnc with vncserver and with tightvncserver and had the same result. 

So something must be up with the Ubuntu setup on the Thinkpad - but what?

Any suggestions very gratefully received...

Dan

---

### Post by timg11 on 2016-06-28
I have the same problem with 16.04 LTS and  x11vnc 0.9.13.   Clipboard allows pasting from Ubuntu into TightVNC client, but copying in TightVNC client will not paste into Ubuntu. 

Has anyone ever found a solution?

---

### Post by supercurro2 on 2016-09-27
I have ubuntu 16.04 and tested a lot of options:

[https://ubuntuforums.org/showthread.php?t=45565](https://ubuntuforums.org/showthread.php?t=45565)

[http://www.nongnu.org/autocutsel/](http://www.nongnu.org/autocutsel/)

but at the moment I dont get to run it properly.

Other info:
[http://www.karlrunge.com/x11vnc/faq.html#faq-clipboard](http://www.karlrunge.com/x11vnc/faq.html#faq-clipboard)


> [SIZE=-0][COLOR=#000000][FONT=&amp]**Misc: Clipboard, File Transfer/Sharing, Printing, Sound, Beeps, Thanks, etc.]**[/FONT][/COLOR][/SIZE]
[COLOR=#000000][FONT=&amp]**Q-123:** [COLOR=#007f00]Does the Clipboard/Selection get transferred between the vncviewer and the X display?[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]As of Jan/2004 **x11vnc** supports the "CutText" part of the RFB (aka VNC) protocol. When text is selected/copied in the X session that x11vnc is polling it will be sent to connected VNC viewers. And when CutText is received from a VNC viewer then x11vnc will set the X11 selections PRIMARY, CLIPBOARD, and CUTBUFFER0 to it. **x11vnc** is able to hold the PRIMARY and CLIPBOARD selections (**Xvnc** does not seem to do this.)[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]The X11 selections can be confusing, especially to those coming from Windows or MacOSX where there is just a single 'Clipboard'. The X11 CLIPBOARD selection is a lot like that of Windows and MacOSX, e.g. highlighted text is sent to the clipboard when the user activates "Edit -> Copy" or presses "Control+C" (and pasting it via "Edit -> Paste" or "Control+V".) The X11 PRIMARY selection has been described as 'for power users' or 'an Easter Egg'. As soon as text is highlighted it is set to the PRIMARY selection and so it is immediately ready for pasting, usually via the Middle Mouse Button or "Shift+Insert". See [this jwz link]("http://www.jwz.org/doc/x-cut-and-paste.html") for more information.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]**x11vnc**'s default behavior is to watch both CLIPBOARD and PRIMARY and whenever one of them changes, it sends the new text to connected viewers. Note that since the RFB protocol only has a single "CutText" then both selections are "merged" to some degree (and this can lead to confusing results.) One user was confused why x11vnc was "forgetting" his CLIPBOARD selection and the reason was he also changed PRIMARY *some time after* he copied text to the clipboard. Usually an app will set PRIMARY as soon as any text is highlighted so it easy to see how CLIPBOARD was forgotten. Use the -noprimary described below as a workaround. Similarly, by default when x11vnc receives CutText it sets *both* CLIPBOARD and PRIMARY to it (this is probably less confusing, but could possibly lead to some failure modes as well.)[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]You may not like these defaults. Here are ways to change the behavior:[/FONT][/COLOR]

[LIST]
[*]If you don't want the Clipboard/Selection exchanged at all use the [-nosel]("http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-nosel") option.
[*]If you want changes in PRIMARY to be ignored use the [-noprimary]("http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-noprimary") option.
[*]If you want changes in CLIPBOARD to be ignored use the [-noclipboard]("http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-noclipboard") option.
[*]If you don't want x11vnc to set PRIMARY to the "CutText" received from viewers use the [-nosetprimary]("http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-nosetprimary") option.
[*]If you don't want x11vnc to set CLIPBOARD to the "CutText" received from viewers use the [-nosetclipboard]("http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-nosetclipboard") option.
[/LIST]
[COLOR=#000000][FONT=&amp]You can also fine-tune it a bit with the [/FONT][/COLOR][-seldir dir]("http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-seldir")[COLOR=#000000][FONT=&amp] option and also [/FONT][/COLOR][-input]("http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-input")[COLOR=#000000][FONT=&amp].[/FONT][/COLOR][COLOR=#000000][FONT=&amp]You may need to watch out for desktop utilities such as KDE's "Klipper" that do odd things with the selection, clipboard, and cutbuffers.[/FONT][/COLOR]

I cheked all of this and it doesnt work, but in this link

[https://prismsoul.wordpress.com/2014/06/11/installing-and-configuring-x11vnc-on-ubuntu-14-04/](https://prismsoul.wordpress.com/2014/06/11/installing-and-configuring-x11vnc-on-ubuntu-14-04/)

and in this

[http://superuser.com/questions/901970/using-clipboard-with-xfce-and-tightvnc](http://superuser.com/questions/901970/using-clipboard-with-xfce-and-tightvnc)

They talk about the option -xkb

So in **/lib/systemd/system/x11vnc.service**

You have to write the options you want.

> [Unit]Description=Start x11vnc at startup.
After=multi-user.target
[Service]
Type=simple
ExecStart=/usr/bin/x11vnc **-xkb** -auth guess -forever -loop -noxdamage -repeat -rfbauth /etc/x11vnc.pass -rfbport 5900 -shared
[Install]
WantedBy=multi-user.target

restart o tested with the comands 

x11vnc -R xkb 

and evuala:  you can paste at x11vnc server with [B][SIZE=4]shift+insert[/SIZE]

Note: also without -xkb works[/B]

---

### Post by timg11 on 2017-03-22
I'm restarting this thread, in the hopes that some solution has been found. 

Server is Ubuntu 16.04 LTS 32 bit. 
Remote is TightVNC View 2.7.10 under Windows.

Problem 1:  Clipboard does not work from TightVNC client to Ubuntu desktop. 
Example. Copy text on Windows machine.  Paste into Windows Notepad to verify clipboard. It works. Select window in Ubuntu through TightVNC. Right-click. Paste option is grayed out. 

Problem 2: File Transfer does not work. Note:  the -tightfilexfer option is included on the server, per the information in x11vnc-help.txt provided in Ubuntu. when starting X11VNCserver in Ubuntu, the prompt for "File Transfer, the TightVNC checkbox was chosen.  However, In TightVNC, the "File transfer" option in the menu is grayed out. 
   
/usr/share/applications/x11vnc.desktop looks like this:

```
[Desktop Entry]
Name=X11VNC Server
Comment=Share this desktop by VNC
Exec=x11vnc -gui -tightfilexfer tray=setpass -rfbport PROMPT -bg -o %%HOME/.x11vnc.log.%%VNCDISPLAY
Icon=computer
Terminal=false
Type=Application
StartupNotify=false
#StartupWMClass=x11vnc_port_prompt
Categories=Network;RemoteAccess;

```

---

### Post by teledyn on 2017-07-07
the server needs to run [FONT=Courier New]vncconfig -nowin[/FONT] -- add this into your ~/.vnc/xstartup before starting your window manager.

---

### Post by timg11 on 2017-07-23
Thanks for the suggestion. My system did not have a file xstartup in .vnc.
The directory contained another directory certs, and a file passwd.

I created the file xstartup in the directory .vnc.
It now has the single line:
```
vncconfig -nowin

```

After restarting the system, I still do not have the ability to paste the clipboard from the host system into the TightVNC server terminal.

---

### Post by timg11 on 2017-07-23
After looking around further, I think my x11vnc is set up to start differently. 
I found /lib/systemd/system/x11vnc.service

which contained:

```
[Unit]
Description=Start x11vnc at startup.
After=multi-user.target

[Service]
Type=simple
ExecStart=/usr/bin/x11vnc -auth guess -forever -loop -noxdamage -repeat -rfbauth /etc/x11vnc.pass -rfbport 5900 -shared

[Install]
WantedBy=multi-user.target
```


so would the -nowin option get added to the ExecStart= line?
Or would another ExecStart line like "ExecStart=/usr/binvncconfig -nowin"   be required?

---

### Post by timg11 on 2018-07-03
I'm still looking for a solution to make the clipboard in TightVNC work.

Perhaps I'm running the wrong version of tightVNC?

x11vnc --version reports:
x11vnc: 0.9.13 lastmod: 2011-08-10

That seems rather old.  I just did
```
sudo apt-get update
sudo apt-get upgrade
```

so apparently this is the latest version?

I've seen [another article]("https://unix.stackexchange.com/questions/169133/how-to-share-windows-clipboard-with-linux-using-tightvnc") that recommended vncconfig. However it is not presently installed. When run I get this:

```
$ vncconfig --help
No command 'vncconfig' found, did you mean:
 Command 'vnc4config' from package 'vnc4server' (universe)
vncconfig: command not found
```


I'm using the setup for x11vnc described on[ this page]("https://help.ubuntu.com/community/VNC/Servers"):

I found[ this article]("http://thomas.patrickdepinguin.com/knowledgebase/tight-vnc") that indicates I can use autocutsel instead of the (unavailable) vncconfig.

I verified that /usr/bin/autocutsel is present. 

I edited  /lib/systemd/system/x11vnc.service

To look like this:


```
[Unit]
Description=Start x11vnc at startup.
After=multi-user.target

[Service]
Type=simple
ExecStart=/usr/bin/x11vnc -auth guess -forever -loop -noxdamage -repeat -rfbauth /etc/x11vnc.pass -rfbport 5900 -shared
ExecStart=/usr/bin/autocutsel -s PRIMARY -fork

[Install]
WantedBy=multi-user.target
```

After restarting the system, TightVNC was not available. The viewer reported the server "actively refused the connection". 

I edited /lib/systemd/system/x11vnc.service again to remove the autocutsel line, and restarted, and TightVNC is able to connect again. But the clipboard still doesn't work, so I'm back at the start.

---

### Post by markingston on 2018-12-16
i've the same problem , but at my case is in Windows 10 vs Debian 9 , client side : windows 10 and server side : debian 9 ,  the option file trasnfer is grayed out,  

 [IMG]https://drv.tw/~marcoantonio_3d@hotmail.com/od/Public/Captura.PNG[/IMG]
but   i want  to make you so clearing you the case ,  you are using x11vnc server , not tightvncserver  i have the self server , but still dont test with tightvncserver on my linux distro debian ,  i tried install tightvncserver but i dont see the real desktop xfce4 ,

---

