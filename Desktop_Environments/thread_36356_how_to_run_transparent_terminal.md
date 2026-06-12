---
title: "how to run transparent terminal"
date: 2005-05-23
forum: Desktop Environments
---

### Post by Digitallysick on 2005-05-23
ive seen some screen shots where peepz have the terminal transparent, and it looks as if its part of the desktop, i have a pentium 3  800mhz with an 8meg ati graphics card and 512 megs of ram, is it possible for me to do??

also ubuntu seems slow sometimes, is there anyway to speed it up?

and how do i remove dup entries from the menu?

---

### Post by Sam on 2005-05-23
[QUOTE=Digitallysick]ive seen some screen shots where peepz have the terminal transparent, and it looks as if its part of the desktop, i have a pentium 3  800mhz with an 8meg ati graphics card and 512 megs of ram, is it possible for me to do??

also ubuntu seems slow sometimes, is there anyway to speed it up?

and how do i remove dup entries from the menu?[/QUOTE]
Go to the profile settings in your Terminal, then you'll have the choice to set a background, set it to transparent.

---

### Post by Behel on 2005-05-23
... and I run transparent terminal on a P3 600MHz with 192M of RAM. It runs flawlessly. May I also add that it is not truly transparency as with OpenGL for instance since it is just a picture of the desktop cropped to the size and location of the terminal... However it looks nice.

---

### Post by cutOff on 2005-05-23
I recommend to use Eterm to do this and more. An example to do Eterm transparent and borderless

```
Eterm --trans -g 90x20+0+360 -L 10000 -b black -f  white --shade 0 -x --borderless --scrollbar 0 --buttonbar 0 -c grey89 &
```

---

### Post by Behel on 2005-05-23
Very nice indeed. Thanks for the command for Eterm... 

but can you open a window menu on Eterm when you click with the right button of the mouse? 

I can't and this can be really annoying for copy/paste of commands...

---

### Post by cutOff on 2005-05-23
hehe, i wonder this same as well.

Can someone give us a clue?

---

### Post by tread on 2005-05-23
For any X application, selecting some text is the equivalent of copying it, and middle click anywhere will paste it there.

This, you will find, is handier than choosing copy and paste from menus :)

---

### Post by Behel on 2005-05-23
100s thanks!

I have a laptop and no middle button on my touchpad... but it  works great if I press the two buttons at the same time for pasting selected texts... Much more practical than menus!

Just another trick that can be useful for Eterm... if you press ctrl+right button, the Eterm menu appears (but no copy/paste but who cares now...), and alt+right calls the window menu...

---

### Post by cutOff on 2005-05-23
[QUOTE=tread]For any X application, selecting some text is the equivalent of copying it, and middle click anywhere will paste it there.

This, you will find, is handier than choosing copy and paste from menus :)[/QUOTE]
Thanks a million mate. 

It works fine.

---

### Post by fng on 2005-05-23
[QUOTE=Digitallysick]ive seen some screen shots where peepz have the terminal transparent, and it looks as if its part of the desktop[/QUOTE]

Mostly they use aterm for such beautifull terminals

---

### Post by angkor on 2005-05-23
[QUOTE=fng]Mostly they use aterm for such beautifull terminals[/QUOTE]

True :) This is my aterm command:

```
aterm -tr -sh 90 -bg black -fg white -fn 7x14 -fb 7x14 +vb +sb
```

---

### Post by tread on 2005-05-23
Does aterm support antialiased fonts now? Thats the only thing that keeps me on gnome-terminal still.

---

### Post by Behel on 2005-05-24
Not convinced by aterm since it doesn't seem  to be possible to have it borderless as I like with Eterm... Am I right?
Besides it looks a lot similar to gnome-terminal with transparency and removed menus  (all this is possible from configuration editor->apps-> gnome-terminal -> profiles ->Default).

---

### Post by angkor on 2005-05-24
[QUOTE=Behel]Not convinced by aterm since it doesn't seem  to be possible to have it borderless as I like with Eterm... Am I right?
Besides it looks a lot similar to gnome-terminal with transparency and removed menus  (all this is possible from configuration editor->apps-> gnome-terminal -> profiles ->Default).[/QUOTE]

I've got aterm borderless allright. In fact I have everything borderless (who needs a title bar anyway?). I use the sawfish windowmanager with the lines theme :-). Maybe it looks very similar to gnome-terminal but it's sooo much faster.

---

### Post by Behel on 2005-05-24
Thank you! Then I may consider Aterm!

But I tried your command and still had borders...  :???:
Have you done anything special? Is it due to Sawfish?

---

### Post by angkor on 2005-05-24
[QUOTE=Behel]Thank you! Then I may consider Aterm!

Have you done anything special? Is it due to Sawfish?[/QUOTE]

Yeah. I use Sawfish with the non-standard 'lines-theme' so everything is borderless. ;-) 

'...Really, really minimal theme.  No useless title bars or
other chrome, just lines.  (Without the title bar, it's
good to know that by default you can Alt-leftclick to
move windows and Alt-middleclick to get the window
operations menu).  The colors, line width and offset
are configurable.....'

