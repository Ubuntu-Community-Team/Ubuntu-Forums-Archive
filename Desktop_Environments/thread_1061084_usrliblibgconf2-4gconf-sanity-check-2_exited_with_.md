---
title: "/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with error status 256"
date: 2009-02-05
forum: Desktop Environments
---

### Post by laket on 2009-02-05
I hope someone can help out:

after upgrading to ubuntu 8.10 64 platform when I login I get this error:

**/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with error status 256**

and afterwards nothing happens...

I created another user on the command-line and the new user logs in w/o a problem, but my old user with all my preferences, emails etc. stays locked out :(

---

### Post by Vadi on 2009-02-05
Some setting got messed up badly.

I'd copy over your data to the new user.

---

### Post by laket on 2009-02-09
> **Vadi said:**
> Some setting got messed up badly.

I'd copy over your data to the new user.

sure that's the easy way....
interesting would be to understand what went wrong and how to fix it...
thx anyway

---

### Post by ivotedforkodos on 2009-04-10
Has anyone figured out what the actual problem is? I get this message every time I start up, but after I click through, I don't seem to have any further symptoms. 

However, my problem is NOT the permissions problem identified here:

[http://ubuntuforums.org/showthread.php?t=917306&highlight=sanity-check](http://ubuntuforums.org/showthread.php?t=917306&highlight=sanity-check)

Any ideas?

---

### Post by Vadi on 2009-04-10
Try executing

> /usr/lib/libgconf2-4/gconf-sanity-check-2

In the terminal. Does it say anything?

---

### Post by ivotedforkodos on 2009-04-11
Nope. It doesn't say anything. How can I find out what the error is? Does anyone know what error status code 256 implies?

---

### Post by Vadi on 2009-04-11
I'm not sure. I looked at the *gconf-sanity-check.c* file, and it does not return 256 anywhere.

I did this this FAQ though, see the "Some other weird thing is wrong with my gconf!!!" section.

After we solve this, a bug report is definitely due.

---

### Post by stereobroo on 2009-05-03
Hi

I just did chmod 1777 /tmp and gnome rocks again ...

---

### Post by reisrocks on 2009-05-03
> **stereobroo said:**
> Hi

I just did chmod 1777 /tmp and gnome rocks again ...

Thanks stereobroo that fixed it for me

---

### Post by crowdedelevator on 2010-01-05
> **stereobroo said:**
> Hi

I just did chmod 1777 /tmp and gnome rocks again ...

 So can anyone explain chmod 1777 /tmp to me? I have the error when booting up 9.10, and im a noob. Maybe this will help. Im desperate to get this done NOW as I have been at this for days. I don't have internet other than my p.o.s. Cell phone, so can anyone help? What do I do?

---

### Post by falconindy on 2010-01-05
1777 implies read/write/execute for everyone on the system. However, when applied to a directory the '1' prefix implies that only the directory owner and group are able to rename and delete files. This is important in a multi-user environment where many users have open files in /tmp.

---

### Post by crowdedelevator on 2010-01-05
Darn, I don't think that'll help me at all... i m a single user on a laptop. But I got 9.10 and had the .ICEauthority error, and fixed it but I had an issue with this as well, and im trying to figure this out. I don't know how to fix it and don't know what to do, where to go or what to type. Im new to all of this and really want this fixed. I don't know how to use commands or what they are. So that makes this difficult for me.

---

### Post by itomatik on 2010-02-04
> **stereobroo said:**
> Hi

I just did chmod 1777 /tmp and gnome rocks again ...

Helped me too! How come? This is madness :D

---

### Post by firey205 on 2010-02-04
This worked for me too.

I think that the /tmp file holds some locking files. Because gconf can't break the lock, it fails. Resetting the permissions means gconf can update the locks and continue as normal.

An "ls -la" in a console will show you all the files in the directory.

---

### Post by nima101 on 2010-02-14
Sometimes, if you try to build a whole project, which you might have taken over the web, if you just run a script -provided in the pack- with superuser privilege to that script it might do anything to your system! such as copying files over the filesystem, changing the permissions, ...

Since this was the reason I got this error, and it is a common mistake to me, I just wanted to let you know about that.

So, be careful about scripts over the net, and read their instructions carefully before running them. (just in case)

---

### Post by scott_m_mil on 2010-02-26
Fixed me up too!

Crowdedelevator: in order to access a terminal you have to select the recovery mode option from grub when the machine boots up.  Then select the terminal option when prompted.  From there you can navigate to the root directory. I believe you should only have to type "cd .." then type "chmod 1777 /tmp"  then reboot and cross your fingers.

Scott

---

### Post by Luke Fleeman on 2010-04-07
So, I also had this problem. 

I had run a picture recovery program that filled my hard drive completely. Then it crashed. When I rebooted, I got this error. So if your problem was created by too much space being filled, this might work, because nothing else did for me.

First, I used a LiveCD I had to "try ubuntu without changes" and when I got in, I used nautilus to go into my hard drive and clear space. I could not trash it though. so I used recovery mode in GRUB, and ran "startX" from the terminal. At that point, I could empty the trash, which freed space, which then fixed it all when i rebooted.

---

### Post by amaresh_83 on 2010-04-08
i faced same problem .. by doing  chmod 1777 /tmp/ .. 

now working fine... 

thanks,
-amaresh chandra Das
[www.eodissa.com:popcorn:](www.eodissa.com:popcorn:)

---

### Post by muddysmind on 2010-06-06
> **reisrocks said:**
> Thanks stereobroo that fixed it for me

worked for me as well thanks!

---

### Post by davitodd on 2010-06-17
> **crowdedelevator said:**
> Darn, I don't think that'll help me at all... i m a single user on a laptop. But I got 9.10 and had the .ICEauthority error, and fixed it but I had an issue with this as well, and im trying to figure this out. I don't know how to fix it and don't know what to do, where to go or what to type. Im new to all of this and really want this fixed. I don't know how to use commands or what they are. So that makes this difficult for me.


What I did for that error was just login, and change the permissions for everyone to read and execute the file.

---

### Post by Peopleunit on 2010-06-26
I've run up against this error on my system as well as the one regarding .ICEauthority.

I was going through the programs I have installed on my system (I'm running 9.10 Karmic), installed a few, and removed a few that I thought might be unnecessary. I didn't make a complete list of those I added and removed but after rebooting I got the errors but am able to continue on normally after selecting close on the error messages.

One of the programs I remember removing was the legacy version of GDM, and after reading this thread I looked to see about finding that folder and sure enough, I don't even have that folder anymore.

I also took another gander at what programs are on my system now and it looks like the full version of GNOME has been uninstalled, yet the program called core essentials of GNOME still remains. I did remove most all the defailt GNOME games related stuff.

I'm thinking that if I reinstall the full GNOME desktop, and then if needed, the legacy version of GDM, things might return to normal, no error messages.

FWIW, when I initially installed Karmic, at first I had issues with GRUB but was able to boot using the recovery option. After installing some of the later updates, that issue seemed to have resolved itself and I was able to select the latest 'normal' version from GRUB.

Initially, I also had quite a bit of difficulty with my video display, being limited to 800x600 with no options found to change it. I beat my brains out trying to resolve that issue, only to find that Intel appears to have ceased providing Linux driver updates for the Intel video chip on my system. Once again, after some time, and after keeping up on the updates, that issue seemed to have been resolved, at least partially, as now I can change my video resolution, but I seem to be stuck using 1280x1024 since now I can't change the refresh rate. That's ok though, I'm happy with 1280x1024. At least its working, and I have good resolution. I don't know that mt video drivers support SGML(?) though.

[COLOR="Blue"]Anyway... I decided to make a post on here, in case reinstalling the complete GNOME desktop and legacy GDM don't fix the errors, before changing the permissions on /tmp, would someone who HASN'T experienced these errors please check the existing permissions on that directory?
[/COLOR]
It seems to me that changing the permissions to 777 might pose a security issue. On a single user PC, it seems to me that 755 permissions might be more appropriate. Thoughts?

---

### Post by afrodeity on 2010-07-15
Not sure about the 777 vs 775 debate. But i've chown'd and chmod'd my home directory to no effect whatsover, also my tmp file.

Think I might have accidently purged the configuration of the config server. Its looking for /var/lib/gdm/.ICEauthority which doesn't exist (no gdm folder). I only have a .ICEauthority in my home folder.

How does one go about reconfiguring the configuration server? Do I have to recreate /var/lib/gdm/.ICEauthority?

---

### Post by jpl888 on 2010-07-15
FYI afrodeity sorted out the missing /var/lib/gdm/.ICEauthority by reinstalling gdm.

---

### Post by afrodeity on 2010-07-15
Hi jpl888,

Beat me too it. Yep, I sorted out the weirdness.

```

sudo chmod 775 /etc/gconf*

sudo apt-get install --reinstall gdm

```

---

### Post by sergut on 2010-08-09
> **crowdedelevator said:**
> So can anyone explain chmod 1777 /tmp to me? 

Just to add a little to what falconindy said... The first 7 means that root can read, write to, and access (execute) the /tmp directory, and the last 7 means that anyone can read, write to, and access (execute) the /tmp directory. 

If some application that is not running as *root* tries to write temp files in /tmp, they need both access and writing permissions (which means giving those permissions to everyone... hence the last 7). Otherwise, the app will complain. 

HTH. For more info, have a look at the manual page for chmod (also typing 'man chmod' in a console): 

[http://www.manpagez.com/man/1/chmod/](http://www.manpagez.com/man/1/chmod/)

;)

---

### Post by sitex on 2010-09-23
Hi,:)
[SIZE=2]me too faced to this error message.
And I could fix it with renaming a file ..

I boot my PC with Fedora 13, then I could not boot my PC with my Ubuntu 10.04 hard disk[/SIZE] [SIZE=2]

So I logged as root and I notice there is an another new file in my file  system (on root "/") with the name "core"[/SIZE] [SIZE=2]
so I renamed It to  "backup_core" and Then Restart the mechine..

Then Everything was  OK. and I could log to my current user account with out any trouble [/SIZE] [SIZE=2]

[You can see the Full story with the site Solutionz.yolasite  by clicking here]("http://solutionz.yolasite.com/linux.php")[/SIZE]

---

### Post by arvin555 on 2011-01-13
Just encountered this problem with my PC running Karmic.
was downloading a large file and it left me with only 50mb of disk space, and I read that this might be a cause for this problem, I think it might be.

Booted up in recovery mode, I was given a choice to free up space, pressed okay and nothing happened, so for good measure I used terminal to run the chmod1777 /tmp suggested.

Rebooted and all was well!
I then found out that i got only 50mb of space, so I started deleting unwanted stuff.

So maybe, I can confirm that one culprit is very very very low disk space, so to avoid this please don't run your drive to full capacity :)

TTFN
Arvin

---

### Post by cmwslw on 2011-01-24
I also had this problem. I don't know if it was the update I did a few days ago or what but the 'chmod 1777 /tmp/' definitely did the trick for me. I was downloading some fairly sizeable files yesterday but nothing huge. And I have 40GB of free space so it can't be that either.

---

### Post by swdinesh on 2011-02-07
I had the same problem after an upgrade for chromium and installting the 
Canon Pixma printer. Definitely the 1777 mode set to /tmp solved the problem for me.
I'm on Maverik 64bit

---

### Post by Astley on 2011-02-08
Out of the blue, I couldn't log in to my desktop with all my data inaccessibly encrypted...

Talk about a scare :)

Tried the things out of this thread, this worked for me:

from r-x------ to rwx------

sudo chmod 700  /home/me


"There's your problem, or at least part of it.  Your home directory is  rw-r--r--  should probably be rwx------  Try this: 'sudo chmod 700  /home/me' as root.  You must have execute permissions on a directory to  be able change into it or any of its subdirectories... or 'sudo chmod  o+x /home/me'"

[http://www.linuxquestions.org/questions/linux-newbie-8/locked-out-of-ubuntu-desktop-by-permissions-error-799626/](http://www.linuxquestions.org/questions/linux-newbie-8/locked-out-of-ubuntu-desktop-by-permissions-error-799626/)

---

### Post by Astley on 2011-02-08
> **Astley said:**
> Out of the blue, I couldn't log in to my desktop with all my data inaccessibly encrypted...

Talk about a scare :)

Tried the things out of this thread, this worked for me:

from r-x------ to rwx------

sudo chmod 700  /home/me


"There's your problem, or at least part of it.  Your home directory is  rw-r--r--  should probably be rwx------  Try this: 'sudo chmod 700  /home/me' as root.  You must have execute permissions on a directory to  be able change into it or any of its subdirectories... or 'sudo chmod  o+x /home/me'"

[http://www.linuxquestions.org/questions/linux-newbie-8/locked-out-of-ubuntu-desktop-by-permissions-error-799626/](http://www.linuxquestions.org/questions/linux-newbie-8/locked-out-of-ubuntu-desktop-by-permissions-error-799626/)


hmm celebrated too soon, able to log in, data in home dir  is still gone :(

---

### Post by marcelloconti on 2011-04-29
Wow, works fine.

"chmod 1777 /tmp"

---

### Post by LatterDaySaint on 2011-05-01
The Answer seems to be "chmod root:root /tmp && chmod 777 /tmp" .
I got this from LaunchPad when I had same error & it worked for me & others by the look of it.
Thought I would give an answer to this thread incase some one comes across this on their search for this problem as I did.

---

### Post by Maheriano on 2011-05-23
I had a different solution. I had just installed Zoneminder which does webcam recording based on motion detection and it had filled my hard drive to capacity. I booted into the command prompt, entered /usr/share/zoneminder/events/main and deleted everything in there. Rebooted and I was fine again.

I got all the exact same error messages everyone else got before that too.

---

### Post by EKa on 2011-06-05
I have this classical problem with 11.04 and tried most of the suggested solutions.  I installed Ubuntu besides XP on Samsung 110 minilaptop.

Are there any precise instructions for a solution? Anyone?

---

### Post by nulty on 2011-06-22
Hey folks!

I have slipped into the unenviable position of posting in this thread. Only problem is I'm sure my problem is more complicated than others. I reinstalled Maverick in partition with Win7 and have */root*,* /home* and *swap *partitions. Currently I'm struggling to get */root *to recognise* /home* on my other partition. 

I'm getting  a blank Desktop with just the wallpaper. Access to ALT-F2 and thus nautilus and bash through that. 

My errors are 

> Could not update ICEauthority file /home/user/.ICEauthority> There is a problem with the configuration server.
(/usr/lib/libconfig2-4/gconf-sanity-check-2 exited with status 256)> 
Nautilus could not create the following required folders: /home/user/Desktop, /home/user/.nautilus. Before running nautilus, please create these folders or set permissions such that Nautilus can create them.The problem arose when I decided to dual boot with Win7 again and tar.gz'd a backup of my old Ubuntu installation (also 10.10) which causes the problem. I've dug through quite a bit of it but I reckon getting home connected to root will solve at least two of the issues.

Hope this gives someone else an idea of their own issue.

---

### Post by nulty on 2011-06-22
I think I just knocked em all down with one fell swoop thanks to this guy and the guy who originally posted it. :

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Nulty 1-0 Ubuntu

---

### Post by earlf on 2011-07-13
It seems like there are variants of this error message.

[[COLOR="Blue"]Launchpad bug #577545[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/577545") in some cases is just an annoying alert menu, while others causes login problems.  [[COLOR="Blue"]Bug 269215[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/269215") has information on various situations where and how the bug occurs. 

For more precise solutions, check if these bug reports offer anything quite similar to your setup/occurence. 

I'm still looking for my fix!

---

### Post by drwatson_droid on 2011-08-05
> **stereobroo said:**
> Hi

I just did chmod 1777 /tmp and gnome rocks again ...
thanks a lot.. it worked like a charm..

---

### Post by timdtz on 2011-08-24
the problem might be encryption of the home directory and auto-login.

cf [http://ubuntuforums.org/showthread.php?t=1694482&page=4](http://ubuntuforums.org/showthread.php?t=1694482&page=4)

---

### Post by searchfgold6789 on 2011-10-04
Hello,
I have added [this problem to the Error Message Wiki]("http://errormessage.wikia.com/wiki//usr/lib/gconf2-4/gconf-sanity-check2_exited_with_status_256"); if anyone wants to add their solution for the general benefit of others, or add technical details about the problem that would be great :D
 - search

---

### Post by hwertz on 2011-12-06
In my case, I had downloaded a file or two to Download instead of /mnt/external/ .  My disk was 100% full.

---

### Post by gorsebush on 2011-12-15
Perhaps my experience with this same error message might help someone more capable than me solve the problem....

I operate Ubuntu 10.04, with two user set-ups - one for administrator, and one for general family use (user).  Somewhere along the way I lost the Network manager icon from the user desktop.  It was not a major problem but recently I started having to log in as administrator to re-enable networking which became a nuisance.  I had never  figured how to restore the network manager applet to the user taskbar.  A couple of nights ago I decided to "fix" the problem and cut the gconfig; config; and configd folders from the  user files, and cut and pasted the equivalent folders from the admin settings. ... rebooted and got the same error message as cited above and cannot now start my computer unless I insert a live C.D. and enter using the "demo" mode.
I can access most of my files by using a live C.D. but many are restricted access and I'm not at all sure how to proceed.  I am not proficient with using the terminal and find the help information hard going.:confused::confused:
I should add that the actual error message reads "There is a problem with the configuration server (/user/lib/libconfig2-4/config-sanity-check-2 exited with status 256)"

---

### Post by bigdawg on 2011-12-16
Thanks Stereobro......your solution resolved this error on my server as well.  Cheers!

---

### Post by vinicius3163 on 2012-04-17
Hi, I run a server using ubuntu 11.04 and no one is able to log to their accounts. None of the previous solutions here worked for me. Hope you guys can help me out.
Thank

---

