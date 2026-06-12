---
title: "A program is still running"
date: 2008-12-04
forum: General Help
---

### Post by elusivespoon on 2008-12-04
I recently started getting a dialog popping up when I try to shutdown that says, "A program is still running:"  So far it has always been an unknown program, with the reason it is not responding. I'd like to set it so my computer just shuts down, killing the program instead of prompting me.

---

### Post by ashen on 2008-12-31
I also have this problem - it doesn't happen every time i shut down but it does happen quite a lot.  The only program I've used everytime when this happens is firefox.

Does anyone have any idea what's causing this?  I've looked through the running processes on system monitor and there's not any listed as unknown.

Cheers,

ashen

---

### Post by JayeD on 2009-01-03
> **ashen said:**
> I also have this problem - it doesn't happen every time i shut down but it does happen quite a lot.  The only program I've used everytime when this happens is firefox.

Does anyone have any idea what's causing this?  I've looked through the running processes on system monitor and there's not any listed as unknown.

Cheers,

ashen

Happening here too. Exact same, firefox use.

---

### Post by cooney on 2009-01-04
Just out of couriousity,

Do you guys try to log out with programs running or have you quit them (especially firefox since that one seems to be the culprit) before logout or shutdown?

I always close everything that I've started before log off/shutdown; but I seem to remember seeing this error window once when I was in a hurry.

Just a thought.

---

### Post by binbash on 2009-01-04
> **JayeD said:**
> Happening here too. Exact same, firefox use.

It happens mostly at firefox 3.1b3.You gonna kill the pid (ps aux | grep firefox)

---

### Post by LoneWolfJack on 2009-01-04
I have this issue in 8.10 too every once in a while... I'm not that sure it's related to FF, seems more like a memory cleanup process or so because I think it only (but not necessarily) happens if I had a program crash in the active session.

I'd call it a less annoying bug but then again it may scare newbies and make them believe that there is a trojan at work or something...

---

### Post by cooney on 2009-01-04
> **binbash said:**
> It happens mostly at firefox 3.1b3.You gonna kill the pid (ps aux | grep firefox)

If you meant 'you gotta' kill... pid...

You shouldn't have to.  Somewhere one process is not communicating with the other when it's time to shutdown.  This is probably something that the firefox developers need to be informed about.

Every OS I've ever operated and that began with a Vic-20 and a "datasette", always advised to save and quit all programs before shutdown.  CP/M, Dos, Mac system 1 - 8, 9, OSX and every version of Windows too.  Try as I said if your not, and see if the symptom goes away.  If it doesn't then that's something to bring to the Dev's attention.

I'm running ff 3.0.5 and hardy 8.0.4.  I religiously quit ff and any other program I've launched before shutdown or logout so, except for the instance mentioned above, do not have this problem at any frequency during my computing experience.  In fact, I run multiple logins for days and weeks at a time and only logout/shutdown when the kernel is upgraded or something else just isn't working properly.

---

### Post by cooney on 2009-01-04
> **LoneWolfJack said:**
> I have this issue in 8.10 too every once in a while... I'm not that sure it's related to FF, seems more like a memory cleanup process or so because I think it only (but not necessarily) happens if I had a program crash in the active session.

**I'd call it a less annoying bug but then again it may scare newbies and make them believe that there is a trojan at work or something**...

Been there  :eek:

---

### Post by cooney on 2009-01-04
> **LoneWolfJack said:**
> I have this issue in 8.10 too every once in a while... **I'm not that sure it's related to FF, seems more like a memory cleanup process or so because I think it only (but not necessarily) happens if I had a program crash in the active session.**

I'd call it a less annoying bug but then again it may scare newbies and make them believe that there is a trojan at work or something...

That's another good point.  I've had ff, opera or something else crash and when I tried to restart it, it would report that it was already running.

That's when I'd have to kill the pid to get it up and running again.  In Windows we would just reboot.   Ooh!  I used to hate that.

---

### Post by LoneWolfJack on 2009-01-04
> That's another good point. I've had ff, opera or something else crash and when I tried to restart it, it would report that it was already running.

Nah, that's yet another different problem. If a program crashes, it won't necessarily be removed as an active program at once (aka turn into a zombie process)... in this case the kernel will kill it after a few seconds. So next time it says FF is still running, wait 2 or 3 secs and then try launching it again.

---

### Post by cooney on 2009-01-04
I've had "zombies" last longer than those sorry @$$ed b-rated movies I used to watch as a kid in the 60's :popcorn:

