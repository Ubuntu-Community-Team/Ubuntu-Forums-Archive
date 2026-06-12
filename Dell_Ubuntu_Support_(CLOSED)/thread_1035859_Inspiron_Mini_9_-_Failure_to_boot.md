---
title: "Inspiron Mini 9 - Failure to boot"
date: 2009-01-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rwine on 2009-01-10
Hi!  We purchased one of these wonderful units from Dell last month for our 11 yr old son.  Last evening, he came to me with what I believe folks call the "White Screen of Death".   The system won't reboot and I am struggling to find a solution.  Up until last night, this system has worked great!  When I called Dell for support....they referred me to an Ubuntu Team who imformed me that Dell did not get a "Service Contract" for the Mini 9 (910).
Here are the specifications for those that might might be able to provide guidance.
Inspiron 910 Intel Atom Processor N270, 1.60GHz, 533 M33Mhz
512 K L2 Cache
1 GB, DDR2, 533MHZ, 1 DIMM

It looks like if I had an optical drive, I could use the Ubuntu 8.04 LTD CD that was provided with the unit.

Any and all guidance would be greatly appreciated.  :-)

Rich

---

### Post by ugm6hr on 2009-01-10
Can you access BIOS to run the "diagnostics"?

Do you have an external DVD drive or large USB flash drive?

What was your son doing when it stopped working?

PS: I have started a separate thread for you.

---

### Post by rwine on 2009-01-10
Hi...thanks for your questions.
Upon booting up the unit, flashes the Dell Logo, then quickly loads Ubuntu.....then "white screen" appears.  I am not knowledgable enough to tell you if I can access BIOS.
Lastly, my son said the he clicked on the "Service Manager" because it said there were 77 updates that were available.  Since then we told him only his parents should help with that.  He indicated that something called "Cheese" started downloading...then everything locked up and *poof*....the system froze.

Sorry, I wish I knew more to give you more details.  We are still trying to understand the Ubuntu system.

---

### Post by ugm6hr on 2009-01-10
I'm using my Mini at the moment - so dont want to reboot to check.... but I think it says something like press 0 for diagnostics, press 2 for BIOS when you first turn it on (around the time of the Dell screen).

There were 177 updates today - that is what he was referring to.  If it crashed during the update, it may be because there was insufficient HD space for the download.  However, Ubuntu downloads all updates before installing them, so if it crashed during the download, it shouldn't have caused any problems.

If it crashed during the installation / configuration stage, then it is entirely possible that something important got corrupted.  It should be possible to boot into a "recovery" console in Ubuntu - but I'm not sure if that function is present on the Dell Mini (it is a customised Ubuntu).

Let me know if you have a 1GB+ USB disk or external DVD drive for reinstallation (if necessary).  I'll reboot in the meantime to find out how this device is set up (I've only had it for 4 days now).

EDIT:
There is no way to enter the grub menu that I can find to go into recovery mode.
Press 0 at the Dell screen to get into the diagnostics page. It sounds like this is a software issue though.
There are no default tty terminals available on Alt-Ctrl-F2 etc

Does your son usually auto-login? Or does he usually enter username and password?  It sounds like Ubuntu loads, but there is a problem with X (the graphical display) which gives the white screen. Is the mouse pointer visible on the screen?

Perhaps try Ctrl-Alt-Backspace from that screen - it may return you to a Terminal login.

---

### Post by rwine on 2009-01-10
Thanks for being patient!  I really appreciate your help.  OK, pressed 2 and believe I got the BIOS screen (says PhoenixBIOS setup Utility).

I currently do not have an external DVD drive for reinstallation, but I have started calling my friends to see if anyone has one before I purchase one.  Likewise I do not have a 1GB+ USB disk.

Regardless....I have this BIOS screen up and eager for your guidance. :-)

---

### Post by rwine on 2009-01-10
Yes, he uses auto-login. The computer no longer requires the "username" and password. The mouse pointer is visible on the screen and we can move it with the touch pad.

---

### Post by ugm6hr on 2009-01-10
OK.

Try Ctrl+Alt+F1 (Ctrl+Alt+Fn+A)

That should drop you to tty1 screen.

Then you need to manually enter the username and password (hope you remember them!)

Hope that works for now.

---

### Post by ugm6hr on 2009-01-10
Assuming that works:

```
df /dev/sda2
```
Should tell you what % of HD space is being used (make sure there is some free).

