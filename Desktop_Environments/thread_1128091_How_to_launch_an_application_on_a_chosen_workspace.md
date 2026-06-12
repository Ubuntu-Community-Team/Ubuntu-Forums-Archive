---
title: "How to launch an application on a chosen workspace?"
date: 2009-04-17
forum: Desktop Environments
---

### Post by ub40d on 2009-04-17
I have a multi-workspace setup, with the "workspace switcher" gadget in a corner of the screen that lets me select one of six (3x2) workspaces.

I would like to be able to launch specific applications in specific desktops (eg from scripts), e.g.

   firefox --workspace 0 1
   evince --workspace 0 2

or

   launch-in-workspace 0 1 firefox
   launch-in-workspace 0 2 evince


(or whatever). Is anything like that possible?

The closest I found was the CompizConfig Settings Manager, as specified in this thread: [http://ubuntuforums.org/showthread.php?t=844385](http://ubuntuforums.org/showthread.php?t=844385)

That allows me to say, for example, that Firefox should ALWAYS appear on workspace 0 1 and evince on 0 2, which is subtly different. For example, if I subsequently double-click to open a pdf in any other workspace, then the pdf window opens in the designated evince workspace instead of where I am (and want it).

So I don't want a global configuration to say "the windows of this application shall always go in that workspace". Instead I would like a command-line option, or a wrapper, that lets me say where to put the application I'm launching, for THIS invocation and not globally, so that I could do for example

launch-in-workspace 0 1 evince document1.pdf
launch-in-workspace 1 1 evince document2.pdf

Is this possible? How?

Thanks

---

### Post by Scubdup on 2009-04-17
I thought I saw something like this asked before. I'm new and ddoubt I can help but just for clarity:

You don't want all instances of a particular app to open in one set workspace.

Rather,

You want an options box each time you open an app (or all apps) that asks which workspace you want it to open in.

Is that right?

---

### Post by ub40d on 2009-04-17
> **Scubdup said:**
> I thought I saw something like this asked before. I'm new and ddoubt I can help but just for clarity:

You don't want all instances of a particular app to open in one set workspace.


Correct.

> 
Rather,

You want an options box each time you open an app (or all apps) that asks which workspace you want it to open in.

Is that right?

No, sorry for being unclear. I definitely DON'T want an INTERACTIVE dialog box asking me each time! Rather, I want something I can use from a command-line script.

When I launch an app the clickety-click way, I just want it to appear in the workspace I'm in.

From a script, however, I want to be able to say: and now open these half dozen apps, putting this one here, that one there, that one over there etc etc. And I want to be able to write different scripts that put the various applications in different places, as needed, WITHOUT this constraining the positions of the applications when I invoke them interactively.

Thanks for helping me clarify. Let me know if it makes more sense now.

---

### Post by zhocchao on 2009-04-17
for your script you can use wmctrl

---

### Post by Scubdup on 2009-04-17
> **ub40d said:**
> From a script, however, I want to be able to say: and now open these half dozen apps, putting this one here, that one there, that one over there etc etc. And I want to be able to write different scripts that put the various applications in different places, as needed.Ah, I see. So without changing anything else, you want a script that opens a particular set of apps in a particular set of windows, say, for eg Load Firefox in workspace 1, Rhythmbox in Workspace 2 playing tune X, and Deluge in workspace 3.

There's prolly a simpler way but [bblaunch]("http://linux.about.com/cs/linux101/g/bblaunch.htm") sounds like it might work...

EDIT: Scratch that, zhocchao's recommendation wmctrl looks better supported.

---

### Post by ub40d on 2009-04-17
> **zhocchao said:**
> for your script you can use wmctrl

Thanks for this suggestion! After a bit of a struggle I finally got it to work (mostly).

Main problem was that the man page has a nice-looking -t option (send window to specified desktop) but it didn't do what I expected because I wanted to send to another WORKSPACE, not to another desktop.

I finally figured I have only one DESKTOP with six workspaces on it, as indicated by:

wmctrl -d
0  * DG: 7680x3200  VP: 0,0  WA: 0,25 2560x1550  N/A

Once I got that, I realized that I couldn't just say "send to workspace n" but I had to compute the new coordinates myself and then change the window's geometry offset. And yes, this works:

Send thunderbird to workspace 0,1:
wmctrl -r thunderbird -e 0,2560,0,-1,-1

Send it to 1,2:
wmctrl -r thunderbird -e 0,5120,1600,-1,-1


So thanks a lot for the tip and I hope the examples above are of help to the next guy with the same problem.

Now the remaining problem I have is that this stuff only works after the window exists. So if my script does

thunderbird
wmctrl -r thunderbird -e 0,5120,1600,-1,-1

then what actually happens is that thunderbird is launched, then the second statement is executed before the thunderbird window exists (and therefore it fails), and then the window appears, in the wrong place of course.

Is there a way to tell wmctrl to wait for that window to appear?

---

### Post by zhocchao on 2009-04-17
use sleep in your script

---

### Post by ub40d on 2009-04-17
Hmmm... you know that's not what I meant I hope... how can I tell when the window has finally appeared? (so that I can stop sleeping)

For now I'm trying with a mix of wmctrl -l and fgrepping the output, but that's a bit disgusting.

---

### Post by arvevans on 2009-05-28
**zhocchao**

Thanks for the info on wmcrtl.  I asked about this in release 8.04, and again in 8.10, but didn't get any response.  Now I know how to do it.

My interest is in adding scripts to start up so that certain workspaces are automatically pre-populated with selected applications when the system boots up.  wmcrtl with a short sleep seems to do exactly what I wanted.

**ub40d**

Thanks for raising this question again.  I had given up on ever finding the answer.

Arv
_._

---

### Post by piyush.popli on 2011-09-09
I know it's been more than 2 yrs since anyone replied on this post and all, but I found this post to be quite helpful and to (sort of) return the favor: @[ub40d]("http://ubuntuforums.org/member.php?u=725420") maybe this might help [http://www.foosel.org/linux/devilspie](http://www.foosel.org/linux/devilspie) (if you're still interested that is).. 

