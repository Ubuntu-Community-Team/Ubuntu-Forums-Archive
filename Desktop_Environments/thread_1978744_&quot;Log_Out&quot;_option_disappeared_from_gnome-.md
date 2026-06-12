---
title: "&quot;Log Out&quot; option disappeared from gnome-shell after latest update"
date: 2012-05-12
forum: Desktop Environments
---

### Post by michaelmestre on 2012-05-12
On Pangolin, after performing an update (on 12/May/2012), the "log out" option disappeared from the menu (on which my name appears) at the top-right of the screen.

How can I restore this (quite useful) option ?

Related subject: How can I activate the CTRL+ALT+Backspace shortcut to kill the X session ?

---

### Post by stevedude on 2012-05-12
Oh man, I sure hope someone can respond with an answer because I can confirm the issue and it is driving me nuts because I use logoff all the time!

I've been searching this Ubuntu Forum and Gnome.Org with no luck in finding a solution.

I can provide a temporary work-around though. Go to [https://extensions.gnome.org/](https://extensions.gnome.org/) and install the "QuickLaunch" extension. 

Create a new launcher (I titled mine "Log Off") and use this in the "Command" portion of your custom launcher (without the quotes): "gnome-session-quit"

Now you will have a new icon on your Gnome-Shell top panel and you can use it to logoff your system. Any launcher you create (.desktop files) will be located under your home folder in /.local/share/gnome-shell/quicklaunch.

I'll be monitoring this post because I would prefer a solution versus a work-around. :-)

---

### Post by layo on 2012-05-12
I am expiriencing the same thing: no log off button in the 'shutdown and notifications' menu. Also, control+alt+backspace does nothing at all.

---

### Post by michaelmestre on 2012-05-13
Thanks for the tip [stevedude]("http://ubuntuforums.org/member.php?u=968808"). Very useful :)

---

### Post by stevedude on 2012-05-14
OK, I did finally find something that worked for me. BE WARNED it was a scary process because #1) I wasn't totally confident in what I was doing and #2) This purges then (hopefully) rebuilds your PPAs that you have installed.

I followed the process as outlined here by typing the commands in Terminal: [http://askubuntu.com/questions/127843/gnome-shell-3-4-i-cant-change-theme](http://askubuntu.com/questions/127843/gnome-shell-3-4-i-cant-change-theme)

My process deviated from the outline in that you are told to respond with an "N" (No) at the end of the process asking you to purge the ricotz/testing ppa, however, I was asked to respond to 2 questions for my system installation. I responded with a "Y" (Yes) when asked to remove old packages because pressing "N" kept repeating the same question. I pressed "N" when asked to purge the ricotz/testing ppa as instructed.

After restarting the shell (ALT F2 then "r"), I had my "Log Out" back! Plus I had another extension working called "Places" to access your folders from the top dash.

Screenshot enclosed:

---

### Post by sammiev on 2012-05-14
I'm surprised it did not effect everyone as I have no issues with the log out and I'm fully updated at all times.

---

### Post by alecz20 on 2012-09-14
Options, buttons, and features come and go with each Ubuntu release, with some updates, and sometimes with restarts.

That is why it's best to rely on more 'robust' ways of doing things.

**To log out From ANY Ubuntu so far press "Ctrl+Alt+Del" and choose Log Out.**

You might be out of luck if your keyboard stopped working.

---

