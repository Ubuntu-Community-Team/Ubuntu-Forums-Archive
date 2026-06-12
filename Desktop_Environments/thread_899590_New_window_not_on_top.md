---
title: "New window not on top"
date: 2008-08-24
forum: Desktop Environments
---

### Post by mod-jkl on 2008-08-24
Hi,

I'm using ubuntu 8.04, sometime, when a new window is created, it does not appears on top but behind the current window. 
Is this a known bug ?

Does the updates of hardy will include gnome updates (new gnome releases) ? 

Thanks for any information

---

### Post by mod-jkl on 2008-08-25
Any ideas ?

---

### Post by mcduck on 2008-08-26
Are you using the desktop effects? If yes, install the compizconfig settings manager (if you haven't already done that), open it and loook under "general" settings. There's an option for "focus stealing prevention level". Change that to "low" or "none".

---

### Post by mod-jkl on 2008-08-26
No, I don't use any effects ..

In that case, do I use metacity or compiz ? (having no effects)

---

### Post by mcduck on 2008-08-26
> **mod-jkl said:**
> No, I don't use any effects ..

In that case, do I use metacity or compiz ? (having no effects)

If the desktop effects are disabled you are using Metacity as your window manager.

---

### Post by Hunkadoodledoo on 2008-09-25
mod-jkl, I'm having the same issue you are.  I've linked to a video of the bug below.

Like you, after a fresh install of 8.04, some windows do not appear on top and take focus after you open them.  In my case, some don't and some do.  I don't know which will or will not.

Here is my setup:
Fresh install of Ubuntu 8.04 Hardy Heron i386
Pentium 4 2.4Ghz
512MB RDRAM
Changed Visual Effects to "None"

Thanks in advance for any help!  Here's the link to watch the bug in action:

[http://www.vimeo.com/1815384](http://www.vimeo.com/1815384)

---

### Post by mod-jkl on 2008-09-26
I have this problem only with firefox and think it is more a firefox bug as the same thing happens on my xp laptop..

For firefox, I used before a menu item that  I created (not to have to go in the internet submenu), now I use the already created firefox item (the one in the internet submenu), and it solved part the problem: at least, when a new firefox window is created by this menu item, it is always on top which was not the case before. Strange as I don't see differences between the 2 menu items, except that one was created during firefox installation and the other was by hand...

But it doesn't solve your problem..

Please let me know if you find something.

ps: if you didn't, you should try to install the updates..

---

### Post by adolfoceli on 2008-09-26
Are you using the desktop effects? If yes, install the compizconfig settings manager (if you haven't already done that), open it and loook under "general" settings. There's an option for "focus stealing prevention level". Change that to "low" or "none

__________________

ADOLFO

[internet marketing](http://www.drivenwide.com)

---

### Post by Hunkadoodledoo on 2008-09-26
I put it in my post that I'm not using desktop effects.  I set Visual Effects to "None".  And I have read that remedy posted in about 5 other threads that seems to help, but only those people using Compiz Fusion.

After I read it those 5 other times, I actually thought I'd give it a try (even though I wasn't using any sort of desktop compositing), so I installed compizconfig-settings-manager and followed the same steps in the 5 other threads.  No change.

I have even gone into the gconf-editor under /apps/metacity/general and changed focus_new_windows from "smart" to "strict".  Nothing.

I'm actually pretty frustrated with two bugs that I seem to be the only one experiencing them.  I'll see if anyone on IRC can point me in the right direction.  If I find something out, I'll let you know.

---

### Post by Hunkadoodledoo on 2008-09-26
Okay, I feel a little better knowing what is causing this problem on my end, but not so good knowing that I have to make a change to my desktop to stop something that happens some times, but not others.

If you noticed in my bug video, I have the Audacious Media Player running.  I have "Always On Top" turned on so that I can always see the playlist and always have access to the playback controls.  It turns out that is what was causing the erratic behavior.  Now, instead of some windows coming to the foreground and taking focus and others not, now, they all come to the foreground and take focus.

So, yay!  I found out what causes the problem.  But now that I've disabled "Always On Top", it makes it more inconvenient to listen to music.

So, why do some of the windows, like the "Main Menu" window come to the front and take focus and others not?  Is this a bug in Gnome, Metacity, Audacious, each other program that doesn't come to the foreground and take focus?  Oh, bother.  Hope this helps you!

---

### Post by Yleeyas on 2008-10-03
Hi Hunkadoodledoo,

I'm glad I found this thread because I thought I was going nuts :)

You are NOT alone. In my case I installed the old XMMS player, which I routinely have set to 'always on top' for the exact same reason as you.
I don't think the problem is with the application. Whatever handles the 'always on top' functionality is screwed up.

Did you submit a bug report (launchpad)?

yleeyas

---

### Post by Hunkadoodledoo on 2008-10-05
Well, that's the thing.  I didn't know which program is the one at fault.

Is it Audacious for not adequately informing the other programs that it is in "Always on top" mode' and that when summoned, they should come to the foreground (at least all the way up to behind Audacious, that is), and take focus?

Or is it Gnome for not keeping the application behavior constant - so while Audacious is in "Always on top" mode all programs behave in a predictable manner?

And could it just be a problem that different programs have implemented different "Come to foreground and take focus" methods?

I'll jump into the gnome-bugs IRC room and see if anyone there would know how to triage this.  I'll let you know how it goes!

Edit:
Okay, I found the bug posted for Metacity and commented and confirmed it over there.  Even though Compiz interferes with Blender's OpenGL window, I've switched to using it as my window manager for now.  Even with Audacity set to "Always on top", windows open correctly.  Hope this gets fixed, though!  Thanks everyone for your help!  Oh, and here's a link to the bug report:

[https://bugs.launchpad.net/metacity/+bug/197288](https://bugs.launchpad.net/metacity/+bug/197288)

---

### Post by pizzach on 2008-10-17
I have been dealing with this problem for at least a year, maybe two.  I have mplayer set to be on top in it's config, so for the longest time I had no idea what was causing the problem.  This is definitely a Metacity bug and not an Audacious or Mplayer bug.  It will always reappear if you select "Always on Top" from the window menu for any program.

When the bug is active, all newly created windows will be placed behind the currently focused window. Not any farther, not any closer.  This is why it only happens "sometimes".  You can test this out if you set focus to sloppy, open up a bunch of gnome-terminal windows, arrange them, and then press alt-f2 to bring up the application launcher window to see where it appears.

Seriously, switching window managers is probably your best choice if you use the feature much.

---

### Post by zarqoon on 2009-03-19
I've just upgraded from gutsy and now i've the exact same problem. I have VLC player set to always on top so that i am able to drag files there from a fullscreen nautilus comfortably.
The most annoying thing is that Instant Message windows wont pop up above the video running in fullscreen now. They used to do that in gutsy.

This thread is kind of old and the bug report on launchpad is even older any chance that someone found a workaround without installing an ancient version of metacity yet?

---

### Post by ulepx on 2009-05-21
Metacity is being smart about window stacking. Applications use some calls which Metacity honors while other calls Metacity ignores/prevents on purpose ("focus stealing prevention"). The author of Metacity has deliberately done this and chose to force his philosophy on users instead of leaving an option for user to chose. Afair, the x11 call in question was XRaiseWindow(). If some hacker out there has too much time at hand I think many (including myself) would appreciate pointing out what to edit in the sourcecode to disable metacity from preventing window focus calls from applications.

Until then its xfwm for me instead of metacity

---

### Post by wbaguhn on 2010-06-02
gconf-editor
apps - metacity - general
enabling auto_raise fixed it for me.

(You may need to restart your session after this - log out/log in should do it.)

---

### Post by wbaguhn on 2010-06-03
> **wbaguhn said:**
> fixed it for me.


Let me amend:

I also had to set
auto_raise_delay to 0

and *now* it's working as I think it should.

---

