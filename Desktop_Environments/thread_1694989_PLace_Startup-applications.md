---
title: "PLace Startup-applications"
date: 2011-02-25
forum: Desktop Environments
---

### Post by Mathias1 on 2011-02-25
Hi!
(First post ^^)
 
I'm using Compiz to place windows in different workspaces.
So, I want a terminal window to start when i boot as a startup application, but I want to place it on workspace 4 (i know how to do this) BUT, when I open a new terminal, i want it to open in my CURRENT workspace.
 
How can i make this happen?

**UPDATE!: ** New problem described on page 4.

---

### Post by Copper Bezel on 2011-02-25
I'm assuming you're using Devil's Pie, then? Since Devil's Pie uses the application name to identify a window, it's not really going to happen unless there's some way to distinguish the window instances. Have you considered just using a different terminal emulator app for the permanent one on Workspace 4, like xterm?

---

### Post by Mathias1 on 2011-02-25
Actually, no...good idea...I could use the Root-terminal, correct? Or is it the same instance as a "regular" terminal?
 
 
What is Devil's Pie exactly? I'm a beginner, but very thirsty for knowledge :)

---

### Post by Krytarik on 2011-02-26
I would use "wmctrl" for those very Startup Application. Basically running two command after each other, the first to open the terminal, then the wmctrl command to immediately move it to the desired workspace.

"wmctrl" is in the official repos.

Manpage: [http://manpages.ubuntu.com/manpages/maverick/en/man1/wmctrl.1.html](http://manpages.ubuntu.com/manpages/maverick/en/man1/wmctrl.1.html)

Greetings.

---

### Post by Copper Bezel on 2011-02-26
Wow, I'd never played with wmctrl. Some neat tools there, although the one thing I couldn't make work myself was moving the item to a specified desktop. I imagine I'm doing something wrong, though.

```
djmcbratney@Sophie:~$ wmctrl -r "fred" -t 0
```

By way of explanation, Mathias, Devil's Pie is a daemon that allows you to specify rules for applications to start maximized, minimized, set to a specific desktop, etc. It's in two parts: the daemon, called devilspie , and the app that controls it, gdevilspie. Krytarik's solution is much simpler and isn't going to cause any extra headaches. 

The simplest way to run both of those commands (to run the terminal, then to move it with wmctrl) would be to make a script: create a text document, put those commands on two separate lines in that order, allow executing the document in its Properties, then set that script in your startup applications.

This is, again, just info for the future, but a root terminal is the same application as an ordinary one, just run by root. You wouldn't want to have it running at start up for at least two reasons - one, it'd ask you for a password, and two, you don't want to accidentally run a command under root when you mean to run it as your user profile, because root doesn't have access to your application settings and because generally anything root does can't be reversed as a regular user. (You might move a directory as root, for example, and then have to elevate to root to delete it later.)

---

### Post by Krytarik on 2011-02-27
Sorry, I didn't mention the root-terminal, I thought it was obvious enough that it has serious implications. ;-)

Unfortunately the <DESK> variable of wmctrl doesn't work currently. So, you have to use absolute "-e <MVARG>" to move windows.

For example, I have to use the following command to switch to my second viewport, instead of simply running "wmctrl -s 1":
```
wmctrl -o 1152,0
```

---

### Post by Mathias1 on 2011-02-27
OK, so I need to create a .sh script, assign it to startup applications.

What will the actual script look like if i want to start a terminal in Workspace 4?

terminal
wmctrl "terminal" -o 4,0

---

### Post by Krytarik on 2011-02-27
> **Mathias1 said:**
> OK, so I need to create a .sh script, assign it to startup applications.

What will the actual script look like if i want to start a terminal in Workspace 4?

terminal
wmctrl "terminal" -o 4,0
Instead of a script you could also use a command like this in the launcher:
```
sh -c "gnome-terminal && wmctrl WHATEVER"
```Sorry for confusing you with the command I posted, those is for a different application of wmctrl, to switch *your view* on the desktop to another workspace.

To move the terminal window to another workspace, you have to consider the following:
- The window's name isn't "terminal", but for example in my case "krytarik@krytarik-desktop:...".
- What are the x/y values of the workspace you want to move it to?
- Where would you like to place the window in the chosen workspace?

So, for example I want to move my terminal window to my second workspace, and place it nearly in the middle of it:
- my screen resolution is 1152x864
- so, the second workspace starts with 1152,0 (x,y)
- "xwininfo" turns out 654x433 (width/height) for the terminal
- so "1152 - 654 / 2" turns out "249" for the offset, plus "1152" for the second workspace results in "1401" for x
- and "864 - 433 / 2" turns out "215" for y

So, my command would be:
```
wmctrl -r krytarik@krytarik-desktop -e 0,1401,215,-1,-1
```Of course you could just use the upper left corner if you like it there, and to avoid such an calculation. ;-)

