---
title: "Firefox in dual monitors"
date: 2008-08-30
forum: Desktop Environments
---

### Post by gmxgeek on 2008-08-30
I have dual monitors set up, each with its own X session. My mouse drags between them, but applications do not. Also, if i have firefox open in one, and try to open another window in the other, then it says firefox is already running and i must close it.

Is there a way to transfer applications between monitors / X sessions, or is there a way to just start firefox in each, Has been on my todo list for quite some time now.

---

### Post by Tzimisce on 2008-08-30
> **gmxgeek said:**
> I have dual monitors set up, each with its own X session. My mouse drags between them, but applications do not. Also, if i have firefox open in one, and try to open another window in the other, then it says firefox is already running and i must close it.

Is there a way to transfer applications between monitors / X sessions, or is there a way to just start firefox in each, Has been on my todo list for quite some time now.

I know you are the one asking here, but could you point me in the direction of where you might have read how to do this? I Have as of yet been unable to find a decent dual-monitor tutorial that actually worked in the long run.

---

### Post by wd5gnr on 2008-08-30
Have you tried: [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

The best answer in mind is to run TwinView or Ximerama so you get a "big screen" but the WM knows to clip to each monitor by default. This hoses up some full screen apps without some further tweaking. The only thing I can't get working right with TwinView is KDE 4.1 Open GL Screensavers which take up 1/4 of the first monitor.

---

### Post by gmxgeek on 2008-08-30
> **Tzimisce said:**
> I know you are the one asking here, but could you point me in the direction of where you might have read how to do this? I Have as of yet been unable to find a decent dual-monitor tutorial that actually worked in the long run.

I just use nvidia-settings. Works very well for me.

I am not even sure that this is possible. I like having separate X screens, as I can't stand twin-view, and find it rather pointless, and xinerama didn't seem quite what i was looking for. Any way to do it with two separate X's?

---

### Post by Cato2 on 2008-08-31
> **gmxgeek said:**
> I have dual monitors set up, each with its own X session. My mouse drags between them, but applications do not. Also, if i have firefox open in one, and try to open another window in the other, then it says firefox is already running and i must close it.

I would simpy have one Firefox running, do a File | New Window in that, and drag it into the other screen.  Maybe you mean something more complex but this would work.

---

### Post by gmxgeek on 2008-08-31
> **Cato2 said:**
> I would simpy have one Firefox running, do a File | New Window in that, and drag it into the other screen.  Maybe you mean something more complex but this would work.

I thought about doing that, but although my mouse will go between screens no problems, applications to not. even if i have only one virtual desktop on each X session, it still will not move between the screens. If i do have more than one vd on one, then it flips it to the next as it normally does.

---

### Post by trouble1313 on 2008-08-31
I hear ya. The only way I found to cope with it with separate displays is to create a launch icon (or start it from a terminal) on each desktop. Of course this doesn't do what you (or I!) really want which is be able to run on both displays at the same time or drag the app over. I haven't tried but what about running firefox as a different user for the second instance? I'd imagine that would work but you'd have to copy over your .mozilla directory to get your prefs. 

-Trouble

---

### Post by gmxgeek on 2008-08-31
> **trouble1313 said:**
> I hear ya. The only way I found to cope with it with separate displays is to create a launch icon (or start it from a terminal) on each desktop. Of course this doesn't do what you (or I!) really want which is be able to run on both displays at the same time or drag the app over. I haven't tried but what about running firefox as a different user for the second instance? I'd imagine that would work but you'd have to copy over your .mozilla directory to get your prefs. 

-Trouble

Problem with that being that if i try to launch firefox in the second session at all, i get a message that it is already running, and imust kill the process or restart. I don't think running as another user would solve this.

---

### Post by Hooya on 2009-01-09
Bump.  I'm trying to solve this same problem.  Any fix yet?

My issue is running Firefox under multiple desktop environments (Ctrl+Alt+F9).  I can only have Firefox running in one at a time, but I'd like to have it running in more than one if possible.  I can only view one DE at one time.

---

### Post by Grumpey on 2009-01-09
Could you just start with seperate profiles for firefox?

Explanation here:
[http://www.canfield.com/content/multiple-independent-firefox-sessions](http://www.canfield.com/content/multiple-independent-firefox-sessions)

It would be interesting if you could just softlink the profiles together to keep them in sync...

---

### Post by Hooya on 2009-01-09
His little TODO at the bottom of the blog is what we want!  I'll keep my eye on that site to see if he figures out a way to do it.

---

### Post by mediajunkie on 2009-06-11
hi all,

I know exactly what you want to do friend, I have been trying myself as I also run 2 X sessions. But we have to understand, that each x session has little to do with the other. (both have their menu and can pretty much run the same applications simultaneously> , EXCEPT for firefox) 

The solution I found working for me is also installing Opera browser. 
I run by default Firefox, but if I need a second window open on the second screen I run Opera. Usually it is for reading purposes if you want multiple browser screens anyway. and although I prefer Firefox, Opera is a very capable, secure and stable browser too. I think that both products are a quality/stability equal. 

So on my second screen, I have added the opera browser icon on the tool bar instead of firefox. 

Note: just don't forget to disable the default browser check on start up. It will drive you crazy to answer no all the time LOL :D

---

### Post by peepingtom on 2009-06-11
```
tom@oxo:~$ firefox --help
Usage: firefox [ options ... ] [URL]
       where options include:

X11 options
	--display=DISPLAY		X display to use
	--sync		Make X calls synchronous
	--no-xshm		Don't use X shared memory extension
	--xim-preedit=STYLE
	--xim-status=STYLE
	--g-fatal-warnings		Make all warnings fatal

```


this Display variable might be the key, ive been using the dirty hack to use a different Firefox profile for each X display. Try it, if you don't i'll play around with it later and post results.

---

### Post by meganox on 2009-09-16
I guess no-one has heard of the -no-remote option to firefox:

[http://kb.mozillazine.org/Command_line_arguments](http://kb.mozillazine.org/Command_line_arguments)

use it like: firefox -no-remote -P profile-to-use

I'm pretty sure it's a bad idea to try to use the same profile for both instances though and I don't think symlinking would make any difference to this.  Maybe have a job at startup that copies the contents of one profile to the other and use Xmarks to sync bookmarks and passwords during the session.  Some extensions are also dumb and use the full profile path in some of their preferences.

---

