---
title: "My experiences with Xubuntu 13.10"
date: 2013-10-25
forum: Desktop Environments
---

### Post by kunaguvarun on 2013-10-25
Installation was smooth, no issues at all.  I just figured that there are a few things that bother me.

1. When playing videos in full screen using VLC media player, top panel doesn't hide automatically.
2.There is no GUI for updater manager, like which I could open and check if there are any updates available. Do I have to use command line?

3.Ubuntu software center got some issues. 
Installation progress bar appears at weird positions like left top corner. (I got a snapshot of it, will post it once I reached home)
Force closed 3-4 times when I try to install my favourite apps

---

### Post by Toz on 2013-10-25
> **kunaguvarun said:**
> 1. When playing videos in full screen using VLC media player, top panel doesn't hide automatically.
I can't replicate this on my 13.10 install. vlc plays properly in full screen mode. Can you try VLC preferences->Video and check the "Always on Top" flag and see if that helps?
> 2.There is no GUI for updater manager, like which I could open and check if there are any updates available. Do I have to use command line?
Settings Manager->System section->Software Updater.
> 3.Ubuntu software center got some issues. 
Installation progress bar appears at weird positions like left top corner. (I got a snapshot of it, will post it once I reached home)
Force closed 3-4 times when I try to install my favourite apps
A screenshot  would definitely help.

---

### Post by kunaguvarun on 2013-10-25
Thanks for the reply.
1.That setting in VLC didn't helped. Refer to screenshot attached.
2.Thanks for the software updater's navigation path. Worked
3.Please refer to the other attachment 

[IMG]http://i.imgur.com/jMK2rAH.png[/IMG]

[IMG]http://i.imgur.com/53Y65pT.png[/IMG]

---

### Post by Toz on 2013-10-25
1. What do these commands return:
```
xfconf-query -c xfce4-panel -p /panels/panel-1/disable-struts
```
```
xfconf-query -c xfce4-panel -p /panels/panel-2/disable-struts
```
```
xfconf-query -c xfce4-panel -p /panels/panel-1 -l
```

3. It looks like its being rendered incorrectly. Is that the default Greybird theme that you are using? If you change the appearance theme, does the problem persist?

---

### Post by kunaguvarun on 2013-10-26
```

varun@varun-pc:~$ xfconf-query -c xfce4-panel -p /panels/panel-1/disable-struts
Property "/panels/panel-1/disable-struts" does not exist on channel "xfce4-panel".
varun@varun-pc:~$ xfconf-query -c xfce4-panel -p /panels/panel-2/disable-struts
Property "/panels/panel-2/disable-struts" does not exist on channel "xfce4-panel".
varun@varun-pc:~$ xfconf-query -c xfce4-panel -p /panels/panel-1 -l
/panels/panel-1/autohide
/panels/panel-1/background-alpha
/panels/panel-1/background-style
/panels/panel-1/enter-opacity
/panels/panel-1/leave-opacity
/panels/panel-1/length
/panels/panel-1/length-adjust
/panels/panel-1/mode
/panels/panel-1/plugin-ids
/panels/panel-1/position
/panels/panel-1/position-locked
/panels/panel-1/size
varun@varun-pc:~$ 

```

No, changing theme didn't helped. Ubuntu software center error doesn't appear no more. But VLC full screen is still a problem.

---

### Post by Toz on 2013-10-26
Try this: With vlc open, and the active window, and a video playing, press "Ctrl+H", then "F". Does that help? ([http://ubuntuforums.org/showthread.php?t=2159794]("http://ubuntuforums.org/showthread.php?t=2159794"))

Bug report [here]("https://bugs.launchpad.net/ubuntu/+source/xfce4-panel/+bug/1005175") - looks like you're not the only one, though I don't understand why I don't have the same problem.

What version of vlc do you have?

---

### Post by kunaguvarun on 2013-10-26
The Ctrl + H and then pressing F keys helped. Now videos are playing full screen. The installed version is 2.0.8

---