ok!

back to the original problem...

---

### Post by cooney on 2009-01-04
> **cooney said:**
> I've had "zombies" last longer than those sorry @$$ed b-rated movies I used to watch as a kid in the 60's :popcorn:

[B]ok!

back to the original problem...[/B]

elusivespoon	Firefox Version = ?
		Ubuntu Verion = ?

ashen		Firefox Version = ?
		Ubuntu Verion = ?

JayeD		Firefox Version = ?
		Ubuntu Verion = ?

binbash		Firefox Version = 3.1b3
		Ubuntu Verion = ?

LoneWolfJack	Firefox Version = ?
		Ubuntu Verion = 8.10

cooney		Firefox Version = 3.0.5
		Ubuntu Verion = 8.04


Fill in the blanks and let's see if there's a common denominator, else:

> I have this issue in 8.10 too every once in a while... I'm not that sure it's related to FF, seems more like a memory cleanup process or so because I think it only (but not necessarily) happens if I had a program crash in the active session.

I'd call it a less annoying bug but then again it may scare newbies and make them believe that there is a trojan at work or something...

---

### Post by JayeD on 2009-01-04
> **cooney said:**
> Just out of couriousity,

Do you guys try to log out with programs running or have you quit them (especially firefox since that one seems to be the culprit) before logout or shutdown?

I always close everything that I've started before log off/shutdown; but I seem to remember seeing this error window once when I was in a hurry.

Just a thought.

I close everything first.

> **binbash said:**
> It happens mostly at firefox 3.1b3.You gonna kill the pid (ps aux | grep firefox)

firefox isn't in the list of running processes. I checked already.

---

### Post by cooney on 2009-01-04
> **JayeD said:**
> I close everything first.



firefox isn't in the list of running processes. I checked already.

Thanx for your response and a good morning to you.  It's only 4:25 AM here and I'm still living Saturday as the night owl that I am.

FireFox (and I luv it) is a memory & resource hog especially if you start adding extensions and keeping 20 or so tabs open.  Add to that two logons both running ff with a total of 50+ tabs open. I was lucky enough to obtain a few much more modern than I had before, computers that both have p4's with 3 to 4 gigs of ram.  One reports in Ubuntu that it has two processors but as far as I can tell that's because it has hyper threading.

I have experienced one phenomenon with both these cpu's.  When ff is running, the cooling fans are a spinning fast and working overtime.  Shut down ff; all is quite.

Opera doesn't seem to care how many tabs are open.  But, then it doesn't have all those cool extensions.  It does however, have a lot going for it in it's native form that ff doesn't.  It has become my main browser because of that.

Don't know what else to say.

---

### Post by elusivespoon on 2009-01-04
Firefox: 3.0.5
Ubuntu: 8.10

> **cooney said:**
> 
Do you guys try to log out with programs running or have you quit them (especially firefox since that one seems to be the culprit) before logout or shutdown?

Yes. There is nothing running but screenlets.

To be clear, it would be nice if Firefox, or whatever the culprit is fixed. But that is not my primary concern. I just want the running program notice disabled. If I press shut down, my computer should shut down NO MATTER WHAT! If I leave a program running that's my fault. I'm sick of hitting shut down, waiting a little bit, closing my laptop and sticking it in my bag only to find an hour later that it has been overheating the entire time.

Succinctly, the problem for me is not firefox, it's the running program notice.

---

### Post by JayeD on 2009-01-05
I would actually prefer to find out what is wrong and fix it :)

---

### Post by cooney on 2009-01-05
> **elusivespoon said:**
> Firefox: 3.0.5
Ubuntu: 8.10



Yes. There is nothing running but screenlets.

To be clear, it would be nice if Firefox, or whatever the culprit is fixed. But that is not my primary concern. I just want the running program notice disabled. If I press shut down, my computer should shut down NO MATTER WHAT! If I leave a program running that's my fault. I'm sick of hitting shut down, waiting a little bit, closing my laptop and sticking it in my bag only to find an hour later that it has been overheating the entire time.

Succinctly, the problem for me is not firefox, it's the running program notice.

Ya know,

The problem IS with ff whether it shows up on the system monitor or not!:x

I was just tryin' to help.  If you read one of my posts above, you would have seen that when I run ff on my tower, it makes my cooling fans scream. To clarify further; when I quit ff the fans still scream.  It's not until I log out that the cpu fans settle down.  Of course when I launch ff the fans start burning there bearings again.

