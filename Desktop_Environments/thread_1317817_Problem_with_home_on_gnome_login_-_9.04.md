---
title: "Problem with home on gnome login - 9.04"
date: 2009-11-07
forum: Desktop Environments
---

### Post by Vinomfire on 2009-11-07
First i'd like to appologize for any mistakes in the placement of this thread or any other general mistakes.

So basicly when i log in to ubuntu, an error pops up that says that the " $HOME/.dmrc file is being ignored" it then procedes to talk about how it wont save settings and that my user needs to onw the file. When ever i log on, whether in gnome or fail safe gnome ( fail safe terminal works), the screen just turns blank except for the pointer. I've only been using ubunu for a couple of weeks, so any help woulb be appreciated. Like i said earlier i can use the terminal, so i can execute commands from there. Thanks

---

### Post by qwety on 2009-11-07
Have you touched at your home folder permissions? If yes, reset them back to normal.

As you can use the terminal, you should upgrade your system by running "sudo apt-get apdate && sudo apt-get upgrade && sudo apt-get dist-upgrade". Before upgrading, read Ubuntu 9.10's release notes and upgrade guide: 

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
[http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

---

### Post by alienclone on 2009-11-07
> **qwety said:**
> Have you touched at your home folder permissions? 

As you can use the terminal, you should upgrade your system by running "sudo apt-get apdate && sudo apt-get upgrade && sudo apt-get dist-upgrade". Before upgrading, read Ubuntu 9.10's release notes and upgrade guide: 

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
[http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910)

you dont need to uprgade, dont know why qwety would even suggest that. 9.04 is a great release to stick with for now since it was working just fine before on your system, cuz 9.10 is still working on the bugs.

but qwety's first sentence was correct, search for commands to change ownership of your .dmrc file.

or maybe the next person to come along can explain how to use the "chown" command

---

### Post by deathrunner1 on 2009-11-07
You could change the permission to the correct permission using this line in the terminal:

```
$ sudo chmod -R 700 /home/username
```

and just change your username to the name of your directory in /home
Hope this helps.

Lynn

---

### Post by Vinomfire on 2009-11-07
Thanks, but whhen i tried that it gave me the same error. After i log in i'm told that the system can't update "ICEauthority file /home/collin/.ICEauthority" (collin is my username). After i hit ok, another error pops up telling me it that " there is a problem with the configuration server". The screen hoes blank again and then another error pops up saying that " there was an error starting up the screen saver: failed to change to directory '/home/collin' permisssion denied. Then one more error tells me it cant create the desktop folder and the nautilus folder because tthe permissions are incorrect. I'll try running the command ( mentioned above) under the root of the system, and if that doesent work, in recoovery mode. If any one has any more tips, that would be great.

---

### Post by deathrunner1 on 2009-11-07
I think from the blank screen you can hit <CNTRL> + <ALT> + <F1> to get to the terminal without having to use the GUI. Let us know how things turn out.

Lynn

---

### Post by Vinomfire on 2009-11-07
Whever i log into any terminal, it tells me that it can't log me into home because i don' t have the right permissions. I'm  also using two hard drives with one mounted to the filesystem (/) and the other to home (/home). Should i just try to update my system or reinstall 9.04, or is there somthing i can do

---

### Post by deathrunner1 on 2009-11-07
I don't know the right answer.  We'll let someone more experienced reply..hope things work out. Personally, I would do a reinstall, but wait for some more input.

Lynn

---

### Post by Vinomfire on 2009-11-07
I think i'll try an upgrade or reinstall. Thanks for all the though. You all were really helpfull.

---

### Post by alienclone on 2009-11-07
> **Vinomfire said:**
> I think i'll try an upgrade or reinstall. Thanks for all the though. You all were really helpfull.

since you are starting over, (which is the course i would take because i am so new to Ubuntu and that is the way i am used to fixing things thanks to Windows not being fixable without a reinstall) you might want to go ahead and check out 9.10 and see how it runs in your machine since you have nothing to lose at this point. but if the threads that have been posted since the release of 9.10 are any indication of how it will turn out, be prepared to go back to 9.04.
i did the dist-upgrade on my test unit from 9.04 to 9.10 with no problems so far, but still using 9.04 on my main unit because it is stable for me.

---

### Post by lswb on 2009-11-07
Before you do the reinstall, open a terminal and try

sudo chown myname:myname .dmrc
chmod 700 .dmrc

---

