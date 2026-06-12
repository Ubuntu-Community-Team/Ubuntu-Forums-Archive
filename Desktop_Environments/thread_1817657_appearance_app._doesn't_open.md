---
title: "appearance app. doesn't open"
date: 2011-08-03
forum: Desktop Environments
---

### Post by bruce herdman on 2011-08-03
Using 10.04 LTS on a Dell Inspiron

No longer able to change the appearance using system/preferences/appearance---it produces the processing icon as the cursor, but then after a few moments disappears. Right clicking the desktop doesn't bring up the window which should contain "change background" either. 

I can't find any way to fix this (on my wife's computer) your expertise and assistance would be greatly appreciated.

Bruce

---

### Post by jerrrys on 2011-08-04
try this:

open a terminal and enter

gnome-appearance-properties %F

what happens?

---

### Post by johansson on 2011-08-05
When did this start?  has it always been this way?  If not, what changed (if you know)?

I screwed mine up (haven't figured out how yet) but in the mean time I can do alt+F2 and then type "gksudo gnome-appearance-properties" to run it.  However this is only a temporary fix as it only changes the root properties and will reset to user settings upon shutdown or logout.  

If that works, I would suggest that it's a permission issue

---

### Post by bruce herdman on 2011-08-06
Thanks. I put in the string you suggested and it returned: "Segmentation fault". Hope that means there is an obvious fix.

Bruce

---

### Post by bruce herdman on 2011-08-06
@Johansson:The machine worked normally until it didn't. No differently compared to the old HP I am running Ubuntu on in my office. We both did up-dates the same day--mine continues to work fine, hers is goofed up (minor goofiness, but aggravating). 

I tried the procedure you used and it works fine on my machine, on the problem system it does not work. So I guess it isn't a permissions problem. 

Thanks for the input though.

Bruce

---

### Post by jerrrys on 2011-08-06
have you tried to fix broken packages?

sudo apt-get -f install

and it said nothing else other than Segmentation fault?

---

### Post by Frogs Hair on 2011-08-07
I just had an issue with this , it seems one of the gnome-themes-ubuntu package had a broken link . It was the New Wave Dark theme specifically . I could not open appearance preferences , synaptic package manager , or gksu nautilus to remove the theme package .

I found success with the software center and was able to remove and reinstall the package. I identified the package due to terminal errors displayed when I tried gksu nautilus .

---

### Post by bruce herdman on 2011-08-07
> **jerrrys said:**
> have you tried to fix broken packages?

sudo apt-get -f install

and it said nothing else other than Segmentation fault?
jerrrys: I'm not sure what to do with sudo apt-get -f install----other than typing it in in a terminal, sorry. And, yes, all it said was Segmentation fault.

---

### Post by bruce herdman on 2011-08-07
Frogs hair: I feel in over my head---I have never used gksu nautilus---I may be old, but I know little about the stuff under the hood....

---

### Post by jerrrys on 2011-08-07
ok bruce, communications are spread out so i am going to give you a list of commands to run in a terminal, run commands one at a time

this will attempt to fix broken packages
sudo apt-get -f install

this will attempt to fix package dependencies
sudo dpkg --configure -a

cleans expired packages
sudo apt-get autoclean

cleans archives and partial cache
sudo apt-get clean

remove unneeded dependencies
sudo apt-get autoremove

to update your package list
sudo apt-get update

to install the updates
sudo apt-get upgrade

happy hunting :)

---

### Post by Frogs Hair on 2011-08-07
> **bruce herdman said:**
> Frogs hair: I feel in over my head---I have never used gksu nautilus---I may be old, but I know little about the stuff under the hood....

```
gksu nautilus
```

The above is terminal command to open Nautilus (file browser) as root , so you have permission to remove items from the file system . A " you do not have permission " message will appear otherwise .

---

### Post by jerrrys on 2011-08-07
found what i think frogs talking about

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/551048](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/551048)

---

### Post by bruce herdman on 2011-08-08
Wow Jerrrys---I'm off to pry my wife away from her computer so I can start trying your suggested actions. Thanks again.

---

### Post by bruce herdman on 2011-08-08
Tried them all. Most came back with 0 in the files/packages changed or modified. Restarted the computer--problem remains. Rats. I did copy the list of commands you provided to a file in my computer for later use. 

Any more ideas? Sorry to be a pest, but I find I'm learning something from each message, so that is a gain.....

---

### Post by jerrrys on 2011-08-09
do what frogs said and open a terminal and enter **gksudo nautilus**.   see if it will tell you the name of the offending package.

EDIT: please post the results

---