So, I assume you ordered your workspaces 2x2, so workspace 4 would be the lower right one, the (simple) command for my desktop would then be:
```
wmctrl -r krytarik@krytarik-desktop -e 0,1152,864,-1,-1
```

---

### Post by Mathias1 on 2011-02-28
This was kind of advanced :P
 
I have a workspace grid of 4x0 (4 spaces in a row, to be clear :) ) and I want the terminal window maximized.

---

### Post by Copper Bezel on 2011-02-28
What's the resolution of the screens? You'd need to place it 3x the width of your screen to the right. It'll start in workspace 1's upper left, and we need to move it to workspace 4's.

---

### Post by Krytarik on 2011-02-28
To maximize the window you can use another capability of wmctrl, but unfortunately both commands have to be run after each other, so I indeed recommend a script now, to have not such a long line.

Or you get the height/width values of the maximized window by using "xwininfo", and set the size also with the "-e" options.

Taking my resolution as example again, x would be "3456" :P, and the script would look like this:
```
#!/bin/sh
gnome-terminal
wmctrl -r krytarik@krytarik-desktop -e 0,3456,0,-1,-1
wmctrl -r krytarik@krytarik-desktop -b toggle,maximized_vert,maximized_horz
```In your case I would also do another thing: Remove the window decoration from the maximized terminal, meaning the title bar in this case.
- go to "System -> Preferences -> CompizConfig Settings Manager -> Window Decoration"
- enter in the field "Decorate windows":
```
!(class=Gnome-terminal & type=Normal & state=maxvert & state=maxhorz)
```- if you do this, you have of course to grab the according height/width values after doing this

---

### Post by Mathias1 on 2011-02-28
This wont work. I'm testing this by creating a launcher to /home/mathias/terminalstartup.sh
But it will just open upp a regular terminal window.
Seems like it won't run the whole script...

this is how it looks now:

> 
#!/bin/sh
gnome-terminal
wmctrl -r mathias@Mathias-ubuntu -e 0,4800,0,-1,-1
wmctrl -r mathias@Mathias-ubuntu -b toggle,maximized_vert,maximized_horz

---

### Post by Krytarik on 2011-02-28
> **Mathias1 said:**
> This wont work. I'm testing this by creating a launcher to /home/mathias/terminalstartup.sh
But it will just open upp a regular terminal window.
Seems like it won't run the whole script...

You are right, we have to use the "DISPLAY" variable when running wmctrl from a script. Sorry, I didn't test it with a script.

So, your script would then be this way:
```
#!/bin/sh
gnome-terminal
DISPLAY=:0.0 wmctrl -r mathias@Mathias-ubuntu -e 0,4800,0,-1,-1
DISPLAY=:0.0 wmctrl -r mathias@Mathias-ubuntu -b toggle,maximized_vert,maximized_horz
```

---

### Post by Mathias1 on 2011-02-28
Noo!
Didn't help that either :(

---

### Post by Krytarik on 2011-02-28
> **Mathias1 said:**
> Noo!
Didn't help that either :(
Check the output of
```
echo $DISPLAY
```
I assumed that your variable is the same, and just yet found the command the get those.

Did you try it actually at startup or also when already logged in? Is there a difference?

---

### Post by Mathias1 on 2011-02-28
echo $DISPLAY gives "0.0"

No difference at startup
although, if I run the launcher for the script, a terminal window pops up, but if I run it again, the terminal opens in the desired viewport.

---

### Post by Krytarik on 2011-02-28
Then try delaying the execution of the wmctrl commands a bit:
```
#!/bin/sh
gnome-terminal
sleep 5
DISPLAY=:0.0 wmctrl -r mathias@Mathias-ubuntu -e 0,4800,0,-1,-1
DISPLAY=:0.0 wmctrl -r mathias@Mathias-ubuntu -b toggle,maximized_vert,maximized_horz
```

---

### Post by Mathias1 on 2011-02-28
Sleep didn't do the trick (tried sleep 10000, no success)

