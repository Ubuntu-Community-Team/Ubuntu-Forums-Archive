---
title: "How to (permanently) add indicators to top Unity Panel"
date: 2011-06-05
forum: Desktop Environments
---

### Post by ezm on 2011-06-05
Hi, I use to be able to add applets to the top panel in gnome in previous versions of Ubuntu (<11.04).  I understand the Unity environment, which I generally like, has changed how one adds things to the top panel.  Now we have indicators?  

Is there a good description of the functionality of these indicators: how to add/remove indicators, where one can find new indicators, etc.  I ask because I have been having trouble adding indicators.  I tried to add the system monitor indicator.  I initially added it by installing it with apt-get.  But every time I reboot it has disappeared and I have to run it again from the menu.  I can't figure out how to make it permanent.

Can anyone help?

---

### Post by garvinrick4 on 2011-06-05
Here are the Unity recommendeds: Do what you will with them:     

 unity-place-applications, unity-place-files, indicator-appmenu,
 indicator-application, indicator-sound, indicator-datetime,
 indicator-messages, indicator-me, indicator-session,
 ubuntuone-control-panel-gtk

 > I can't figure out how to make it permanent.No more panel adding to panel.

Put what you want on the launcher. Run say system monitor and right click on it in launcher and
add to launcher. Then either click on it to run or Windows key and # on the launcher at same time will open.

When you login click on your user name and on bottom panel choose classic Ubuntu and is gnome2 like you are
used to but give Unity a run once you get used to it, works just great. Windows key and A will open all Applications.
Lots of different key commands starting with Windows key, a,s,w give em a go.

---

### Post by Copper Bezel on 2011-06-05
> I can't figure out how to make it permanent.

In the Dash, search for Startup Applications. Create a new entry with the command you're using to run it. What you're adding to the panel is actually a daemon displaying an indicator, as you said, rather than a panel object in its own right, so it only shows up if the daemon is run.

---

