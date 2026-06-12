---
title: "What's up with applications logging me out?"
date: 2010-07-19
forum: Desktop Environments
---

### Post by rifter on 2010-07-19
It defies explanation from a systems point of view.  Starting an application should not cause the user to be logged out, no matter what that application does.

When I first encountered this, it was a problem with Chromium.  One day it got updated, and after that for a good while if I ever had to kill and restart Chromium the restart caused me to be logged out.  No, it did not crash the X server.  Not at all.  As a matter of fact all my applications gently closed just like they would if I had chosen log out from the menu.  Mind you, this generally happened because pulseaudio would start acting up, using 100% CPU without accomplishing anything (as in it was not playing sounds) so I would have to kill that with pulseaudio -k, but then any application that makes sounds will not make sounds anymore when you do that unless you restart them.  I might have tried seeing whether starting chromium, quitting it, and then restarting it did the same thing; I vaguely remember doing that and having it do the same thing.

An update or two later, Chromium stopped doing that.  An update or two after that, it started again.  Eventually it stopped.  I don't know what about the updates fixed the problem, but it is still very strange to me that starting an application would cause me to log out.

Another time I was faced with not being able to log in because I was immediately logged right back out.  This happened after a bad reboot (wherein I had tired of the system locking up on me - this seems mainly to be an I/O problem I would like to fix at some point) ... basically I hit the power switch and when I came back up and tried to log in, I was logged right back out.  This time the culprit (as I guessed) was corruption, at least I think it might have been, in the session files that save what programs were running so they can be restarted.  It could just as easily been that one of the programs that was getting restarted was causing the issue.  In any case logging into failsafe gnome and turning off that feature fixed it.  I seem to recall having to do something extra to delete the sessions but I can't remember right now.  In any case I never ever used that feature again.  It boggles my mind that starting apps on startup will do this, yet here it is.

Fast forward to more recently.  Again we have bad reboots, but this time there are no naughty saved sessions of applications to blame.  However, there are still the startup applications.  Lo and behold, logging into failsafe gnome and then turning off all the startup applications worked, and I could log into regular gnome again.  I gradually turned on just a few of them, although the volume control was a lost cause, and continued on my way.

Then it happened.  One day, I am sure after a bad reboot but even if it wasn't there have been many since, I could not log in to regular gnome, and even if I went into failsafe and turned off every startup application I was still out of luck.  This is where we are now.  I can't log in at all except into failsafe.

This presents three puzzles, two of which may be academic at this point:

1) Again, how can launching an application log a user out?  That does not happen on any other system I have ever used other than Ubuntu.  Heck, it never happened to me in Ubuntu until at most a few months ago.

2) Okay, I get that if something is writing to a file, and it doesn't get to finish because someone cold-booted the thing or killed it, the internal consistency of that file is not guaranteed.  In other words, it will probably not look right to the program next time because it has been corrupted in this way.  However, this begs the question of what Gnome is writing to that is getting corrupted.  The session files storing what applications are running I will give you.  But with that feature turned off, what do we have left that would be getting written to 24/7?  I would think that the user preferences would get opened for writing when you change them and then only opened for reading after.  But even if that weren't the case, I would still wonder not only why, but what could be being written there and how is this stopping logins from working?  I suppose it is possible that just because the file is opened for writing something nasty could happen even if data wasn't supposed to actually be being written, but I am skeptical this would happen a lot.  It makes more sense that Gnome is writing something and not finishing, and that for some reason whatever it is working on is so important that you cannot possibly log in, not even with an error message.

3) What files should I be looking for as a culprit?  Now I think I have read elsewhere about nuclear options like creating a whole new user, or deleting everything under ~/.gnome2 or something, but to me this has to be beyond what is actually breaking.  Doing the former is really crazy, but even the latter means resetting all the settings that have anything to do with gnome.  As often as I am having to reboot it would be very sad to have to set up everything all over again each time I did.  I would hope that there was something more specific I could look for here.

Whatever the problem is, I don't think bouncing the user right back to the login screen without so much as an error is the right answer for these situations.  It creates confusion.  For many people I am sure it's fairly indistinguishable from having the wrong password or something.  I get that losing the user context because you just logged him off is a sticky enough problem, but there has to be some way.  Even an error in a cryptic logfile in some arcane location I would live with, but for the average user it would not be good enough.

For the record I am using Ubuntu 9.10 AMD64 with all the updates.  I have not updated to Lucid yet because: 
1) I have never had a dist upgrade work -EVER-.  It always required reinstalling everything from scratch again.  I don't have time for that now, but at some point I will swallow the pain and go for it anyway.
2) Given what has gone on in 9.10 bugwise, it seems to me a good idea to wait awhile for people to find and squash the new and exciting ones in Lucid.  That's true for any product.  I usually do wait for things to cool down a bit before jumping in.
3) I don't have time to deal with that right now.  It's enough to deal with what goes on with my system at this point, but beyond that I do kind of want to use my system for things other than tinkering with exciting problems with the operating system and attendant applications.  As things are, just dealing with blockers and showstoppers when they interrupt workflow is quite enough.  I guess this is covered under #1 and #2.

---

