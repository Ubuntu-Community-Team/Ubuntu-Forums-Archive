---
title: "Xgl, Xgame, and Unreal Tournament 2004."
date: 2006-04-21
forum: Gaming &amp; Leisure
---

### Post by pbaehr on 2006-04-21
I've looked around and found a surprisingly small amount of information regarding this problem.

When I'm running Xgl-Compiz, Unreal Tournament will load, but it runs horribly. Awful framerate, tiny screen, missing textures. I've found suggestions that say to use Xgame. ([http://xgame.tlhiv.org/](http://xgame.tlhiv.org/)) Basically, it launches a new x-session for your game to run on.

This works, however, certain textures show up as invisible making it impossible to play.

Has anyone found a workaround for running Xgl alongside 3d games? Worst case I'll scrap Xgl since it's just eye candy anyway, but it's so sexy...

---

### Post by GameGod on 2006-04-21
Unfortunately, I think we need better graphics card drivers before OpenGL apps can run well in XGL...

When you use Xgame, did you make sure it ran the regular plain old X server instead of XGL?

To play tremulous, I just run the command:
```
sudo X :1 -ac & DISPLAY=:1 tremulous
```

Change the "tremulous" part to whatever you need to run for UT. Once your game finishes, you might have to give a ctrl-alt-backspace to kill the plain X server if you see a grey background...

Good luck!

---

### Post by pbaehr on 2006-04-21
At work now, but I'll give that a shot when I get home. Thanks for the help.

I'm fairly certain Xgame is not loading Xgl since it's just a good ol' fashioned X-windows background with nothing on it. The game worked *better* if you ignore the fact that large portions of the map were invisible to me. I'll give your command a shot later, though and maybe it will do the trick.

Not that I don't have faith in GameGod, but any other workarounds you all use are still welcome just in case this doesn't work in my situation. Especially anyone who has experienced the same trouble.

---

### Post by crane on 2006-04-22
[QUOTE=GameGod]Unfortunately, I think we need better graphics card drivers before OpenGL apps can run well in XGL...

When you use Xgame, did you make sure it ran the regular plain old X server instead of XGL?

To play tremulous, I just run the command:
```
sudo X :1 -ac & DISPLAY=:1 tremulous
```

Change the "tremulous" part to whatever you need to run for UT. Once your game finishes, you might have to give a ctrl-alt-backspace to kill the plain X server if you see a grey background...

Good luck![/QUOTE]
What does this command do? Do I hop on another console (alt F2 maybe )
and run this? Does it start a new X server with out xgl?

---

### Post by GameGod on 2006-04-22
Sorry, to clarify:
That command starts a new "plain old" Xorg X server, and switches the display to it, and then runs the command "tremulous" on that display.

If you wanted to play UT, you'd just drop to the terminal and run something like:
sudo X :1 -ac & DISPLAY=:1 unrealtourney

(replacing "unrealtourney" with the actually executable name...)
One note though: I find that if "sudo" asks me for my password, it'll have trouble executing the second command. The workaround is to type something like "sudo foo", so that there's a sudo session active, and then when you run the above command you won't be asked for you password and it'll "just work".

---

### Post by pbaehr on 2006-04-22
GameGod. You are truly a God among Games.

That little trick did exactly what I needed. My game is running, sans sound, but I'll tackle that next. You've definitely got me in a better spot than I was before, though. Now I can have my fancy Xgl effects and Unreal Tournament, too!

---

### Post by pbaehr on 2006-04-22
A quick 'killall esd' got the sound problem fixed. Everything is well in the world. Thanks again. You've made my life much easier.

---

### Post by pbaehr on 2006-04-22
I did a little more playing around and I thought you might be interested to know that the trouble you are having with sudo can be taken care of by running
```
sudo dpkg-reconfigure x11-common
``` and setting the users allowed to start a new x-session to "ANYONE" in the first part. Then just press enter for the second question. That way, you don't have to use sudo to start your new x-session and you won't have to fuss with using a false sudo command before it. Thanks again.

---

### Post by crane on 2006-04-23
[QUOTE=pbaehr]I did a little more playing around and I thought you might be interested to know that the trouble you are having with sudo can be taken care of by running
```
sudo dpkg-reconfigure x11-common
``` and setting the users allowed to start a new x-session to "ANYONE" in the first part. Then just press enter for the second question. That way, you don't have to use sudo to start your new x-session and you won't have to fuss with using a false sudo command before it. Thanks again.[/QUOTE]
when I run the code above it get the following errors

```
Package `x11-common' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: x11-common is not installed
```

what's up with that? Is it because I am in the Xql server?

Also with the first command does the game run as root or user?

---

### Post by pbaehr on 2006-04-23
The package the command I gave to reconfigure isn't on your system it looks like. I don't know a whole lot about what it actually does so I can't help you too much. I came across it in another guide.

The first command that GameGod gave will run the game as root. The command I supplied that didn't work for you makes it so you can run the game as user. You'll have to look into what that package is and why you don't have it or don't need it to figure it out.

If you're adventurous and you want to keep trying, here's another solution that someone presented on the page I found this on:

> 
I think this is an easier way:

Code:

sudo gedit /etc/X11/Xwrapper.config

Change
Code:

allowed_users=console

with
Code:

#allowed_users=console allowed_users=anybody

and save. Users can start X session now.


Finally, your user info says you're running Breezy. I'm running Dapper. Since you're running Xgl, maybe you're in Dapper and just haven't changed your user settings. Either that or you're one of the people who managed to get Xgl set up in Breezy in which case, I have no idea at all. Good luck.

---

### Post by GameGod on 2006-04-23
> GameGod. You are truly a God among Games.

Thanks, but I snagged that line a post a while back in the Dapper forums. ;)
(I can't remember who originally posted it, but it's a life saver!)

> The first command that GameGod gave will run the game as root

Close, but the line I posted above only runs the X server as root... it runs the game as your usual user (For it to run the game as root, it'd have to be "sudo ... && sudo ...")

Thanks! :)

---

### Post by pbaehr on 2006-04-23
Ah, true.

---

### Post by sanderjd on 2006-04-23
GameGod, your suggestion of 
```
sudo X :1 -ac & DISPLAY=:1 tremulous
```
has been extremely helpful, but is there a way to make this run in a window rather than a whole screen? I'm not very familiar with this X command, and I can't seem to find any documentation about it, so any pointers would be appreciated. Thanks.

---

### Post by crane on 2006-04-23
[QUOTE=GameGod]Thanks, but I snagged that line a post a while back in the Dapper forums. ;)
(I can't remember who originally posted it, but it's a life saver!)



Close, but the line I posted above only runs the X server as root... it runs the game as your usual user (For it to run the game as root, it'd have to be "sudo ... && sudo ...")

Thanks! :)[/QUOTE]

Thanks for the reply. This works great for me is I have already run a sudo command in the term. If I haven't it just tries to start the game and errors out. It never askes for my passward though.

---

### Post by crane on 2006-04-24
[QUOTE=GameGod]Unfortunately, I think we need better graphics card drivers before OpenGL apps can run well in XGL...

When you use Xgame, did you make sure it ran the regular plain old X server instead of XGL?

To play tremulous, I just run the command:
```
sudo X :1 -ac & DISPLAY=:1 tremulous
```

Change the "tremulous" part to whatever you need to run for UT. Once your game finishes, you might have to give a ctrl-alt-backspace to kill the plain X server if you see a grey background...

Good luck![/QUOTE]

This command has all my games running. Is there any way to run this as a script? So I do not have to open terminal and run it?

---

### Post by Andeim_ on 2006-04-25
Hello I have the same problem as pbaehr but when I type the solution of GameGod, I'am front of a grey screen.....
I give you what I can read when I press ctrl+alt+backspace
```

damien@ubuntu:~/ut2004$ sudo X :1 -ac & DISPLAY=:1 ./ut2004
[3] 7082

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15-ubuntu1 x86_64
Current Operating System: Linux ubuntu 2.6.15-21-amd64-generic #1 SMP PREEMPT Fri Apr 21 16:42:20 UTC 2006 x86_64
Build Date: 16 March 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Tue Apr 25 18:21:16 2006
(==) Using config file: "/etc/X11/xorg.conf"

The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols

Errors from xkbcomp are not fatal to the X server

FreeFontPath: FPE "/usr/share/X11/fonts/misc" refcount is 2, should be 1; fixing.

The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

Can't find 'ini:Engine.Engine.GameEngine' in configuration file

History:

Exiting due to error


```

---

### Post by Andeim_ on 2006-04-25
It's good I use xgame for the moment :)

---

### Post by tejo on 2006-05-14
I found this very useful to run nonxgl opengl games under xgl
maybe can help

[http://www.compiz.net/viewtopic.php?id=175](http://www.compiz.net/viewtopic.php?id=175)

---

