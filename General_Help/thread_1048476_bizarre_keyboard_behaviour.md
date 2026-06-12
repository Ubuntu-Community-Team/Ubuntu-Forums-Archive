---
title: "bizarre keyboard behaviour"
date: 2009-01-23
forum: General Help
---

### Post by pmcginley on 2009-01-23
ok, i posted this under hardware, but i think that was maybe the wrong place, so i'll try here:

my keyboard is acting very strangley, and i'm beginning to lose my mind.  every now and then (that is to say, quite often) a key that i press will decide that i have not let go.  annoying enough if it's just a llllllllllletter repeat, but even more annoying if it's control or shift or backspace.  it's also sometimes delayed, so not the last key i hit.  what's more, it's not my keyboard, because it doesn't happen at all in windows.  i've tried various combinations of turning off 'key presses repeat...' etc in the keyboard preferences, but nothing changes.

i'm using intrepid on a toshiba m-series laptop.  this just began out of the blue a few days ago; before that i'd been computing happily 100% in ubuntu for several months.  this is starting to make things completely impossible - i'm impressed i got through this post.  help!

---

### Post by pmcginley on 2009-01-24
really?  no ideas whatsoever?  am i doomed?  i'm out of options other than a total reinstall or returning to windows - it's becoming more or less unbearable...

*someone* must find this particular piece of bizarrity a worthwhile challenge - i'm beat!

---

### Post by gettinoriginal on 2009-01-24
I am only guessing, but in system, pref, keyboard, uncheck repeat, then immediately reboot to let the system reset :confused:

---

### Post by pmcginley on 2009-01-24
hooray, a reply!!!   :)

i have fiddled with the keyboard preferences, although i didn't reboot afterwards, so i'll give it a shot and report back.  it would be annoying not being able to use keyboard repeat, but a lot less annoying than this current situation.  thanks for helping me try to troubleshoot this oddity!

---

### Post by pmcginley on 2009-01-24
nope, sadly, that hasn't done it.

i can't imagine how this could be related, but i'm clutching at straws here, so i'll mention it: another (milder) oddity has begun, at approximately the same time.  occasionally when i switch to my firefox window, the title bar, with the min, max, and close buttons, is gone.  i have to f11 into fullscreen, and then back out to get them back.  this problem i know is highly documented and has been narrowed down to beryl (i don't what that is) and compiz (which i'm using) but none of the recommended fixes have worked for me.  i can't think of any relation compiz could have with my keyboard though.  and i can't think of any event (new software install, etc) that correlates time-wise to the appearance of these two problems.  everything was running beautifully!

any other guesses?  even longshots could help me zoom in on what the problem is.  

is there any chance an old keyboard could work in windows but be too worn out for ubuntu?

---

### Post by pmcginley on 2009-01-24
hm, and maybe another clue: i've now noticed that when i go to shut down or restart i get a window that says:


'a program is still running:

[blank where the name of said program ought to be]
not responding'


this is, of course, after having exited all running applications.  i'm not familiar enough with process names to recognise if there's anything in my system monitor that shouldn't be there - is there something i should look out for as possibly causing this (and maybe other) problems?

---

### Post by gettinoriginal on 2009-01-25
System, Administration, System Monitor, Processes, check to see if an application is running that you did not start. There may be an app auto starting that you are unaware of.  I am giving a screenshot of my processes for comparison. 
About the firefox window and the title bar, F11 twice, **manually** minimize firefox, close firefox, then reopen and maximize with max button.[ATTACH]100988[/ATTACH]

---

### Post by pmcginley on 2009-01-25
thanks for the tips.

as an update:  it seems that somehow a keyboard *can* behave differently in windows and linux on the same machine.  i couldn't take it anymore, and did a complete reinstall of ubuntu.  and my little button-sticking problem was immediately apparent.  so i guess it is my keyboard wearing out, since it just started out of the blue last week.  and yet, still no problems if i boot in windows.  i wouldn't have thunk it possible.  weird.

not sure what i'll do now.  buy a mac? ;)

---

### Post by pmcginley on 2009-01-25
i can't believe i'm going to beat this dead horse, but i've just come across some more evidence in the favor of weirdness:

thanks to another thread i discovered the xev application, which shows real time feedback about keystroke actions.  all the keys that are causing problems show themselves as working perfectly under xev - no 'sticking' or any other odd behaviour.  they show a 'keypress' event, and then a 'keyrelease' event, without delay or fault.  but my problem persists.

i'm wondering now if it could have anything to do with a recent update? i reinstalled ubuntu, but i stupidly didn't think to check for my problem until everything was fully updated and all my software was reinstalled.  i hadn't installed any new software when the problem started, but some update??  is there a way to uninstall updates?  it would be something from on or soon before jan.20th...

---

### Post by pmcginley on 2009-01-29
bbbbbbbbbbbbbbbbumppppppppppp

still suffering my random key repeats.  nearly guerrilla deleted my entire home folder yesterday.  any other ideas?

---

### Post by rolandrock on 2009-01-29
A long shot...

I had a similarish problem a while ago that was workedaround by hitting both shift keys at the same time.  If memory serves me right, it turned out to be an 'accessibility' program that was behaving strangely with my hardware.  There are such settings in compiz so you could try disabling that to narrow the field.

Several software/hardware upgrades later, my problem has not recurred.

Happy hunting.

---

### Post by pmcginley on 2009-01-29
hmm, i've disabled all the accessibility options in compizconfig, but sadly that hasn't done it.  how can i completely disable compiz?  i've selected 'none' under 'system/preferences/appearance/visual effects'; is that the same as disabbbbbbbbbbbbbbbbbbbbbbbbling it (woops - there it goes again)?

about this workaround - did anything happen when you hit both shift keys?  any kind of confirmation or window opening?  i get nothing.

there's also this mysterious SCIM input method setup that seems to have something to do with keystroke combinations and shortcuts, but i have no idea what that is.  could it be involved?

thanks for the lead rolandrock!

---

### Post by Roving Sign on 2009-01-29
I have the same issue - occasional key repeats. Did everything you did as well - still the occasional misfire. Once a sentence or so...only slightly annoying though.

This is a hard one to resolve - since I cant INTENTIONALLY make this happen...it makes it hard to test.

---

### Post by pmcginley on 2009-01-29
> **Roving Sign said:**
> This is a hard one to resolve - since I cant INTENTIONALLY make this happen...it makes it hard to test.

well, i'm glad to hear i'm not the only one - no offense...  ;)

