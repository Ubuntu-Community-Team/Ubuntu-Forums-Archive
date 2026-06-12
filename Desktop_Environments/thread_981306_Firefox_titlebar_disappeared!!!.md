---
title: "Firefox titlebar disappeared!!!"
date: 2008-11-13
forum: Desktop Environments
---

### Post by gneo on 2008-11-13
Hello All,

Got a little problem. Everytime I run Firefox it takes up the whole screen and the titlebar is missing (so I can't see the "minimise window" or the "close window (x)" buttons. That only happens with Firefox. Odd? The only way to see the "Applications" etc menus is to quit firefox!!! Help?

---

### Post by Cobbs on 2008-11-13
Try pressing F11, thats the shortcut key for fullscreen mode.  Maybe FF is just starting in fullscreen mode.

---

### Post by gneo on 2008-11-13
It's not maximizes. By pressing F11 it maximizes, and by pressing it again it goes normal (as in: I can see the titlebar). However, if I close it and open it again I have the same problem. Weird eh?

---

### Post by Fire_Chief on 2008-11-13
I also experience this problem intermittently on my Lenovo T60 laptop. Not sure if it is related to the ATI video drivers (wouldn't think so but you never know). If anyone knows why it does this and how to make it stop, please share your wisdom.

The F11 hotkey does maximize and then correctly un-maximize the window and the title bar does re-appear so that is at least a workaround...but still irritating.

Thanks!

---

### Post by nisarg on 2008-11-13
same issue here!
this is happening for me since yesterday. 
i use FlashBlock extension - which i remember updated roughly the same time... not sure if thats what is causing it? 
i have tried removing the extension, but that hasn't helped...

any ideas anyone?

---

### Post by gneo on 2008-11-14
Problem insist. Any help? Anyone?

---

### Post by binbash on 2008-11-14
It is compiz workaround plugin bug.

System > Preferences > CompizConfig Settings Manager > Workarounds > General 

Untick legacy fullscreen support

---

### Post by Merlintrix on 2008-11-15
> **binbash said:**
> It is compiz workaround plugin bug.

System > Preferences > CompizConfig Settings Manager > Workarounds > General 

Untick legacy fullscreen support

That worked beautifully. Thanks!
How come the error was Firefox specific though?

---

### Post by Ichido on 2008-11-15
Here is Where & How I fixed mine:
1)Synaptics Package Manager->
2)Downloaded & Installed "Compizconfig-settings-manager 0.7.4-0ubuntu2".
3)System>Preferences>Advanced Desktop Effects Settings>Utility>
4)Un-Checked "Scale Window Title Filter".
:)

---

### Post by Jan Ziska on 2008-11-30
> **binbash said:**
> It is compiz workaround plugin bug.

System > Preferences > CompizConfig Settings Manager > Workarounds > General 

Untick legacy fullscreen support

this didn't work for me. I have compiz disabled via the no special effects setting. Would this be the reason?

---

### Post by PeeZz on 2009-01-18
> **binbash said:**
> It is compiz workaround plugin bug.

System > Preferences > CompizConfig Settings Manager > Workarounds > General 

Untick legacy fullscreen support

This did the job for me. Strange though...

---

### Post by earthtux on 2009-02-18
I didnt enable compiz, but i still get this weird behavior
anyone can help me?
thx

---

### Post by Spalding on 2009-03-14
I don't have Compiz in my System>Preferences menu but I have the same problem.  My install is just a month old and all was fine until a couple of few weeks ago - could it have been an update?  I'll update now and see if there is a fix in the new updates (yeah, right!).  I am using an Invidia driver but that was a week or so before the problem appeared.

---

### Post by ihasapancake on 2009-03-15
Hit "Alt-F2" to bring up the "Run Application" box and type in (without the quotes): "metacity --replace" and see if that restores the title bar. It worked for me.

---

### Post by munkydust on 2009-07-12
Worked for me. Thank you very much!

---

### Post by moody_mark on 2009-07-14
Thank you from me too, I thought id gone mad, upgraded from 8.04 to 8.10 and it started going like this. Shame we cant thank people in the forums anymore.

---

### Post by 3dmatrix on 2009-07-17
> **ihasapancake said:**
> Hit "Alt-F2" to bring up the "Run Application" box and type in (without the quotes): "metacity --replace" and see if that restores the title bar. It worked for me.

It worked for me too :)

---

### Post by TNT1 on 2010-09-28
> **ihasapancake said:**
> Hit "Alt-F2" to bring up the "Run Application" box and type in (without the quotes): "metacity --replace" and see if that restores the title bar. It worked for me.

Shot. I just ran upgrade manager, installed new kernel, rebooted and my title bars in all windows were gone. This trick worked. Thanks.

---

### Post by BagB on 2011-02-17
Even if this thread is a bit dated, here goes -

For my system - Ubuntu 10.04, with CompizConfig Settings Manager installed. On the "CompizConfig Settings Manage" I had to select "Preferences" on the left panel, and use for the "Backend" the option - "Flat-file Configuration Backend". This freezes most inputs, so I had to reset the machine by switching the power off. On restart I got back the title bar and was back in business.
 
 I know its not an elegant solution, but it worked for me

---

### Post by Copper Bezel on 2011-02-17
Ironically, because I primarily use Chrome and am running on a netbook and because Firefox is heavy but handles video better than Chrome, etc., while I've never had this problem, I do have Firefox set up through Compiz to always run maximized and without window decorations. = )

---