---

### Post by Krytarik on 2011-02-28
> **Mathias1 said:**
> Sleep didn't do the trick (tried sleep 10000, no success)
"sleep 10000" means 10.000 secs. ;-)

But it works completely when run when already logged in?

---

### Post by Mathias1 on 2011-02-28
Only if I run the launcher, leaves the terminal window that pops up and then run the launcher again...

---

### Post by Krytarik on 2011-02-28
OMG, this just drives me nuts! I had a similar issue recently, but I don't remember how exactly it was. I tried any obvious setup in the last half an hour, but it only works if there is already a terminal window open, this is just odd. I have to do some further testing and am hopefully able to report tomorrow.

---

### Post by Copper Bezel on 2011-02-28
Aha - I need this one too, and although I don't know the command, I know you do! It's the preface command that displaces a process into a separate application session. I've been trying to find your explanation of how to use it for a very similar purpose, but I couldn't remember where you mentioned it.

As it is, we're running a script that starts Gnome Terminal, *then waits for it to end* before moving on with the next line.

---

### Post by Krytarik on 2011-02-28
> **Copper Bezel said:**
> Aha - I need this one too, and although I don't know the command, I know you do! It's the preface command that displaces a process into a separate application session. I've been trying to find your explanation of how to use it for a very similar purpose, but I couldn't remember where you mentioned it.

As it is, we're running a script that starts Gnome Terminal, *then waits for it to end* before moving on with the next line.
You mean "setsid", I tried it already, as I thought of the same like you. But just upon writing this post, I eventually managed it. You have to run it in background with "&" and delay the execution of wmctrl a bit.```

#!/bin/sh
gnome-terminal &
sleep 1
DISPLAY=:0.0 wmctrl -r krytarik@krytarik-desktop -e 0,1152,0,-1,-1
DISPLAY=:0.0 wmctrl -r krytarik@krytarik-desktop -b toggle,maximized_vert,maximized_horz
```But I'm actually wondering if there is no way (currently) to really open it at the desired workspace, I remember having seen or even tested such an option a few years ago. I'll do a web search about it.

---

### Post by Copper Bezel on 2011-02-28
Yeah, I could swear I'd seen a simpler way to do this, too, but at least you got it working. And thanks for the command despite my near incoherence in asking for it. = )

---

### Post by Krytarik on 2011-02-28
I searched for a while now. And unfortunately there seems really to be no way to specify a workspace for a program on its startup. All the methods either involve
- wmctrl (like we did)
- Compiz and Devilspie, both of which fix the app to the specified workspace, meaning in our case: if I open a terminal while being on workspace 1, it would automatically open on workspace 4 instead ;-)

And I believe I also searched before posting in this thread initially.

---

### Post by Mathias1 on 2011-03-01
It still won't work..I'm really not liking this :(

---

### Post by Krytarik on 2011-03-01
> **Mathias1 said:**
> It still won't work..I'm really not liking this :(
Did you try it with a longer delay!?

---

### Post by Mathias1 on 2011-03-01
Sorry.
It DID work, although only with a test-launcher.

---

### Post by Krytarik on 2011-03-01
So, I had time to test it really at startup. Some apps are a bit tricky to run at startup, sometimes you have to delay its startup until the desktop is loaded. So, I added a 13 secs delay before even the terminal is run, but you may have to fiddle a bit to get the perfect values for your system.```

#!/bin/sh
sleep 13
gnome-terminal &
sleep 1
DISPLAY=:0.0 wmctrl -r krytarik@krytarik-desktop -e 0,1152,0,-1,-1
DISPLAY=:0.0 wmctrl -r krytarik@krytarik-desktop -b toggle,maximized_vert,maximized_horz
```

---

### Post by Mathias1 on 2011-03-02
This seems interesting...will test when I get home.
 
THANK YOU for your patience and your excellent help! :)

---

### Post by Mathias1 on 2011-08-17
So, I'm reviving this thread as a new problem has risen.

I'm now running 11.04 and it work OK.
The startup-applications is placed exactly where I want them.
But after a while, ALL the placed applications jumps a workspace left.

For instance, I have Tweetdeck on my 2nd workspace, maximized and it jumps to my first workspace.

Anybody knows why?

---

### Post by Mathias1 on 2011-08-20
Bump..?

Can I log the windows placement or virtual desktop somehow?
Seems like something messes with the identifier for the viewports.

---