i think the key is to determine that it definitely *isn't* just a hardware fault.  does it occur if you're booted in another OS; can you reproduce it with another keyboard in the same machine.  you can also test how your machine is receiving keystroke commands with the xev application i mentioned.

i'm finding it's happening more and more now.  its been about 2 weeks since it appeared.  and, yes, if it were only a slight annoyance when entering text it wouldn't be so bad, but it's using key-commands (ctrl-c, ctrl-v, del, multi-selecting with shift, etc) that causes problems.  now i find i have to avoid *all* key commands or i find myself in situations like yesterday where i deleted one file with the delete key, and it went off and deleted half the files in my home folder before i could react.  luckily they only went into the trash and i could recover them all.  even letter keys - i usually can't tell it's happening, and if i right-click something it will automatically launch whatever command is associated with the letter it thinks i've been holding down for the last 3 minutes...

with every minute update i hope it will magically go away, but so far no luck.  it's debilitating.  i'll give it another week or so, but if i'm still not getting anywhere i may have to give up and return to xp...

---

### Post by rolandrock on 2009-01-29
Doing what you did should be sufficient to disable compiz so that is ruled out.

As for the workaround, When I pressed two shift keys, there were no messages or windows but the repeating key would stop immediately (until it happened again).  I also had unpredictable case changes and strange Alt-TAB behaviour all of which were reset by the SHIFT-SHIFT thing (sometimes Ctrl-Ctrl worked too I think).

I definitely believed this was a software issue at the time but I am a bit more hazy about it now.

I don't suppose you have anything in /etc/X11/xorg.conf other than the default?  Mine reads:

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Other than that, I am at a loss.  Time to break out the hardware-hammer.

---

### Post by pmcginley on 2009-01-29
> **rolandrock said:**
> I don't suppose you have anything in /etc/X11/xorg.conf other than the default?

well: my xorg.config is rather short - no 'inputdevice' section at all.  here is the entire file (with the warning text at the top removed):


Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


does that tell us anything?  i'm a bit lost in there, i'm afraid.  i already gave up trying to get my s-video out to work for fear of mucking about in there...

---

### Post by Roving Sign on 2009-01-29
Another key that seems to work strangely is the up and down arrow keys - 

If I use them on this forum - it seems like the key outputs enough strokes to to scroll all the way to the bottom of the screen - the screen even goes grey...and CPU activity spikes. Not sure its related - but similar for sure.

---

### Post by oscarsfriend on 2009-01-29
I had a similar problem, though not quite so bad (keys would occasionally repeat, and adjusting the key repeat settings in gnome had little effect, other than to minimize the problem).  Could it be related to the bug reported [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/264196"), and the other mentioned further down the page?  It appears to be due to a buggy evdev driver.

Try running this from a terminal:
```

sudo kbdrate -r 25 -d 500

```

Which will manually set the keyboard rate and delay (adjust the settings how you like).  If this works out, then you will need to set this to run at boot.  I would suggest adding this line to /etc/rc.local (before the line that reads "exit 0"):

```

kbdrate -s -r 25 -d 500

```

This worked for me, at least, and is better than the workaround given at the top of the bug report (the one I give above is taken from the comments further down that page).

---

### Post by pmcginley on 2009-01-29
> **oscarsfriend said:**
> Try running this from a terminal:
```

sudo kbdrate -r 25 -d 500

```


thanks ocsarsfriend - as a quick try this hasn't done it for me, but i will explore those bug reports a bit more.  what i still don't understand is why this would have just started out of the blue?  i was having no problems up until 2 weeks ago...

if it might help to narrow it down, i'm not sure it's *just* a key repeat issue in my case.  to explain: each time i try a possible fix, i then open my thunderbird inbox for the quickest/easiest signs of whether the problem is resolved.  i select one message, then hold down ctrl and try to select another in the list.  what shows me that i still have a problem is that 

a) initially it acts as though i'm *not* holding down ctrl, ie, it selects the 2nd message while deselecting the first.

b) after several seconds it begins selecting multiple non-adjacent messages as it should

c) when i release the ctrl key it continues adding every message i click to the multiple selection, and i can usually only get it to stop by hitting shift and/or ctrl again multiple times

hm, yes, typing that out has made me think: key repeat is one thing, but it shouldn't be *key-repeating* keys like ctrl, shift, etc, at *all* should it?  they should be durational (function if held down, cease if not).  is that a clue?

---

### Post by oscarsfriend on 2009-01-29
> **pmcginley said:**
> thanks ocsarsfriend - as a quick try this hasn't done it for me, but i will explore those bug reports a bit more.  

Oh well, it was worth a try, anyway.

> **pmcginley said:**
> what i still don't understand is why this would have just started out of the blue?  i was having no problems up until 2 weeks ago...

Is it possible you updated something then, maybe the X server?  Other than that, I can't help - I hope you figure it out though.

---

