---
title: "Getting cron to work"
date: 2008-12-10
forum: General Help
---

### Post by sn0m on 2008-12-10
Hi guys
I have made a script which is as follow:

#!/bin/bash

# a simple script to capture 2 hr of tar 
mplayer -vc null -vo null -ao pcm:fast:waveheader:file=stream.wav "http://tar.serverroom.us:9078/" &
# the & sets the job running in the background

sleep 2m

kill $! # kill the most recently backgrounded job
------------------------------------------------------
#improve sound quality and volume using sox
sox stream.wav -n stat > stats 2>&1 || exit 1
VOL=$(grep 'Volume' stats | sed 's/^.*[ \t]//')
sox -v $VOL stream.wav aLive.wav || exit 1
rm stream.wav
------------------------------------------------------
#convert to mp3
for i in *.wav; do
 if [ -e "$i" ]; then
   aLive=`basename "$i" .wav`
   lame -h -b 192 "$i" "$aLive.mp3"
 fi
done
------------------------------------------------------
#need to clear up
rm *wav stats

#end

it is saved in /home/sn0m/bin which I have exported to $PATH, so it is  now part of executable directories.

next is to set it to run at particular times using cron.

Therefore I ran crontab -e and edited using nano to the following settings:

 # m h  dom mon dow   command
* * * * * /home/sn0m/bin/record_aLive

then ctrl o and ctrl x

and out.
According to my understanding the script should run every minutes, but it dosen't. I'm a bit stuck and would appreciate if someone could tell me what am I doing wrong in here?

Regards
Sokol

---

### Post by JohnFH on 2008-12-10
A few things to check:
- does it have executable permissions?
- can you run the script ok outside of cron?  ie. directly from the command line.
- the text below is taken from the crontab man page.
```
Although cron requires that each entry in a crontab end in a  newline  character,  neither
the  crontab command nor the cron daemon will detect this error. Instead, the crontab will
appear to load normally. However, the command will never run. The best choice is to ensure
that your crontab has a blank line at the end.
```

A final tip:
- when I want to be sure a script has been run I put a beep command at the start, so it's immediately obvious whether it's worked or not.

Hope that helps.

---

### Post by sn0m on 2008-12-10
Hi JohnFH
Thanks for getting back to me.
The script works flawlessly outside cron, I just need to do the usual ./record_aLive.

this is the la of my bin file:

 sn0m@sn0m-laptop:~$ ls -la ~/bin
total 44
drwxr-xr-x  2 sn0m sn0m 4096 2008-12-10 21:41 .
drwxr-xr-x 68 sn0m sn0m 4096 2008-12-10 22:35 ..
-rw-r--r--  1 sn0m sn0m  483 2008-12-10 21:41 mpl_tar~
-rw-r--r--  1 sn0m sn0m  501 2008-12-10 21:41 mpl_tir_liv~
-rwxr-xr-x  1 sn0m sn0m  501 2008-12-10 21:41 mpl_tir_live
-rwxr-xr-x  1 sn0m sn0m  797 2008-12-10 21:41 record_aLive
-rw-r--r--  1 sn0m sn0m  797 2008-12-10 21:41 record_aLive~
-rwxr-xr-x  1 sn0m sn0m  827 2008-12-10 21:41 record_liv_from_tirana
-rw-r--r--  1 sn0m sn0m  827 2008-12-10 21:41 record_liv_from_tirana~
-rwxr-xr-x  1 sn0m sn0m  806 2008-12-10 21:41 record_rikoshet
-rw-r--r--  1 sn0m sn0m  806 2008-12-10 21:41 record_rikoshet~
sn0m@sn0m-laptop:~$ 

as you can see it has x power.

regards 
Sokol

---

### Post by reality1011 on 2008-12-10
paste the output of "sudo crontab -l"

---

### Post by JohnFH on 2008-12-10
> **sn0m said:**
> Hi JohnFH
Thanks for getting back to me.
The script works flawlessly outside cron, I just need to do the usual ./record_aLive.

this is the la of my bin file:

-rwxr-xr-x  1 sn0m sn0m  797 2008-12-10 21:41 record_aLive


The only time I had this exact behaviour was when I didn't have a newline at the end of the crontab file, so edit your crontab file and make sure there's a newline at the end of it.

```
man 5 crontab
```
gives more detailed information than the standard crontab manpage.

```
ps aux | grep cron
```
will check that the cron process is actually running.

---

### Post by sn0m on 2008-12-10
Thanks for helping me chaps. this is the output:

sn0m@sn0m-laptop:~$ sudo crontab -l
[sudo] password for sn0m: 
# m h  dom mon dow   command
* * * * * /home/sn0m/bin/record_aLive
#new line 
sn0m@sn0m-laptop:~$ crontab -l
# m h  dom mon dow   command
* * * * * /home/sn0m/bin/record_aLive
#new line                                                    



