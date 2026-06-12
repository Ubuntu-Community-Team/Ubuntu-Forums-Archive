---
title: "Audacity problem"
date: 2004-11-29
forum: Desktop Environments
---

### Post by Arbiter on 2004-11-29
I'm trying to run Audacity.  The first time I started the program, it started fine and went right through the initial setup procedure fine.  I used the program perfectly fine, then after I rebooted the machine it gives me an error message "there was an error initializing the audio I/O layer, you will not be able to play or record audio  Error : Host Error"

It gives me this problem when I try to run the program as my regular user, but no problem at all when I run it as root using sudo.

Any help would be greatly appreciated.

---

### Post by wulf on 2004-12-18
Any thoughts on this one? I'm experiencing a similar problem. Audacity works fine when run from the command line but throws up the same error mentioned above when run from the menu icon I set up.  :-k 

I'm not even running it using *sudo* but from my normal user account. Using the CLI is not the end of the world but I'd prefer to keep things a bit neater.

Any ideas?

Wulf

---

### Post by john280z on 2004-12-18
Same here, Audacity runs OK from the command line (non root terminal), runs OK from File Manager, gives me the "initialize audio I/O" error when run from the menu icon.

Thanks,
john

---

### Post by wulf on 2004-12-18
Nice to know I'm not alone ;)

If there's no obvious answer, perhaps a bug-report could be filed. In some ways, it's a minor thing but all these little bits will make a difference in people's experience of Ubuntu and whether they're likely to stick around.

Wulf

---

### Post by crun on 2004-12-18
I had the same problem - what helped for me is to turn off the ESD sound deamon:
 
 $ killall esd
 
 and then restarting Audacity. Hope this helps for you guys.

---

### Post by wulf on 2004-12-18
I've written a little script to kill off esd, run Audacity and then, when Audacity is closed, restart the ESD daemon. It seems to run okay when launched from the menu but I'll see how it works next time I reboot!

Cheers,

Wulf

---

### Post by john280z on 2004-12-18
The "killall esd" (run from a user terminal) allows Audacity to run normally on my install.

john280z

---

### Post by wulf on 2004-12-19
Here's the script I'm using:
```
#!/bin/bash

killall esd
sleep 3  # To give the previous command time to fully complete
/usr/bin/audacity
esd
```I've saved it in my personal program directory (*~/bin* - I set this up when I install a new Linux and add it to my PATH to provide a convenient home for all my scripts) and given it executable permissions. This is the file called by my menu icon and seems to work smoothly.

Wulf

---

### Post by lukem on 2004-12-19
Happened to me too!  It happened right after I installed lame, so I uninstalled lame and no luck.  Next I reinstalled Audacity and still no luck.  Works ok from a user terminal though.

---

### Post by wulf on 2004-12-19
Try my little script and see if that does the job.

Wulf

---

### Post by lukem on 2004-12-19
Thanks Wulf, your script works fine.  Still a little annoyed that a work around is necessary, but it's lots better than not working.  I'll keep digging.
Thanks again.

---

### Post by wulf on 2004-12-20
[QUOTE=lukem]Thanks Wulf, your script works fine.  Still a little annoyed that a work around is necessary, but it's lots better than not working.  I'll keep digging.[/QUOTE]
That is a good idea. I'd like to understand why you can run it from the command line without worrying about ESD whereas it becomes an issue from the menu. I think I have the same problem with gxine; I haven't checked properly but (without paying too much attention) I noticed on Saturday night that I didn't get sound when I used my menu item but it did work when I ran it from the CLI. It could have been something else or a one off blip but it may be related (in which case it probably affects lots of other programs as well).

Obviously, that involves some reading (what does ESD do?) and some observation (what processes are running? how does it change when I run a program from the menu or the CLI?) but it will be easier if there are a few of us working on it!

Wulf

---

### Post by lukem on 2004-12-21
Found a very interesting post on a problem with not being able to use sound for more than one app at a time.  Located at:

[http://www.ubuntuforums.org/showthread.php?t=8235&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=8235&highlight=sound)

This was on page one - post #9-  and rather than stopping esd, the idea was to make sure everything was using it.  

still got a long way to go!

L

---

### Post by wulf on 2004-12-21
Yes - that looks relevant. Well spotted!

Wulf

---

### Post by lukem on 2005-01-02
Well Wulf, I think the script is the only way to go.  I've been searching for a week and finally found this at the bottom of an Audacity web page.  

[http://audacity.sourceforge.net/unix.php](http://audacity.sourceforge.net/unix.php)


"Are you using a soundserver like aRts (commonly found with KDE) or esd (commonly found with GNOME)? If so, you will need to kill it first before using Audacity! Example:

killall artsd "

So that's it I guess.  Thanks for your help and have a great year.  Let me know if there is a link where I can hear your bass.

[email]lukem10@adelphia.net[/email]

---

### Post by wulf on 2005-01-02
[QUOTE=lukem]So that's it I guess.  Thanks for your help and have a great year.  Let me know if there is a link where I can hear your bass.[/QUOTE]
Isn't it amazing how everything you want to know is already written down... it just takes time to find it! :D 

I haven't really done much with Audacity yet - my musical efforts have been concentrating more on playing around with Lilypond.

BTW, you can hear my playing on MP3 files at both the band websites given in my signature - the stuff on the Lovesjones site is all that bass, while the ET website features a range of instruments. :D

Wulf

---

### Post by viuks on 2005-01-30
Hmmm... I did it wery simply. Just added permissions.
```
# chown viuksi /dev/dsp
# chmod 666 /dev/dsp
``` 

And then I can Audacity easy from any shortcut

---

### Post by Darren Crotchett on 2005-02-07
Interesting.  

I haven't tried rebooting or logging out and back in after changing the permissions of /dev/dsp.  But, the killall esd did solve the problem I was having with Audacity and Skype.  Skype would sit there and look like it was connecting.  But, nothing would ever happen.  Audacity would give the same errors as indicated above.  Yet, my music player would work fine.

If anyone reading this thread happens to have a better explanation, I'd be interested in hearing it.

I'll be curious to know if changing the permissions fixes my problems with starting the programs from icons as opposed to typing them in from the terminal.

BTW, the sound problems didn't start for me until I upgraded to Hoary.

Another question comes to mind.  If killall esd solves the problem, what is esd needed for?

Darren

---

### Post by Razvan on 2005-02-07
esd is the sound daemon of gnome

if you tell your programs to do so they can all put their sound output to esd and it mixes it up and throws it at your soundcard...so you dont have to worry about getting a hardware mixer working

i dont have a clue what audacity is, but maybe there is an esd-plugin for it so you can have it put its sound in the big can as well

---

### Post by Darren Crotchett on 2005-02-07
Thanks for the info.

The most promising solution that I can find is to start these applications with:
esddsp ./app-name

But, I can't find esddsp in Synaptic.  The esd man page indicates its an related file, but the man page for esddsp does not exist.

Any idea which package it might be located in?

For the benefit of Ubuntu, the developers might want to work on this problem.  Audacity is a supported package.

Thanks again,
darren

---

### Post by tkrag on 2005-03-18
I believe esddsp is in the esound-clients package

---

### Post by Darren Crotchett on 2005-03-18
[QUOTE=tkrag]I believe esddsp is in the esound-clients package[/QUOTE]

Eventually, I found it.  I do believe that you are correct.  However, I could never get it to work.  Whenever I wanted to use Skype or Audacity, I just ended up killing esd.

Yesterday, I installed the Kubuntu stuff.  So, at the moment, I'm using ALSA.  In addition to sound working for me as I expect, everything is faster.  I really enjoy the Gnome integration, look and feel of Ubuntu, but I like KDE too.  And, I really appreciate the bump in speed.  I feel like I got faster hardware, but I digress.

---

### Post by jameswilhelm on 2005-03-31
I have the same problem on Warty.

Audacity runs OK as myself or root when run from the commandline. The audio i/o error appears when trying to run it from the launcher I created on the taskbar.

Dragging the non-working launcher to the desktop results in a working launcher on the desktop! Copying this working launcher to the desktop or dragging it to the taskbar results in a non-working copy of the launcher.

This is, at best, a workaround and does not solve the problem. Perhaps it points to where the problem might be?

---

### Post by Cordate on 2005-05-08
I couldn't get the kill command to work in the terminal... 
```
# $killall esd
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd/socket
This socket already exists indicating esd is already running.
Exiting...
```
...but I opened the System Monitor and killed ESD from there and now Audacity works.

---

### Post by zero[] on 2005-06-03
considering that many applications do not support ESD but I would still like to use ESD most of the time since the programs i most frequently use do support esd (so that more than 1 application can play sound at the same time) this was my little workaround for the problem:
first, i created a script */usr/bin/esoundtoggle* that toggles esd (kills it if it's running, starts it if it isn't)

[I][INDENT]#!/bin/bash

if [ $( pgrep esd ) ]; then
[INDENT]killall esd[/INDENT]
else
[INDENT]esd[/INDENT]
fi[/INDENT][/I]

next, i made the script executable: *sudo chmod +x /usr/bin/esoundtoggle*

then, i wanted to be able to quickly access the script using a keyboard shortcut so i ran gconf-editor, went to /apps/metacity/global_keybinding and changed the value of run_command_x (x being the first number that is available) to <mod4>s (win key + s). then, in /apps/metacity/keybinding_commands i set the value of command_x to esoundtoggle.

now when i want to toggle esd, i simply hold down the win key and press s
kills it if it's running, starts it if it's not  ;-)

---

### Post by jiyuu0 on 2005-06-03
i've encountered the same problem, and i think (step 11 and 12) will do the trick
[http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

---

### Post by hackerjosh on 2005-06-14
If you don't use any apps that need esd, another option would be to disable esd. Go to the System menu > Preferences > Sound. Uncheck the "Enable sound server startup" box. You will not hear GNOME sounds anymore. But Audacity should function as expected. Now you won't have to worry about killing esd each time you want to run Audacity and other programs.

[edit:] Oops. The person before me said the same thing.

---

### Post by timelord726 on 2005-06-21
Your script looks great, zero[], but when I run it I get this:
```
danny@danny-ubuntu:~$ esdtoggle
/usr/bin/esdtoggle: line 3: [: 17145: binary operator expected
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd/socket
This socket already exists indicating esd is already running.
Exiting...
```
I changed the name to esdtoggle by the way.  Any suggestions?

---

### Post by ibanez88 on 2005-08-04
I got Audacity working using the original Gnome menu entry by install the alsa-oss package in universe.  It is an an OSS-compatibility wrapper for ALSA.

Edit - 

No, that's not right.  after a logout / login I get the same error - in fact I get it even if launched from command line.

Thanks for that script, though, it does work for me.. 

however upon exiting audacity I lose the system sounds (even though esd is re-activated).  Strange... 

So it seems the easiest workaround is to disable esd from loading at session startup altogether...  Its a shame because I really like the gnome system sounds.

By the way the issue occurs with Kino as well.

---

### Post by HaroldJohnson on 2005-08-08
I prefer not to mess with my system sounds, so I'm just going to continue running Audacity from the Terminal.  When I can figure out how, I may also remove the Audacity icon from the Applications menu so I'm forced to start the program from a command line.

---

### Post by Clutterbug on 2005-09-28
I'm afraid NOTHING of what's suggested helps me with my AUDACITY problems.:confused: 
Just to let you know.  I have been suggested to update UBUNTU itself and will try that later.

---

### Post by tmckellar on 2005-12-12
[http://audacityteam.org/wiki/index.pl?LinuxIssues](http://audacityteam.org/wiki/index.pl?LinuxIssues)

Audacity is an OSS application. Theoretically it works with the OSS wrapper for Alsa. It is stated as being buggy though. Audacity will work on my system as root but not normal user. I also have to do this whenever I run Jackd, Ardour, and Jamin. This is basically a lack of permissions to directly access the soundcard/s. I have read there is a way to change this to put audio in the normal user group but haven't looked into it very deeply. Has anyone tried going into the "Menu Editor" and right clicking on the Audacity icon and going into the properties and adding gksudo before audacity in the command entry?

---

### Post by galgoz on 2006-01-17
[QUOTE=wulf]Here's the script I'm using:
```
#!/bin/bash

killall esd
sleep 3  # To give the previous command time to fully complete
/usr/bin/audacity
esd
```I've saved it in my personal program directory (*~/bin* - I set this up when I install a new Linux and add it to my PATH to provide a convenient home for all my scripts) and given it executable permissions. This is the file called by my menu icon and seems to work smoothly.

Wulf[/QUOTE]

Sorry, I am new to linux and don't know how to do this.  I assume I open a text editor, copy and paste all the code in and then save the file.  What do I save the file as, what is the correct extention?

---

### Post by paiger on 2006-02-14
I found the following solution on another site that helped.
These problems can be fixed by replacing esd with polypaudio as follows:

   1. Open a terminal
   2. Type sudo apt-get update
   3. Type sudo apt-get install polypaudio
   4. Say "y" to all the questions

---

### Post by Ambugaton on 2006-02-14
Wulf's script is pretty cool. But I'm not exactly Linux savy:-k   so can anyone tell me what exactly to do with it? I'm having the same audacity problem as you guys. Any guide lines would be appreciated. :) thanks.

---

### Post by Ambugaton on 2006-02-14
Well i tried Paiger's quick fix but now I have no sound at all. Yes, audacity runs fine but its not much use if I can't hear anything :confused:  Any ideas?

---

### Post by KCMiller3 on 2006-02-20
[QUOTE=galgoz]Sorry, I am new to linux and don't know how to do this.  I assume I open a text editor, copy and paste all the code in and then save the file.  What do I save the file as, what is the correct extention?[/QUOTE]

this is how I set it up.  there are many ways to do it but this is a simple graphical way of doing it....

1) create a text file with the code.  The easiest way is to go into the terminal and type "sudo gedit" to open the text editor with root permission. 
2) save that file to usr/bin as "audacityfix" (you will need the root permissions if you didnt use sudo gedit)
3) make the text file executable by going into nautilus with root permission ("sudo nautilus") and finding the audacityfix file you just created.  Right click on the file and go to properties.  Go to permissions tab and check all 3 execute tabs.  This is the GUI way of doing it.
4) change the menu link to link to the new file by going into application menu editor and right clicking on the audacity menu link.  Click on properties and change the command: "audacity" to "audacityfix".

