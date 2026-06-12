---
title: "Enemy Territory leads to Nautilus hang."
date: 2007-06-13
forum: Gaming &amp; Leisure
---

### Post by Kumeelyun on 2007-06-13
I didn't know if this belonged here or in the beginner section. If it is deemed to be in the other section, I'll happily let it be moved.

Quick background: I recently switched to Linux after over a decade on Windows. I have been running Ubuntu Studio for 2-3 months now on a 3GHz dual-core Intel box with 3GB ram and ~950GB hard drive space.

I was trying out some games, having already installed *Nexuiz* and *Warsow* (both very fun) and I decided to try out *Enemy Territory*. I downloaded the latest file (version 2.60, a .run file) from [Splash Damage's website]("http://www.splashdamage.com/?page_id=14"). Through a right-click on 'Properties' I gave the .run file permission to execute, and double-clicked, letting the file install. upon starting it up, no sound was coming through (bummer) but it seemed to run OK.

My main problem, however, came whenever I tried to navigate to my home directory. When I open a Nautilus window pointed to *"/home/(myusername)/"* The window would go dark and *gkrellm* shows at least one CPU running up to 99-100% (meaning, of course, that it's hanging). If I force quit the window, another would pop up and hang again. I would have to log out and log in again to make it go away. I can use Nautilus to navigate to any other location with no problems, but going to that directory will hang it.

I tried using the terminal, and found I could access the location there with no hangs. I navigated in there a bit. I found I could run *Nexuiz* from there with no problem, other programs run fine from the Start menu, and no files appear to be missing. However, when I navigated to the *Enemy Territory* folder and tried to start it there, it won't run. Terminal says no file or command exists even though *ls* shows the file to be right there. At this point, I'd rather just not deal with *Enemy Territory* right now, remove it, and move on.

If anyone could please answer my questions, they are these:
[B]1. Would removing Enemy Territory remove my hang problem?
2. If so, what would be the best way to do this?[/B]

I also wish to share something I've learned from this situation with other [newbs]("http://www.cad-comic.com/comic.php?d=20060823") like myself:

*While Nautilus is a fine way to navigate the environment, don't let that make you lazy. **Learn to use the terminal.** If I had just left it at a hanging window and not used the terminal, I might not have the insight into the problem I have now. After encountering a few situations like this and using the terminal to delve deeper into the workings of your system, plain ol' text might not seem all that boring and uninteresting anymore (even to a visually-oriented graphic designer like me :D )*

Thanks for reading and answering if you have any insights of your own. I shall now continue with my [computer networker-roommate's]("http://www.thejoe.com") assigned reading: [How To Look Like A UNIX Guru]("http://www.cs.usfca.edu/~parrt/course/601/lectures/unix.util.html").

---

### Post by asipi on 2007-06-14
It is not quite clear for me dude. Ok that u downloaded the installer and gave executable right to it. But did you installed? And the problem occurs when u try to run ET or is it coming from the running that installer?

I recommend to run that installer from terminal with command
```
gksu etinstallerfilename.run
```
because to install it properly you need root privileges. After installation download et2.60b patch (use google to find it) because most of the current mods and servers need it.

Refer here if you have problem again.

PS: Is your system a 64bit system?

---

