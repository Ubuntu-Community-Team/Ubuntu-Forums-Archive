---
title: "The Compiz Metacity bug is Worse in 11.4- No Cube"
date: 2011-04-30
forum: Desktop Environments
---

### Post by Densdoor on 2011-04-30
[COLOR=red] Well I upgraded to Ubuntu 11.4 to get the bug  fixed to run my printer. Under "Classic" mode I finally got my cube  back. I said finally because NOW it stops working when you switch to  Metacity to fix the windows tops (close, minimalize buttons) So now what  was just a bug that did that now turns off cube altogether when  choosing Metacity. I need my cube or I'll ditch the whole Ubuntu!

 I need  Metacity window tops and cube working at same time. [/COLOR][COLOR=red] I can log out and back in and the cube is back, but window tops are gone  too. Applications/System Tools/ Compiz Fusion Icon and under Select  Window Manager- Metacity is "Checked" (quote unquote) but to recheck it  used to JUST fix window tops and NOW it takes the cube away. WHY oh WHY  Cant we have things work! 
[/COLOR]


[COLOR=red]I hope they fix it or somebody can help. I also note the Simple Compiz Manager wont be set cause it says conflicts. (Not that this was a fix for this but....)
[/COLOR]
[COLOR=red]-Dennis
[/COLOR]

---

### Post by mc4man on 2011-04-30
log out, then in (to compiz
Open ccsm and enable the Window Decoration plugin

(if the cube is a compiz plugin how do you propose to run it in  metacity?

---

### Post by Densdoor on 2011-04-30
It ALWAYS worked before under MetaCity  windows. The Cube in 10.10
It still does when you log in fresh but then windows tops are gone. The box is checked Metacity and you recheck it and bamm windows have tops and cube is gone.
In 10.10 windows got tops when you did all that but Cube stayed (in metacity)

-Dennis

I enabled that windows Decoration BTW.

---

### Post by Densdoor on 2011-04-30
Right now-

I switched to Compiz and not Metacity. I got window tops (after reboot)

My windows under Compiz also had and have a second problem- They were stuck to the top of screen. I found setting in Manager Enaable Move etc...

I think it is fixed now.

-Dennis

Thanks [mc4man]("http://ubuntuforums.org/member.php?u=320715") - I really do not understand things exactly, Just been observing it. I am new to Ubuntu as of a week ago.
I have windows TOPS and Cube spinning under Compiz not Metacity now. Thats goal.

---

### Post by mc4man on 2011-04-30
When you tried to switch from wall to rotate/cube it's likely all the compiz plugins got unset. That's why you lost window deco ect.
It's possible you still may have some useful ones disabled, though the upside was you got rid of some unuseful ones (particulary when using rotate (which I use

If inclined you could do this - open a terminal and type  ccsm, press enter. Let it fully load and you'll see all the plugins loaded listed in the terminal
You could copy and post

Ex. here's what I'm using atm w/ rotate/cube, 
> ~$ ccsm
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Clipped....
Initializing compiztoolbox options...done
Initializing scaleaddon options...done
Initializing mousepoll options...done
Initializing text options...done
Initializing move options...done
Initializing gnomecompat options...done
Initializing regex options...done
Initializing decor options...done
Initializing scale options...done
Initializing opengl options...done
Initializing fade options...done
Initializing expo options...done
Initializing cube options...done
Initializing composite options...done
Initializing animation options...done
Initializing resize options...done
Initializing rotate options...done
Initializing unityshell options...done
Initializing vpswitch options...done
Initializing place options...done


---

### Post by Jesus_Valdez on 2011-05-01
The cube is a feature of Compiz, is impossible to having working under Metacity.

I don't understand what you mean by "windows top", you mean the bar with the windows name or what are you trying to fix?

Are you trying to move the order of the buttons in the windows?

_________________________-


Ohh I remember something, for some unknown reason in 10.10 windows didn't have decoration when I log in, is that your problem? When you log in windows appear "naked"?

I fixed that really easy by just adding the command "compiz --replace" (without quotation marks) to Startup programs.

---

### Post by Densdoor on 2011-05-01
OK You people are speaking from a knowledge perspective. I am just speaking from what I seen and experience with a partial ignorance of what Metacity even means, etc....

10.10 came with Metacity (I think) I went about installing everything Compiz I could and proceded to set my Cube up.

Under Applications/ System Tools/ Compiz Fusion Icon
Now under Icon when loaded- It said Select Window Manager
Choices are Compiz or Metacity.

When I started to get no tops to my windows
Which means in my crude way of saying it No Close (X) No Minimalize, and no Open all the way and no title

You had to close windows from the bottom tray.

If you switched the thing Back (I think) to Metacity then windows would have tops again and cube worked fine. 

PROBABLY and I am know seeing this was not supposed to be happening.

I know in Ubuntu 11.4 the Classic does not let you install the Simple Compiz config thing as it states there is a conflict.

I didn't fully understand Compiz config which (full controls with wobble window, etc... as you had to check many things (dont get bogged on that ) Iam just saying I did not know too much and......

Back to Metacity- I THOUGHT that was a windows look with the tops of windows and you could move windows and rezize etc... as when it rock and rolled with no window tops I switched to Metacity and then all that would be fixed and cube also worked (10.10 NOT 11.4 which apparently fixed)

Now Iam getting Metacity is Not a Windows appearance but a WALL version desktop where the cube panes just load as screens and no rotate see cube, etc...

(Oh also note- Metacity would be checked when it rocked and rolled but you had to selct the check like you were checking it and then the windows tops would be there and the cube worked- 10.10)
-Dennis

THANKS ALL, because I am learning and loving all this!

---

### Post by Jesus_Valdez on 2011-05-01
OK here's what you are going to do.

Next time you log in and see no windows borders you are going to open a terminal (Programs / Accessories / Terminal) and write:

> compiz --replace


That should give you window borders and the compiz effects, like the cube.

---

### Post by Densdoor on 2011-05-01
Jesus-

I was talking experience of what I saw.
My 10.10 had things working that were not supposed to.
When it rock and rolled into Compiz settings when I was moving the cube BUT STILL HAD METACITY box checked.........

Then I saw no window tops and windows couldn't do various things. WHY?????
Because you have to configure all that in Compiz Manager- the window settings but not in Metacity.

So when I upgraded to 11.4   The Metacity checkbox (WHICH I ALWAYS had checked in my 10.10 gave NO CUBE so I thought 11.4 had the bug. It was my 10.10 which was whacked out .

So NOW I installed 11.4 Ubuntu and run in classic mode with my Compiz cube and am set to Compiz Windows in manager and etc.... read above.

Anyhow I say NOW- HOW IS IT GOING TO HAPPEN AGAIN. It will not. 

Now When I thought I had a bigger bug, I had no bug, but was used to how things worked when I had to work around the bug.

Thanks anyhow-
Dennis

11.4 fixed my problem of conflicting stuff working together. I now had to learn right way to use.

---

### Post by Densdoor on 2011-05-01
Jesus,
Before I had two things-
The system not working AS IT SHOULD in 10.10
and me not understanding what was what.

Now both are fixed.

But you were saying - would have fixed problem in 10.10 but it got fixed via upgrading.

THANKS-
-Dennis

P.S. the reason I upgraded in the first place was spending 4 hrs trying to get my printer to work, then on upgrade reboot, it did it on a click!

---

