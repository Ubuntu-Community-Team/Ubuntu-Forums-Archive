---
title: "ssh X Forwards with mirror DISPLAY"
date: 2009-06-30
forum: Desktop Environments
---

### Post by LKjell on 2009-06-30
Sometimes we just want to learn something new and make the fun out of stuff.
ssh tunneling X is very powerful. A case scenario is that we have a remote machine that has some programs that is not installed on the local machine and want to run those programs on the local machine.

One way to do this is:
```
ssh -X -l username remote
```

Now any program we initiate will be displayed on the local machine. If we want to display this on the remote system we have to change the $DISPLAY variable. Usually it is like this:
```
DISPLAY=":0.0"
```

There is a problem with this, but fancy if you want to spoke your granny. You cannot use your program since you cannot view it. It is displayed on a remote machine. Therefore the question is: Is it possible to display on local and remote machine at the same time?

-----

Now to another idea. I want to make a new session with my local machine. Then I can press ctrl + alt + f7 and crtl + alt + f8 to switch from local to remote. To do this I do like this I need to get to another tty. So I press ctrl + alt + f1 and login. From there I type 
```
xinit -- :1
```

A box will show up. In the box I type
```
ssh -X -l username remote
gnome-session
```

And voila I get a gnome desktop but with remote setting. But what I want is to mirror that gnome-session so it display locally and remotely. Eventually I want to tap in an existing session on the remote machine.

An application to this is that I want to show another user how to navigate on the remote machine while I do it remotely.

---
The next idea might seem rather inconvenient since you can just extra cables. And that network speed is often a bottleneck.

Well I have a laptop and want to show my friends some of my gaming technique. I have a game which is installed locally. I want to connect remotely and use that nice plasma screen. Therefore I want to mirror my screens and use my laptop to play on while my friends can watch the plasma tv. Of course I could just buy a cable to plug the plasma tv to my laptop. But assume a friend of mine is kind of drunk and stumble on wires a lot. Therefore I do not want any cables.

Therefore the question is do anybody know how to do these and configure them?

Thanks in advance

---

### Post by tgalati4 on 2009-06-30
VNC allows two users to take control of the mouse/keyboard.  It's slower than X-forwarding, but it serves its purpose.

As for your drunk friend.  Hide the beer with a neighbor.  Just don't expect all of it to remain when you go back to retreive it.

---