### Post by pmcginley on 2009-01-29
> **oscarsfriend said:**
> Is it possible you updated something then, maybe the X server?  Other than that, I can't help - I hope you figure it out though.

it's eminently possible, but only if something came through as a recommended update in the update manager.  is there a dated list of recently issued updates somewhere?  and is it possible to roll them back?  i'd happily revert to an older version of x if an update is causing this - it was fine before...

---

### Post by oscarsfriend on 2009-01-29
> **pmcginley said:**
> it's eminently possible, but only if something came through as a recommended update in the update manager.  is there a dated list of recently issued updates somewhere?

Try File > History in synaptic, and have a look about.  I'm not sure if it keeps records of updates there or not, but I'd guess it probably does.

> **pmcginley said:**
>  and is it possible to roll them back?  i'd happily revert to an older version of x if an update is causing this - it was fine before...

Short of reinstalling from the CD and **not** updating whatever broke things, I'm not sure, but it maybe possible.  But before you go down that road, it might be worth trying a few more things first.

Try jumping out of X to a terminal with Ctrl+Alt+F1 (Ctrl+Alt+F7 to get back), and login, and try typing there and see what happens.  I guess that should tell you whether the problem is with X or not.

If that works OK, then try creating a new user account in gnome (or whatever desktop you use), and log into that account and play about and see what happens - I've had gnome go screwy in the past after its config had gotten corrupted.

Another possibility is that it might be a hardware problem, like the plug on the cable that connects your keyboard to the motherboard might have worked loose, and needs to be unplugged and plugged in again.  Try booting up a Live CD and seeing what happens there.

---

### Post by pmcginley on 2009-01-29
> **oscarsfriend said:**
> Try File > History in synaptic, and have a look about.  I'm not sure if it keeps records of updates there or not, but I'd guess it probably does.

indeed it does!  unfortunately i forgot i've already done a full reinstall since this started, so all updates to the system i've done this time round were done in one fell swoop.  makes it harder to isolate...

> **oscarsfriend said:**
> Try jumping out of X to a terminal with Ctrl+Alt+F1 (Ctrl+Alt+F7 to get back), and login, and try typing there and see what happens.  I guess that should tell you whether the problem is with X or not.

hm, well, everything works fine there, but it's hard to be sure - my problem is very rarely (but not never) with letter keys; it's almost always command keys (ctrl, shift, del, etc).  harder to test in a terminal, although shift and del seemed to be working fine.

> **oscarsfriend said:**
> If that works OK, then try creating a new user account in gnome (or whatever desktop you use), and log into that account and play about and see what happens - I've had gnome go screwy in the past after its config had gotten corrupted.

equal screwiness immediately apparent in a new user account.

> **oscarsfriend said:**
> Another possibility is that it might be a hardware problem, like the plug on the cable that connects your keyboard to the motherboard might have worked loose, and needs to be unplugged and plugged in again.  Try booting up a Live CD and seeing what happens there.

i'm pretty sure i've ruled out hardware problems already, as it doesn't happen in windows at all, and also i was able to test key responses with xev, and everything reads as it should.  ah, but yes, i'll try booting from the cd and see what happens...  will report back...

---

### Post by pmcginley on 2009-01-29
well - now i'm really confused.  i booted from the cd, and my problem was there, bigger than ever.  what does that tell me?  that it can only be hardware?  it didn't happen before, it's happening now, and it happens even with the live cd.  so it can't be some random update, right?  but it doesn't happen in windows, and xev...  well now i'm completely, completely baffled...

---

### Post by oscarsfriend on 2009-01-30
> **pmcginley said:**
> well - now i'm really confused.  i booted from the cd, and my problem was there, bigger than ever.  what does that tell me?  that it can only be hardware?  it didn't happen before, it's happening now, and it happens even with the live cd.  so it can't be some random update, right?  but it doesn't happen in windows, and xev...  well now i'm completely, completely baffled...

Hmmm... So it does it from the Live CD, and it does it when you reinstalled - and it **doesn't** do it from Windows, ruling out hardware problems.  The only thing I can think of is that maybe you originally upgraded to Intrepid from Hardy, keeping some old config files on the way, and these have been overwritten during an update some time after the initial install, and are of course lost with fresh install or booting from a Live CD.  So, **did** you initially upgrade to Intrepid or install from scratch?  If this is the case then I can only suggest a reinstall of Hardy, and stick with that for the time being if it works OK (it is LTS), and maybe try a Jaunty Live CD when it's ready.  If you didn't upgrade then I'm at a loss.

---

### Post by Tomatz on 2009-01-30
> **pmcginley said:**
> bbbbbbbbbbbbbbbbumppppppppppp

still suffering my random key repeats.  nearly guerrilla deleted my entire home folder yesterday.  any other ideas?

Does it happen with another keyboard?

---

### Post by pmcginley on 2009-01-30
> **oscarsfriend said:**
> Hmmm... So it does it from the Live CD, and it does it when you reinstalled - and it **doesn't** do it from Windows, ruling out hardware problems.  The only thing I can think of is that maybe you originally upgraded to Intrepid from Hardy, keeping some old config files on the way, and these have been overwritten during an update some time after the initial install, and are of course lost with fresh install or booting from a Live CD.  So, **did** you initially upgrade to Intrepid or install from scratch?  If this is the case then I can only suggest a reinstall of Hardy, and stick with that for the time being if it works OK (it is LTS), and maybe try a Jaunty Live CD when it's ready.  If you didn't upgrade then I'm at a loss.

tell me about it.  nope, the live cd i'm running is the same one i originally installed from - intrepid from the start.  does the live cd make use of *anything* on the machine (drivers or anything?) that could have changed since my initial install?

so am i right in assessing that a broken keyboard would be broken in both windows and ubuntu, or is there *any* chance it could behave differently in each?

