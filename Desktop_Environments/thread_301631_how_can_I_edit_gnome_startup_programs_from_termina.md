---
title: "how can I edit gnome startup programs from terminal?"
date: 2006-11-17
forum: Desktop Environments
---

### Post by eggdeng on 2006-11-17
When installing Beryl, I added entries using Gnome->Preferences->Sessions->Startup programs. As Gnome now refuses to start up, I need to undo these changes from the terminal, but I don't know which file(s) to edit. Help appreciated!

---

### Post by scrooge_74 on 2006-11-17
I manage to screw my user a few hours ago when Open Office hanged on me. The solution I found in another thread was to do the following, do it from safe mode:

sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure gnome-session
sudo dpkg-reconfigure gnome-desktop-data
sudo dpkg-reconfigure gnome-menus
sudo dpkg-reconfigure gnome-system-tools
sudo dpkg-reconfigure gnome-applets

That fix what ever got broken

good luck

---

### Post by eggdeng on 2006-11-18
Thanks for the tip. I tried it but, sadly, it didn't work. ](*,)

---

### Post by fribacka on 2006-11-18
Hi. There is a file containing satrtup programs. ~/.gnome2/session-manual on my computer.

---

### Post by eggdeng on 2006-11-18
Thanks for the suggestion but the file doesn't exist on my edgy install. I've sort of got around the problem by entering as root, creating a new user with admin rights & copying stuff over. Still it would be nice to know where gnome keeps the startup info.

---

### Post by fribacka on 2006-11-18
I used Gnome as window manager when i had Mandriva installd as well. The files ```
 ~/.gnome2/session-manual
~/.gnome2/session 
``` existed then. I belived that they were standard. The sesion-manual file is for your own startup programs and the sesson file has more programs for te system. This i the contains of mi files:


~/.gnome2/session-manual 
```

[Default]
num_clients=2

0,RestartStyleHint=3
0,Priority=50
0,RestartCommand=xterm -geometry 80x20-20-40 
0,Program=xterm

1,RestartStyleHint=3
1,Priority=60
1,RestartCommand=gaim 
1,Program=gaim 
```

~/.gnome2/session
```
[Default]

0,id=1037f090ed000116368530300000078010003
0,RestartStyleHint=2
0,Priority=40
0,Program=nautilus
0,CurrentDirectory=/home/gustav
0,CloneCommand=nautilus --sm-config-prefix /nautilus-JNA1oX/ 
0,RestartCommand=nautilus --sm-config-prefix /nautilus-JNA1oX/ --sm-client-id 10
37f090ed000116368530300000078010003 --screen 0 --no-default-window 

1,id=1037f090ed000116368530200000078010001
1,RestartStyleHint=1
1,Priority=40
1,Program=gnome-volume-manager
1,CurrentDirectory=/home/gustav
1,CloneCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-DKd
GwZ/ 
1,RestartCommand=gnome-volume-manager --sm-config-prefix /gnome-volume-manager-D
KdGwZ/ --sm-client-id 1037f090ed000116368530200000078010001 --screen 0 

2,id=1037f090ed000116368530400000078010004
2,RestartStyleHint=1
2,Priority=50
2,Program=update-notifier
2,CurrentDirectory=/home/gustav
2,CloneCommand=update-notifier --sm-config-prefix /update-notifier-cs5BG1/ 
2,RestartCommand=update-notifier --sm-config-prefix /update-notifier-cs5BG1/ --s
m-client-id 1037f090ed000116368530400000078010004 --screen 0 

3,id=1037f090ed000116368530600000078010006
3,RestartStyleHint=2
3,Priority=50
3,Program=gnome-cups-icon
3,CurrentDirectory=/home/gustav
3,CloneCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-O2YoD2/ 
3,RestartCommand=gnome-cups-icon --sm-config-prefix /gnome-cups-icon-O2YoD2/ --s
m-client-id 1037f090ed000116368530600000078010006 --screen 0 

4,id=1037f090ed000116368530200000078010002
4,RestartStyleHint=2
4,Priority=40
4,Program=gnome-panel
4,CurrentDirectory=/home/gustav
4,CloneCommand=gnome-panel --sm-config-prefix /gnome-panel-3VUyJK/ 
4,RestartCommand=gnome-panel --sm-config-prefix /gnome-panel-3VUyJK/ --sm-client
-id 1037f090ed000116368530200000078010002 --screen 0 

5,id=1037f090ed000116368530100000078010000
5,RestartStyleHint=2
5,Priority=20
5,Program=metacity
5,CurrentDirectory=/home/gustav
5,DiscardCommand=rm -f /home/gustav/.metacity/sessions/1163892155-14420-32828629
69.ms 
5,CloneCommand=metacity 
5,RestartCommand=metacity --sm-save-file 1163892155-14420-3282862969.ms 

num_clients=6 
```

