---
title: "XGL questions"
date: 2006-09-12
forum: Desktop Environments
---

### Post by lwr on 2006-09-12
Hi,

I've just got XGL working :grin: - very nice it is too. Trouble is, none of the keyboard shortcuts work, so all I can do at the moment is wobbly windows and seeing the cube spinning by as I switch workspaces. How do I configure them? I tried doing conf-editor and going to the compiz section, but I can't see anything I think would do it.
Also, how do I theme compiz? Where do I get gcompizthemer from?
Thanks for your help

Luke

---

### Post by The Pinny Parlour on 2006-09-12
Open Terminal
```
csm
```
hit enter

---

### Post by frequenicity on 2006-09-12
I am pretty sure that gconf-editor no longer has any baring on the newest Compiz update. Use "csm" command and edit from there. It's much more user-friendly anyhow.

---

### Post by lwr on 2006-09-12
I just get:
```
bash: csm: command not found
```
Do I need to install something else first?

---

### Post by PathSpace on 2006-09-12
Go ahead and install csm.  You might also want to make sure that you have compiz-manager installed as well.

```
su
(Enter root password)
aptitude update && aptitude install csm compiz-manager
```

---

### Post by frequenicity on 2006-09-12
Sounds like your compiz may not be up do date. Go into your Synaptec Package Manager and make sure that you have the latest available csm, compiz, compiz-themer, compiz-pluginz, compiz-*whatever*

Also, sudo apt-get (install?) update/upgrade to make sure your repositories are pulling the latest.

---

### Post by lwr on 2006-09-12
I've updated the repos. All I've got in synaptic is compiz, compiz-gnome and compiz-kde (the latter not installed). There's no csm or anything else.

---

### Post by frequenicity on 2006-09-12
You are missing one of the newer repos. Unfortunately I am at work right now so not at my linux box...

If nobody else helps you by 5pm today, PM me a list of your repos and I will take a look.

---

### Post by lwr on 2006-09-12
I keep getting
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

Should I just try later, yeah?

P.S. 100th post!

<Note: posted before post I'd read #8>

---

### Post by PathSpace on 2006-09-12
Try adding this repo to sources.list:

```
deb http://media.blutkind.org/xgl/ dapper main aiglx
```

Take out the "aiglx" is you do not use AIGLX.

---

### Post by lwr on 2006-09-12
Thanks everybody for your help. I've got most things sorted now. It turns out the keyboard keys weren't working because the installation of XGL messed up my general keyboard settings. 
However, I've still got a few problems. When I launched Compiz Manager, it seemed to change a lot of things, like if I hover over something to get a description, it bulges out instead of fading like it did before. And if I ctrl-alt-click to spin the cube, I get like a filmstrip. I'm completely over-whelmed by options, so any help would be much appreciated.
Thanks

---

### Post by frequenicity on 2006-09-13
The default settings with Compiz/XGL can be a bit unwanted at times. For me, I had to adjust the Wobbly setting or else I would get major headaches. But basically everything is customizable. Do a search for various specific things that you would like to change...and if you need help list them individually. There are also a lot of good reference guides to overall rundowns of the features (see: google search, compiz forums). 

There are a lot of options, but since most of them are just graphical there is little to no harm in tweaking things and seeing what happens.

---

### Post by lwr on 2006-09-13
XGLs doing some strange things, and doesn't seem to be taking my notice of what I change in the settings. When I start the computer, I've got compiz-manager to run automatically. The cube works fine, but the menus are insanely annoying, bouncing everywhere. So I use Compiz Manager to go to metacity, then back to compiz. This time, the menus only fade (which is what I think the setting tell it to do), but now if I do ctrl-alt-click to turn the cube, i just get like a filmstrip - no cube at all. Any ideas what's going on?

---

### Post by frequenicity on 2006-09-13
When you do CTRL ALT left/right arrow do you get the same result?

---

