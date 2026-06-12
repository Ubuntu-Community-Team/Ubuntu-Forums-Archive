---
title: "Cron"
date: 2006-07-10
forum: Desktop Environments
---

### Post by Sonofmoog on 2006-07-10
Of all the Linux applications I've had problems with, cron has proven the most intractable.  I just can't seem to get it to work .. Present situation:

I've created a simple shell script to remind me to take my medicine, and created a cronjob to launch that script every day at 18:00.  The script works, but the cronjob doesn't execute.  Or, if it does execute, there is no output to the screen, and no system record that I can find.  Please know that both crond and anacrond are running.  

I launch gnome-schedule and the job is listed (it was created as root, if that matters), but there is nothing in /etc/crontab or /etc/anacrontab or /etc/cron.daily.  Nor is there anything in /var/log/messages.  I begin to think that Gnome works a lot differently than KDE in managing cronjobs.  

The cronjob is 0 18 * * * /$HOME/Scripts/Remindme

Two questions:  Where in Ubuntu can I check to see whether a cronjob has executed?  Assuming it does execute, how can I make sure it sends output to STDOUT?

TIA

---

### Post by simonn on 2006-07-10
There will not be any output to the screen by default on a cron job. Cron jobs are not connected to a terminal so stdout goes nowhere.

