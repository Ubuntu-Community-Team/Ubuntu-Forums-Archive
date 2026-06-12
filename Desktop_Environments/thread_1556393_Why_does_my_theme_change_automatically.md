---
title: "Why does my theme change automatically?"
date: 2010-08-19
forum: Desktop Environments
---

### Post by Mystiann on 2010-08-19
Hey all, I have a question
Recently I updated my ubuntu and since then strangest things began happening (well maybe they're not that strange, but as I'm pretty much a new user, I don't know how to solve them). I turn on my laptop and everything is normal and as it should be, but after a while my theme automatically changes and all icons and everything...it becomes different. When I try changing it, my panels go back to normal (or sometimes they go normal on their own), but the icons and the layout of the inside of the folders remains changed until the next time I restart my session. Is there a possibility of solving this situation, is it because of the updates, or something else? :S

Help would be appreciated! 
Thanks in advance

---

### Post by earthpigg on 2010-08-19
is this possibly correlated with using a KDE app?

it happens to me from time to time, as well, when i start kolourpaint. 

gnome isn't designed to work with kde apps, but it 'kinda sorta' does. this behavior is why i say 'kinda sorta'.

when this happens, you can go to system -> preferences -> appearance, and that usually fixes it. if not, click on a different theme and back to your original.

---

### Post by Mystiann on 2010-08-19
Oh, I'd never thought of that. I am using Amarok (and KMess), both of which are KDE apps, so that could be a reason. And it would also explain a bunch of other things as well.

What you said though, I tried doing that already, but it doesn't go back to normal completely until I either log off and then back on or restart the laptop.

---

### Post by AvgUser on 2010-09-16
Same issue here...  Has happened a few times week before last & just now again today @11:35CST...  If it is a KDE related thing I have no clue what it is as I am only running 1 KDE app that I know of and it (along with all other apps) has been running several days w/o any interruption. The only app I started today was "terminal"...

Shouldn't the change of theme be logged somewhere?  Any help appreciated...

---

### Post by akshay.toraskar on 2010-12-29
Here is also same problem but i think these is because of KDE........
:popcorn:

---

### Post by mcduck on 2010-12-29
Actually running a KDE app *shouldn't* have any effect on Gnome. Of course the Qt app itself will use Qt theme and not fit with the rest of your desktop, but it really shouldn't cause any problems with your GTK theme.

When that kind of thing happens, check that gnome-settings-daemon is running, and try to restart it if necessary.

Of course if, for some reason, the KDE app starts KDE's settings daemon that could be the reason for such problems.

I suppose the important thing here is if your theme changes to some other normal theme, or to the default blue/gray theme. Changing to default theme would be pretty good sign that gnome-settings-daemon has crashed or didn't start at all, while changing to any other them would really be a strange thing...

---

### Post by alexpennos on 2010-12-29
I have exactly the same problem described in post #1.
I personally dont use any KDE app. so its not their "fault".
The problem for me started when I installed the Orta theme. Since then I have every time the same problem, even when starting with ubuntu default theme. 
Please have a look:
[IMG]http://img263.imageshack.us/img263/7205/workspace1082.png
This is how it looks even when trying to select another theme after the "theme crash"
Some more info:
```
alexandros@alexandros-laptop:~$ gnome-settings-daemon

** (gnome-settings-daemon:2451): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:2451): WARNING **: Could not acquire name
alexandros@alexandros-laptop:~$ 

```

---

### Post by earthpigg on 2010-12-30
did you install that theme via a .deb?

if so, can you show us where you got the .deb from?

---

### Post by alexpennos on 2011-01-03
> **earthpigg said:**
> did you install that theme via a .deb?

if so, can you show us where you got the .deb from?

Here it is...
[http://skiesofazel.deviantart.com/art/Orta-184118297](http://skiesofazel.deviantart.com/art/Orta-184118297)

---

### Post by sosukeinu on 2011-01-03
I swear I did a search for this kind of thing before I posted, but here is a thread I started talking about the same thing. [http://ubuntuforums.org/showthread.php?t=1658863](http://ubuntuforums.org/showthread.php?t=1658863) (don't know if they can be combined somehow) anyway, I put some screenshots of what is happening for me in that post. For me, the problem seems to be related to compiz, but i can't be sure.

---

### Post by earthpigg on 2011-01-03
> **alexpennos said:**
> Here it is...
[http://skiesofazel.deviantart.com/art/Orta-184118297](http://skiesofazel.deviantart.com/art/Orta-184118297)

orta seems to be more than a theme, it has a 1300 line python script that i'm assuming you ran (perhaps even as root? it seems to want to put things in /usr/share....). im not going to run it (i have no reason to trust the author's intentions or quality control abilities), but it seems to include an uninstaller operation. you've already run it, have you considered doing so again and looking for an uninstall option?

---

### Post by alexpennos on 2011-01-03
> **earthpigg said:**
> orta seems to be more than a theme, it has a 1300 line python script that i'm assuming you ran (perhaps even as root? it seems to want to put things in /usr/share....). im not going to run it (i have no reason to trust the author's intentions or quality control abilities), but it seems to include an uninstaller operation. you've already run it, have you considered doing so again and looking for an uninstall option?
Yes, indeed, there was an uninstall option, which I chose. I tottaly uninstalled it and the problem still occurs, 1/10 boots.
:confused:

---

### Post by sosukeinu on 2011-01-03
Just found this [http://www.uluga.ubuntuforums.org/showthread.php?t=1575703](http://www.uluga.ubuntuforums.org/showthread.php?t=1575703) seems to be a much more widespread problem than I anticipated.

---

### Post by SkiesOfAzel on 2011-01-13
> **earthpigg said:**
> orta seems to be more than a theme, it has a 1300 line python script that i'm assuming you ran (perhaps even as root? it seems to want to put things in /usr/share....). im not going to run it (i have no reason to trust the author's intentions or quality control abilities), but it seems to include an uninstaller operation. you've already run it, have you considered doing so again and looking for an uninstall option?


  Orta doesn't need to put anything in /usr/share it just gives you the option to do so if you wan't to install it for all users. You can install everything locally, including the configuration app. You also don't need to use the python app to install the theme, you can just drag and drop it to the Appearance Preferences window.

  Now, i don't know about my quality control abilities, but as for my intentions, you don't need to guess them. The file is a python script and not a binary, so that anyone can inspect it for himself.

---

### Post by Clutchface on 2011-02-12
This is happening to me to... In 1/5 boots the theme has automatically changed!

In order to "fix" this problem I just have to open the preferences folder and click on my selected theme (which is already selected)... & it works... weird & annoying!?

---

### Post by robire on 2012-01-24
I got the same problem.
My desktop changed as well . even I did not used any program I had not used before
And now even what theme I am trying I cannot restore the original Settings.
This must be a bug or a intruder at my system.
What is the developers view to this ?
Is developer team informed ?
I really got serious concerns if my computer is doing things I did not tell him.

And as well my computer is FOOLING me, if I am highlighting text to copy
and then move the mouse in top to the appearing menue where I can select
copy or cut or whtever the menue disappears.
That is really annoying 

robire

---

### Post by totalmachine on 2012-03-26
Write this code in /etc/xdg/autostart/gnome-settings-daemon and it will be fixed probably:

1)Open gedit editor: sudo gedit /etc/xdg/autostart/gnome-settings-daemon

2)and then write this code in that file and save it: Exec= bash -c "sleep 2; /usr/lib/gnome-settings-daemon/gnome-settings-daemon"

---

