---
title: "accessing root"
date: 2006-06-16
forum: Desktop Environments
---

### Post by unisol on 2006-06-16
how do i get root access in ubuntu desktop i open a terminal and type sudo bash it asks for password which i give but i says it is invalid is this a problem in xterminal emulation and how can i fix it

---

### Post by bruce89 on 2006-06-16
You just type the commands you want to ren as root with sudo in front.

---

### Post by aysiu on 2006-06-16
Instead of ```
su
Password:
apt-get update
exit
``` you do ```
sudo apt-get update
Password:
``` Read more here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by ayoli on 2006-06-16
[QUOTE=unisol]how do i get root access in ubuntu desktop i open a terminal and type sudo bash it asks for password which i give but i says it is invalid is this a problem in xterminal emulation and how can i fix it[/QUOTE]
when you sudo command the password needed is your user password not your root password. didn't you use the wrong password?

---

### Post by aysiu on 2006-06-16
[QUOTE=ayoli]when you sudo command the password needed is your user password not your root password. didn't you use the wrong password?[/QUOTE]
unisol shouldn't have a root password. There's only one password asked for during installation... unless you do an expert install.

---

### Post by ayoli on 2006-06-16
that's true i just renember i had to do a sudo passwd to set a password to root.
my mistake :)

---

### Post by raptros-v76 on 2006-06-16
this may be a bit offtopic, but in dapper, is it still a bad idea to set a root password?

---

### Post by Ramses de Norre on 2006-06-16
It's allways a bad idea.. The reasons for using sudo haven't changed.

---

### Post by aysiu on 2006-06-16
It's not a bad idea. It's just different.

If you read this...
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

...you can see the pros and cons of the *sudo* model, as opposed to the traditional root model.

---

### Post by ayoli on 2006-06-16
since i m new to ubuntu i didnt know about this policy, thx for link aysiu, i learnt something today ;)

---

### Post by aysiu on 2006-06-16
ayoli, you may also want to check this out:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by ayoli on 2006-06-16
[QUOTE=aysiu]ayoli, you may also want to check this out:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)[/QUOTE]

that says:
"If you're already familiar with Linux and just wonder why Ubuntu/Kubuntu uses sudo instead of root, this page isn't for you. "

so this page isnt for me, i m new to ubuntu not to linnux, thx anyway, that could be helpfulllllor someone else ;)

---

### Post by aysiu on 2006-06-16
Cool.

---

### Post by jgcamp99 on 2006-06-16
Not this topic again ! ;) How much more secure is cracking a user id & password and trying sudo as opposed to cracking root & it's password. Once in, the intruder uses the wiki to reenable the root password/account, then can do pretty much anything they want to your computer. They can even sudo the user they crack to their heart's content. I assert sudo is no safer than having a separate root enabled password protected account. Bottomline Ubuntu creates the root account and disables it, reenabling it takes a few moments.

You know what I like most about re-enabling the root account. When logged in as root, you can simply click on icons and it works as best it's going to.

---