Have a look at [http://www.die.net/doc/linux/man/man1/write.1.html](http://www.die.net/doc/linux/man/man1/write.1.html).

Also, off the top of my head, the cron job definition is not correct, it should read:

```

0 18 * * * [user] "$HOME/Scripts/Remindme"

```

Replace [user] with the user it should be run as. The "s are there incase there are spaces in the path name. Probably not neccesary inthe case, but a good habit to develop anyway.

---

### Post by Sonofmoog on 2006-07-10
> **simonn said:**
> There will not be any output to the screen by default on a cron job. Cron jobs are not connected to a terminal so stdout goes nowhere.

Thanks for your reply.  I'm assuming then there is no way to redirect the output of a cronjob to stdout, or to specify a display to output to?

I don't suppose there's a GNOME equivalent of kalarm?

---

### Post by simonn on 2006-07-12
Sorry about the delay, but I was not sure how to do this exactly so did not want to post until I had tested it.

Install zenity (via apt-get, synaptic etc).

The simple way:

Use the following line in /etc/crontab

```

0 18 * * * [user] DISPLAY=:0 zenity --info --text "[message]"

```

What this is doing is running the zenity command to display an info type message box with your message on display 0. If you are not logged into gnome (well... X actually) then the command will fail.

It is important that you replace [user] with the user name of the user you log into gnome with. If you do not then the command will fail. You can use xhost to allow other users to send display GUI apps on your gnome session, but this is a touch insecure.

This also assumes you log in with display 0 - this is very likely if you are the only person logged in to your PC at one time. I would however use...

The harder, but more complete way:

If there are multiple people logged in via X windows then it becomes more complicated. It is possible to determine which displays are being used locally by using ls /tmp/.X*-lock, but I have not found a way to determine which user is logged into which display. However, unless you have used xhost to allow other users to use your display, as mentioned above, you can send it to all local displays and rely on the fact that unless the command is being run as the user specified in the cron job it will fail for displays the specified user is not logged into - if that makes sense. 

The below does this:

```

0 18 * * * [user] ls /tmp/.X*-lock | sed 's/\/tmp\/\.X\([0-9]*\)-lock/DISPLAY=:\1 zenity --info --text \"[message]\"/' | sh

```

I have not figured out how to deal with remote X displays... yet.

---

### Post by Sonofmoog on 2006-07-15
Thanks for your help, Simon .. Sorry to be so late acknowledging, but I wanted to give your suggestion time to work.  The bad news is it does not.  I can cut and paste from your post, or from my crontab, into the commandline, and it works fine.  But, I see nothing onscreen qt the scheduled time, and there is no record anywhere that the job executes.  Gnome apparently writes to /var/log/syslog instead of /var/log/messages, but there is nothing in either file about my cronjobs.  Here is the line from /etc/crontab

```
0 18    * * *   reb     Display=:0 zenity --info --text  "Take your medicine"
```

I want to thank you again for your help.  Zenity looks to be a nifty tool for shell scripts, so I come away from this with something ..

---

### Post by Thund3rstruck on 2006-07-15
You can check on the status of cron jobs by checking the syslog
```

cat /var/log/syslog | grep -i cron

```

output sample:
Jul 15 03:00:01 (none) crond[222]: USER root pid 266 cmd fakecall.tcl
Jul 15 04:00:01 (none) crond[222]: USER root pid 267 cmd restart
Jul 15 04:02:40 (none) crond[222]: crond 2.3.2 dillon, started, log level 8
Jul 15 05:00:01 (none) crond[222]: USER root pid 223 cmd /busybox/tivowebplus/tivoweb

---

### Post by Kadin2048 on 2006-07-15
I just thought I'd put in one other suggestion. This may or may not be what you want to do, but with my 'reminder' cron jobs, instead of having it send a message to the screen or console, I have it send me an email message instead.

This is pretty easy to do using the mail command; you just say ```
sh ~/[yourscript] 2>&1 | mail -s "Daily Reminder" [youremail]@[whatever].com
```

This requires that you have postfix working and that your ISP doesn't block outgoing connections on port 25, or that you've configured postfix to use your ISP's mail server instead.

I use scripts like this to send me reminders (I can even have it send me text messages to my cellphone via email) and also to run batch operations and email me the results at night (e.g. rsync jobs).

The little 'mail' program doesn't get a lot of respect, but it sure is handy.

---

### Post by Sonofmoog on 2006-07-15
> **Thund3rstruck said:**
> You can check on the status of cron jobs by checking the syslog
```

cat /var/log/syslog | grep -i cron

```

Thanks.  I did so, and have verified that my cronjobs are running, but nothing is going to stdout.  I know this because I am not seeing anything ..

---

### Post by Sonofmoog on 2006-07-15
> **Kadin2048 said:**
>  ```
sh ~/[yourscript] 2>&1 | mail -s "Daily Reminder" [youremail]@[whatever].com
```

I will need something like this eventually, so I'll file this away for reference, but for the moment, I'm trying to do two things:  

When I'm at the computer oblivious to the time, I need an automatic interrupt reminding me to take my medicine ..

When I get up in the morning, I want my computer to wake me by playing music I like.  

In KDE, kalarm does this really well.  I haven't found the means to do this in GNOME yet ..

---

### Post by mikeym on 2006-07-30
Hi I know this is a bit late but I am reasurching the same problem and I have come up with this:

```

53 20 * * * export DISPLAY=$(who | awk ' BEGIN { FS=" " } /'`whoami`'/ { print $2 }' | head -n1) && zenity --info --text "Take your medicine"

```

'who' gives you a list of the users who are logged on and their displays. I am assuming that the first one in each case will be the users X session display. you could replace the whole '`whoami`' bit with the users name if you are being specific, but I am installing this using "crontab -e" in which case I am not supplying the users name directly and have used this to be more general.

I suspect the problem you had with the first suggestion just stemmed from the chaining of the 2 commands - as far as I know a space alone wont do. I have used '&&' and I have used 'export' for good mesure so that any scripts called will get the same display.

---

### Post by ardchoille on 2006-07-30
> **Sonofmoog said:**
> Of all the Linux applications I've had problems with, cron has proven the most intractable.  I just can't seem to get it to work .. Present situation:

I've created a simple shell script to remind me to take my medicine, and created a cronjob to launch that script every day at 18:00.  The script works, but the cronjob doesn't execute.  Or, if it does execute, there is no output to the screen, and no system record that I can find.  Please know that both crond and anacrond are running.  

I launch gnome-schedule and the job is listed (it was created as root, if that matters), but there is nothing in /etc/crontab or /etc/anacrontab or /etc/cron.daily.  Nor is there anything in /var/log/messages.  I begin to think that Gnome works a lot differently than KDE in managing cronjobs.  

The cronjob is 0 18 * * * /$HOME/Scripts/Remindme

Two questions:  Where in Ubuntu can I check to see whether a cronjob has executed?  Assuming it does execute, how can I make sure it sends output to STDOUT?

TIA

I wrote up a cron tutorial, hope it helps:
[http://ubuntuforums.org/showthread.php?t=102625](http://ubuntuforums.org/showthread.php?t=102625)

---

### Post by mettavihari on 2007-06-02
I have tried this in my Ubuntu 7.04

1 6 * * mon DISPLAY=:0 /usr/bin/gmplayer -fs <filename.mov> 

it does not come up on the screen.

I would much appreciate to have help on this.

Regards
Mettavihari

---

### Post by mettavihari on 2007-06-02
I have also tried the following

14 14 * * mon export DISPLAY=:0 /usr/bin/gmplayer -fs <filename.mov> 
14 14 * * mon export DISPLAY=:0 &&  /usr/bin/gmplayer -fs <filename.mov> 
14 14 * * mon export DISPLAY=:0 && /usr/bin/gmplayer -fs <filename.mov> |sh

Non of them seems to work
I get this error in my syslog error file

Jun  2 14:14:02 metta-lap /USR/SBIN/CRON[6648]: (metta) CMD (export DISPLAY=:0 /usr/bin/mplayer -fs /home/metta/test.mov)
Jun  2 14:14:02 metta-lap /USR/SBIN/CRON[6647]: (metta) MAIL (mailed 195 bytes of output but got status 0x0001 )
Jun  2 14:15:02 metta-lap /USR/SBIN/CRON[6675]: (www-data) CMD ([ -f /usr/share/moodle/admin/cron.php ] && /usr/bin/php -f /u
sr/share/moodle/admin/cron.php > /dev/null)

The command from the shell
/usr/bin/mplayer -fs /home/metta/test.mov
works fine.


regards
Mettavihari

---

### Post by simonn on 2007-06-02
Firstly, the following is the command you want to use:

```

DISPLAY=:0 /usr/bin/gmplayer -fs <filename.mov> 

```

In *nix you can specify environmental variables on the command line before you execute a command. In this case you are setting the DISPLAY variable to :0. This informs X applications  to use display 0. 

Press ctrl + alt + F1 and log in to the console. Now run the above command. Press ctrl + alt + 7 to return to your X/Gnome/KDE whatever session. 

Is the movie playing? 

If not then go back to the console and check any output and post here.

If it is, then I suspect that what you have to do is add the following to the top of your crontab:

```

MAILTO=""

```

I may be completely and absolutely wrong, but:

Jun 2 14:14:02 metta-lap /USR/SBIN/CRON[6647]: (metta) MAIL (mailed 195 bytes of output but got status 0x0001 )

Hints at some kind of mail related problem.

---

### Post by mettavihari on 2007-06-04
Thank you for the reply.

1 6 * * * DISPLAY=:0 /usr/bin/mplayer -fs /home/metta/test.mov

I can do as you say: run the command from CTRL Alt F1 and it run on the screen when I switch to F7

I can ssh to the box and execute the command from that shell and It will run 

However cron will not run the command.

Perhaps there is something in the enviroment of cron that make the cron-command not go to the display.

The funny part is that the command works in a Slackware box that I have running.  But not in Ubuntu.

I have switched over to Ubuntu for this box and need it badly working in Ubuntu. 

regards
Mettavihari

---

### Post by simonn on 2007-06-04
Try

1 * * * * DISPLAY=:0 /usr/bin/mplayer -fs /home/metta/test.mov > /tmp/mplayer.log 2>&1

Wait for a minute to tick over and then post the output of the following here:

cat /tmp/mplayer.log

---

### Post by mettavihari on 2007-06-16
Thank you for that.

It works if I redirect the output like that 
however that may not be a proper solution.

Here is a snip of the mplayer.log file

Help to debug the messages in this file would be appreciated

regards
Mettavihari

----------------  ---------------  ----------------  


MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm)   2400+ (Family: 6, Model: 8, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/Data/playlist/Test-22-dvd.vob.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  8000.0 kbps (1000.0 kbyte/s)
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12  [fs]
A:   0.3 V:   0.0 A-V:  0.240 ct:  0.000   1/  1 ??% ??% ??,?% 0 0              
A:   0.3 V:   0.2 A-V:  0.085 ct:  0.004   2/  2 ??% ??% ??,?% 0 0              
A:   0.3 V:   0.2 A-V:  0.076 ct:  0.008   3/  3 ??% ??% ??,?% 0 0              
A:   0.3 V:   0.3 A-V:  0.068 ct:  0.012   4/  4 ??% ??% ??,?% 0 0              
<snip>
A:  14.8 V:  14.6 A-V:  0.187 ct:  0.084 363/363  5% 69%  0.7% 71 0             
A:  14.9 V:  14.7 A-V:  0.200 ct:  0.087 364/364  5% 70%  0.7% 72 0             
A:  14.9 V:  14.7 A-V:  0.239 ct:  0.090 365/365  5% 70%  0.7% 73 0             
A:  15.0 V:  14.7 A-V:  0.276 ct:  0.093 366/366  5% 70%  0.7% 74 0             
A:  15.1 V:  14.8 A-V:  0.339 ct:  0.096 367/367  5% 70%  0.7% 75 0             
A:  15.2 V:  14.8 A-V:  0.387 ct:  0.099 368/368  5% 71%  0.7% 76 0             
A:  15.3 V:  14.9 A-V:  0.420 ct:  0.102 369/369  5% 71%  0.7% 77 0             
A:  15.4 V:  14.9 A-V:  0.468 ct:  0.105 370/370  5% 71%  0.7% 78 0             
A:  15.4 V:  14.9 A-V:  0.479 ct:  0.106 371/371  5% 72%  0.7% 79 0             

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

A:  15.5 V:  15.0 A-V:  0.531 ct:  0.106 372/372  5% 72%  0.7% 80 0             
A:  15.6 V:  15.0 A-V:  0.564 ct:  0.106 373/373  5% 72%  0.7% 81 0             
A:  15.8 V:  15.1 A-V:  0.703 ct:  0.110 374/374  5% 72%  0.7% 82 0             
<snip>
A:  77.0 V:  77.0 A-V:  0.013 ct:  7.424 1923/1923  5% 59%  0.6% 0 0            
A:  77.1 V:  77.1 A-V:  0.005 ct:  7.423 1924/1924  5% 59%  0.6% 0 0            
A:  77.1 V:  77.1 A-V:  0.006 ct:  7.422 1924/1924  5% 59%  0.6% 0 0            

Exiting... (Quit)

---

### Post by simonn on 2007-06-18
This looks like an mplayer problem.

What happens if you do the following in a terminal window when logged into gnome?

```

/usr/bin/mplayer -fs /home/metta/test.mov

```

Liek is says in the mplayer log:

```


Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
- Try -ao sdl or use the OSS emulation of ALSA.
- Experiment with different values for -autosync, 30 is a good start.
- Slow video output
- Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
- Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
- Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
- Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
- Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.

```

Someone went out of their way to write the helpful text above for you to just ignore. Think about it.

Try different -vo settings and maybe cache e.g.

/usr/bin/mplayer -cache 8192 -fs /home/metta/test.mov

/usr/bin/mplayer -vo x11 -cache 8192 -fs /home/metta/test.mov

/usr/bin/mplayer -vo xv -cache 8192 -fs /home/metta/test.mov

Also, try adding:
 -vc ffmpeg 

To the above.

It is more than likely one or a combination of the following parameters that will solve the problem -vo -ac -vc -cache. However, read the mplayer doco and it may be worth asking on the mplayer list.

---

### Post by Unconscious on 2007-09-10
ummm...  why not just use kalarm under gnome. I do. It works for me.

---