use GREP to search your home directory for files with similar content

---

### Post by aidanr on 2006-11-19
~/.config/autostart

---

### Post by eggdeng on 2006-11-19
Go raibh maith agat Aidan, for the suggestion. I'm not sure if I'm reading the path to the file you mention correctly but I have no (hidden) file of that name in my home directory.:-|

---

### Post by fribacka on 2006-11-19
Search for the personal session file directory:
[code] $ sudo updatedb; locate session-manual [code]
But I'm not sure that your installation has these session controll files. Gnome has a log viewer: gnome-system-log. Parhaps you can look there for the startup information. I do think that it only shows the contain of directory /var/log/.

---

### Post by KinematicGrunt on 2006-11-19
If the problem is that gnome crashes back to the login screen after  adding 'beryl-manager' to the startup programs. Do the following:

Login via 'Failsafe Terminal'
enter the commands:

cd ~/.config/autostart/

rm beryl-manager.desktop

exit and login, it should no longer crash.

---

### Post by eggdeng on 2006-11-23
I've tried using grep to find a file with the beryl-manager entry with no result and also tried entering as root and cding to ~/.config/autostart/ but I get a no such file or directory error. I've noticed some of you are using different versions of ubuntu so this may be the reason. In any case, I have been able to make a new user in the admin group so I think I'll stop knocking my head against this one. Thanks again for all the help!

---

### Post by jamesrose on 2006-11-23
Cant you just add the program to the Xsession file?


Im not sure that would work but its in /home/username/.xsession

---

### Post by eggdeng on 2006-11-23
I took one last look at this after seeing the last post and it's finally solved. James may be using a different version too as there is no .Xsession file in any of my users' home directories. But I did stumble on the .config/autostart directory a couple of you were talking about. The full path is /home/username/.config/autostart; I can't understand how it got away from me up to now.
It contained a file for each of the three entries I added to the session startup programs tab, so I removed these and was able to log in with no problems. Thanks again & hope I haven't wasted much of your time!

---

### Post by usererror on 2008-05-27
> **eggdeng said:**
> I took one last look at this after seeing the last post and it's finally solved. James may be using a different version too as there is no .Xsession file in any of my users' home directories. But I did stumble on the .config/autostart directory a couple of you were talking about. The full path is /home/username/.config/autostart; I can't understand how it got away from me up to now.
It contained a file for each of the three entries I added to the session startup programs tab, so I removed these and was able to log in with no problems. Thanks again & hope I haven't wasted much of your time!

To Clarify this even more.

In Ubuntu 8.04 create a folder in ~/.config/autostart/

then you can create your start up items like this example:

**filename:** firefox-2.desktop 

the contents of **firefox-2.desktop** contents:

```


[Desktop Entry]
Type=Application
Encoding=UTF-8
Version=1.0
Name=No Name
Name[en_US]=Firefox
Comment[en_US]=Web Browser Firefox
Comment=Web Browser Firefox
Exec=firefox-2
X-GNOME-Autostart-enabled=true


```

I hope this helps someone else.  I needed his because I was making an internet kiosk.

---

