---
title: "At command"
date: 2013-03-27
forum: Desktop Environments
---

### Post by linuxonbute on 2013-03-27
I am having problems with this command.
I have a python script which I have been playing with and what it does is mail me a message.
Now if I run it directly it works fine but I wanted a regular reminder so I thought I might use the 'at' command

To test it out I tried these:
at -t 03271658 `./runmyscript.py`
at -t 03271658 `/home/norman/runmyscript.py`
at -t 03271700 -f ./runmyscript.py
at -t 03271700 -f /home/norman/runmyscript.py
but none of them work.

I can do the following:
> 
 at now + 1 min `echo Hello> ./hello`warning: commands will be executed using /bin/sh
at> ^C

cat hello 
Hello

at now + 1 min `echo goodbye> ./hello`
warning: commands will be executed using /bin/sh
at> ^C
cat hello 
goodbye



I know there are other ways but I would like to get this working. Any ideas please?

---

### Post by matt_symes on 2013-03-27
Hi 

Two points; use ctrl + d to schedule the job, not ctrl + c. This will send the EOT character to at. Be aware it's using sh and not bash to run any scripts.

```

matthew-S206:/home/matthew % at now + 1 min
warning: commands will be executed using /bin/sh
at> echo hello > /home/matthew/test1
at> <EOT>
job 14 at Wed Mar 27 20:17:00 2013
matthew-S206:/home/matthew % cat test1
hello
matthew-S206:/home/matthew %
```

Also the at command is similar to cron in that it does not have the environment your user has.

Let me give you an example.

To play the gangnam style video, i can navigate into my Music directory and type

```

matthew-S206:/home/matthew/Music % pwd
/home/matthew/Music
matthew-S206:/home/matthew/Music % mplayer PSY_-_GANGNAM_STYLE_&#44053;&#45224;&#49828;&#53440;&#51068;_M_V-9bZkp7q19f0.mp4
```

This will quite happily play the video.

However this, using at, this will not work

```
matthew-S206:/home/matthew/Music % at now + 1 min                                            
warning: commands will be executed using /bin/sh
at> mplayer PSY_-_GANGNAM_STYLE_&#44053;&#45224;&#49828;&#53440;&#51068;_M_V-9bZkp7q19f0.mp4
at> <EOT>
job 15 at Wed Mar 27 20:22:00 2013
matthew-S206:/home/matthew/Music % 
```

That is because it is missing some of my environment.

This, however, will run the video

```
matthew-S206:/home/matthew % at now + 1 min
warning: commands will be executed using /bin/sh
at> DISPLAY=:0 /usr/bin/mplayer /home/matthew/Music/PSY_-_GANGNAM_STYLE_&#44053;&#45224;&#49828;&#53440;&#51068;_M_V-9bZkp7q19f0.mp4
at> <EOT>
job 16 at Wed Mar 27 20:23:00 2013
matthew-S206:/home/matthew % 

```

I have supplied full paths and the DISPLAY environmental variable. Make sure you are supplying everything at needs to run your script

I hope that helps.

Incedently, i have used at and mplayer as an alarm clock in the past.

**EDIT:**

I think you know this from your first post but i thought i would mention it for any others looking at this thread who do not know.

You can pipe commands into at.

```
echo DISPLAY=:0 /usr/bin/mplayer /home/matthew/Music/PSY_-_GANGNAM_STYLE_&#44053;&#45224;&#49828;&#53440;&#51068;_M_V-9bZkp7q19f0.mp4 | at now + 1 min
```
Kind regards

---

### Post by linuxonbute on 2013-03-27
Thanks Matt 
/home/norman/runmyscript.py | at -t 03272233
did the job.
I hadn't thought about the environment :p

---

