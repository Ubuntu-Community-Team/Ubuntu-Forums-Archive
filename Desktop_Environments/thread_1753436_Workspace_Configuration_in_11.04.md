---
title: "Workspace Configuration in 11.04"
date: 2011-05-09
forum: Desktop Environments
---

### Post by peaceFrogs on 2011-05-09
In Unity, is there a way to have applications start up on different workspaces at login. Example, when I login I want the terminal and a blank text document to open up on workspace 2 and chrome to open on workspace 3. 
I am also wondering if it is possible to name each workspace.

Thank you in advance

---

### Post by Copper Bezel on 2011-05-09
Yes and no. There's a package called wmctrl that can be installed from the repositories and that can move windows around from a shell script. That means that if you have two programs in your Startup Applications, you can also put a bash script that invokes wmctrl in your startup applications to move them to the appropriate workspaces simply by moving them to the appropriate position on the virtual desktop with x,y coordinates. 

```
wmctrl -r gedit -e 0,1500,-1,-1,-1
```

where "gedit" represents some part of the window's title, non-case-sensitive; "-e" is the option for a geometry modification; "0" is the window's gravity and shouldn't be changed; "1500" stands in for the desired x value of the window, which you'll have to adjust to the size of your desktop; and the "-1"s indicate that other geometry values (width and height) should remain unchanged.

This script will also need to be delayed, since it will start the moment you click the log in button but needs to wait until all the windows you've decided to run have launched. The first line of the script would need, then, to be something like 

sleep 40s;

Your final script will look something like

```
#!/bin/bash
sleep 40s;
wmctrl -r gedit -e 0,1300,-1,-1,-1;
wmctrl -r @ -e 0,1600,-1,-1,-1
wmctrl -r Chrome -e 0,-1,1000,-1,-1
```

to wait an allotted period of time, move gedit and the terminal to the workspace on the right, and move Chrome to the workspace below.

---

### Post by peaceFrogs on 2011-05-09
Didn't end up trying your solution copper, but I managed to find something else that works for me. Went to the 'Place Windows' plugin for compiz, then under the 'Fixed Window Placement' tab there is an option called 'Windows with fixed viewport.' Here I created a viewport on which each application is to open. Its pretty self explanatory from here.

So again its ccsm>Place Windows>Fixed Window Placement>Windows with fixed viewport

---

### Post by Copper Bezel on 2011-05-09
Oh, cool. I knew that Put could be used to move windows by a keybinding, but I've never really played with Place. I'm also really, really liking Place's "modes", which again I'd never played with - "Under Pointer" is *nice*.

---