You can get it at: [http://themes.freshmeat.net/projects/lines_/](http://themes.freshmeat.net/projects/lines_/)

It takes a bit of getting used to but it's my favourite.

You can find see a screenshot [here](http://www.xs4all.nl/~gerben77/Screenshot.png)

---

### Post by 23meg on 2005-05-24
if you've got your terminal window borderless and transparent, you'll probably not want it to appear in the window selector as well. you can do it using devilspie; refer to [this thread](http://www.ubuntuforums.org/showthread.php?t=12455&highlight=Eterm+devilspie) for this nice trick.

---

### Post by angkor on 2005-05-24
Ooo nice, thanks...I'll look into that :) Or maybe I'll just remove the window-list from my panel....do you perhaps know if it's possible to get a transparant workspace-selector in the gnome-panel??

---

### Post by trash on 2005-05-24
Nice, i've been looking how to do this...

but when i run Eterm i get..
Eterm:  Error:  Can't open pseudo-tty -- No such file or directory
Eterm:  Error:  Unable to run sub-command.

EDIT: ok found fix in man...  Esetroot [-display display] [-scale] pixmap ...
what values would i use for display and scale?
Thanks

Just tried it on my pc and it works fine, its on the mac that I am having this problem.

Also on the pc I just made an Eterm_script to use at startup... added it to the startup programs and it works but with a different non-transparent background. What do I need to change here...
```
 #!/bin/sh
Eterm --trans -g 70x20+0+260 -L 10000 -b black -f  white --shade 0 -x --borderless --scrollbar 0 --buttonbar 0 -c grey89 &
``` 
```
chmod 755 Eterm_script
```

---

### Post by 23meg on 2005-05-24
[QUOTE=angkor]Ooo nice, thanks...I'll look into that :) Or maybe I'll just remove the window-list from my panel....do you perhaps know if it's possible to get a transparant workspace-selector in the gnome-panel??[/QUOTE]
 none that i know of, unfortunately. devilspie works well, and you can remove Eterm from the pager as well.

---

### Post by Behel on 2005-05-26
I kept Eterm finally...

Is there any possibility to have the terminal sticked to the desktop so that when I minimize all windows, the terminal stays open?

Also, is it possible that the terminal starts with every session? I have added the exact previous Eterm command to the startup programs in System -> Preferences -> Sessions, but it strangely starts with a non transparent background... Any ideas?

Thanks

BL

---

### Post by Digitallysick on 2005-05-27
yeah i need a way for it to start up as well, im new at the script thing, some of these people are beyond smart, i would never figure out these type things

---

### Post by Behel on 2005-05-30
Hey,

Many good infos in this thread:
[http://ubuntuforums.org/showthread.php?t=36811](http://ubuntuforums.org/showthread.php?t=36811)

Works great for me...

---

### Post by spencer on 2005-05-31
[QUOTE=Behel]... and I run transparent terminal on a P3 600MHz with 192M of RAM. It runs flawlessly. May I also add that it is not truly transparency as with OpenGL for instance since it is just a picture of the desktop cropped to the size and location of the terminal... However it looks nice.[/QUOTE]


Is there a way to make terminal truly transparent instead of the cropped picture. Mac os x terminal has a command to make its terminal truly transparent so you could see through text underneath terminal. 

-spencer

---

### Post by angkor on 2005-05-31
[QUOTE=spencer]Is there a way to make terminal truly transparent instead of the cropped picture. Mac os x terminal has a command to make its terminal truly transparent so you could see through text underneath terminal. 

-spencer[/QUOTE]

There is, but it's still a bit unstable. Read this thread on how to try it out:

[http://www.ubuntuforums.org/showthread.php?t=20769](http://www.ubuntuforums.org/showthread.php?t=20769)

---

### Post by spencer on 2005-05-31
Thanks for the link. I'll read the thread and try it out. Can you tell me what the instabilities are? Maybe the answer is in the thread you gave me. Thanks.

-spencer

---

### Post by spencer on 2005-05-31
[QUOTE=angkor]There is, but it's still a bit unstable. Read this thread on how to try it out:

[http://www.ubuntuforums.org/showthread.php?t=20769](http://www.ubuntuforums.org/showthread.php?t=20769)[/QUOTE]



Installed transset and xcompmgr then followed the rest of the HOW TO: guide and now can adjust the terminals transparency when I want to read text underneath terminal. ubuntu looks nice with xcompmgr but I could do without the shadows and all. It does slow system down a considerable amount, at least mine which is an older Gateway pc. Otherwise works good so far. I think I'll just use transset to adjust the terminal transparency and do without xcompmgr unless of course I need xcompmgr for transset to work. One thing I wish transset did was only make the inner window portion transparent instead of the entire window. But who am I to complain? Well I guess I just did on what is probably a ticky tac grip. I'm looking forward to slowly making a bigger jump into the linux world and Ubuntu has done a great job. Thanks.

-spencer

---

### Post by bpilgrim1979 on 2005-07-26
thanks for tips guys!

---