### Post by aysiu on 2006-06-16
[QUOTE=jgcamp99]
You know what I like most about re-enabling the root account. When logged in as root, you can simply click on icons and it works as best it's going to.[/QUOTE] What I like most about pressing Alt-F2 and typing ```
gksudo nautilus
``` or ```
kdesu konqueror
``` is that I also can click on icons and its works as best as it's going to, but I don't have to go to a separate login screen and then log out again when I'm done--I can run a root window within my user account and operate as both root and user, depending on the task I'm trying to accomplish.

Let's compare a launcher for a new login (for root) and a launcher for *gksudo nautilus*:

**Launcher for new login**:
Click button.
Wait for login screen to load up.
Type in *root*.
Type in root password.
Wait for root to login.
Open up Nautilus.
Make changes.
Close Nautilus.
Log out.
Type in user password to get back into user account.

**Launcher for *gksudo nautilus***:
Click button
Wait for password prompt
Type in user password
Make changes in Nautilus
Close Nautilus

I don't see what advantage logging as root holds. It's not that *sudo* is more secure. It's just more convenient.

---

### Post by ayoli on 2006-06-16
i found the sudo way nice cause you're not supposed  be logged as root on a machine, that's dangerous

---

### Post by jgcamp99 on 2006-06-16
"Some idiots in the Linux camp will say "you shouldn't have to edit such-and-such a file." That's simply not true. Most Linux users aren't just users--they have to install and configure stuff themselves (as Dell or HP won't do it for them), usually configuration files and system files that normal users don't have to touch (say, in order to adjust the possible screen resolutions or install new software). You do have to edit these files from time to time. It's in your best security interests to have to go out of your way to edit them, but you should still be able to occasionally edit, move, copy, and rename files that only an Administrator (or Root) can modify."

These aren't my words, but I'd rather have something fail because it doesn't work rather than add a new variable to the troubleshooting.

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

being logged in as root is not dangerous, there are people in this forum alone that have hosed their Ubuntu installation just the same as being root, using sudo. There are instances where sudo is the heir apparent for blame for a package not installing/working, is it sudo, is it something that would have gone right, being logged in as root. I consider myself a newbie to Linux an dUbuntu in general, in the 2 weeks I've used it, I have yet to hose/break the install or a single application. To date, the only break is a auto login issue with gnome/gdm. This is because it's buggy and broken from the install from synaptic package manager.

---

### Post by aysiu on 2006-06-16
You realize you're quoting me, right?

On that webpage, I espouse using *sudo*, not root--mainly for convenience, not security. As far as I know, for all practical purposes, they're equally secure--as the intelligence of the user and the strength or weakness of the password more than accounts for any variation in default security between the two models.

---

### Post by jgcamp99 on 2006-06-16
I realize it's quoted and regardless of who said it, it comes back to the reality that having root at a system administrator's availability is a lot easier than trying to remember variations of command line sudo. Let's say anyone puts Ubuntu on their box, yeah they use it for a few days and get somewhat comfortable with it, what if they don't spend hours combing google for this, are they ever going to be able to adjust those files or do they ever do anything to this system except get frustrated with it and go back to windows. I'm not saying that Windows is the best way, but when the system administrator does it that way, understands and knows it that way, but why penalize that guy for simply just doing it thru root. The sudo method, is it still available, even if root is allowed to login ? If the answer is yes, it doesn't matter which method you espouse is better, you've taken one option away from the system administrator by disabling that root login. How can that be defended and justified ? Especially since auto login doesn't work at this point in time and the password is prompted to be input at a login screen ?

Further, 

gksudo nautilus
kdesu konqueror

How much longer does it take to open the terminal window or whatever else to type in these commands. You made a big issue of typing in root and a password at the login screen. The word root is a 4 letter word, 1 shorter than either gksudo or kdesu and utilizes "oo", the same letter "o" back to back . nautilus or konqueror, just as difficult to remember as a password, but by the simple fact that  sudo uses them, wouldn't you say you just gave the hacker your password without even making them "brute force" the system for the root and password. gksudo and kdesu under sudo, just as common knowledge to a Linux hacker as the word root, nautilus or konqueror more common than a privately secured password.

I understand sudo works better for you, it doesn't for a large majority of those who are accustomed to root accounts. I think it's a plus Linux does this for users. It's quicker and easier to try things on the fly when an application or whatever goes on dirty and has degrees of success when you are root. That convenience is invaluable for many system administrators, why should they have to issue terminal commands to do certain things that are more readily done and easier as root and graphically with a mouse ?

---

### Post by aysiu on 2006-06-16
Once the launcher is created for *gksudo nautilus*, you don't have to keep typing it. You just press the button. My example is a valid comparison--one launcher launches a new login session. One launcher launches the file browser as root.

---

### Post by jgcamp99 on 2006-06-17
Can I quote you again ?

"Most new Linux users just want to be able to click and drag and drop. So these two new commands should be your new bestfriends..."

"If you're using Ubuntu (Gnome), the command you want is gksudo nautilus"
===============================================
<user>@UBUNTU606LTS:~$ gksudo nautilus
(nautilus:9001): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
===============================================
OK, on a lark I did what you said should be my new best friend. This is what was returned from your "gksudo nautilus" command. Right off the bat, even though file manager opened up shortly afterwards. I read these things, probably like many others and even moreso when I'm unfamiliar with something like I am with the gksudo nautilus command. There's something about the words "Warning", "rejected" and "failed" that raises a flag. To me this means that file manager may have opened up successfully, but it was handled "dirty". So who wants to proceed with this ? Right now the uncertainty is, that although the system still works, something obviously didn't go right with this, even though I followed your instructions to the letter. What will happen on logout or reboot, is it going to have bigger issues or is the slate wiped clean and it's as if nothing like this was ever done ?

And shortly after this happens, it shows up here as a thread or in this case my post to show others. As this is your suggestion, what should one do when this occurs, or should I spend hours waiting for a reply, meanwhile scouring the internet for a crumb or speck of a hint telling me to do something else first or that this is standard and should be expected, something that is the way it's supposed to work ?

---

### Post by aysiu on 2006-06-17
It's fine.

You're seeing those errors because you're running it from the terminal.

Press Alt-F2 and type it if you want.
Make a launcher icon for it.
Make a keyboard shortcut for the command.
Do whatever works for you.

It doesn't negate the fact that it is still more convenient and faster than logging in separately as root just to make a few drag-and-drop or point-and-click file changes.

Does this output scare you? ```
gksu gnome-app-install
warning: could not initiate dbus
** (gnome-app-install:17595): WARNING **: return value of custom widget handler was not a GtkWidget
Got non-package menu entry gnome-commander.desktop
Got non-package menu entry kiso.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Got non-package menu entry granule.desktop
Got non-package menu entry kmyfirewall.desktop

