---
title: "Ubuntu 16.04 Hanging Intermittently on Boot After Update"
date: 2017-11-25
forum: Desktop Environments
---

### Post by mongo42 on 2017-11-25
Hi all,

I am somewhat new to the whole Linux thing (I got fed up with dealing with Microsoft), so I am just a little lost.  I have been using Ubuntu 16.04LTS for a couple of months flawlessly, and just recently, presumably after an update to the kernal and video drivers, started to experience an occasional hang when booting the system.  It does not happen all of the time (about every 5th boot), and after the boot sequence is finished it is solid as a rock.  When it does happen, my only recourse is to hard boot, which leaves a whole bunch of orphaned files (which are cleaned up on shutdown).  The hang is sometimes on the Ubuntu splash screen, but more often it happens a couple of seconds after I enter my password and my desktop is loading (in which case, the screen becomes completely unresponsive, and I have to hard boot).  The below is about all I know to do for keeping things clean, and I have no idea what I am looking for in the logs (I think I can find where it happened, but cannot interpret the errors):

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get clean
sudo apt-get autoremove
```

I would be happy to post log files here, but I have no idea which ones are relevant.  Please help!

My setup:
Gigabyte Aorus  GA-Z270X-Gaming K7
32GB RAM
NVidia GeForce GTX 1050Ti
Ubuntu 16.04 (kernal 4.10.0-40-generic)

---

### Post by DuckHook on 2017-11-25
Welcome to the forums, mongo42.

Your posting instincts are admirable with enough info to go on from the beginning. The only thing I did was add [noparse]```
 and 