ff spawns something in Ubuntu and makes it eat up cpu cycles.

You got a few choices:

live with it
whine to the devs
or don't use it

You don't have to be so hostile.  I don't look nothing like that dork that I use as an icon.  And I'm sure I got a lot more hours with computers than you.  Just trying to help.  There is a common prob here despite the individual symptems.  If you can't answer the two simple questions I asked without hostility, then shut the f up.

Last time I'll f'in try to help any of you a-holes.

:confused:

---

### Post by JayeD on 2009-01-05
I appreciate the help [img]http://www.emofaces.com/en/smilies/w/white-flag-smile.gif[/img]

---

### Post by elusivespoon on 2009-01-05
Cooney,
my apologizes for the way my post appeared. I should have written it more clearly. I didn't intend for it to come across as hostile (the all caps was to express my irritation with Ubuntu). I just wanted to be clear that my concern is different than the majority. Again, I'm sorry.


Oddly enough I shut my computer down today with Firefox running and open, and no pop up message. So I got what I wanted, but I'm sure it's not the last I'll see of the program running message.

---

### Post by cooney on 2009-01-07
> **elusivespoon said:**
> Cooney,
my apologizes for the way my post appeared. I should have written it more clearly. I didn't intend for it to come across as hostile (the all caps was to express my irritation with Ubuntu). I just wanted to be clear that my concern is different than the majority. Again, I'm sorry.


Oddly enough I shut my computer down today with Firefox running and open, and no pop up message. So I got what I wanted, but I'm sure it's not the last I'll see of the program running message.



Actually,

I'm sorry that my response was hostile. Nothin' like adding more gas to the fire. Please accept my apologies.

More to the point; There's something about firefox that loves to eat cpu cycles. Even when it's 'not running'. Your conundrum is that when you 'close' your notebook, it overheats; even after you thought you shut it down. My conundrum is that my fans are working overtime while it's supposed to be sleeping in a first login, a second login or whatever.

I really believe, even though our individual problems seem remote & unrelated, that there's a common denominator. I just can't peg it down.

Just tryin' to get to the bottom of it.

Very frustrated here also,

Bob
__________________
Results not guaranteed. Your libraries may vary.

---

### Post by cooney on 2009-01-07
> **JayeD said:**
> I appreciate the help [img]http://www.emofaces.com/en/smilies/w/white-flag-smile.gif[/img]

Thank you. JayeD!

It's been a rough (ruff) year and I need to get back into the swing here.

---

### Post by cooney on 2009-01-07
Guys & gals,

I'd still like to have the following blanks filled in as I would like to fill a bug report out if I had enough info.

elusivespoon Firefox Version = ?
Ubuntu Verion = ?

ashen Firefox Version = ?
Ubuntu Verion = ?

JayeD Firefox Version = ?
Ubuntu Verion = ?

binbash Firefox Version = 3.1b3
Ubuntu Verion = ?

LoneWolfJack Firefox Version = ?
Ubuntu Verion = 8.10

cooney Firefox Version = 3.0.5
Ubuntu Verion = 8.04

---

### Post by cooney on 2009-01-07
It's kind of spooky but, I rebooted and am running anything & everything but firefox and my fans are quite.

Without ff running, WOW! What a difference!

---

### Post by cooney on 2009-01-07
Here's a few pics to demonstrate the diff with ff

Note how the time between the posts.  (well it was a good 20 minutes & reboot to regain control before I did a grammar check) I had to reboot to get my systems attention.

You got probs?

---

### Post by todak on 2009-01-07
Mine used to be the same way. So, I typed in **about:config** in the firefox address bar and typed ```
browser.cache.memory.enable
``` into the **filter** bar and the set the value to **false**. That solved all my firefox memory hog problems. If it does not help, then change the setting back to **true**. Hope this helps! :D

---

### Post by cooney on 2009-01-07
see [this]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/16465")

and [this]("http://ubuntuforums.org/archive/index.php/t-492999.html")

and [this]("https://lists.ubuntu.com/archives/ubuntu-mozillateam-bugs/2008-July/048544.html")

Do I need to keep going?

---

### Post by cooney on 2009-01-07
> **todak said:**
> Mine used to be the same way. So, I typed in **about:config** in the firefox address bar and typed ```
browser.cache.memory.enable
``` into the **filter** bar and the set the value to **false**. That solved all my firefox memory hog problems. If it does not help, then change the setting back to **true**. Hope this helps! :D

