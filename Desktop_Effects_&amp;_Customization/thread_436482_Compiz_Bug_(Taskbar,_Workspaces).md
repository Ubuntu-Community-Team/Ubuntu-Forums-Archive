---
title: "Compiz Bug (Taskbar, Workspaces)"
date: 2007-05-07
forum: Desktop Effects &amp; Customization
---

### Post by mike richards on 2007-05-07
hey guys,
i have this problem while using compiz (desktop effects that came with 7.04). when i open certain programs (firefox, thunderbird, totem, and probably some others) they stay in the taskbar on all of my 4 workspaces. and if i try to open it from the taskbar on another workspace than the one i opened them on, it will rotate the cube and switch to the workspace that i opened the program in. although if i disable desktop effects the problem does not exist, so i know it has to do with compiz (desktop effects). I have tried re-installing ubuntu 3 times, and it doesnt fix it. infact the bug is there even with a perfectly fresh install  of ubuntu, and the first thing i do is try out to see if the bug is there, and its still stuck on all workspaces in the taskbar.

has anyone else have this problem, or know how to fix it?

Thanks in advance.

---

### Post by go_dragons on 2007-05-08
I have not had exactly the problems you described but I too am having a problem with the workspaces when I enable compiz in 7.04. I hope you dont mind me tagging on my problem since these are related topics.

The wobbly windows work great, but whenever I enable desktop effects my pager always defaults to one workspace. I change it to 3 workspaces by right-clicking the pager and using the preferences dialog box. After that if I try to change workspaces it does NOT do the cube effect and I lose my taskbars as well. I can move other windows into the different workspaces and they continue to work as usual, but no taskbars except on the first workspace.  I have this problem reguardless if I have the 'cube desktop' effect enabled or not.

Perhaps I need to change a compiz pager setting instead of the gnome pager?

---

### Post by kpolice on 2007-05-08
One workspace is the way it works, it's not a bug.

It's like 4 work space but sticked together into one so it can be mapped into the cube.

---

### Post by mike richards on 2007-05-08
kpolice, would you care to explaine? i dont see how it would make sense to only make a few programs stay in all the workspaces taskbars.. and all the rest act normal and remain in the workspace that i opened it in. i find this extremely frustrating. i asked in #ubuntu IRC channel and they said it was a bug, but why is it only me who has this? i dont think they would make compiz like this purposely. by the way, even if i disable workspace cube. and just use classic workspaces. the issue still exists, but this time those certain programs (firefox, thunderbird, totem) are actually able to be opened on other workspaces, thats even MORE messed up. and all the others programs stay in the workspace where it should be, like NORMAL.. man this is annoying.. 

heres an easier way to explaine my problem.. when you start up ubuntu. and you open lets say, for example, 3 windows and one of those windows is firefox.. now you switch to a different workspace.. what is supposed to happen?? its supposed to be a blank taskbar and a fresh area to work. right? well not for me, firefox is still in the taskbar. and if i try to open it (click on it), then it rotates the cube back to the first workspace where it originally was launched in.

if you watch this [VIDEO]("http://www.youtube.com/watch?v=ZNvKfHWu4O0") from (1:10 - 1:12) you will see him switch workspaces, and they have new empty taskbars. thats what it should be like.
sorry if my problem still isnt clear, i find it difficult to explaine the issue im having. if it is, let me know and ill try to explaine better.
thanks for the replies.i really would like to get to the bottom of this.

Note: when i say "Taskbar" i mean the "Window List". I think thats what its called in ubuntu.

---

### Post by mike richards on 2007-05-08
any ideas on what could possibly be causing this?

---

### Post by mike richards on 2007-05-09
actually, i decided to make a video of my problem. i really would like some help on this.  here is a screen cast of my problem.