---

### Post by pmcginley on 2009-01-30
> **Tomatz said:**
> Does it happen with another keyboard?

i have to admit i haven't been able to try another keyboard.  i am a bit isolated where i am and don't have access to a spare.  i will be heading into the city next week and will do so then.  however, i thought i had enough info to rule out a hardware problem.  also, in my research on this and related bugs i have read accounts of outboard keyboards (i'm on a laptop) behaving differently even when the problem is definitely software...

---

### Post by oscarsfriend on 2009-01-30
> **pmcginley said:**
> does the live cd make use of *anything* on the machine (drivers or anything?) that could have changed since my initial install?

No, it will use whatever default config files come with the Live CD, though I suppose some of the config files on the Live CD may well be different to those on a fresh install from the same CD, since a Live CD is a different setup to a proper install.

> **pmcginley said:**
> so am i right in assessing that a broken keyboard would be broken in both windows and ubuntu, or is there *any* chance it could behave differently in each?

I suppose it is possible that it might somehow be "broken" just enough to not work with Linux but to still work with Windows.  As Tomatz suggested above, it might well be worth plugging in an external keyboard, if you have one lying around, and giving that a try just to finally eliminate the possibility of a faulty keyboard.  [EDIT: Just seen your reply above while I was writing this: yes it might well work differently and the problem not show up, but if it does then you know for sure it's not a hardware problem.  If it doesn't then you're back where you started.]

The only other advice I can offer is to try a Hardy Live CD, and if that works try installing that instead.  Things may well work differently there, and as it's long term support, you might be better off with it until you can find a newer version that works well enough, Jaunty and beyond.  I remember when Gutsy came out, some people had problems with it and rolled back to Feisty, others got on with Gutsy fine.

---

### Post by pmcginley on 2009-01-30
thanks for all your help oscarsfriend (and others).  i will try a usb keyboard when i can get my hands on one.  meanwhile i'm downloading hardy now, and we'll see what happens...

---

### Post by pmcginley on 2009-01-30
welp, indeed, my problem persists with the hardy live cd.

fwiw, i've now discovered a reliable key combination to stop the action, by holding to key in question and hitting shift (deduced by way of rolandrock's suggestion of hitting both shift keys - thanks).  so if my ctrl is 'stuck', if i hold crtl and hit shift, it stops.  if it's the shift key, i can hold one shift and hit the other.  up till now i've just been hitting ctrl or shift repeatedly, which eventually seems to stop it as well, but much less predictably.

this is fine when am aware that a key is stuck, but the real problem is when it catches me off guard...

---

### Post by meanmrmustard on 2009-02-05
> **pmcginley said:**
> bbbbbbbbbbbbbbbbumppppppppppp

still suffering my random key repeats.  nearly guerrilla deleted my entire home folder yesterday.  any other ideas?

Just to let you know you're not alone.
I've waaatched and seen a letter repeat several times after I've released the key.
I also have the title baaar and three buttons disappearing - when I moouse ovvver them they return.

I'm not bothering to corrreect the keypress errors. I'm sick of it and going back to an earlier version. I'm convinced it's Ibex that's at fault...
Hardy didn't do it, nor Gutsy nor Feissty, etc...

---

### Post by Tomatz on 2009-02-05
This might help:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/39315](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/39315)

> Here is the best workaround I have came up with.

Add the following to lines to /etc/rc.local and reboot.
modprobe -r psmouse
modprobe psmouse rate=40

:/

---

### Post by pmcginley on 2009-02-05
> **Tomatz said:**
> This might help:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/39315](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/39315)


hmm, that's an interesting one - it's a lot to digest, and a bit in-deep technical for me, but i shall try to dig through it.  i'm nervous about the fact that most of the suggestions date from 2006, and i'm running ibex - i'm not sure most of the fix attempts are compatible.  although one thing i find compelling is the fact that someone mentions that it seems to be a toshiba specific bug, which is what i have (approx. 5 year old toshiba satellite m-series laptop).

in any case, the suggested mods to rc.local have not worked for me, sadly.  meanwhile, i have now had the opportunity to try an external keyboard, and frustratingly it works perfectly, which once again points to a hardware fault, except, again, for the fact that there are no problems in windows and xev insists the keyboard is working perfectly.

and in response to meanmrmustard: this is definitely not a version problem for me - i have now tried a hardy live cd, as well as an intrepid, kubuntu, and even fedora live cd, and the problem is continually present.  i would happily switch to an older version if it would fix things.  meanwhile, i also had the disappearing-title-bar problem, and fixed it by changing my theme under system/preferences/appearance.  it was apparently a bug in one of the window themes (i forget which - human perhaps?).  i changed to a customized theme with a 'glossy' windows border, and that did the trick...

---

### Post by Donalb on 2009-02-06
I like this part of one of your earlier posts;
"there's also this mysterious SCIM input method setup that seems to have something to do with keystroke combinations and shortcuts, but i have no idea what that is. could it be involved?"

I'm having also seemingly random but different keyboard problems to you. One was space being replaced by asterisks when writing on online forums. It makes your eyes bleed trying to read. Another is not accepting some keys in certain applications (Thunderbird yesterday, Firefox & forums this morning).

One thing I'm sure of it's not keyboard hardware, as I have an new laptop with external keyboard, and it happens on both.

The cause (for me) seems to SCIM somehow. It happened in the middle of a long post I was writing this morning. Plenty of paragraphs were done when all of a sudden FF wouldn't allow me type anymore.It was trying to put in other stuff, a floating text box would jump up and maybe, maybe if a pressed random keys I might get some weird ASCII box thing entering instead. 

