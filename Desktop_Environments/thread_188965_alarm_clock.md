---
title: "alarm clock"
date: 2006-06-04
forum: Desktop Environments
---

### Post by nickdr on 2006-06-04
i used to use a playlist to wake me up every morning in windows, so i was wondering how i could do this in ubuntu. 
i use rythymbox as my player, and when i save a playlist and then double click it from the file browser it is empty, even though i added music to it and then saved it. i think that i need to solve this problem first. or i might not have to do that in ubuntu (in windows i would use task scheduler and have it open my saved playlist.
also what program would i use in ubuntu that is the equivilant of window's task scheduler?

---

### Post by Denis on 2006-06-04
I don't know windows task scheduler, but I guess it's a program that allows you to confige to run a program automatically (at a given time)?

In Linux you've got "cron" to do that. It's quite easy to use. It has a bootup service so it always runs as a daemon in case it has to start something. 

You can see a list of items scheduled for cron by typing "crontab -l" (in the terminal) At this moment you'll probably get a message that there is nothing scheduled. 

To add new "jobs" to cron, you can type "crontab -e". This wil create a text file for the new list of tasks. 

The syntax is as following: 
[min] [hour] [day of month] [month] [day of week] **[program to be run]**

So the following example will move "picture.png" to the directory "/home/you/pictures" every day at 5 o'clock. The "*" means you want to do it **every** day, month (and day of the week)

0 5 * * * **mv picture.png /home/you/pictures**

Most of the times console commands are used with cron, but normally it is also able to start graphical programs. Just try to run rhythmbox with it (let's say at 10 past 6 in the morning). I think the "-- play" option starts playing the playlist. 
[edit] it looks like rhythmbox needs the play command when allready started, so just add *this* on a second line. One minute later e.g.[/edit]

10 6 * * *  rhythmbox
*11 6 * * * rhythmbox --play*
Make sure to save the list you just edited. 

Day of the week may also be interesting for you, since you don't want to wake up at 6 when it's saturday e.g. :) 

Of course your computer should be on and logged in at the moment you want the job to be executed. If your motherboard supports this you can even let your computer start up at a time given, which does provide a lot of opportunities...

You can find much more complete information over here: [http://www.scrounge.org/linux/cron.html](http://www.scrounge.org/linux/cron.html)
 
Or just look for "cron" on the internet.

---

### Post by bionnaki on 2006-06-04
just install beep-media-player and the alarm plugin (look in synaptic)

---

### Post by shamrock_uk on 2006-06-04
Or if you prefer the graphical approach, 

```
sudo apt-get install kalarm
``` will do the trick. It's fairly comprehensive and can play horrible wakey-up sounds to you in the morning.

If you set it to start up Amarok or similar, then it can resume playing on startup if you prefer to have access to your full playlist of more soothing music!

---

### Post by Corey on 2006-07-13
Kinda ridiculous there isn't a real alarm app (or applet) in gnome. hmmm... still learnin' python. May have found me a real project. Unless someone else beats me to it.

---

### Post by vassalle on 2006-08-03
really wish someone would write a stand alone alarm clock for linux/ubuntu. theres like a dozen of them for mac osx already, most of them are free, not that shareware crap.

its not that i dont like built-in alarm clock in bmp, xmms or amarok.. i just feel that it would be much neater/easier to have a separate program for that. something like [this]("http://www.macupdate.com/info.php/id/20597") maybe? 

just my 2 cents

---

### Post by tzulberti on 2006-08-03
There is also one called lsalarm, but i can not find the deb package (debian has one). I don't think one should build an alarm clock, there are many at freshmeat.net or sourceforge.net

---

