---
title: "compiz Application Switcher mouse/screen focus issues"
date: 2011-05-05
forum: Desktop Environments
---

### Post by Nisitiiapi on 2011-05-05
Under Natty, it seems there's a huge bug with the Compiz Application Switcher.  Not the Ring Switcher, Shift Switcher, or Static Application Switcher, just the standard "Application Switcher."  Whenever I enable it, if you switch between windows using "ALT+Tab," mouse and keyboard events in the switched-to window don't register on the screen.  But, if you minimize and restore the window, or maximize restore it, the problem is fixed and you can see the mouse and keyboard events did actually occur.

Here's an example: if both firefox and gedit are running and I use "ALT-Tab" to switch over to gedit, I can type a sentence and nothing appears in gedit.  I can click on the "File" menu and it won't display.  But, if I minimize or restore the window and bring it back, everything I typed will be there.

Interestingly, it's not universal to everything on the screen.  In my example, if I switch back to firefox, using "Ctrl+Tab" to switch between open tabs does nothing, except you can actually see the title bar of firefox change to match the tab it should be switching to.  If you minimize firefox and bring it back, it will actually be on the tab you switched to.

Since the events seem to occur, but not appear on the screen, I'm not sure if this is a compiz bug, a natty bug, or display driver bug (I'm using the fglrx driver for my ati card).  I have found the problem exists in both Unity and gnome session.  Disabling the Application Switcher in CompizConfig Settings Manager eliminates the issue.

The behavior has persisted through about 3 clean installs of Natty (64-bit).  Has anyone else seen this happen with the Application Switcher or found a setting to fix it?  Thanks.

---

### Post by kamleshb on 2011-05-05
I was looking through the forums to see if there was a fix for this problem, and I see someone else has it as well.

I have tried "Reset to Defaults" in ccsm and "gconftool-2 --recursive-unset /apps/compiz-1" but that has not fixed it.  This only occurs on one of my three PC's however.  I am running 32-bit.  My video driver is also fglrx.  But one of my other working PC's has the same configuration.

Thanks in advance for any help with this.

---

### Post by boreal6 on 2011-06-01
I also have this problem - when switching between different applications, my keyboard intermittently works. With enough clicking around, it seems to work again - I still haven't figured out exactly when this is happening, or what is fixing it. From what I can tell, it usually happens when I go between different workspaces. 

Any ideas?

---

### Post by Copper Bezel on 2011-06-01
This latter problem I have on 10.10 as well. It's unrelated to the (rather serious) Application Switcher bug in Natty. Does it only seem to happen with certain applications? I can consistently cause input fields in Opera not to work by switching workspaces using the Viewport Switcher plugin (but opening a menu in Opera or switching to another application and back on the same workspace, or even going out to Expo view and back, all return things to normal.)

---

### Post by Parsa86 on 2011-06-03
This problem seems to also exist on Mint 11 running Compiz standard setting, and with Chrome open

---

### Post by ds_mart on 2011-06-05
I too have this exact same problem after I upgraded from Ubuntu 10.10 to 11.04.  Unsure if its Compiz or Unity but I'm using fglrx drivers.  At least compiz actually works for me in 11.04, I never got fglrx and compiz to play nice in 10.10.

Thank you Nisitiiapi for the workaround.

---

### Post by kamleshb on 2011-06-20
Curiously for me, I no longer have this problem. On Friday, after applying  all pending Ubuntu updates and rebooting, Alt-Tab works properly once again.

---

### Post by 00arthuryu on 2011-06-23
> **kamleshb said:**
> Curiously for me, I no longer have this problem. On Friday, after applying  all pending Ubuntu updates and rebooting, Alt-Tab works properly once again.

Still doesn't work for me...

---

### Post by razhangwei on 2012-10-07
I found a solution to this problem, even though it seems not perfect. You can solve this problem by cancel the mipmap in application switcher=>general. Similar bug with static application switcher can also be resolved in this way.

---

### Post by overdrank on 2012-10-07
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

