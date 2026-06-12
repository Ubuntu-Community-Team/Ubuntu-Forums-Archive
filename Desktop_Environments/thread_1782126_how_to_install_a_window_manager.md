---
title: "how to install a window manager"
date: 2011-06-14
forum: Desktop Environments
---

### Post by enimeizoo on 2011-06-14
Hello,
I am trying to install clfswm. I am able to run it from a tty.
I start a new X server with
```
startx xdm --:1
```

Then in the new X server, I run
```

clisp -K full full /home/seb/Downloads/clfswm-1102/load.lisp

``` 

What I want to do is to be able to select it from the graphic session login screen. (just like openbox )

I tried to fill a .desktop file in /usr/share/xsessions :
```

[Desktop Entry]
Encoding=UTF-8
Type=Application
Exec=screen -dmS clfswm clisp -repl -q -ansi -K full /home/seb/Downloads/clfswm-1102/load.lisp
Name=The almighty lisp window manager.
Comment=full common lisp window manager.

```

It just doesn't work. Actually, I get an entry in the session selection thing, but when I try it, the login screen disapears a sec or two, and then comes back. If after that I try to open a session with another window manager/desktop manager I get a black screen (with a few things in it) that looks like clfswm, but I can't do anything in it.

I'm quite new to that (I have only used kde and gnome until now, and installed openbox to try to see how it works) so I don't know what to do right now.

In case it helps,[ the installation instructions]("http://trac.common-lisp.net/clfswm/wiki/Setup"). I didn't try putting the said line in my $HOME/.xsession or wherever it should be because I thought it would replace the kde login (and that is not what I want). I think what I want is a .desktop file in /usr/share/xsessions/, I'm just not sure what to put in it.

Thanks for your help.

---

### Post by Copper Bezel on 2011-06-14
If you're worried that having a .xinitrc there will cause every session to log into clfswm, you could always erase the file from the console if the problem arises (cd ~; rm .xinitrc). I can't test it as I'm on 10.10 and 10.10 handles the display variable differently from 10.04, but I believe that this step is required. Krytarik, another 10.04 user here, mentioned that he had to have that file in place to use custom sessions.

---

### Post by enimeizoo on 2011-06-14
Thanks for your answer, but I'm sorry, I forgot to update my profile here, I am running 11.04 since last week.
Anyways, after a bit more searching I got it working.

/usr/share/xsessions/clfswm.desktop :
```

[Desktop Entry]
Encoding=UTF-8
Type=Application
Exec=/usr/bin/clfswm
Name=The almighty lisp window manager.
Comment=

```/usr/bin/clfswm :
```

#!/bin/bash
exec clisp -K full /home/seb/Downloads/clfswm-1102/load.lisp

```Now I'm looking for a way to use it inside kde (instead of kwin, not sure it is possible), or use plasma-desktop in it.

(edit) I couldn't run plasma-desktop in it, but plasma-netbook works just fine. I just don't have panels, but I don't use any anyways.

---

### Post by SnakeHunt2012 on 2012-09-01
I have meet a similar problem.

When I came into the clfsWM form lightdm, the screen become black, and after about 30 seconds, it came back to the lightdm so I have to go back to unity to ask you.

Hope for help...

Ps: Ubuntu 12.04 Precise

---

### Post by overdrank on 2012-09-02
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

