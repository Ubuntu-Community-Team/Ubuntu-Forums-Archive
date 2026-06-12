---
title: "CD Rom Automounting in Ubuntu Server"
date: 2009-06-02
forum: General Help
---

### Post by ejcdke on 2009-06-02
I decided to go 100% terminal on my home server and I setup Ubuntu Server.  I have everything working great, but I wan the CD/DVD Rom drive to automount upon disk insertion, and unmount when I push the eject button, exactly what happens in Ubuntu Desktop.  My ultimate plan is to setup automatic CD/DVD ripping that occurs when I insert the disk.

I tried using autofs, which I got up an running, but I can't seem to figure out how to make it work with my automated ripping goals.  At this point, I wish I could setup whatever Ubuntu Desktop uses for automounting in the command line.  Any ideas?  I've been digging through web pages for the past week but I didn't see anything major beyond "autorun" at [http://sourceforge.net/projects/autorun/](http://sourceforge.net/projects/autorun/) but it appears to be a dead project.  Thanks in advance for any advice.

---

### Post by upbeat.linux on 2009-06-02
Can you edit /etc/fstab and add an entry for your cdrom device?  After that reboot and see if it mounts.

---

### Post by ejcdke on 2009-06-02
I just SSHd into the server and pulled up the fstab and see that it reads:

```
/dev/scd0 /media/cdrom auto ro,noauto,user,exec 0 0
```

Would the "noauto" mount option be the problem?  It is my understanding that using the "auto" mount option would mount the drive at boot-up, which one would want for a hard drive.  Since this is a DVD drive, it might not have a disc in it a boot up and thus shouldn't be mounted.  I guess I'm a little confused as to how auto/noauto works in terms of a DVD drive.

---

### Post by upbeat.linux on 2009-06-02
Sorry. You are correct auto-mount wouldn't help mounting the CD/DVD drive when a disc is inserted.

autofs seems like your best bet. how are you trying to rip from the cd/dvd? do you have a script to post here?

---

### Post by cariboo on 2009-06-02
I'm running Jaunty server, and the cd's automount on insertion. There isn't any notification though, so you still have to cd into /media/cdrom.

---

### Post by ejcdke on 2009-06-02
I knew I missed stating something... I'm using Server 8.04 LTS.  I would use Jaunty, but I built a multipurpose box with OpenVZ that runs a few containers to handle wbserver, media server, and Asterisk duties, along with one container I can experiment in without fear of shutting down Asterisk.  If Jaunty automounts, I might do an install into a VM on my laptop to see how it works before I proceed.

My plan is to run a script and funnel the CD ripping through ABCDE, [much like this post on the hydrogen audio forums.]("http://www.hydrogenaudio.org/forums/index.php?showtopic=17100")  I haven't actually scripted anything yet as I'm still looking to nail down the automounting of the drive.  I have autofs running fine, so I'm starting to think that I might as well keep the autofs solution and map script execution to a keyboard button.  That way ripping is still nice and easy, and will not require a monitor (and my wife can use it too).  I will use HandBrakeCLI for the DVD ripping.  

I'll be sure to post whatever I end up doing so that others might benefit.  Thanks for the Info.

---

### Post by ejcdke on 2011-01-25
I've recieved a few PMs about this thread recently.  Unfortunately, I lost all my work in The Great Seagate Hard Drive Failure of 2010.  Even my backups died.  I learned an important lesson that day.  I really don't need the feature anymore, so I never rebuilt my work.  I'll provide some of my sources to at least give some people a starting point.

First, there is no rock solid solution.  Everything has to be done with bash scripts.  I mapped all my scripts to keyboard commands. Pressing F1 launched a CD ripper, F2 launched a movie ripper, F3 launched a Movie with subtitles ripper, and F4 launched a TV show DVD ripper.  The TV show option didn't work well at all and I just resorted to manually ripping these things.  I could probably have gotten DVD movie ripping down to one key, but I didn't have much time to toy with the scripts.

First, if your CDs do not automatically mount, then install Autorun at [http://sourceforge.net/projects/autorun/](http://sourceforge.net/projects/autorun/)

If you don't care about DVD ripping, then skip autorun and follow these instructions [http://sudocode.blogspot.com/2009/06/auto-rip-audio-cds-in-ubuntu-server.html](http://sudocode.blogspot.com/2009/06/auto-rip-audio-cds-in-ubuntu-server.html), otherwise, setup autorun and read on.

I'll start with CD ripping.  Install ABCDE via [http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html) and follow some of the instructions at [http://www.hydrogenaudio.org/forums/index.php?showtopic=17100](http://www.hydrogenaudio.org/forums/index.php?showtopic=17100).  Both these sites combined should get you up and running.  

Develop the command you want to use to and then create a bash script to launch that command.  Once you have your script setup, make a hotkey for the script using the instructions at [http://linuxgazette.net/issue55/henderson.html](http://linuxgazette.net/issue55/henderson.html).  You can set any key to invoke the script.

For DVD ripping, install the Handbrake command line interface.  Setup separate scripts for each type of handbrak command you might want to use and then map those to a hotkey as well.  

There may be other new options out there, I'm not sure, but this is what I ended up doing.  It worked well and I was able to have my wife sit by the computer and rip all her CD's just by hitting F1 for each disk.  It was great.  She then did the same for her movies.  I had to manually rip the TV shows since that was just too much of a pain to script out given that each show disc could be very different from the last, but that was much less work than ripping her whole colleciton of CDs and DVDs.  

If I end up with more info from working with the people who PM me, then I will post it here.  If anyone has any thoughts on the topic, feel free to share--it was a fun little project at the time.

---