```[/noparse] tags to your output for clarity.

A few things that will help next time:

[LIST=1]
[*]If a hang occurs, try <Ctrl>+<Alt>+<F1> to get to a shell session. From there, you can try to log in and shut down properly with:```
sudo poweroff
```
[*]If everything is completely unresponsive, try the REISUB method to shut down cleanly. Explanation is here: [https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[*]
[*]To see what process is creating the hang during boot, disable the splash screen by pressing <ESC> during boot. You should now see all of the boot processes roll by. Note the hanging process. Personally I don't like the splash screen at all because I don't like my boot process to be hidden, so I disable the splash screen permanently in GRUB.
[*]
[*]Log files are difficult to interpret even for experts. If you have an idea of what events are causing the hang, then post those specific lines to this thread and hopefully some guru will help. To preserve their formatting, please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.
[*]
[*]If you don't know what the cause of the hang is, then guesstimate a time and post the output of syslog from roughly those time periods.
[*]
[*]The usual method used to hunt through log output is to filter it through grep, looking only for lines with keywords. Example:```
egrep -i 'error|warn|fault|fatal|fail' /var/log/syslog
```This chops the output down to somewhat more manageable proportions. You refine the search by adding/subtracting search terms between the two apostrophes.

The log files to look at are syslog kern.log and dmesg. They are all located in /var/log You can pipe the output through *less* or to a file for easier analysis. Since you should know the specific time that the hang occurs, it shouldn't be too hard to narrow down the lines that are the culprits.
[/LIST]
Give all of that a try and post back the output.

---

### Post by mongo42 on 2017-11-25
Thank you for your direction, DuckHook...:)  It has only hung a few times on the splash screen, and when it does not I don't see it anyway (well, maybe a flash).  My system drive is an SSD, so it goes by real fast anyway.  Most of the time it hangs after the desktop is loaded (or still loading?), within a few seconds.  In other words, after the desktop is displayed (post-password entry), a couple of seconds later everything just freezes...?!?  I know that does not make whole lot of sense, but is there a way I can look at what process is holding things up at that point?  If I can get to a command line (<Ctrl>+<Alt>+<F1>), how would one recognize the hanging process using 'ps'?  And, as I said, it is intermittent (the browser I'm typing on is on the Ubuntu box, so it's working fine this boot).  I will try your suggestions next time it happens and get back to you, along with any log entries I can identify.  Thanks again!

---

### Post by DuckHook on 2017-11-26
> **mongo42 said:**
> …how would one recognize the hanging process using 'ps'?
If you can actually get to a working shell session, then the best way to see what is using up cpu cycles (for example) is not *ps* but *top* or *htop*.

---

### Post by mongo42 on 2017-11-28
OK, it happened again this morning (it hung while the desktop was loading post-password entry).  As suggested, I hit <Ctrl>+<Alt>+<F1>, which brought up a command line.  I was then able to shut down the system gracefully, and bring it back up (which showed no problems...?!?).  To my pedestrian mind, this presents two possibilities:

Door #1) The X-Window was shut down completely, leaving me at a command line, and a 'top' showed nothing out of the ordinary (no processes seemed to be hogging the CPU)
Door #2) The X-Window was still frozen in the background, and a login shell was created.  Since 'top' showed nothing amiss, the frozen GUI was "stuck" and could not continue to load.

Both of these conclusions point to the problem being the GUI, since I had complete responsiveness once in the command shell (this tells me that the kernal is not the bad guy).  Beyond that, I have no idea how to trouble-shoot further.  A friend at work suggested that it is the X-Server that is acting wonky (remember, this is intermittent), and that anytime a kernal is updated the X-Server should be updated as well. Since I now have a workaround for the occasional freeze (after the desktop is finished loading, everything is rock-solid), maybe a forthcoming update might address the problem...?  I will post back next time with log snippets if the problem persists.  Any suggestions as to further trouble-shooting?

---

### Post by DuckHook on 2017-11-29
You've really got to give yourself more credit. It's hardly pedestrian for a two-month user to demonstrate the Linux-savvy that you've already shown.

The strong likelihood is Door #2, though we can't rule out #1 and perhaps a hidden door besides. I wish I could be more definitive, but that's the simple truth of the crazy arcane Linux world.

Since you've shown admirable versatility with the command line for one so new to Ubuntu, here are command line instructions that I think you can easily master. Print out this post if you have to, so that you can refer to it in the absence of a desktop.

What we're trying to do is read some logs from the command line while your desktop is "frozen". The command to do this is simply:```
dmesg
```…but you will need to take special measures to record its output so that you can post it here after you successfully get to a desktop session. The easiest way is to output *dmesg* to a file that can then either be attached to your next post or just copy-&-pasted into a [noparse]```
[/noparse] box. *dmesg* output tends to be big, so an attachment is probably best. To pipe it into a file and put the file on your desktop, do:[code]dmesg > ~/Desktop/dmesg.txt
```This will output a file called dmesg.txt on your desktop that should contain all the output from *dmesg*.

You may wish to look at *dmesg* now, just to familiarize yourself with it and to know what to expect. You can run it in a terminal session and prevent it from scrolling by like lightning with:```
dmesg | less
```Piping it through *less* will let you view it one page at a time. It's a record of most of the processes that are occuring on your system since boot. Therefore, we would be interested in the last few lines since these presumably were generated just leading up to the hang. Please do it right afterwards because we don't want too many other processes added to it after the hang.

It may also be worthwhile to have a look at *syslog* now, instead of waiting for the next hang. This is the log that captures most of what *dmesg* does, but whereas *dmesg* only lasts for that session, *syslog* is actually written to your log files and sticks around between reboots. It's harder to read though because it runs together a number of boot cycles. The command to read syslog is:```
less /var/log/syslog
```You can also use the graphical Gnome log reader built into Ubuntu called "System log". Be prepared for an eyeful.

---

### Post by mongo42 on 2017-12-03
Well, I made it 4 days without a problem, but it just hung again.  Restarting with Your instructions is a lifesaver, but I would like to fix the problem once and for all. I attached a truncated version of the dmesg file from the incident (the forum tells me that the size limit is 19.5kb, whereas the dmesg file is 62.5kb).  Hopefully, it will shed some light as to what I am doing wrong...

[ATTACH]277728[/ATTACH]

---

### Post by DuckHook on 2017-12-04
Nothing jumps out from your dmesg report, so I want to confirm that this is the dmesg report from your failed login session and not one that you generated after recovery.

If above assumption is true—that this report is from the proper session—then wait for next freeze-up and from a shell session generate the following report:```
journalctl > ~/Desktop/journalctl.txt
``````
cat xsession-errors > ~/Desktop/xsession-errors
``````
cat xsession-errors.old >> ~/Desktop/xsession-errors
```…making sure that the last command contains double greater-than signs to append output to the file instead of replacing it.

Also, let's try resetting your Xauthority right now:```
rm ~/.Xauthority
```…then reboot. The system should generate a new .Xauthority file. This one is a long shot, but worth trying because it does no harm. As an aside, the *rm* command completely deletes a file and must be used carefully. When working on the command line, Linux assumes you know exactly what you are doing and will not ask for further confirmation.

---

### Post by mongo42 on 2018-01-01
Well, since my last post, it has happened twice, and always on starting the GUI (not on shutdown).  Weird thing is that neither time the <ctrl>-<alt>-<F1> combo would get me to a login prompt.  Both times, the screen just blanked, and then the monitor would go to standby, as if no signal were being sent.  All the while, the computer hardware keeps on truckin' like nothing happened (judging from the mother board status code).  Since I could not get a shell to come up, I had to hard restart both times.... I could not get the logs from the frozen session.  At this point, I am thinking that if I can get the System Monitor up before the freeze, it might show what process is hanging the system.  I will continue to try to get the reports you specified next time it freezes.  Thanks again for your help!

Oh, what directory does the "xsession-errors" file live in?

EDIT: I found the xsession-error files (they are hidden in the user directory).  I have attached the xsession-error report (even though they are from a different session, I grabbed them right after the reboot?)  I will attempt to get them from a command shell next time it hangs.

[ATTACH=CONFIG]277998[/ATTACH]

---

### Post by mongo42 on 2018-01-12
Just happened again, and this time I was able to open a command shell and get the docs you asked for (I had to zip them for size):

[ATTACH]278165[/ATTACH]

Thanks!

---

### Post by ragazzid on 2018-01-15
Hey, it may sound crazy but happened to me, do you mind checking your `/etc/fstab` and see if you swap partition is being mounted correctly?

---

### Post by mongo42 on 2018-01-22
Sorry for the delay.  I checked my fstab file, and all seems to be in order. When I initially modified the fstab to add several external partitions to automount on boot, I made a small error in the UUID.  Needless to say that the whole thing would not boot at all (I had to boot from the install disk, change to root, mount the main partition, and fix the fstab).  Everything boots fine 99% of the time, and the remaining 1% appears to be at random...

---

### Post by mongo42 on 2018-01-25
... and another one...;)

[ATTACH=CONFIG]278325[/ATTACH]

---