I've started trying to find more info on SCIM, which is particularly unhelpful and with an awful GUI that explains nothing. I'm suspecting that because SCIM uses hotkey combinations there might be some problem there. My posts on the subject are getting me nowhere. I am caustic in my dislike of whatever SCIM is, and it's ability to jump into the middle of what I'm doing and screw over.

---

### Post by Tomatz on 2009-02-06
Press ***ctrl alt f4***, wait a few seconds then press ***ctrl alt f7*** and see if that temporarily stops the problem.

---

### Post by Donalb on 2009-02-06
Hey Tomatz, not sure if that was meant for me, I have no wish to hijack someone elses thread.
If it was meant for me , thanks. Funnily enough the problem (floating text box, no text entry) came back when I was writing an email. I tried as you suggested, it had no effect. I tried a 2nd time, and I got logged out after the first step Ctrl+Alt F4. I was unable to get back into the gui so I reset. Problem is gone (again) but I'm no closer to resolution either.

regards
ps where's the "Thanks" button gone?

---

### Post by Tomatz on 2009-02-06
> **Donalb said:**
> Hey Tomatz, not sure if that was meant for me, I have no wish to hijack someone elses thread.
If it was meant for me , thanks. Funnily enough the problem (floating text box, no text entry) came back when I was writing an email. I tried as you suggested, it had no effect. I tried a 2nd time, and I got logged out after the first step Ctrl+Alt F4. I was unable to get back into the gui so I reset. Problem is gone (again) but I'm no closer to resolution either.

regards
ps where's the "Thanks" button gone?

No problem ;)

I just read over at the arch forums that someone with the same problem as the OP was able to temporarily (till next boot) fix the issue by doing the above.

BTW there are no more "Thanks" until the forums are fixed :(

---

### Post by pmcginley on 2009-02-12
> **Tomatz said:**
> I just read over at the arch forums that someone with the same problem as the OP was able to temporarily (till next boot) fix the issue by doing the above.

thanks for that - i gave it a go, no luck though.  the mystery continues...

and donalb - don't worry about 'hijacking' the thread - i've more or less given up on finding a solution for my problem, so if it can end up helping someone one else with something along the way, all the better...  : )

---

### Post by benblout on 2009-02-27
> **pmcginley said:**
> ...it's not my keyboard, because it doesn't happen at all in windows....
Are you sure it isn't happening in Windows?  In a later post you say you might have to go back to Windows, which makes it sound like you are not using Windows recently, or at least not very often.  This just has the feel of a hardware problem to me.

---

### Post by pmcginley on 2009-03-02
> **benblout said:**
> Are you sure it isn't happening in Windows?  In a later post you say you might have to go back to Windows, which makes it sound like you are not using Windows recently, or at least not very often.  This just has the feel of a hardware problem to me.

it's true that i'm not using windows at all these days, but i have tested extensively and repeatedly in windows to see if i can replicate my strange keyboard behaviour, and i can't.  no matter how much i try, everything works perfectly in windows.  however, i have now accepted that it is somehow hardware related, as i have now tried an external keyboard in ubuntu, and it also works perfectly.  so i, with mild disbelief, have now come to accept that my old keyboard must somehow be too worn out for linux, but not too worn out for windows.  perhaps windows has some kind of error recognition/correction in it's drivers - i don't know.  all i know is i seem to have run out of options...

---

### Post by kuritsubaji on 2009-03-14
Glad to bump up this thread if you're still having problems as I am having a weird keyboard issue isolated only to 8.10 and not windows nor KDE 4.:?  But nothing that involves repeating keys.

I have a USB keyboard that's not that old, less than a year, and it will just stop working altogether.  But only in ubuntu.  There are preliminary symptoms too.  I'll look down at the key board and the numlock will be off(when it should have been on) and it will take two tries to make it light back up.  Then, later on, I'll be typing along and all of a sudden, nothing. No response on any keys. Nada. Short of doing a reboot, I'll have to unplug and re-plug the keyboard to get it to work again.  I installed KDE on an entirely different hard drive(I use a mobile rack) and I haven't had the problem show up on it. The system itself is only a few months old(I just did a major upgrade back in October) and the mobo is top o' the line so I don't think it's an issue with the BIOS.

Anybody have any clues about that?

BTW, McGinley, have you tried cleaning out the keyboard with some compressed air at least?  I know your problem seems to be isolated to one OS as well, but for some reason, laptops tend to get a bit more dusty under the keys.  You know, the keyboard is easy to remove on most laptops.  Usually at the top of the key board, hiding between the keys on the top row, you should find two tabs.  Some are the kind that you just push in with the tip of a pen or a small flat screwdriver, and some are the kind that you have to slide out of the surrounding case.  This can make it easier to investigate the condition of the keyboard and can make cleaning easier.  Mind the components underneath:shock:

---

### Post by kuritsubaji on 2009-03-16
bump

I'm bumping this again because the problem the keyboard not responding has gotten so bad that I've resorted to plugging my keyboard into the front of my computer because unplugging and re-plugging is the only workaround. 

Silly... 

I would try another keyboard (although I still think this one is fine) but the only other one I have at the moment is a PS/2.

---

### Post by benblout on 2009-03-16
> **kuritsubaji said:**
> I'm bumping this again because the problem the keyboard not responding has gotten so bad that I've resorted to plugging my keyboard into the front of my computer because unplugging and re-plugging is the only workaround.Have you looked at the syslog while all this is happening?

---

### Post by upchucky on 2009-03-16
this is a laptop, re-seat the ribbon cable of the keyboard, it has come loose from heat. try a usb keyboard to prove.

---

### Post by kuritsubaji on 2009-03-16
> **benblout said:**
> Have you looked at the syslog while all this is happening?