(gnome-app-install:17595): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:17595): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:17595): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed

(gnome-app-install:17595): HtmlUtil-CRITICAL **: html_stream_cancel: assertion `stream->cancel_func != NULL' failed
``` Because that's the output you get when you launch the Add/Remove Applications command from the terminal. *gksudo* can be run from a terminal, but it's much better in a launcher or from Alt-F2 (the run dialogue).

Now, if you want to log in as root because you are *used* to doing so, then just admit that you just don't feel like trying something new.

---

### Post by jgcamp99 on 2006-06-17
aysiu, I really do like you, but trust me on this one ! Below I will show you what being logged in as root does and what the differences are:

===============================================
root@UBUNTU606LTS:~# gksudo nautilus
root@UBUNTU606LTS:~#
===============================================
These are the terminal results and the file manager opened right up, this tells me the command line in the terminal was nice and clean, no error messages. The file manager opened right up and in the same location that it did under the Ubuntu user account, only I know there weren't any errors. But now, I beg to ask why would I even need to issue the gksudo nautilus command, I'm logged in as root, so how is sudo more convenient, in this instance alone ? It doesn't work in my ubuntu user account, but does flawlessly as root, where I don't need to do that anyways. I can simply open my file manager from the menu tree that Ubuntu has already created, yet you prefer that I press Alt-F2 and type it, and so on, whatever works best for me ? Which again, is displayed prominently that it functions properly when logged in as root and it's superfluously unnecessary to being logged in as root.


"It's fine.

You're seeing those errors because you're running it from the terminal.

Press Alt-F2 and type it if you want.
Make a launcher icon for it.
Make a keyboard shortcut for the command.
Do whatever works for you.

It doesn't negate the fact that it is still more convenient and faster than logging in separately as root just to make a few drag-and-drop or point-and-click file changes.

Now, if you want to log in as root because you are used to doing so, then just admit that you just don't feel like trying something new."

---

### Post by aysiu on 2006-06-17
[QUOTE=jgcamp99]But now, I beg to ask why would I even need to issue the gksudo nautilus command, I'm logged in as root, so how is sudo more convenient, in this instance alone ?[/quote] You're not supposed to launch the *gksudo nautilus* command when you're logged in as root. The whole point of the command is that it lets you avoid logging as root. 

> It doesn't work in my ubuntu user account Sure, it does. You just got scared off by the terminal messages because you chose to launch it from the terminal. It works fine.

> yet you prefer that I press Alt-F2 and type it Well, that's because I don't use it that often. If you find yourself using it often enough, it's worth creating an icon launcher for it or, better yet, a keyboard shortcut for it. Once you've done that, it's much more efficient than logging in as root separately to make changes.

---

### Post by aysiu on 2006-06-17
You know, this could just go on forever. I don't think either one of us is going to budge on this.

Let's just leave it at you preferring to log in as root, and I preferring to launch *gksudo nautilus*.

It's all about choice, right?

---

### Post by jgcamp99 on 2006-06-17
"Does this output scare you?"

Quite frankly, yes, that output you have listed should raise concerns for anyone. And when you are looking that just about every other thread/userid in this forum is started or responded to by a newbie, this elicits a first line response of running back to MS Windows, cash in hand. Users want reassurances that something went clean.

To be honest with yourself or anyone else in this forum, you downlaod and install Ubuntu for the very first time, during your initial and subsequent OS setup, you see the words, "warning: could not initiate dbus", wth is a dbus ? why is it not initiated ? Obviously something in Ubuntu thinks that it should be initiated. That's the 2nd line of output. And be honest, the words critical and failed wouldn't disturb any rational, logical thinking human being too ?

---

### Post by jgcamp99 on 2006-06-17
"You know, this could just go on forever. I don't think either one of us is going to budge on this.

Let's just leave it at you preferring to log in as root, and I preferring to launch gksudo nautilus.

It's all about choice, right?"

Deal ! Oh, but wait Ubuntu doesn't allow root to be able to log in by default, it's disabled. So much for choice, unless you become sophisticated enough to re-enable the root password and allow for graphical logins in gnome.

---

### Post by aysiu on 2006-06-17
[QUOTE=jgcamp99]"Does this output scare you?"

Quite frankly, yes, that output you have listed should raise concerns for anyone. And when you are looking that just about every other thread/userid in this forum is started or responded to by a newbie, this elicits a first line response of running back to MS Windows, cash in hand. Users want reassurances that something went clean.[/quote] Well, that's the output of running the Add/Remove Applications command from the terminal.

