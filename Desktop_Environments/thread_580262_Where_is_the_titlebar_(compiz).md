---
title: "Where is the titlebar (compiz)?"
date: 2007-10-18
forum: Desktop Environments
---

### Post by joeri_83 on 2007-10-18
I just upgraded to Gutsy, and decided to try the desktop effects. I've installed the advanced settings, but this problem existed before that too. What happens is that as soon as I turn on the effects the titlebar disappears, which is annoying. The maximised windows are properly maximised as if there should not be a title bar. How do I get it back. 

Also the Application menu (and the other two) are really slow, is there any way to improve that?

---

### Post by gaboro on 2007-10-18
well, this happens since yesterday. before that i've never had problems w/ compiz/beryl, not even since gutsy beta.

if i open a terminal and type [FONT="Courier New"]emerald --replace &[/FONT] it brings the titlebars back but they disappear again as soon as i close the terminal window - i haven't got a clue why.

it might worth a bug report if reproducable on several machines...

cheers
gaboro

---

### Post by joeri_83 on 2007-10-18
I don't seem to have emerald installed. I did notice however that if I start a terminal with the effects turned on the terminal doesn't load properly. There is just a blank white area on the screen.

---

### Post by Tickle Me Elmo on 2007-10-18
I'm seeing similar things using compiz/emerald. The top-menu/titlebar disappears, Gdesklets only shows in one desktop, but not the others and when choosing themes the entire shabang either crashes or shows some strange graphics in the gdesklets boxes (with no background on the desktops).

---

### Post by z0phi3l on 2007-10-18
Install emerald, if you don't have it, alternatively instead of running emrald from the terminal, use Alt+F2 (run command) and start Emerald that way, if it works you could add it to your startup sessions.

---

### Post by joeri_83 on 2007-10-19
I tried using emerald, but it doesn't seem to do anything.

---

### Post by peterx14 on 2007-10-19
I had this problem and found the solution (in another thread... but I can't find it now) was:
 sudo nvidia-xconfig --add-argb-glx-visuals -d 24

NOTE: I am using an nvidia graphics card; if you are not using an nvidia card, this won't work!!

---

### Post by joeri_83 on 2007-10-19
I do have an nvidia card, but it doesn't help. If I choose custom settings it immediately changes back to "none". If I choose Extra the titlebars are still gone. Any other ideas?

---

### Post by joeri_83 on 2007-10-19
Turns out it did work, so thanks a lot! :)

The menus are still really slow though -- is there any fix to that?

---

### Post by peterx14 on 2007-10-22
Glad you can see your title bar now!

Re the menus being slow... I've no idea; It all seems fine for me.

---

### Post by moon2js on 2007-10-22
My title bars are missing when visual effects (gutsy) are enabled, too.

I'm using (what I assume is) a somewhat dated ATI card:

```
Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection
```

Has anyone had any luck with [this fix]("http://www.pendrivelinux.com/2007/10/17/ubuntu-desktop-effects-fixing-the-missing-titlebar/")? It says to add to xorg.conf:

```

Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
```

This didn't work for me.

Next time I'm at the machine, I'll try fooling with emerald.

Curious though -- those of you who have missing title bars, did you upgrade to Gutsy from Feisty or is it a fresh Gutsy install?

---

### Post by peterx14 on 2007-10-22
> **moon2js said:**
> Curious though -- those of you who have missing title bars, did you upgrade to Gutsy from Feisty or is it a fresh Gutsy install?

Myself, I upgraded from Feisty. I did not have any desktop effects enabled with Feisty.

---

### Post by joeri_83 on 2007-10-22
I upgraded from Feisty, but I had the effects turned off in that version.

Regarding the menu bars I found a solution in another thread. It had to do with dual screens.

Again, thanks for the help. :)

---