### Post by frequenicity on 2006-09-13
Also, in csm, are the boxes checked beside "Desktop Cube" and "Rotate"

---

### Post by lwr on 2006-09-13
No, that's fine, and I see the cube as it should be. Same when switching between workspaces/viewports by clicking on the switcher app in the panel on the bottom right of GNOME. It's also OK when dragging windows across to another workspace.

---

### Post by lwr on 2006-09-13
> **frequenicity said:**
> Also, in csm, are the boxes checked beside "Desktop Cube" and "Rotate"

Yep, both checked

---

### Post by chaosgeisterchen on 2006-09-13
//edit

oh my.. I should have read the second page before posting :(

---

### Post by frequenicity on 2006-09-13
Rotate Cube > Mouse > Initiate should be set to CTRL and ALT checked, and Button "1"

yes?

---

### Post by lwr on 2006-09-13
> **frequenicity said:**
> Rotate Cube > Mouse > Initiate should be set to CTRL and ALT checked, and Button "1"

yes?

Yep.

---

### Post by lwr on 2006-09-13
Just so you can see what this 'filmstrip' things looks like:

[IMG]http://www.truthdesigns.co.uk/ubuntu-hacker/nocube.png[/IMG]

---

### Post by frequenicity on 2006-09-13
I am at a loss. Sorry, I have not dealt with this particular problem before. Is it like it's trying to switch applications (same as ALT+Tab)? If so, check the Application Switcher settings (in csm) and make sure that under the mouse tabe nothing is checked and all of the buttons are set to "Disabled". That's the only thing I can think of that looks like a film strip.

---

### Post by frequenicity on 2006-09-13
OOOOOOOOOOOHHHHHH

Desktop Cube - Mouse tab - Change "Unfold" Button to disabled and THEN uncheck any of those boxes.

---

### Post by lwr on 2006-09-13
Aha! Excellent! That seems to have sorted it nicely. Thank you very much frequenicity, and everyone else who's helped. It's hugely appreciated. Thanks again.

Luke

---

### Post by frequenicity on 2006-09-13
No problem. Enjoy XGL

---

### Post by lwr on 2006-09-14
One other question. When my computer starts up, compiz-manager loads some horrible settings (ie not what I've specified), then i have to switch to metacity, then back to compiz to get the settings i want. Is there a way round this, so it just loads what I want first time?
Thanks again

---

### Post by frequenicity on 2006-09-14
What all is in your startup in regards to compiz?

---

### Post by lwr on 2006-09-14
i've got 'thefuture', which I think is what the guide I used called XGL, and 'compiz-manager', in that order. One other question while I'm at it; how do I quit XGL so I can run other OpenGL programmes?

---

### Post by frequenicity on 2006-09-14
Hmm...I believe compiz-manager is that red cube at the top right? I took that out of mine. Also, if you are using the "csm" then I BELIEVE you should have compiz-start in your startup script instead of thefuture (at least I do...but depending on how up to date you are with evertying you may still be running thefuture.) To test this, take both of those out of your startup, then after startup run "compiz-start" from the terminal. If it works, then just put that in your startup. If it doesn't, you can just run "thefuture" from the terminal and then you will know that is the one you need.

As for ending it, I believe you can end it like you would any other process with either a kill command or in your system monitor but to be honest I have never had to do that so I am not sure.

---

### Post by lwr on 2006-09-14
Ah yes! Excellent, that seems to have solved it. And it turns out that OpenGL powered stuff works fine when XGL's running (I think that must have been an old problem I heard about that they've since sorted), so all is right in the world of XGL. Thank-you so much frequenicity for all the help you've provided. It's people like you that make these forums so great, and in tern make Ubuntu so great! Thanks again!

---

### Post by frequenicity on 2006-09-14
No problem. I had to jump through several hoops to get mine working correctly so I knew where you were coming from. These forums were a great source of information and the number one reason Ubuntu is my number one choice for a distro.

---