todak,

I'm gonna try that now; do a total reboot;  and get back with the results.

Thanks for some fresh input on an old and ongoing problem!

---

### Post by cooney on 2009-01-07
Ain't perfect but better.  I'd like to know what some of those other about:config settings do

thanx again

bob

---

### Post by cooney on 2009-01-07
never saw ff report being asleep before that change

---

### Post by ashen on 2009-01-09
Cooney,

Thanks for your help.  Sorry to post and run before - i've been busy and not had a chance to check the forums!

ashen 
Firefox Version = 3.0.5
Ubuntu Version = 8.10

I haven't checked to see if firefox is still running when the problem occurs, but it doesn't happen every time.

I'm also running Foxmarks and the GoogleToolbar.

Cheers,

ashen

---

### Post by cooney on 2009-01-10
elusivespoon,

> I'm sick of hitting shut down, waiting a little bit, closing my laptop and sticking it in my bag only to find an hour later that it has been overheating the entire time.


Even though you're using a portable and I'm using a tower; the common problem here is overheating/excessive cpu cycles or somethings still running that shouldn't be after shutdown/suspend/hibernate or the computer sitting there waiting for you to return from lunch.

Did you try todak's advice:

> Originally Posted by todak  
Mine used to be the same way. So, I typed in about:config in the firefox address bar and typed 
Code:
browser.cache.memory.enable
into the filter bar and the set the value to false. That solved all my firefox memory hog problems. If it does not help, then change the setting back to true. Hope this helps!

I know that it doesn't cover:

> a dialog popping up when I try to shutdown that says, "A program is still running:"

I've seen that dialog once or twice in the past but I assumed that I forgot to shut down some app that required my attention.  My bad?

That setting todak refers to definitely calmed down my cooling fans while having two ff's running on two different logins with both of them not being accessed.

In fact it took running something like gnome-mplayer to get the fans above idol after the change.

Did you at least try it?  The point of these forums is to get a resolve.  Or at least which path to take to get us to 'Oz'. ;)

Thanx again todak.

---

### Post by elusivespoon on 2009-01-11
Unfortunately the problem is so sporadic that I can't really be sure if it's gone. I haven't found a consistent way of making the dialog pop up.

Worse yet I have a more dire problem that is currently sucking up all my time, so this is on the backburner for the moment.

---

### Post by richardh9936 on 2009-03-17
Don't panic.  These people think it's a remnant from Firefox.  See 
 [http://ubuntuforums.org/showpost.php?p=6629969&postcount=9]("http://ubuntuforums.org/showpost.php?p=6629969&postcount=9")

---

### Post by kamssada on 2010-01-29
[http://www.youtube.com/watch?v=lELZWqqnxFc](http://www.youtube.com/watch?v=lELZWqqnxFc)

from your description it looks like we may be having the same issue, check my video out...

---

### Post by kamssada on 2010-01-29
Anyne with a solution?

---

### Post by no2498 on 2010-01-29
im just asking
any of you ever look in ( gstreamer-properties )
to set the x sever to no

this is from cheese

You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

---

### Post by Docaltmed on 2010-02-14
> **no2498 said:**
> im just asking
any of you ever look in ( gstreamer-properties )
to set the x sever to no

this is from cheese

You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

What does this do to your video?

---

### Post by Jbike on 2010-10-19
I don't know that this has anything to do with Firefox. I will be careful to see if I ever open FF when I see the bug and report back. I'm running two Athlon 64 machines with different Motherboard manufacturers (both nvida but different chipsets) in my house that have the bug. Both are 10.04, both are running the 64bit version, and both have the bug almost every logout or shutdown whether or not FF is running. Interestingly, on one of these machines I duel booted the 32 bit version of 10.04, and  this install has NEVER exhibited the bug! I also really want to get to the bottom of this one. 

Any more news on this one? 
Jbike

---

### Post by Jbike on 2010-10-22
So I tried shutting down after a fresh boot without starting firefox (or any program for that matter) and I still get the logout bug telling me that a program is still running (a program that doesn't show up in the system monitor). 

Any additional ideas? 

I forgot where I found this, but is this the bug?

[https://bugzilla.gnome.org/show_bug.cgi?id=546755](https://bugzilla.gnome.org/show_bug.cgi?id=546755)


thx 
Jbike

---