### Post by clever on 2007-10-22
> **peterx14 said:**
> I had this problem and found the solution (in another thread... but I can't find it now) was:
 sudo nvidia-xconfig --add-argb-glx-visuals -d 24

NOTE: I am using an nvidia graphics card; if you are not using an nvidia card, this won't work!!

I had the missing titlebar and also the problem with a totally white Terminal window.  I used this command (which was tricky since I couldn't see what I was typing!) and it initially didn't do anything, but when I logged out and logged back in, everything was back to normal.  I don't know whether it was this command that fixed it, or if just logging out and logging back in would have fixed it.

> **moon2js said:**
> 
Curious though -- those of you who have missing title bars, did you upgrade to Gutsy from Feisty or is it a fresh Gutsy install?

Mine was a fresh install, not an upgrade.  In fact, I didn't have this problem at all initially after the install yesterday.  It happened to me when I booted up today.  Like I said above, I don't know whether just logging and logging back in was enough to fix it.

---

### Post by ktulu1115 on 2007-10-23
> **joeri_83 said:**
> Turns out it did work, so thanks a lot! :)

The menus are still really slow though -- is there any fix to that?

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764/")

i've got the same issue too.

---

### Post by arsenicx101 on 2007-10-23
I experienced exactly the same problem described here:
Upgraded from Feisty to Gutsy, enabled Desktop Effects, all window titlebars disappeared.
Specs: Sony Vaio SZ230, nvidia GeForce Go 7400.

The follow solution worked for me.

Add 
    *Option         "AddARGBGLXVisuals" "True"*
to the "Screen" section in /etc/X11/xorg.conf file.

Log off then log back in.

**NOTE:** Make sure that if you are using Advanced Desktop Effects Settings you have _checked_ the box for Effects > Window Decoration. Otherwise, changing the xorg.conf file will make no difference.

My

---

### Post by phirestalker on 2007-10-23
the ones with slow menus is it possible you have older graphics cards? mine is a ATI radeon 9550 and the speed is great, the problem I am having is that when I choose a theme in emerald it doesn't take effect, I have to log in and out. also I am VERY disappointed in the scope of the theme it should AT LEAST be able to make the color of the INSIDE of the windows kinda match the effect of the window borders. Right now it really looks disgusting. I expected better when they made XGL the default for gnome sessions even if they warn it's a beta, it should function but crash sometimes, instead of not functioning at all???

---

### Post by moon2js on 2007-10-24
OK, I finally figured out that for some reason compiz was never fully installed on my Gutsy system. I think specifically the missing package was compiz-gnome, but I'm not sure. I just went through and installed all the supported compiz packages and now effects seem to be working, with title bars even!

I upgraded from Feisty via synaptic button, so I'm not sure what went wrong, but I also found out that displayconfig-gtk wasn't installed (no "Screens and Graphics" menu option under Administration). Now I'm wondering what else wasn't installed with the Gutsy upgrade.

---

### Post by puqing on 2007-10-25
Hi, has your problem been solved?

My computer has an Intel graphic chip, and the title bar appears ok whether the effects are turned on or off. However, in Gimp, when I click the top of a menu and separate it from the main menu, the menu doesn't have title bar or frame. But when the effects are turned off, the menu has title bar and frame.

It looks like a similar problem with yours, although a little different.

Thanks!

---

### Post by dark_harmonics on 2007-10-25
[http://ubuntuforums.org/showthread.php?t=545806&highlight=missing+titlebar](http://ubuntuforums.org/showthread.php?t=545806&highlight=missing+titlebar)

Check that post. It worked on a computer i had that had the same problem. Basically its this: Enable Window Decorations and add gtk-window-decorator to the command part of the window decorations.

---

### Post by faradesla on 2007-10-26
> **peterx14 said:**
> 
 sudo nvidia-xconfig --add-argb-glx-visuals -d 24

This worked for me, too.
First, however, I turned off all effects found in System/Preferences/Appearance so I could actually see the terminal window.

Typed in the command Peter (and others) mentioned above, gave it my password, and apparently nothing happened.

Logged out, logged back in, then went back to Appearance and re-enabled the desktop effects. It works just fine, now. :D

---

### Post by epromd on 2007-11-03
tks a lot!! its work for me, just like faradesla explain

---

### Post by gb5uqx on 2007-11-03
Running the command

gtk-window-decorator

Will bring the title bar back, seems to be a bug. Happens to me when I close any Wine application. Iritating or WHAT !!!!.

---

### Post by Gold3n on 2007-11-06
I've currently tried all the solution posted here but can't get it to work; however, I'm in a bit of a different situation.

I have my computer set to Seperate X screens for dual monitors. My Screen 0 works perfect no issues, my Screen 1 has no titlebars. When I go into compiz it gives me the option of selection screen 0 or 1 but with screen 1 selected it window decoration still effects screen 0. 

When I use the command: gtk-window-decorator 
It says screen 0 already has decorations but makes no mention of screen 1. Does anyone know what I need to add to that command to specify screen 1 instead fo the default screen 0?

Thanks for any help.

---

### Post by jslmg on 2007-11-13
This just happened to me, following a compiz crash.

As I was working happily along in OpenOffice, the first sign of trouble was when I couldn't unminimize Ooo or Gimp. When I clicked on Ooo or Gimp in the panel window list, neither would come to the front. Moreover, they appeared to be on the fourth workspace, since their shapes appeared in the panel workspace switcher. However, I could not switch to that workspace--the pager wouldn't let me go there.

The only way to get my Ooo and Gimp back was to close them both in the panel window list, then reopen the documents I was working on.

Shortly after I reopened Ooo, compiz and all its components suddenly crashed--it all disappeared. So, I logged out and logged back in--not a full restart. After logging in, I had Compiz back, with all effects, but when I opened Firefox, I had no titlebars. Same was true of other windows. I opened CCSM, to see if I could find a fix. I had seen some mention of settings in the Place Windows plugin on this forum, but I couldn't locate them. 

Finally, I decided to try this command in terminal:

```
emerald --replace
```

That brought the titlebars back, but they disappeared again as soon as I closed terminal.

On a hunch, I decided then to just restart the computer completely. I did, and when I was back in Ubuntu, full Compiz and the titlebars!

So, maybe the best way out in one of these many crashes of Compiz and Emerald is to just restart the computer.

---

### Post by woodsby on 2007-11-23
I had the same problem with two monitors.  I have all of my window decorations on screen 0 and none on screen 1.  I run emerald as my window decorator, and found out today that the following works... finally!

System>Preferences>Sessions>Startup Programs

Add "emerald --screen 1"

It was that simple for me... so glad i figured that out... it was driving me bananas.  Hope that helps someone else out there.
As for the slow menus on the primary display - there is a bug reported for this.  It happens no matter which display you set as your primary display - when I had my CRT as my primary, it did the same thing.  Hopefully they'll fix that soon.

---