I checked the syslog and it only shows when I plug in the key board with many blank time markers and no indication of anything out of the ordinary.

```
Mar 16 08:04:29 THEFUTURE -- MARK --
Mar 16 08:24:29 THEFUTURE -- MARK --
Mar 16 08:44:29 THEFUTURE -- MARK --
Mar 16 09:04:29 THEFUTURE -- MARK --
Mar 16 09:24:29 THEFUTURE -- MARK --
Mar 16 09:32:58 THEFUTURE kernel: [38933.910704] usb 1-5: USB disconnect, address 4
Mar 16 09:33:03 THEFUTURE kernel: [38938.740008] usb 1-5: new low speed USB device using ohci_hcd and address 5
Mar 16 09:33:03 THEFUTURE kernel: [38938.955850] usb 1-5: configuration #1 chosen from 1 choice
Mar 16 09:33:03 THEFUTURE kernel: [38938.970626] input: Plus More Enterprise LTD. USB-compliant keyboard as /devices/pci0000:00/0000:00:0b.0/usb1/1-5/1-5:1.0/input/input7
Mar 16 09:33:03 THEFUTURE kernel: [38939.028582] input,hidraw1: USB HID v1.10 Keyboard [Plus More Enterprise LTD. USB-compliant keyboard] on usb-0000:00:0b.0-5
Mar 16 09:33:03 THEFUTURE kernel: [38939.034957] input: Plus More Enterprise LTD. USB-compliant keyboard as /devices/pci0000:00/0000:00:0b.0/usb1/1-5/1-5:1.1/input/input8
Mar 16 09:33:04 THEFUTURE kernel: [38939.113460] input,hidraw2: USB HID v1.10 Mouse [Plus More Enterprise LTD. USB-compliant keyboard] on usb-0000:00:0b.0-5
Mar 16 09:44:29 THEFUTURE -- MARK --
Mar 16 10:04:29 THEFUTURE -- MARK --
```

---

### Post by kuritsubaji on 2009-03-16
> **upchucky said:**
> this is a laptop, re-seat the ribbon cable of the keyboard, it has come loose from heat. try a usb keyboard to prove.

pmcginley has the laptop with the repeating keys issue...

I'm having my problem of the keyboard stopping altogether happening on a new desktop.

---

### Post by benblout on 2009-03-17
> **kuritsubaji said:**
> I checked the syslog and it only shows when I plug in the key board with many blank time markers and no indication of anything out of the ordinary.Well, I am out of ideas, sorry.

If it works in KDE and not Gnome, then it sure seems like a bizarre Gnome bug.  You'll probably have trouble getting attention for the bug, though you could try.  I would be curious if it continued with a different USB keyboard, but I don't have any further ideas of how to actually fix it.

> **kuritsubaji said:**
> pmcginley has the laptop with the repeating keys issue...

I'm having my problem of the keyboard stopping altogether happening on a new desktop.
I think upchucky didn't read the thread real carefully before responding.

---

### Post by fieroboom on 2009-03-17
> **pmcginley said:**
> bbbbbbbbbbbbbbbbumppppppppppp

still suffering my random key repeats.  nearly guerrilla deleted my entire home folder yesterday.  any other ideas?

Well, since we're grabbing at straws...
Linux keyloggers can make a keyboard do that. The only two I've ever used are uberkey and lkl. They seem to do fine with USB keyboards, but any serial keyboard will stutter, sometimes severely.
You can run
```
ps aux|grep uber
```
or
```
ps aux|grep lkl
```
But then again, if there's a keylogger on your machine without your knowledge, then it's binary is most likely going to have a different name, which means neither of those commands will show you anything.

Another idea is to reconfigure your X server:
```
dpkg-reconfigure xserver-xorg
```
During the config, you can (re)specify your keyboard layout.
Other than those two, I don't really have any other ideas ATM...
:D
-Paul

EDIT:
Oops, I didn't read all 5 pages... Please forgive me if I just missed something...

---

### Post by pmcginley on 2009-04-04
> **upchucky said:**
> this is a laptop, re-seat the ribbon cable of the keyboard, it has come loose from heat. try a usb keyboard to prove.

thanks for the tip upchucky - is this something i should try even though my problem only happens in linux, and not in windows?  could my cable be too loose for one but not the other?  i don't like messing about in there if i don't have to. a usb keyboard works fine, by the way.

> **fieroboom said:**
> Well, since we're grabbing at straws...
Linux keyloggers can make a keyboard do that.

hm, interesting.  however, i have no idea what a keylogger is.  i ran the two bits of code you suggested, but i don't know what the responses are telling me, if anything:

patrick@patrick:~$ ps aux|grep uber
patrick  29588  0.0  0.0   3236   796 pts/1    S+   14:41   0:00 grep uber
patrick@patrick:~$ ps aux|grep lkl
patrick  29614  0.0  0.0   3236   796 pts/1    S+   14:42   0:00 grep lkl

does that mean something?  i'm still getting my key-repeat problem.  i'm not sure how to follow through on your other suggestion (reconfiguring my x server).

---

### Post by orbitalHermit on 2009-04-25
pmcginley, I'm having the same problem, where a key seems to stick.  In my case, it seems to be one of the modifier keys (Shift, Ctrl, Fn, or Alt).  My system is a brand new clean install of ubuntu 9.04 on a new Asus laptop.  (I also tried Fedora 10, which had the problem too.)  Like you, I've seen no problems with the keyboard in Windows Vista, which I've been using on the same laptop.

It's extremely frustrating, as I've been forced to restart X (with ctrl-alt-backspace) when it happens, since no other keyboard combinations seem to do anything, and the mouse (technically, a touchpad) buttons don't respond properly.  (The Applications, Places, System, and Shutdown menus do not expand when right- or left-clicked, though they do highlight, and stay highlighted once clicked.)