People don't really seem to mind running the Add/Remove Applications command at all because most of the time... they don't run it from the terminal. If you want, I can amend my page to recommend peope use Alt-F2 or create a launcher or keyboard shortcut instead of launching it from the terminal.

Right now it's a little vague: > Most new Linux users just want to be able to click and drag and drop. So these two new commands should be your new best friends...

If you're using Ubuntu (Gnome), the command you want is gksudo nautilus

If you're using Kubuntu (KDE), the command you want is kdesu konqueror  Almost makes it sounds as if they should be input in the terminal.

What do you think--change it?

---

### Post by unisol on 2006-06-17
i dont have a root password my password works when logging on at the log-in screen but when i try to use an app that requires root privileges it tells me the password is invalid ive built this up from a server install and i solve something else everyday  im learning a little at a time thanks to you guys

---

### Post by ayoli on 2006-06-17
have you got this line in your /etc/sudoers (hve a look with: cat /etc/sudoers) ?
```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```
if not edit your sudoers file with visudo as root.

you also may ad your user to adin group if youruser doesnt belong to it by typein:
sudo adduser your_user admin

---

### Post by martal on 2006-06-17
I'm going to have to try and install the official ATI driver soon. It's always failed with 'must be logged in as root' or similar.

If I start off the terminal session with su, will I get to the end?

---

### Post by ayoli on 2006-06-17
[QUOTE=martal]I'm going to have to try and install the official ATI driver soon. It's always failed with 'must be logged in as root' or similar.

If I start off the terminal session with su, will I get to the end?[/QUOTE]

sudo works for that in a term:

sudo command

where command is the command to install what you want

---

### Post by martal on 2006-06-17
Not for this ATI driver, it doesn't!

Just tried su, with user pass. Authentication failed.

Looks like I must setup root password.

---

### Post by ayoli on 2006-06-17
ah, have a try with su
but if your root haven't got yet a pasword you have  o set it before with:

sudo passwd root

you ll be asked for your user password, then enter twice your new root password

---

### Post by martal on 2006-06-17
Yep. Done that. Now downloading ATI.

---

### Post by jgcamp99 on 2006-06-17
"Almost makes it sounds as if they should be input in the terminal. What do you think--change it?"

I think it would make for a better "How to", it would steer someone completely away from whatever might be misconstrued as a failed operation that is conveyed thru the x-term.

I've seen love and hate posts regarding Ubuntu, even though I'm getting some negative feedbacks thru the x-term. It just drives me to find a way to install it another way where the warm fuzzies of going completely clean is what I'm after. What prompted me to go after the re-enable of the root login was that I tried installing the flash player 7 and under the user account, it kept kicking me to a manual install. The notes with that zip file told me manually all I had to do was copy a couple of so files to the plugins of Firefox. That's when I went to that directory, copied the files there and it told me I had to be root to do that. So after reenabling root, that manual effort went flawlessly, it worked over to the ubuntu user account too. Since then, I haven't pursued sudo whatsoever. I was hit by the same updates everyone else has received thru the auto update process. So I log out, go back in as root and download, install & apply them. I'm ecstatic with Ubuntu with full functionality. I think because Ubuntu first goes onto any system as a live cd, that allows for the test drive, so root logins are totally unnecessary, but the minute I put it on as the hdd install, I feel I need the root login for what we've discussed. 

I just got a Vista Beta dvd and it's good until 6/1/2007. Ubuntu has me sooooo pleased, I honestly don't care whether I install Vista at this stage, who knows in a few months I may be inclined, but for today, why should I want an OS that requires an 800 Mhz system instead of a 400 Mhz system as the minimum requirement ? Advantage Ubuntu.

---

### Post by aysiu on 2006-06-17
[QUOTE=jgcamp99]"Almost makes it sounds as if they should be input in the terminal. What do you think--change it?"

I think it would make for a better "How to"[/QUOTE] I've changed it. Let me know what you think of the revision.

The first instruction asks for Alt-F2. Later on on the page, I say that if you find yourself using the command often you should create a launcher icon for it.

---

### Post by jgcamp99 on 2006-06-18
aysiu, super job, had a question though. Will preface it with: alt-F2 gets the run dialogue box to pop up, the run in terminal option is still there. When gksudo is run in the terminal either with the alt-F2 "run in terminal" box checked or just simply thru the X-terminal window. Why does gksudo nautilus have those error messages when logged in as the ubuntu user and it doesn't as root ? My other question, what is the difference between the run command and the x-terminal ? Windows has something similar too, Run can be used or the old DOS C: prompt can be brought in. I was under the impression that run and x-terminal were using the same processes, just that x-terminal brought it up in the traditionally 1980's command prompt window ?

---

### Post by aysiu on 2006-06-18
You know, those questions are kind of beyond me, actually. Someone who's more knowledgeable will have to answer those.

Good questions, though.

---

