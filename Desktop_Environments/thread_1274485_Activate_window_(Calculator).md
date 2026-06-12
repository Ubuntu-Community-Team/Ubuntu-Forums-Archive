---
title: "Activate window (Calculator)"
date: 2009-09-24
forum: Desktop Environments
---

### Post by Wild_Doogy on 2009-09-24
2nd time installing Ubuntu on my computer, went back to windows for games over the summer, and I am really loving 9.04.

I just installed Qalculate and got it to replace the normal calculator, but I have one problem/grievance: When I press the calculator button on my keyboard, Qcalulator opens up just fine, EVEN if I ALREADY have one open. this makes logical sense from the computer's point of view, but I am wondering if it would be possible to have Ubuntu search to see if its already running and "bring that window to top" if it finds it?

guessing I am going to need a bash script or something of the sort, but I have no idea how I would do this.



Wild_Doogy

---

### Post by Giblet5 on 2009-09-24
That's the default behavior.

To clarify: you want a "launch-new/raise-existing-to-current-desktop" script?

That depends on a lot of things like what desktop you use, how many screens you have defined, multiple desktops, etc.

It can be done, sure, but if you aren't a shell programmer I'd recommend using the taskbar or Avant then look at it and see if it's open already.

---

### Post by Wild_Doogy on 2009-09-24
> **Giblet5 said:**
> That's the default behavior.

To clarify: you want a "launch-new/raise-existing-to-current-desktop" script?


Yes,exactly.

> **Giblet5 said:**
> That's the default behavior.
That depends on a lot of things like what desktop you use, how many screens you have defined, multiple desktops, etc.

It can be done, sure, but if you aren't a shell programmer I'd recommend using the taskbar or Avant then look at it and see if it's open already.


Ok, sounds like I should just deal with it. Not too much of a problem, when I am doing school work, I shouldn't have any other windows open anyways.

(I'll just close Youtube now :P)


Wild_Doogy

---

### Post by kaibob on 2009-09-24
You can try the following, which works for me. You have to change the command to start the program and the title, which is a portion or all of the text string shown in the title bar. Qalculate would be good because it's unique.

I dont' know if wmctrl is installed by default. If not, it's small and in the repo's. 

```
#!/bin/sh

command="/path/to/Qalculate"
title="Qalculate"

running=$(wmctrl -l | fgrep -o -m 1 "$title")

if  [ "$running" ] ; then 
   wmctrl -a "$title"
else
   $command
fi
```

EDIT 11.14.09

I found an alternative approach that does the same thing but works a bit faster. It uses the xdotool utility, which is in the repo's. For example:

```
#!/bin/sh

title="Mozilla Firefox"
command="firefox"

number=$(xdotool search -title "$title")

if  [ "$number" ] ; then 
   xdotool windowactivate "$number"
else
   $command
fi
```

EDIT: 04.25.10

I found a third approach that is simplest by far and, based on some timing runs, is actually the fastest. The following is a sample that loads Firefox:

```
#!/bin/sh

title="Mozilla Firefox"

command="firefox"

wmctrl -a "$title" || $command
```

BTW, the second approach, involving the xdotool utility, does not work correctly under compiz with lucid. I don't know why.

---

### Post by Wild_Doogy on 2009-09-26
Thanks Kaibob! That did the trick.

I had to install wmctrl
```

sudo apt-get install wmctrl

```


and I had to do a little editing to the script, thanks for writing the code for me, works like a charm.



```


#!/bin/sh

command="gcalctool" # command to run the program
title="Qalcula"  # part of the window title.

running=$(wmctrl -l | fgrep -o -m 1 "$title")

if  [ "$running" ] ; then 
   wmctrl -a "$title"
else
   $command
fi


```



I then saved this to a file called test.sh and set "Allow executing file as program" in properties, under the Permissions tab.

every time I click on it, it brings my program to the top, running a new one if there isn't one running.



Wild_Doogy

---

