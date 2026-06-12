---
title: "I need an application that would shut down my computer after some specified time."
date: 2006-04-23
forum: Desktop Environments
---

### Post by sup on 2006-04-23
A friend of mine showed me a small application she sometimes uses to shut her computer when she listens to music before going to sleep. It was neat, just a clock to set up and nothing more. However, she uses windows XP. I was wondering, if something similar exists for linux?

I know I could use cron for that, but when I am usually going to bed, I am not really in a mood for command line - I have not come accross a gui for cron, is there any at all, btw?

---

### Post by Qrk on 2006-04-23
You shouldn't even need cron. The shutdown command itself has a timer functionality.

```
sudo shutdown -hH 60
```

Will turn off your computer and shut off the power in 60 minutes. If you want a gui, just make it into a bash script with a launcher.

---

### Post by Wolki on 2006-04-23
That's pretty smart qrk, didn't know shutdown has a built-in timer...

If you want a more flexible gui than a simple launcher with a fixed value, you can use zenity. something like:

```
#!/bin/bash
shutdown_time=$(zenity --scale --title="Automated Shutdown" --text="Please select for how many minutes the computer should continue running." --min-value="1" --max-value="240" --value="60")
shutdown -hH ${shutdown_time}

```

save this as "shutdown-script" or similar somewhere then make a launcher in gnome to "gksudo  /path/to/shutdown-script". Click on it and you will get a window with a slider allowing you to fine-tune for how long you want the music to play.

---

### Post by super on 2006-04-23
@wolki + qrk
very slick. i like it.
thanks!

---

### Post by henriquemaia on 2006-04-23
[QUOTE=sup][...]
I know I could use cron for that, but when I am usually going to bed, I am not really in a mood for command line - I have not come accross a gui for cron, is there any at all, btw?[/QUOTE]
[URL="http://gnome-schedule.sourceforge.net/"]

gnome-schedule[/URL]
kcron 

Both on the repositories.

---

### Post by Qrk on 2006-04-23
[QUOTE=Wolki]That's pretty smart qrk, didn't know shutdown has a built-in timer...

If you want a more flexible gui than a simple launcher with a fixed value, you can use zenity. something like:

```
#!/bin/bash
shutdown_time=$(zenity --scale --title="Automated Shutdown" --text="Please select for how many minutes the computer should continue running." --min-value="1" --max-value="240" --value="60")
shutdown -hH ${shutdown_time}

```

save this as "shutdown-script" or similar somewhere then make a launcher in gnome to "gksudo  /path/to/shutdown-script". Click on it and you will get a window with a slider allowing you to fine-tune for how long you want the music to play.[/QUOTE]

I can't believe I haven't heard of zenity before. I'm going to go through all of my bash scripts and make them gui enhanced. Thanks! ;)

---

### Post by sup on 2006-04-24
Wolki: thanks, I think it will do. Zenity looks great, by  the way.

---

### Post by Ramses de Norre on 2006-04-24
What's the -H option for?

---

### Post by super on 2006-04-24
[QUOTE=Ramses de Norre]What's the -H option for?[/QUOTE]

the [FONT="Courier New"]-h[/FONT] is for halt. you can also use [FONT="Courier New"]-r[/FONT] for reboot

---

### Post by ximok on 2006-04-25
You can also use "at".  at is like cron, except its a one time use thing... 


so, if you want your machine to perform a function (like download your favorite podcast then shutdown) type
at [the execution time]

your little script

then hit CTRL-D

and use atq to see your jobs.

atrm will remove them

```

root@dvr:~# at 11:59 am
warning: commands will be executed using (in order) a) $SHELL b) login shell c) /bin/sh
at> wget http://myfavoritepodcast.mp3 && shutdown -h now
at> <EOT>
job 1 at 2006-04-25 11:59
root@dvr:~#

```

---

### Post by spade_shark on 2006-04-26
Great tips guys.  I have added this to the tool belt.  What about this idea?
 
This requires no linux knowledge.  But should only be attempted by professionals!

Get a string with a large weight attached.  Find a candle and several matches.  Set the string up on a diagonal, with weight above power switch.  For longer run time put candle farther from string.  For shorter listening, bring candle closer to string.  Light before bed and set "time".  Enjoy :)

---

### Post by Ramses de Norre on 2006-04-26
[QUOTE=super]the [FONT="Courier New"]-h[/FONT] is for halt. you can also use [FONT="Courier New"]-r[/FONT] for reboot[/QUOTE]
Yeah, I know about -h but I meant -H

---

### Post by m_memmory on 2006-05-09
[QUOTE=Wolki]That's pretty smart qrk, didn't know shutdown has a built-in timer...

If you want a more flexible gui than a simple launcher with a fixed value, you can use zenity. something like:

```
#!/bin/bash
shutdown_time=$(zenity --scale --title="Automated Shutdown" --text="Please select for how many minutes the computer should continue running." --min-value="1" --max-value="240" --value="60")
shutdown -hH ${shutdown_time}

```

save this as "shutdown-script" or similar somewhere then make a launcher in gnome to "gksudo  /path/to/shutdown-script". Click on it and you will get a window with a slider allowing you to fine-tune for how long you want the music to play.[/QUOTE]


I've copied that code and saved it as a file called *shutdown* and then went to create a launcher called *shutdown pc* but nothing seems to happen when I double click on the launcher.

Is there some kind of launcher options that I need to set or something?  Or is there some extra thing I need to do with the code?  I tried doing *sudo apt-get installl zenity* just in case I didn't have that but I get a message saying I've already got the updated version of it.

Sorry if I'm missing something - I'm a total newbie when it comes to linux really.

EDIT:
I've since cut the zenity code and run that from a terminal window on it's own and that works fine so I think it could be something in the way it's being run from the launcher.  I've tried *gksudo path/to/file/shutdown* and also *"gksudo path/to/file/shutdown"* but it never seems to work.

---

### Post by mcduck on 2006-05-09
[QUOTE=m_memmory]I've copied that code and saved it as a file called *shutdown* and then went to create a launcher called *shutdown pc* but nothing seems to happen when I double click on the launcher.

Is there some kind of launcher options that I need to set or something?  Or is there some extra thing I need to do with the code?  I tried doing *sudo apt-get installl zenity* just in case I didn't have that but I get a message saying I've already got the updated version of it.

Sorry if I'm missing something - I'm a total newbie when it comes to linux really.

EDIT:
I've since cut the zenity code and run that from a terminal window on it's own and that works fine so I think it could be something in the way it's being run from the launcher.  I've tried *gksudo path/to/file/shutdown* and also *"gksudo path/to/file/shutdown"* but it never seems to work.[/QUOTE]have you made the script file executable? if not, run 'chmod +x /path/to/file.sh'

---

### Post by m_memmory on 2006-05-09
Thanks so much... that's got the script working (I assume it'll shut the PC down but I'm not going to test it just yet as I'm in the middle of some important stuff)

I don't know whether it was altering the file properties that I needed to do or whether it was actually renaming the file - to begin with my file was called *shutdown* so I renmaed it to *shutdown.sh* then ran that commmand you gave me.

Now when I run it comes up with the graphical interface as it should.  That zenity is really cool - I didn't know linux had such an easy way of creating interfaces to terminal commands like that, I think more learning could be in store here.

Thanks once again.

---

### Post by bluenova on 2006-05-09
[QUOTE=Ramses de Norre]Yeah, I know about -h but I meant -H[/QUOTE]
I assume -H stands for hour, as it's the time argument.

---

### Post by Ramses de Norre on 2006-05-09
shutdown needs a time indication even when no extra options/flags are specified.

---

