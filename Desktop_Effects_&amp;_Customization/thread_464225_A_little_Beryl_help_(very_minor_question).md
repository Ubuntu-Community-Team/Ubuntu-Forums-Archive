---
title: "A little Beryl help (very minor question)"
date: 2007-06-04
forum: Desktop Effects &amp; Customization
---

### Post by ticopelp on 2007-06-04
Hey, this is not an emergency -- Beryl is working fine on my machine, but I was toying with some settings and I seem to have changed something. Previously, in the panel window list, Beryl would only show the taskbar items for a particular desktop, i.e. if I switched to another virtual workspace, all the items in the previous workspace's taskbar would not show up in the new workspace's window list. I hope I'm being clear about what I mean here.

Anyway, I seem to have changed something, or something bugged out, so that now the window list items for ALL my workspaces show up in all the window lists. Since I tend to have a lot of programs open and flip between workspaces a lot, this means a very crowded taskbar. I've searched all over for the option I seem to have accidentally checked, but I have no idea what I might have changed. Any ideas? 

Thanks.

---

### Post by blackened on 2007-06-04
This is a setting in the "Window List" panel applet. Right click the Window List, go to Preferences, in the "Behavior" tab select "Show windows from current workspace".

---

### Post by ticopelp on 2007-06-04
> **blackened said:**
> This is a setting in the "Window List" panel applet. Right click the Window List, go to Preferences, in the "Behavior" tab select "Show windows from current workspace".

Thanks for the reply! I just checked the preferences, and it currently is set to just show windows from the current workspace. And yet all the windows show up in all the workspaces. 

I should also mention that when I set my window manager to Metacity, the windows and workspaces behave as they should... that's what led me to believe it's a Beryl thing.

---

### Post by blackened on 2007-06-04
Hmm, I guess I had never noticed this before. I can't find a setting anywhere in the beryl manager that has any effect on this. It's either a bug or an oversight (of ours and theirs).

---

### Post by ticopelp on 2007-06-04
> **blackened said:**
> Hmm, I guess I had never noticed this before. I can't find a setting anywhere in the beryl manager that has any effect on this. It's either a bug or an oversight (of ours and theirs).

Yeah, I can't find anything either. 

Thanks for your help anyway!

---

### Post by blackened on 2007-06-04
No worries, I have a feeling the option is there, I'm just overlooking it or it's well hidden.

---

### Post by mikec13 on 2007-06-06
I had the same problem yesterday...  Here's what fixed it for me:

"Author:   	dwallor [ Sat Feb 24, 2007 5:54 am ]
Post subject:  	Re: How do I get each cubeface to be a different workspace?
Unfortunately, the Window List Content property is not the problem. The problem occurred for me no matter what the Window List Content property was set to.

Fortunately, I found the solution a few minutes ago.

Short Answer:

Open Beryl Settings Manager, go to General Options, and change "Number of Desktops" to 1. Cube will not be affected, each Cube viewport will become a separate workspace, and Window List will only show windows on current viewport. Remember to still make sure that the Window List properties are set to "Show windows from current workspace".

Explanation:

"Number of Desktops" in Beryl Settings Manager apparently changes that same setting as when you change "Number of Workspaces" in the Gnome Panel's Workspace Switcher properties. It has no affect on how many sides your cube has . If it's set to anything higher than one, then the Cube viewports apparently can not be considered separate workspaces by Gnome. If it's set to one, then each side of the Cube will be considered a workspace since you don't have multiple Gnome workspaces.

Additionally, setting "Number of Desktops" or "Number of Workspaces" to "1" allows you to use the Gnome Panel's Workspace Switcher jump to a different part of the cube. "Show names in switcher" apparently does not function correctly in this mode, and "Show only the current workspace" vs "Show all workspaces" has not affect on the Workspace Switcher.

Once you've reduced the number of Gnome workspaces to 1 so that Cube can take over, you can still choose "Show windows from current workspace" or "Show windows in all workspaces" in Window List, so make sure have that set to the first setting.

if you use Window Selector (the drop down menu of windows), it apparently loses the multi-workspace functionality when Cube is in control of the workspaces. Normally, it will separate the list by workspace with a line between each workspace. If you set Gnome's workspaces to 1 so that Cube can take over, Window Selector will list them all as if they're on one workspace. I have it on my panel, but I rarely use it, so I'm not really concerned about it."

[http://forum.beryl-project.org/viewtopic.php?f=39&t=3897&start=0&st=0&sk=t&sd=a&view=print](http://forum.beryl-project.org/viewtopic.php?f=39&t=3897&start=0&st=0&sk=t&sd=a&view=print)

---

### Post by ticopelp on 2007-06-06
Thanks a lot, mikec13. That is in fact the solution; I found it on another site and was just coming here to post that same thing! Thanks a lot!

---

### Post by blackened on 2007-06-06
A ha, I knew it was there somewhere. Thanks for the help mikec13.

---