[http://www.youtube.com/watch?v=OD8NJFZkmJE](http://www.youtube.com/watch?v=OD8NJFZkmJE)

i open a few windows, one of them being firefox. then i switch to a different workspace and firefox is still there??? why? the rest of the windows remain only in the workspace they were launched in, and firefox should do the same. i want a new empty taskbar. thats how it should be like.

then if i click on the firefox tab in the taskbar from a different workspace, it will rotate the cube back to the workspace that i launched it in.

all of this also applies to thunderbird, and rarely totem.

Please help me out here, Thanks in advance.

---

### Post by vnkatesh on 2007-05-09
i also face the same problem... both that some of the windows open in one workspace appears on the taskbar on the other workspace and reloading compiz reduces the number of workspaces to 1, which can be increased by preferences,... happens even with fresh install... should be some bug...

---

### Post by mike richards on 2007-05-09
wow, this is extremely wierd i just realized something. if i launch forefox/thunderbird from the quicklaunch or the applications menu, it works perfectly normal and only in one worspace (good).. but if i launch it from the desktop icon, then the problem persists.. so now i know it has to do with compiz.. and with launching from desktop icon..

---

### Post by thx_1138 on 2007-05-09
I had the same issue where i would lose my cube effect
Just install "gnome-compiz-manager" package using your own prefered method (synaptic or terminal)
This will install an entry under System--->Preferences--->GL Desktop
Run it and select the workspaces tab and under viewports simply enter 4 to get back your cube.
At least that how it worked for me...... good luck

---

### Post by mike richards on 2007-05-09
thnx_1138, yea, i already have "gnomne-compiz-manager" installed, and i use GL Desktop for all my settings.. btw i dont have any problems with my cube.. it functions perfectly fine.. the problem is with firefox/thunderbird and compiz workspaces..

[http://www.youtube.com/watch?v=OD8NJFZkmJE](http://www.youtube.com/watch?v=OD8NJFZkmJE)

i find it hard to beleive im the only one who has encountered this problem..

can someone try it out and see if its the same for them? heres what you do.. make a desktop icon for firefox (drag it from the applications menu), and then launch firefox from the desktop icon. then rotate to the next workspace and see if firefox is there..

thanks again.

---

### Post by brickbat on 2007-10-19
I had the same problem.  I figured it out.  In short the problem is the virtual desktop settings in compiz.

Here is how i fixed it.  I went through this procedure because i was also having problems with the workspace switcher.

1. Make sure your panel workspace switcher is working properly.  If it isnt remove it from your panel and then add a new one. Right click it and set the number of workspaces you want. Remember this number.
2. Reset all compiz settings in System/Preferences/Advanced Desktop Effects Settings/Preferences/Reset to Defaults
3. Set Workspaces properly Click on Back to go back to the compiz settings main menu and select General Options/Desktop Size and Select X,1,1 where X is the number of workspaces you had in the workspace switcher.
4. Reselect other compiz features you want

Bob should be your uncle.

---

### Post by JoelP on 2008-03-05
Hi,

I am having the same problem now with Gutsy. Was there a fix found?

It seems like there a two concepts for a workspace - one provided by Compiz, the other by whatever normally provides workspaces (Gnome itself?).
When I right-click on the application's icon in its in window (the at top left), there is "Move to workspace Right" and "
Move to another workspace >" which expands to "Desk 1" and "Desk 2". Yet I have four deskops in a cube, not two. When I click "Move to workspace Right", the window disappears - never to be seen again.
I suspect all the windows are showing up in the taskbar on every desktop because the taskbar is using the wrong workspace concept - in which all windows are on Desk 1.

I hope that made some sense. Aynways, perhaps there was a fix found already?

Thanks.

---

### Post by JoelP on 2008-03-05
Somehow I didnt see the post by brickbat.

But still no luck none-the-less.

When I loaded up the workspace switcher in the panel, it confirmed my suspicions that are two programs trying to give me workspaces functionality at once. When I change workspace using the panel applet, the windows disappear just like they do when 3D is off. but I can also do 3D workspace switching - but the workspaces aren't the same. workspace 2 from the panel is not the same as workspace 2 in compiz.

---

### Post by JoelP on 2008-03-05
I feel like a tard for replying to myself so many times.

Fixed.

I should have looked around a bit more first. Found the here
[http://ubuntuforums.org/showthread.php?t=566395](http://ubuntuforums.org/showthread.php?t=566395)
at Post #7
I had Number of Desktops set to 2. I must have done this while trying to get dual screen working. Taskbar and dual screen both work fine when this value is 1.

---