If there is a reasonable amount free, plug into ethernet cable / router:
```

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by rwine on 2009-01-10
OK.  Entered user name and password.  What is on the screen now is.....

jacob@jacob:&#732;$

Not sure what to due next.....

---

### Post by rwine on 2009-01-10
doesn't look good....

Filesystem  1K-blocks 3555040  Used 2944464  Available 427036  Use% 88%

---

### Post by rwine on 2009-01-10
I will check back with you later tomorrow.  Thanks for your all your help.  I'm going to leave the machine alone "as is" until I hear back from you &/or anyone else about my next steps.  As I reported...it looks like the HD is already pretty full.  Not sure how that happened so fast unless the 177 updates you spoke had that much of a significant impact.

Take good care!  Rich

---

### Post by ugm6hr on 2009-01-10
EDIT: > Feel free to read this post - but the recommendation is based on a reading error I made last night.  See my new post #14.

Sorry about leaving mid-help. Unavoidable.

Anyway - your df appears to show you only have a 4GB HD. Is that right? I thought that all the Dell Minis came with at least 8GB.  Mine has used "2887900" - so your son has used about an extra 6MB for files - not a huge amount.  Ask him if there is anything opn there that he needs (i.e. can you just delete all of his personal files / settings etc)?

I remember hearing that some of the early devices reported they only had 4GB - I will do some googling and get back to you.

The "jacob@jacob:&#732;$" merely means you are logging into the computer at the "command line" - so the computer still works (good news).  Just have to get the software issue resolved.

Will edit this post as soon as I've found out more about the 4GB HD issue.

EDIT:
Found 2 things:
1. The Dell Mini 9n in USA apparently only had 512MB RAM / 4GB HD - is that the model you have?
2. [https://help.ubuntu.com/community/DellMini9](https://help.ubuntu.com/community/DellMini9)
> Some early Mini 9 systems shipped with Ubuntu pre-installed may report smaller disk space than expected (ie. 4GB instead of 8GB or 16GB). The "missing" space is on the system, but remains unformatted. This has been resolved in later factory installed systems as well as in an update at the Dell Mini repositories. Perform all updates and it should be resolved. 

First, lets see how many updates actually downloaded:
```
ls /var/cache/apt/archives
```
This will list all the updates that have downloaded alphabetically - just tell me what the last one in the list is (just the bit before the version number is fine).

I would start by deleting Trash (replace jacob with son's username if incorrect):
```
sudo chown -R jacob ~/.local/share/Trash
rm -rf ~/.local/share/Trash/*
```

Then I would suggest deleting personal files in /home (it would be possible to save them to a USB stick if necessary) to create a little more space (at least 20MB to be safe).  This can be done from the commandline too with the "rm" command.  For example, the following would remove the entire contents of your "Documents" directory, while prompting for a "y" to delete each file / directory (can repeat for "Music", "Pictures", "Videos", "Desktop"):
```
rm -ri ~/Documents/*
```

You can also delete any files in the "Home" directory (i.e. not in a subdirectory) with:
```
rm -i ~/*
```

Then complete the installation of whatever has been partially installed:
```
sudo dpkg --configure -a
```

Then fix whatever is currently broken:
```
sudo apt-get install -f
```

At this stage, recheck to see how much space you have.
```
df
```

In theory, you should be able to reboot into the desktop again now.

```
sudo reboot
```

Of course, not all the updates will necessarily have installed.  But let us know how you get on with that lot first.

If you have the 9n with only 4GB, this is likely to be a recurrent problem, so you will have to plan your updates carefully.  Consider removing any unused applications, and not storing files on the internal HD.

---

### Post by anjilslaire on 2009-01-10
The base model have a 4gig SSD, thats correct.
[http://www.dell.com/content/products/productdetails.aspx/laptop-inspiron-9?c=us&cs=19&l=en&s=dhs](http://www.dell.com/content/products/productdetails.aspx/laptop-inspiron-9?c=us&cs=19&l=en&s=dhs)

If it's that full, then its likely that may the issue with the GUI.

---

### Post by ugm6hr on 2009-01-11
> **rwine said:**
> Filesystem  1K-blocks 3555040  Used 2944464  Available 427036  Use% 88%

I have just realised my mistake: you have about 400MB free (not 4MB).  Which makes sense with 12% free of a 4GB HD.

So don't worry about my previous comments; just do the following (at jacob@jacob command line):

```
sudo dpkg --configure -a
sudo apt-get install -f
sudo reboot
```

This should allow you to log back in.  Once in, open a Terminal and ensure the updates complete properly:
```
sudo apt-get update
sudo apt-get upgrade
```

Then lets free up some space (delete the update files taking 175MB space):
```
sudo apt-get clean
```

Nevertheless, you will need to be careful about future updates.  Best to use the Terminal, and ensure you have at least 200MB free space before each one.  Deleting Trash (as above) is useful.

---

### Post by rwine on 2009-01-11
Great news!  Thanks to your guidance, I believe I have the system "restored".  I have no wireless connection, but this is consistant with how the system came directly from Dell last month.  It took an Ubuntu specialist that Dell put me in contact with to get this wireless feature functioning.

To answer your other questions apropos the computer....I confirm it is a 4GB Solids State Hard Drive/ 512K L2 Cashe.  I looked at the Hardware and it says the unit has 6.8GB total....with 5.30 used and 1.50 currently available......

Currently I am using the ethernet connect to finish downloading and updating the 81 remaining files (Ubuntu security?).  SO FAR....so GOOD!  :-) 

I'll update this thread as soon as I have new information....thanks!

---

### Post by ugm6hr on 2009-01-11
Glad you are back on track.  The wifi issue is strange.  

It's a BCM4312 PCI wifi (14e4:4315) card that uses the new "wl" driver (confirm with "lspci -nn | grep BCM43").  This new update should not have caused you to lose it.

Having said that, it should also have worked "out of the box" (as mine did).  However, this driver is apparently not the most stable out there - here's hoping that the new linux-restricted-modules improves the situation.

If it doesn't work - report back...

---

### Post by rwine on 2009-01-11
Hi ugm6hr,

After downlading the 81 remaining updates and rebooting....the system appears to be workign better and better.  The wireless issue resolved itself and I only have one remaining issue.  The most popluar websites my son visits are not loading completely or not loading correctly.  I believe a new version of Foxfire was downloaded.....maybe that version on this operating system is causing an issue...not sure.  I had to download Adoby Flash (for Foxfire) and it doesn't seem to help me.....

Any ideas?

Thank you very much for all your help!


edit.....websites are [www.clubpenguin.com](www.clubpenguin.com) and [www.miniclips.com](www.miniclips.com)

My son really enjoys these websites but I cannot get them to run correctly now (ps....before "the crash"...they ran without any issues or needing to download any addition plug in programs)......RW

---

### Post by ugm6hr on 2009-01-12
Try this: [http://ubuntuforums.org/showthread.php?p=6529628#post6529628](http://ubuntuforums.org/showthread.php?p=6529628#post6529628)

Essentially, the update has moved the Firefox settings from "firefox" to "web browser" - thus removing the plugins too.

By creating a link from one to the other, a restart of Firefox should sort that out for you.

PS: No need to apply the xmodmap fix if you don't want it.

---

### Post by rwine on 2009-01-12
Hi again ugm6hr!!!!

Can you provide step by step instructions from the start-up point after the machine is booted up and running please????   I am not comfortable trying to guess "how" to complete the changes your mention.  Just treat me as a complete idiot....lol.

Thanks!  Rich

---

### Post by ugm6hr on 2009-01-12
I have re-edited that entry to be much more thorough.

However, the simplest way is to copy and paste in the Terminal:
```
ln -s ~/.mozilla/firefox/ ~/.mozilla/"web browser"
```

Make sure you do this exactly, since any spelling errors will make it fail to work.

Then just restart Web Browser.

---

### Post by rwine on 2009-01-12
Don't laugh to hard....but how do I get to the Terminal????  Is this the same as the "c:" for a Windows machine?  No clue how to get there....

Did I say I ws an idoit?.....lol

---

### Post by ugm6hr on 2009-01-12
How did you run the commands here? [http://ubuntuforums.org/showpost.php?p=6531777&postcount=14](http://ubuntuforums.org/showpost.php?p=6531777&postcount=14)

Anyway:
It's in the main menu at the top left:
Applications -> Accessories -> Terminal

---

### Post by rwine on 2009-01-12
got there from the "white screen".  I did get to the terminal and entered the code as typed.....response is.....ln: target ' browser" is not a directory......

---

### Post by ugm6hr on 2009-01-12
I suspect you have missed a " at the start of "web browser"

Copy and paste if you can.

But it might be the existing directory causing problems:
```
rm ~/.mozilla/"web browser"
```

Then try again.

---

### Post by rwine on 2009-01-12
I started to make the changes the other way when I got your last response.  The current "renamed" web browser has two fies in it.....
3895c701.default and a second file called profiles.ini

Perhaps I got impatient and started fixign this issue two different ways and created "a mess".....

---

### Post by ugm6hr on 2009-01-12
The renamed web browser should have an arrow on the folder, indicating it is a link rather than an original folder.

The contents of "web browser" should be identical to "firefox"

Nevertheless, you could still run the 2 Terminal commands as described - it will delete the web browser folder and recreate a symlink.

---

### Post by rwine on 2009-01-12
One additional question.....how do I keep his HD clean of "garbage"?  Is there a "Disk Cleanup" command like there is with Windows to keep his system running free and clear?

---

### Post by rwine on 2009-01-12
The two files appear identical (Foxfire & web browser).  Thank you.  I'll try the other 2 Terminal commands you wrote and see what happens.  Thanks for your patience!!!!

---

### Post by ugm6hr on 2009-01-12
> **rwine said:**
> One additional question.....how do I keep his HD clean of "garbage"?  Is there a "Disk Cleanup" command like there is with Windows to keep his system running free and clear?

Sort of.

Although it is actually easier to do from Terminal too.

```
sudo apt-get clean
sudo chown -R jacob ~/.local/share/Trash
rm -rf ~/.local/share/Trash/*
```

The 1st deletes the downloaded update files (won't undo the updates). 2nd ensures all the Trash is able to be deleted (uncertain if this is necessary - it generally isn't). 3rd deletes all the Trash.

You can do this with the GUI too (if you prefer):
Equivalent:
1. System -> Administration -> Synaptic -> Settings -> Preferences -> Files

Temporary Files should be set to "Delete downloaded packages after installation"

Plus, if your disk is already filled up, there's a handy button there labeled "Delete Cached Package Files". Click this to re-claim your drive space.

3. Open the File Browser
In left column - left-click "Deleted Items", then click "Empty Deleted Items" on right

---

### Post by rwine on 2009-01-12
Thanks!  Followed youyr instructions for keeping the system clean.

Apropos the web browser.....pages are still not loading correctly and sometimes NOT loading at all.  Doesn't appear to be working any better.  Should I follow the additional instructions.....enter at the Terminal....

echo "keycode 115 = F11" > .Xmodmap

then reboot?

---

### Post by ugm6hr on 2009-01-12
That won't do anything to FF.

Have you restarted Web Browser?

Those websites work fine on mine.

If after a restart they remain problematic, then perhaps Flash needs to be reinstalled.

---

### Post by rwine on 2009-01-12
Downloaded Adobe Flash Player 10 for Ubuntu 8.04....closed browser and rebooted.  No change
Here is some additional information.....the machine now has Yahoo Web Browser.  Several times when the system doesn't load a webpage....I have to "select" ...Force Quit to close out page since it is un-responsive.  Can we consider "starting over" by removing everything then trying this again?

One other thing for your to know....before this all happened, we loaded Procon Latte as a means of limiting where our son could go.  It is a website filter that parents can load onto their machines to keep the kids away from porno sites...etc.

Thx!

ps.....where do I send the money for all your help?

---

### Post by ugm6hr on 2009-01-12
Have to say, I've not had any luck using Flash 10.  When you downloaded it, how did you install it?  Reason I ask - it does not come in a lpia .deb for installation.

I'd suggest you go back to Flash 9 in the repo:
```
sudo apt-get install --reinstall flashplugin-nonfree
```

Just make sure that you have done the web browser link properly - give the output from:
```
ls -l -a ~/.mozilla
```

Also - you can remove the Yahoo toolbar:
```
sudo apt-get remove yahoo-toolbar-extension
```

Restart Web Browser again, and see how it goes.

Is it just those websites you mentioned earlier?

PS: My User CP has gone wrong - so will not be notified of responses.  I will try and keep an eye out for replies from time to time.

EDIT: I will do a bit of research on Procon Latte - I have never heard of it before.

---

### Post by rwine on 2009-01-17
Hi again....been away for business and haven't had any luck with computer web browers and those websites I spoke of....they still won't load correctly or just will NOT load at all (Miniclips.com  Clubpengiun.com  Webkinz.com)

Let me ask this....what about removing the "newest version" of FireFox and reinstalling older version.  The version that came with the computer worked just fine.  Somewhere along the way the updates (177) messed us up.   BTW....I did remove the ProCon Latte (content filter) program, reopened web brower....and then rebooted (still no luck).

Any and all assistance would be greatly appreciated!!!!!!!

Rich

---

### Post by ugm6hr on 2009-01-17
This is nothing to do with the new FF. Those websites are all flash based.

Presumably your flash plugin has been lost somehow.

Try my suggestions already given and report back.

PS: it is nothing to do with Procon-latte

---

### Post by rwine on 2009-01-17
output from: ls -l -a ~/.mozilla is:

total 16
drwxr-xr-x  4 jacob jacob 4096 2009-01-12 06:31
drwxr-xr-x 43 jacob jacob 4096 2009-01-17 09:48
drwx------  3 jacob jacob 4096 2008-12-07 01:22 extensions
drwxr-xr-x  3 jacob jacob 4096 2009-01-12 07:56 firefox
lrwxrwxrwx  1 jacob jacob   28 2009-01-12 06:29 web browser -> /home/jacob/.mozilla/firefox

Can you list the commands that tell me what verson of the Adobe Flash Player is installed.....I did use the following commands to reinstall the older version and remove the newset flash 10

ps...looks like the system installed..."../flashplugin-nonfree/install_flash_player_9.tar.gz



Rich

---

### Post by ugm6hr on 2009-01-17
To see if that has installed flash correctly, close and re-open FireFox.

In the url bar (**i.e. NOT in Terminal**), type the following: ```
about:plugins
```

Mine is attached for comparison.

---

### Post by rwine on 2009-01-17
ok....under Default Plugin......no file and nothing Enabled

much farther down under Shockwave Flash

Mime Type
application/x-shockwave-flash

Description
Shockwave Flash

Suffixes
swf

Enabled
Yes

I don't see anything that specifically says Adobe Flash 9.0

---

### Post by ugm6hr on 2009-01-17
It sounds like you have Flash installed.  It should say something like:

> Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r152

I'm afraid I'm not sure why it's not working.

Not all Shockwave sites are linux compatible.  But most miniclips.com games seem to work OK on mine.

---

### Post by rwine on 2009-01-17
I think I found a "potential" cause.  According to the "Add-ons" tab, it appears the the version of Flash that is now loaded on the computer is Shockwave Flash 8.0 r99  Gnash 0.8.2 the GNU Flash Player.

I'll report back if anything new happens.
Thanks!

---

### Post by ugm6hr on 2009-01-17
> **rwine said:**
> I think I found a "potential" cause.  According to the "Add-ons" tab, it appears the the version of Flash that is now loaded on the computer is Shockwave Flash 8.0 r99  Gnash 0.8.2 the GNU Flash Player.

That makes sense.  You have Gnash rather than Adode Flash currently working.

Close Firefox and try this:

```
sudo apt-get purge gnash-common
sudo apt-get autoremove
sudo apt-get install --reinstall flashplugin-nonfree
```

Then try launching Firefox again.

---

### Post by rwine on 2009-01-17
It's finally working!!!!!!!   Thanks so very much for all your help, guidance and patience!!!!!!

Take care!  Rich

---

### Post by ugm6hr on 2009-01-17
No worries.

Glad it's sorted.

Presumably, following the FF re-install, Flash plugin went a bit wrong, and you were prompted to install Gnash (which sometimes appears as the default choice - not sure why, it doesn't work very well).

So installing Flash didn't work until Gnash was removed.

Given your HD space issue, you might want to empty your cache again:
```
sudo apt-get clean
```

---

### Post by rwine on 2009-01-17
Thanks!  I took care of that then reloaded the ProCon Latte add-on.  The unit is 100% restored thanks to YOU!

Would it make sense to upgrade/add more memory to the computer?  I don't think he will need more anytime soon, but I am concerned about the updates causing issues again and "we" may want to add additional program at some point in time down the road.   What size of a HD did you purhase for your Mini 9?

---

### Post by ugm6hr on 2009-01-17
Mine came with 8GB HD and 1GB RAM (base model in UK).

Unfortunately, I have no idea how to upgrade the internal HD.  RAM is easy to upgrade, but it would mean binning (or selling on) your existing RAM stick.

In reality, I am not sure exactly what the cause of your problem was.

Simple precautions to take before future updates:
Empty trash
*sudo apt-get clean* (removes previous installation files)
*df /dev/sda2* (check free HD space)
*sudo apt-get upgrade* (this will tell you how much space is required before doing anything - if the amount required is within 100MB of your free space - pause and ask for advice here first)
Agree to updates

---

### Post by anjilslaire on 2009-01-18
Rather than
```

sudo apt-get clean

```
all the time, set Synaptic to automatically delete the downloaded updates after install:
System>Administration>Synaptic Package Manager
Settings>Preferences>Files
Select 
"Delete downloaded packages after installation" 

No more worries about that part at least :)

---

### Post by Ryback on 2009-01-22
Thanks for all the help here **ugm6hr** - my new mini arrived today and I had some similar problems after processing the updates.  All solved now thanks to this post! :D

---

