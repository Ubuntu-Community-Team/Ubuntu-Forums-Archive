---
title: "Default panel, deleted some items by mistake, can't find them to put back"
date: 2010-05-23
forum: Desktop Environments
---

### Post by kero4 on 2010-05-23
Hi,

I was playing around with the default panel that has the power icon (wrong lingo maybe) and the network/sound icons, etc.

I deleted some items including the power icon and now for the life of me can't find it in the panel applets list in lubuntu.

Is there a way to restore the default panel with the settings as when I first installed lubuntu.

I also played with some spacings and other settings so would rather just get it back to normal/restore it vs add all the items back on and then play with the spacings again.

Thanks

Rod

---

### Post by SlidingHorn on 2010-05-23
I, personally don't know a way to restore the defaults, but I believe the applets originally loaded are as follows:

Top Panel (may not be the exact order -- I've changed mine):
Menu Bar
2 Application launchers (Help & Evolution)
Indicator Applet
Clock
Notification Area

Bottom:
Show Desktop
Separator
Window List
Trash

---

### Post by kero4 on 2010-05-23
What I find most odd is regardless of panel top or bottom or both, I have no option to get that little power button icon back, the one that lets you log out, or shut down, etc etc.

I am not sure if this is an lubuntu issue of just an issue I have?

---

### Post by SlidingHorn on 2010-05-23
> **kero4 said:**
> What I find most odd is regardless of panel top or bottom or both, I have no option to get that little power button icon back, the one that lets you log out, or shut down, etc etc.

I am not sure if this is an lubuntu issue of just an issue I have?

knowing it was lubuntu would have helped ;)  I'm not sure if LXDE has the same applets, but the one for Gnome is called "Shut Down..."

I forgot to list it apparently

---

### Post by deeminter on 2010-05-23
To re-install applets such as the Shut down applet do the following:
Right click the panel and select from the drop down list "Add to Panel"
scroll down the list until you come to the "Shut Down" applet, then left click on the applet,then left click "Add".
Hopefully this will assist you.

deeminter

---

### Post by kleskjr on 2010-05-23
most probably you have removed the notification area.
as deeminter said, right click on the panel then click add to panel and choose notification area

---

### Post by kero4 on 2010-05-23
Here is what is listed, I don't see any of which has been mentioned above

CPUFreq LED
Battery Monitor
CPU Usage Monitor
Keyboard Layout Switcher
Desktop Number/ Workspace Name
Temperature Monitor
Network Status Monitory
Volume Control
Spacer
Menu
System Tray
Destkop Page
Task Bar
Directory menu
Minimize All Windows
Digital Clock
Application Launch Bar
Seperator

That is it, any other advise before I just create a new one and leave that one important icon off?

---

### Post by iceburgundy on 2010-07-06
Ah, yes.... I got messed up with the panel as well....   The Lubuntu logo-ed start button was removed by accident, as well as the power button.  

I don't know how to restore the default panel, but since I just installed Lubuntu, I created a new user account and the buttons were all there again. (Preferences-->Users and Groups)

I created the new user account, logged in with it, changed it to an Administrator account, and deleted the account with the messed up panel. You can keep the files from the old account. 

It's not exactly what you may want to do, but it is a way.  I just wanted to share what I did.

---

### Post by cavalier911 on 2010-07-06
[B]Bring back the Shutdown button on the right corner of lxpanel.
[/B]
```
sudo cp /usr/share/lxpanel/profile/Lubuntu/panels/panel ~/.config/lxpanel/Lubuntu/panels
```
Change owner:group to the local account from root.
```
sudo chown owner:group  ~/.config/lxpanel/Lubuntu/panels/panel
```

```
lxpanelctl restart
```

---

### Post by larry.said on 2010-08-06
All you have to do is add the indicator applet in the add to panel window

---

### Post by cavalier911 on 2010-08-06
As of the Lubuntu Lucid release there was no indicator applet support.
> 
Hi,

I just pushed the first version of indicator-applet support for lxpanel
into Maverick repository. It may take some times to appear in official
repository, so I put it in Lubuntu PPA if people want to test it.

Screenshot for people who doesn't know about indicator applet :
[http://people.ubuntu.com/~gilir/Lubuntu-indicator-applets.png]("http://people.ubuntu.com/%7Egilir/Lubuntu-indicator-applets.png")

You need to :
- update lxpanel to version >= 0.5.5-4ubuntu2
- install lxpanel-indicator-applet-plugin
- install some indicator packages (like indicator-messages and
indicator-application).
- add indicator applets to your panel

The support is not the same that for Ubuntu applications. For now, only
Pidgin and gnome-power-manager have some support for them.

It's also not by default on Lubuntu installation for now, since it's not
memory free, not many Lubuntu applications used it and some useful
indicators have hard depends on GNOME.

Happy testing :-)

Regards,
Julien Lavergne


_Simple method to bring back default panel:_
Move the old panel file out in case you want to reference it for your custom configs.
```
mv ~/.config/lxpanel/Lubuntu/panels/**panel** ~/
```Restart lxpanel 
```
lxpanelctl restart
```Now we have default panel configuration including Shutdown button
Notice config file **panel** is not created until you change the default panel configuration.

---

### Post by spillage2 on 2010-08-07
I know to restore your panel setting there is a website where you can get a small .sh progame to restore to default, save you current setting and also restore your saved setup.

very simple but got me back to where I needed to be after not locking the icons and letting my kids on the comp.

I cannot remember the site but would be happy to email you the file if needed.

Spill.

---

### Post by cavalier911 on 2010-08-07
Spill
Ubuntu is about sharing what you have and what you know with the whole community.Why email the script to one individual when you can attach it in your reply to this thread and share it with the world? 
On the toolbar of the Message: box is a paperclip icon ,click on it to upload/attach the script to your reply.Another way is to scroll down beneath the Submit Reply/Preview Post buttons Additional Options/**Attach Files**,click on Manage Attachments button,browse to the script and upload.

---

### Post by spillage2 on 2010-08-22
ok no problems here it is..just extract the tar and run the .sh file.

---

### Post by aguilera2k on 2011-07-14
> **cavalier911 said:**
> [B]Bring back the Shutdown button on the right corner of lxpanel.
[/B]
```
sudo cp /usr/share/lxpanel/profile/Lubuntu/panels/panel ~/.config/lxpanel/Lubuntu/panels
```
Change owner:group to the local account from root.
```
sudo chown owner:group  ~/.config/lxpanel/Lubuntu/panels/panel
```

```
lxpanelctl restart
```


This worked on LUBUNTU 11.04

---

### Post by djsimmonds on 2011-10-01
in case anyone didn't realize, the power applet on lxpanel is actually just another "application launch bar", with "shutdown" as the application. however, "shutdown" is not in the list of application. if you want to add an application to this list, it needs a *.desktop file, and instructions for doing so are here: [http://forum.lxde.org/viewtopic.php?f=21&t=113](http://forum.lxde.org/viewtopic.php?f=21&t=113)

---

### Post by Finitemight on 2011-11-11
yea restarting the panel should do the trick. It should not have to come to having to do that though. It should be simple to drag and drop icons into the lxpanel, and customize it without having to open up terminal and once again running codes.

It slightly defeats the purpose of a GUI in my opinion, but hey i guess whatever works...

:)

---

