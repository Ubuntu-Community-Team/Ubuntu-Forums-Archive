---
title: "hotkey that launches or gives focus to caluclator"
date: 2007-12-06
forum: Desktop Environments
---

### Post by rubberglove on 2007-12-06
Because I find myself needing a calculator periodically, I've added a shortcut to launch the calculator (I did this using compiz in gnome, and the settings in kde).

That works pretty great, but it occasionally leaves me with a few calculators open. 
Is there a setting/command I can use that would first check to see if an application is open.
If it is, give it focus, if it's not launch it and then give focus?

Either kde or compiz-based solutions would be great...


thanks

---

### Post by spupy on 2007-12-06
Hi! I just wrote this script for myself (for a program called gTodo). I made small editions and now it works for the calculator. Here is the code:
```
#!/bin/bash
# If gcalctool is not running, start it; otherwise bring the window to my focus

calcwin=`wmctrl -l | grep -m 1 -o "Calculator"`
calcid=`wmctrl -l | grep -m 1 "Calculator" | grep -o -e "0x[a-z0-9]\{8,8\}"`
if [ $calcwin = "Calculator" ];
	then
		wmctrl -i -R $calcid
	else	
		gcalctool &
fi
```
Put this code in a text file and make it executable with 
```
chmod +x startCalc.sh
```
(assuming you named the script file startCalc.sh), or you can make it executable thru the properties dialogue in your file manager.
To use this script you will need this little program (it's called wmctrl):
```
sudo apt-get install wmctrl
```
I don't know how the calculator is called in KDE, so you need to change some lines. First, replace all occurrences of "Calculator" with a word from the title of your calculator (kcalc if it is called so, can't remember.) Remember to keep the quotes and notice that this word is case sensitive. Also replace the "gcalctool" with the command that starts your calculator (keep the &). 
Put this script somewhere and make a compiz key shortcut to execute it.
A little explanation how it works. First, the wmctrl lists all windows, we search them for a window named with Calculator; we also get the ID of the window. A little IF shows if we found a calc window. If there is one, the command "wmctrl -i -R" brings it to the current desktop and gives it focus. If no calculator window has been found, we just start the program.
That's it! If you have any questions or you didn't understand something, don't hesitate to ask!

Cheers.

---

### Post by rubberglove on 2007-12-07
Fantastic - that's exactly what I was looking for!

wmctrl seems pretty useful for that sort of thing.

I modified the script slightly - (speedcrunch is the KDE  calculator). The first grep doesn't seem necessary, since calcid will be null if that window is opened. 

```

#!/bin/bash
# If speedcrunch is not running, start it; otherwise bring the window to my focus

#calcwin=`wmctrl -l | grep -m 1 -o "SpeedCrunch"`
calcid=`wmctrl -l | grep -m 1 "SpeedCrunch" | grep -o -e "0x[a-z0-9]\{8\}"`
if [ $calcid ];
	then
		wmctrl -i -R $calcid
	else	
		speedcrunch &
fi

```


But, playing with wmctrl, I realized it can be even simpler - the window can just be addressed using the window name, instead of the id:

```

#!/bin/bash
# If speedcrunch is not running, start it; otherwise bring the window to my focus

calcwin=`wmctrl -l | grep -m 1 -o "SpeedCrunch"`
#calcid=`wmctrl -l | grep -m 1 "SpeedCrunch" | grep -o -e "0x[a-z0-9]\{8\}"`
if [ $calcwin ];
	then
		wmctrl -R SpeedCrunch
	else	
		speedcrunch &
fi

```

This seems to work fine even if there are multiple "SpeedCrunch" windows open...

thanks for the tip

---

### Post by spupy on 2007-12-07
> **rubberglove said:**
> But, playing with wmctrl, I realized it can be even simpler - the window can just be addressed using the window name, instead of the id.

Yes, i thougth of that, but the gnome calculator has different titles for different modes, so...
Thx for the code additions, you seem good at bash scripting. ;)

---