sn0m@sn0m-laptop:~$ ps aux | grep cron
root      5319  0.0  0.0   3412  1028 ?        Ss   23:27   0:00 /usr/sbin/cron
root      5834  0.0  0.0      0     0 ?        Z    23:28   0:00 [cron] <defunct>
sn0m      5835  0.0  0.0      0     0 ?        Z    23:28   0:00 [cron] <defunct>
sn0m      7092  0.0  0.0   3244   824 pts/1    S+   23:31   0:00 grep cron
sn0m@sn0m-laptop:~$ 

ta
Sokol

---

### Post by JohnFH on 2008-12-10
Those defunct processes look suspicious.  Try restarting cron to see if that makes a difference:
```
sudo /etc/init.d/cron restart
```
If that doesn't work, try killing those defunct processes:
```
sudo kill -9 5834 5835
sudo /etc/init.d/cron restart
```
If that fails to get rid of those defunct processes, reboot the machine and check that the defunct processes have gone.

---

### Post by sn0m on 2008-12-10
Hi John
this is what I get after clearing of settings in crontab -e and only editing the sudo crontab -e.
This is what it looks like:

sn0m@sn0m-laptop:~$ sudo crontab -l
# m h  dom mon dow   command
* * * * * /home/sn0m/bin/record_aLive
# 
sn0m@sn0m-laptop:~$ crontab -l
# m h  dom mon dow   command

sn0m@sn0m-laptop:~$ ps aux | grep cron
root      9318  0.0  0.0   3412  1024 ?        Ss   Dec10   0:00 /usr/sbin/cron
sn0m@sn0m-laptop:~$ sudo kill 9318
sn0m@sn0m-laptop:~$ sudo /etc/init.d/cron restart
 * Restarting periodic command scheduler crond                           [ OK ] 
sn0m@sn0m-laptop:~$ ps aux | grep cron
root      9751  0.0  0.0   3412  1024 ?        Ss   00:02   0:00 /usr/sbin/cron
sn0m      9760  0.0  0.0   3240   804 pts/2    R+   00:02   0:00 grep cron
sn0m@sn0m-laptop:~$ 

there's still a question mark in it which I don't know why?
Thanks
Sokol

---

### Post by JohnFH on 2008-12-10
The question mark is nothing to worry about, it just means there's no terminal associated with that process (that's true of virtually all processes).   The 'grep cron' process was started from a terminal though and so the value for that process is the name of the terminal (in this case pts/2).  If you type 'tty' into the same terminal that you issued the ps command from, you should see the output '/dev/pts/2'.

The only thing I can think of now is that I've noticed that your cron job is setup for the root user only and that may affect how your script is run.  So instead of running 'sudo crontab -e', run 'crontab -e' and include your cron rule there.

---

### Post by andrew.46 on 2008-12-10
Hi,

I did not realise when we spoke before that you were setting your *own* crontab with sudo. To set your own crontab you do not need to specifiy sudo and in fact when you do this you are setting a crontab for root, not yourself.

Try running these 2 commands, this shows root's crontab:
```

sudo crontab -l
```

and this should show *your* crontab:
```

crontab -l
```

Hopefully the problem lies in this? Have a look at your crontab syntax as well, there should be a space between the [COLOR="Red"]**[/COLOR]s: [COLOR="Red"]* *[/COLOR] rather than [COLOR="Red"]**[/COLOR] and no spaces after [COLOR="Red"],[/COLOR] so [COLOR="Red"]mon,tues[/COLOR] rather than [COLOR="Red"]mon, tues[/COLOR].

  Andrew

  Andrew

---

### Post by sn0m on 2008-12-11
Thanks andrew for your reply.
This is my output:

sn0m@sn0m-desktop:~$ crontab -l
# m h  dom mon dow   command


#exp
* * * * * /home/sn0m/my_scripts./exp

#record alive
00 21 * * mon,thu /home/sn0m/my_scripts/record_aLive.sh

#record Live from Tirana
00 10 * * mon,wed,thu,fri /home/sn0m/my_scripts/record_liv_from_tirana.sh

# record Rikoshet
00 12 * * tue /home/sn0m/my_scripts/record_rikoshet.sh

sn0m@sn0m-desktop:~$ sudo crontab -l
[sudo] password for sn0m: 
no crontab for root
sn0m@sn0m-desktop:~$ 

could I kindly ask you guys to post your crontab -l output so I can compare them to mine.
It is too frustrating trying to deal with it. One of my favorite bands, the iron maiden have a lyric where they say "so close yet so far away" and it does feel like it.
Regards
Sokol

---

### Post by andrew.46 on 2008-12-11
Hi!

> **sn0m said:**
> 
could I kindly ask you guys to post your crontab -l output so I can compare them to mine.

This is the cron I use for my ftgws script:

```
andrew@skamandros~$ crontab -l
# Runs the live-to-air ftgws script:
30 22 * * sun /home/andrew/bin/ftgws_download.sh
```

Hope this is some help,

  Andrew

---

