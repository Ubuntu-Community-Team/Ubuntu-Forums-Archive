---
title: "Prevent sleep mode while using Samba"
date: 2012-03-19
forum: Desktop Environments
---

### Post by Sosigene on 2012-03-19
Hi, 
 
I would like to find a way to prevent/disable temporarily the sleep mode on my Linux box while I am accessing data over Samba from my others computers on my network (mostly Windows PCs). 
 
Since I do not use it as a full time server, I don't want my Linux box to be powered on all the time. Furthermore, I can easily power it on again from a simple WOL command. 

From what I read, there is no "official" way of doing this. 
 
So far, I found this solution that is quite simple. 
[http://aikar.co/2011/03/03/ubuntu-prevent-sleep-samba/](http://aikar.co/2011/03/03/ubuntu-prevent-sleep-samba/) 
 
The guy proposes basically to check a string in smbstatus to verify if there is a file lock and then simulate a user action to reset the sleep mode timer. However, the command he uses for that, "gnome-screensaver-command --poke" doesn't exist anymore in Gnome 3. 

My first try was to replace this by &#8220;xset&#8221; but it didn't work. I believe that xset have only an impact on the screen and not on the sleep/hibernate state.
 
From what I read on others sites and from google searches, I would need to use the dbus command to achieve the same thing. However, dbus inhibitor "lives" only as long as the app who called it is  running. That means that it cannot be use in the same simple way described in the first example. 

I know that I could solve my problem by manually disable the sleep/hibernate mode via VNC each time I need to access Samba.  But as they say, there must be a better way. :)
 
My questions are: 
 
1- Is there a simple and clean way to automatically disable temporarily the sleep mode when certain applications are running (i.e. Samba) and then resume normally? I would prefer not reinventing the wheel. 
 
2- If not, could you help me to figure out a way to do it with dbus? 
 
3- Is a software like qbittorent, for example, use dbus
 to achieve this or is there another way?

Last piece of information: I also use my my Linux box locally (with mouse and keyboard). That means that &#8220;NOT using samba&#8221; should not automatically triggers the sleep mode.
 
Thank you *VERY MUCH* 
 
---------------------------------- 
Sosigene

---

### Post by Sosigene on 2012-03-21
Nobody can help me with that ?

I mean, disabling sleep/hibernate while sharing over a network is something that OS X and Windows do automatically. There must be a way to do that in Linux.

thx

---

### Post by Magnetizer on 2012-04-08
Hello Sosigene,

half a year ago, I wrote a Perl script that inhibits the screensaver / sleep mode via a dbus command depending on the load that some processes generate.

Yesterday I started to think about editing the script to implement a differentiation between disabling the screensaver and/or disabling the sleep mode. The idea is that the screensaver pops in while I am making lengthy backups of my computer via dejadup but to prevent it to go to sleep as the latter would disrupt the backup proces. I have not implemented this but I am looking into possible solutions.

Nevertheless, if I understand you correctly the script as it is would already solve your problem, wouldn't it?

I will attach the script, so you can have a look at it.

Hope this helps..;-)

PS: I added .txt to the name of the script otherwise it can not be uploaded. You can remove this, though. Make the script executable via 'chmod +x screensaver_prevention' and you can run it.

---

### Post by Sosigene on 2012-04-11
Thank you a_kaldenhoven!!!

You are right, that could solves my problem as I don't really care about the screensaver at this point.

I did not have time yet to check your script, but I will as soon as possible. I did myself quite a bit of Perl in the past so I should be able to figure it out.

As soon as I have tested it, I will come back in this thread to make a follow-up.

If you ever find time to modify your script to differentiate screensaver and sleep modes, I would really like to have a look to it.

Thank you very much. Really! :)

---

### Post by Magnetizer on 2012-04-11
Hi Sosigene,

you are very welcome. I am happy if people can make use of the scripts I wrote.

If you have any feedback, let me know.

If I can find the time for the differentiation between screensaver and sleepmode, I will post an update.

Have fun with the script.

Regards,

Andre

---

### Post by claudius139 on 2012-05-28
Did you find a solution finally because I have the same problem and just cannot find a solution. I have Ubuntu 12.04 and it's my Plex Media Server but It's going to sleep even if samba is sharing the movie I'm watching. 

How can I prevent that?

---

### Post by Magnetizer on 2012-05-30
> **claudius139 said:**
> Did you find a solution finally because I have the same problem and just cannot find a solution. I have Ubuntu 12.04 and it's my Plex Media Server but It's going to sleep even if samba is sharing the movie I'm watching. 

How can I prevent that?

Claudius,

have you tried the script I posted? You have to put it on your Plex Media Server and configure a process that should trigger the prevention of the screensaver/sleepmode.

In principle you should be able to solve your problem with it.

Do you think you know what to do?

---

### Post by claudius139 on 2012-05-30
Well that's the thing, I have the script but I'm simply not a Linux guy... :(

In the script, do I have do add 'Plex media Server' in the processes section?

Do you think you can give me some indication on how to do it please? 

1. What to modify in the script?
2. Where to put it?
3. How to add it to make it check? cron?

I know the basics, how to move, copy and edit files put that's pretty much it!

Thank in advance!

---

### Post by Magnetizer on 2012-05-30
Hi Cluadius,

I will start a private conversation with you to get this straightened out.

Kind regards,

Andre

---

### Post by Magnetizer on 2012-06-04
Hello everybody,

I have written a little Python indicator (attached) that can be used to manually or automatically disable the screensaver/suspension.

The script is designed for Ubuntu 12.04 but it could also work in other Linuxes using GTK/Gnome.

Using this indicator you can flexibly prevent the screensaver from interrupting an important process. For instance you could inhibit the screensaver while making a backup of your system, while watching flash movies on the net or while streaming a video from your media system.

There are some triggers that can be set in the script that determine whether the screensaver/suspension should be temporarily inhibited.

Those triggers are:

* max system load exceeded
* max incoming / outgoing network traffic
* a predefined process exceeds it's maximum CPU usage

Those triggers can be set in the settings section of the script.

You can also choose the theme (radiance or ambiance) by editing the line:
THEME = 'icons_light_theme'

With this the indicator icon matches the theme of your desktop.

You can add the script to the startup applications so that it runs when you reboot your machine.

For this add a startup application and set the command to:

bash -c "sleep 15 && cd ~/bin && /usr/bin/python -u ./screensaver_inhibitor_indicator.py 2>&1 > /dev/null"

If you have any questions, let me know.

Have fun and take care!

Kind regards,

Andre

---

### Post by vegastrey on 2012-07-05
Did you get preventing suspend when plex media server is active working? I'm interested in doing the same thing.

---

### Post by Magnetizer on 2012-07-06
Hi vegastrey,

I did not try using the script on a plex media server but it seems to me that this would surely be possible.

You will have to define the network activity that should inhibit the screensaver. As I got from "claudius139" the network usage clearly distinguishes if you are streming a video or not.

So you can set up the script and run it when the plex media server is started.

If you have any questions how to do so, just let me know.

---