I'll be trying to start xev next time this happens, to see if that helps me diagnose anything.

---

### Post by pmcginley on 2009-04-26
> **orbitalHermit said:**
> pmcginley, I'm having the same problem, where a key seems to stick.  In my case, it seems to be one of the modifier keys (Shift, Ctrl, Fn, or Alt).  My system is a brand new clean install of ubuntu 9.04 on a new Asus laptop.  (I also tried Fedora 10, which had the problem too.)  Like you, I've seen no problems with the keyboard in Windows Vista, which I've been using on the same laptop.

well, that's both good and bad news.  good in that there's finally someone else that seems to be having the same problem ( i no longer feel like i'm trying to convince anyone that the crop circles are real), but bad in that i was hoping maybe trying jaunty might sort out my problem.  if you get anywhere with it, *please* let me know.  i've learned to live with it now, rather like a missing limb, but i'd be very grateful for a prosthetic (or spontaneous regeneration would be even better).

as for stopping the madness when it occurs, mine seems to stop itself after awhile if i just stop typing, or if it's a modifier key (which, like you, it usually is) i seem to be able to stop it by holding down said key and hitting shift.  my default move is shift+shift, ctrl+shift in quick succession when it occurs, and that often sorts it out.  the worst is the flying del key though...

---

### Post by dalrympm on 2009-04-29
I'm not sure why I couldn't find this posting a while ago, maybe I was looking before January.  At any rate, you're not going crazy because I had the same problems.  I never saw a correlation with control keys, I'd basically just be typing and and a key would start to repeat until I typed another key.  I just upgraded to Jaunty 9.04 and I haven't noticed the problems BUT I'm now finding that every now and then a typed key gets missed.  I'm not sure if this bug is mor <- (just did it) annoying than the repeating key or not... I think it is only because it is happening more frequently than the repeated key.

I'm using a Dell Studio 15 that came with 8.04 originally installed.

---

### Post by dalrympm on 2009-04-30
I just experienced my first instance of a repeating key this morning on Jaunty 9.04.  I think I'm going to have to downgrade at this point because it doesn't seem like anyone believes this is a problem and I have no way of reliably repeating it.

---

### Post by pmcginley on 2009-04-30
i too have now upgraded to jaunty, hoping it might make a difference, but no changes, still can't use any modifier keys.  i don't know that downgrading will help you - i've had the same problem with every version of linux i've tried, and that's many.  it started one day out of the blue, and it seems it's here to stay.  i presume there aren't that many of us experiencing this problem, or it might be given some attention?

---

### Post by dalrympm on 2009-05-01
Definitely looks like a Kernel issue... I haven't gone through the bug report thoroughly but it looks like there was a fix up in place a month ago (so definitely not in the latest Jaunty).  

[http://bugzilla.kernel.org/show_bug.cgi?id=9998](http://bugzilla.kernel.org/show_bug.cgi?id=9998)

In summary, apparently this is happening due to having "smart" battery support.  

Don't have time to go through the bug thoroughly right now but will see if there is a way out in the next few days.

---

### Post by dalrympm on 2009-05-01
Ok, I read through and it looks like the fix is in Kernel 2.6.30 and Jaunty is 2.6.28-11.  I'm not a Kernel hacker but I have some friends that might be able to show me how to swap out Kernels (if that's even possible).  On the bright side, it looks like we really aren't crazy and there IS a fix.  If I'm able to get it working, I'll post here.

---

### Post by pmcginley on 2009-05-02
> **dalrympm said:**
> Definitely looks like a Kernel issue... I haven't gone through the bug report thoroughly but it looks like there was a fix up in place a month ago (so definitely not in the latest Jaunty).  

[http://bugzilla.kernel.org/show_bug.cgi?id=9998](http://bugzilla.kernel.org/show_bug.cgi?id=9998)

that thread seems to be specifically addressing a *dropped* keystroke problem, which, while possibly related, could i imagine also have very different causes to our *repeating* keystroke problem.  or am i reading it wrong?

---

### Post by dalrympm on 2009-05-02
I can't remember how I got to that bug (web developer so I clear my cache often) but I remember the path that got me there was specifically referring to lost keystrokes and repeats... they seemed to be related.  It looks like the 2.6.30 kernel will be ready in a few more weeks, I don't think I'm prepared to deal with a release candidate but once it's out I'm going to install it right away.  Apparently they can be installed using the package manager as long as you have the proper repository in your list of sources.

---

### Post by houseworkshy on 2009-05-03
I'm having problems with my keyboard after installing Jaunty too.  The unshifted key to the left of z which which should give the mirror image of / ( sorry but I am unable to type the character ) is producing < instead. It is also wrong when shifted as it gives > and not the one which looks like a colon with short lines instead.  The < and > characters can still be typed from the usual keys. Other keys are also wrong for the standard UK layout which I use.  I did the obvious and went to keyboard in preferences,  on changeing layouts despite the keys matching in the diagrams they refused to budge and stuck to whatever this setting is. I doubt that it is any layout at all as some characters are missing and some can be typed multiple times.  If this is a bug it is one which, on this system, only affects the special characters as all the alphanumeric keys are mapped correctly.  I can't even switch targets in Oolite and am being forced to get on with some work instead.  Please help.

---

### Post by luisama on 2009-05-04
i hope this help to anyone.

for the people that their problems started with jaunty it probably its the new X version, i myself find in problems when look that the new version of X handle key press and release events WRONG, it can be verified by anyone with XEV. NORMALLY it should send a key press event and key release only, now the bug version send key press and release events endessly while the key is pressed, thats not the way everyone expect, thats not the way every program for X has written all this past years, leading to totally erratic behaivor in various applications.

for pmcginley, i had a "similar" problem... but with my touchpad, i started to get the left click pressed after i released it, same with other buttons, and sometimes with the cursor acting xtrange, it was an old laptop. i read all your threat and fell so familiar that made me reply. im also had the problem in ubuntu, in those back days i dual boot windows and the touchpad work without problems there, so same as you i "assume" it was not hardware issue. i also try reinstalling, back then i think i was hacked or get some spyware, keylogger, etc.  reinstall, fresh install even on live cd the problem came back, like you. it happened unexpected from one day and it only get worst with time. before it appears i use ubuntu for years in the same laptop without a single issue like you. i also buy a USB mouse to descart driver problems. i deal with the problem like you for months trying to "solve it", and believe when i tell you i understand how frustating was, fear of just click anything, hoping you dont have to restart or have unreparable damage... finally i give up, deleted ubuntu, installed windoiws xp and sold the laptop, and with that money i pay the laptop im using now. sorry to tell you this, i wasnt 100% sure it was hardware related and wasnt to open it or pay someone to check it, the evidence tell me that it was a touchpad dying, i just dont want to believe it, i never either understand why it worked in windows, my guess is that windows driver are specific to one hardware, in linux one driver should work for hundreds of devices, also the windows driver are maded by manufacter, maybe they put some redundancies in case some circuit fail, who knows... i dont want to kill your hopes, but if the problem is getting worse and you cant live with a keyboard attached to your laptop, i advice sell it like me, if still works ok in windows.

if you can and still want figthing, my 2 cents
-if the problem is in the driver getting or passing all release events to X, it should be enough to re-click just the key, dont need for shift combinations or pressing more keys, if the combination of keys is needed maybe indeed you have some damage in the drawboard (dont know its english name) beneat the keys.
-with XEV you should not just check the keys, you should try to emulate a normal use like writing a mail for example, to see if the problem appears, you can see if all the key press events and release happend, find if is not a sync problem, or maybe the buffer fill up to fast when many events happend in a short time, flushing the buffer and losing some events, etc
-i read all the threat, but you dont mention or i dont get it clear, the repeat event from keys its random, from keys dont even pressed or just hapend when the actual key is pressed, if its not random, it could be that the driver is not catching or sending all the events (i really doubt is a driver issue, since your problem start without changing any driver, and you havent the problem with the same software and drivers months ago) or the 2 boards get stick when you press the key, that could be the reason why sometimes the repeat expire aftertime, same that you must click the key a random times to separate the 2 boards (dont know english very well, i talk about that plastic filled with metallic lines that made contact at the press of the key). i can tell you how cheap and easily fail those boards, one fail at me without a reason, just shut down a working keyboard laptop, guard in the closet for 1 year, turned up and several keys not work at all, the physycal problem was a tiny spot in a metallic line get rooted (dont know if is the rigth word).also i friend keyboard die at a liquid accident, do you have one?
-if the repeat is not random you can live more easy avoding pressing delete, enter, control, alt, etc all the keys that could trigger to lose data, crashes, keyboards shortcuts, bindings, etc you can install a virtual keyboard or use XTE (come with xautomation) to send key events directly to X,

good luck, i truly walked your path and was hard and frustating

---

### Post by geerm on 2009-05-12
hi, let me start off by saying registering to this forums without beeing able to click shift was fun, asking people to post the caracters i couldnt type and then past them, ;d, 

i've been having this problem and it might me coincidence or not, but i disabled the visual effects [had it on extra and put it on none] while this didnt solve it completly, at least i'm able to alt tab again, and yes, when i put it on extra again i couldnt alt tab anymore, still, no shift or ctrl tho, only by restarting is this solved

---

### Post by dalrympm on 2009-06-10
2.6.30 was officially released today so I gave it a try.  I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

Unfortunately I must not have selected the correct wireless driver so I've had to roll back to the previous kernel.  However, I did test with a lot of typing while I was running the new Kernel and I didn't experience the missing keys or the repeating keys.  I don't have any more time this week to get my drivers working but I will give it a go again next week and let you know if longer use sees anything unusual.

---

### Post by dalrympm on 2009-06-19
I started using 2.6.30 for a more extended period of time yesterday and today and I'm sad to report that it fails on both missing keys and stuck keys.  I think I'm rolling back to Ibex since I had fewer problems with that release.

---

### Post by pmcginley on 2009-12-13
well, in case anyone has read through this whole thread and/or has been suffering from a similar problem: today, almost a year after my mysterious sticky keyboard problem first arose, it equally mysteriously went away.  i am now using karmic, but upgraded weeks ago to no affect.  i had gotten used to not using keyboard shortcuts and turning my key repeat off and forgotten about it, to be honest.  but today, something suddenly seemed different.  so i tried some old tricks, turned the key repeat back on, crtl-clicking and shift-clicking all over the place, and everything is back to normal.  i've installed *no* updates today, although there are some waiting.  it's possible that it's been fixed since the last updates came through a week or so ago and i just didn't notice, but i don't think so.  in any case, the moral of the story is:  if something smells fishy, it probably is!  many, many people, and much evidence, pointing to this being a hardware fault with my old worn out keyboard.  but a few clues (which i won't detail again, but are elsewhere in this thread) really made me think that wasn't possible.  and indeed it wasn't.  i guess i'll never know what was really wrong, but i don't really care - i've got my keyboard back, hurrah!

to dalmrypm, if you're still out there: you seemed to be having a very similar problem to me - here's a nudge to check and see if it might have fixed itself!

(ps - maybe someone who's better at forum etiquette can tell me if i should now mark this thread as solved.  my problem has gone away, but i certainly wouldn't know how to solve it...)

---