this should take care of the error and you can still run audacity from the terminal without using the fix by typing "audacity" since we did not delete the original audacity bin file!

---

### Post by ibanez88 on 2006-02-21
post editied for clarity:  I'm getting the same problem that others are describing.  Thanks for the fix wulf.  In my case the script seems to disable all system sounds until I log out of my x session and log back in again.  Note that after I quit Audacity, and hit ctrl-c in an xterm to regain my prompt, I hear the esd test sounds but still no system sounds for the remainder of the x session.  A slight tradeoff I guess.  Thanks.

---

### Post by chrisbs on 2006-04-28
the short script worked for me: 

killall esd
sleep 3
/usr/bin/audacity

I changed the esd line though - it would on starting - so I added esd & so it would start in the background - and that worked just fine.  Esd gets restarted on my box now and I can run audacity!  

Finally.  I'm happy  now.

---

### Post by Roasted on 2007-02-02
Some people are saying here if you run audacity from terminal, it runs fine with no error. I still get the error.

Others are saying if you kill esd and run it, it'll run fine. I STILL get the error.

What gives?

---

### Post by konungursvia on 2007-02-22
They didn't work for me either. I'm running Dapper with gnome. :(

---

### Post by jolene on 2007-02-27
I open Audacity in terminal to get around the "audio i/o layer" problem, but then when I try to play a track, I get the error "Error while opening sound device. Please check the output device settings and the project sample rate." I know it should be self-explanatory, but humour me. :mrgreen:

---

### Post by villindesign on 2007-03-19
:~$killall esd did not work for me; what did is :~$aoss audacity
let me know if this works for you.

---

### Post by Roasted on 2007-05-03
I have NO idea if this was talked about in this thread or not since I last looked in it, but here goes. I had this thread saved in my favorites and I couldn't figure out why, then I realized I used to have this problem.

The I/O error I used to get was because I had a music player open. In most cases it was Audacity. I found if you have any kind of music player in (at least the few I've tried) you get this error. So I close out of everything, THEN optn Audacity, and it works just fine, no error. Trick is, nothing music oriented can be opened. THIS INCLUDES MYSPACE PROFILES WITH MUSIC ON THEM!

Try that and see how it works.

---

### Post by vitvitalik6314 on 2007-05-15
spam

---

### Post by dastinel6791 on 2007-05-15
spam

---

### Post by iasam757826 on 2007-05-15
spam

---

### Post by Nedved117618 on 2007-05-15
spam

---

### Post by mister_p_1998 on 2007-05-15
Just turn off system sounds, thats all I had to do...
Steve

---

### Post by PurpleZoe on 2008-01-14
> **jolene said:**
> I open Audacity in terminal to get around the "audio i/o layer" problem, but then when I try to play a track, I get the error "Error while opening sound device. Please check the output device settings and the project sample rate." I know it should be self-explanatory, but humour me. :mrgreen:

I'm having the same issue.
The only glitch popping up on my end is the:

*Error while opening sound device. Please check the output device settings and the project sample rate.*

I can't seem to get around it by shutting off system sounds or the EDS mix option in Preferences-Sound.

I'm a Linux Noob (Ubuntu), and not sure how to start this from the command line. It might or might not help to try it. Audacity is a great program and we want to continue using it for our pod mixes. Hopefully there won't be a need to find another program.

Any suggestions?

Grazi.

---

### Post by PurpleZoe on 2008-01-14
Got it!

I found the solution with some suggestions between this thread and an Audacity thread here:
[http://audacityteam.org/forum/index.php?sid=45f668b608a94e69b8eb2bc21c49d0dc](http://audacityteam.org/forum/index.php?sid=45f668b608a94e69b8eb2bc21c49d0dc)

I resolved the error by searching in Administration- Synaptics Package Manager- for: Alsa
Then I marked the following for installation and selected 'Apply': Alsa-oss, Alsa-gtk, Alsa-edk
Then I typed into terminal: Aoss Audacity (as suggested in this thread).
Worked like a charm.
I'll be starting Audacity from terminal from now on just to avoid the drama, in case I haven't fully resolved this.

:guitar:

Happy Days are here again ^_^

---

### Post by mister_p_1998 on 2008-01-14
You need to go into System, Sounds and turn OFF system sounds

---