Thanks
Piyush

---

### Post by roberg@iafrica.com on 2012-02-10
I come all the way from IBM S360. In the early 80's I started on cp/m, then (for practical reasons, I have to use what my customers use) I switched to MSDOS 1. I have been through *every* release since then, including every Win release. (You may commisserate.)

In 2009, I started to move to Ubuntu (thanks to VirtualBox, I can satisfy the customer need).

I am a true believer regarding the principles of Open Source, but I must tell you, it has been a bit like changing religions or politcal parties.

Getting one's head around this is not an easy matter. Eish!

I love the idea of different workspaces and apps running in a particular workspace. I have allocated CTL+ALT+[1..=] (US Keyboard) to 12 workspaces, and always open my most used apps in the same workspace. 

I have been looking for a quick way to launch these, but not as a startup routine, because I sometimes need to just quickly start up, do something, and do not want to replicate the Windows loooooooong start up process.

So, this discussion seems just the tickect. But jsut how to do it, still beats me. 

Would someone be prepared to share an actual script file with a bit of instruction on how to edit/run it?

Unfortunately, I don't get much time to play in the tech space I would like to anymore, and so i have to relearn how to do these things every time a do it again.

The little grey cells seem to have a real problem with data loss! :(

---

### Post by Krytarik on 2012-02-10
> **roberg@iafrica.com said:**
> I love the idea of different workspaces and apps running in a particular workspace. I have allocated CTL+ALT+[1..=] (US Keyboard) to 12 workspaces, and always open my most used apps in the same workspace. 

I have been looking for a quick way to launch these, but not as a startup routine, because I sometimes need to just quickly start up, do something, and do not want to replicate the Windows loooooooong start up process.
[..]
Would someone be prepared to share an actual script file with a bit of instruction on how to edit/run it?
If you are using Compiz as your window manager, please see this thread:

[http://ubuntuforums.org/showthread.php?t=1847298](http://ubuntuforums.org/showthread.php?t=1847298)

Regards.

---