### Post by bruce herdman on 2011-08-10
Jerrrys: tried gksudo nautilus, but found nothing I knew how to handle. Unfortunately, more explicit directions are required for me to manipulate nautilus to find a suspected bad package. Somewhere in the mass of files, by going down a tree from system/usr/etc/bin/gnome (or whatever!) I suspect I would be able to find the appearance program, but......and then what would I do? I hate being a dumbarse about this stuff.

I appreciate your patience and assistance.

---

### Post by jerrrys on 2011-08-10
we finally meet again, online at the same time :D

after you did the gksudo thing, i was hoping for an error message.

i have done further research on this and the only other thing im finding is basically what frogs pointed to.  a bug that from all indications has been fixed, but has been a subject for a while.
do you recall changing themes/icons? the names?

---

### Post by bruce herdman on 2011-08-10
If I understand you correctly, I should have received an error message when I opened nautilus if there was a bad file, yes?

I looked at the bug file link, it didn't seem to apply, exactly, to our situation.....

No changes in theme or icons----the problem was first noticed when my wife tried to change the background picture---she doesn't change other stuff, or, not intentionally. She said she hasn't changed anything except background for a long long time.

I understand 11.04 is soon to be out, and I'm hoping it will clear this up if I haven't found an answer (with lots of help *g*) before then.

---

### Post by jerrrys on 2011-08-10
"If I understand you correctly, I should have received an error message when I opened nautilus if there was a bad file, yes?"

that was my hope

11.04 is out, but if you upgrade to 11o4 you may just carry the problem with you. a fresh install would be better.  if you decide to go this route, be sure to try it before installing it.  11o4 has its problems too.

since you haven't change your appearance settings, it looks like a dead end has been reached.  but i would like to see a screenshot of your "icon" folder for one last thought on it.  so if you would:

gksudo nautilus and navigate to file system>user>share>icons and take a pic of whats inside your icon folder.  if you cant get it all on the screen go to the tool bar, then view and select compact view

---

### Post by bruce herdman on 2011-08-10
Jerrrys: I hope this works--seemed a little strange to do this way. Here goes.

---

### Post by Frogs Hair on 2011-08-10
Appearance Preferences is run as part of the gnome-settings-daemon . Run the following command and post the output .```
sudo gnome-settings-daemon
```

A next step after that would be to open the synaptic package manager and use the search to locate the gnome-settings package .  Right click on that line , mark for re-installation , and select apply

---

### Post by bruce herdman on 2011-08-10
sudo gnome-settings-daemon results in (attached)

synaptic package manager next? 
Of Note: the mouse buttons reverse when I go to the synaptic package manager---the left is still marked but it acts like a right button mouse until I unselect left and re-select it. Is this a clue?

---

### Post by bruce herdman on 2011-08-10
Frogs hair: I did the synaptic package manager thing---your screen shot was very helpful!!---but the problem remains.

Very frustrating. I appreciate your help---none the less

:confused:

---

### Post by jerrrys on 2011-08-11
[COLOR=#000000][FONT=Sans Serif]when using synaptic package manager to locate a package you can:[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=Sans Serif]open SPM and click on a package, any package.[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=Sans Serif]then start typing in the name of the package your looking for.[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=Sans Serif]SPM will go to that package as you type the package name.[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=Sans Serif]bruce; please reinstall **gnome-icon-theme**[/FONT][/COLOR]

---

### Post by bruce herdman on 2011-08-11
Jerrrys: I used the spm to reinstall gnome-icon-theme---but it didn't fix the problem.

Looking at the thread, I see you advised (if I tried it) doing a clean install of the OS (?). How do I do that other than down loading an ISO image? Do I have to wipe the hd of the current OS first? 

Thank you for the effort you have expended on this for me.

---

### Post by jerrrys on 2011-08-11
well, sorry to hear that all efforts have failed.

if you wish to install 11o4 you will have to burn a CD (.iso).

are you dual booting with windows?

---

### Post by bruce herdman on 2011-08-11
Yes, my wife's machine is a dual boot so she can use her "win-only" book writing program. No comparable program available on Linux-based systems so we have to keep it.

Sounds as if you have run out of options for me to try. Rotten luck, that. I do appreciate all the help you and Frogs Hair have offered the last few days. Thanks to you both and if you come up with another idea of something to try, I'll be checking back often.

Bruce

---

### Post by jerrrys on 2011-08-11
good luck to you

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dual+boot+install&sa=Search&cof=FORID:9#986](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dual+boot+install&sa=Search&cof=FORID:9#986)

---

### Post by bruce herdman on 2011-08-12
Thought I'd let you know. The clean install of 11.04 was successful after downloading a special driver and driver installer (Broadcom 4318). The help and encouragement you gave me made me keep working on finding a solution to the wireless connection problem and I finally found it.

Thanks again.

---

