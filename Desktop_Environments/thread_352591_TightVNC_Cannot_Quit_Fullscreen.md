---
title: "TightVNC: Cannot Quit Fullscreen"
date: 2007-02-03
forum: Desktop Environments
---

### Post by fourthirtysix on 2007-02-03
I am using tightvnc and recently tried fullscreen mode, and I find that the F8 menu popup is not always working.

Sometimes the F8 popup menu won't come up at all. Sometimes it comes up and I can switch out of full-screen and back to fullscreen one time, but then it won't popup anymore.

When I am on the remote machine, I have no way to "get back" to the local desktop to quit the program and I become stuck when the F8 stops showing up.

Does anyone have any suggestions on why the F8 menu is not always appearing? I love VNC but I won't be able to use it as I would like if the fullscreen gets locked / frozen due to the menu not showing up.

Thanks

PS: are there any alternatives for linux-to-linux remote desktop that are as "good" as VNC?

---

### Post by kebes on 2007-02-03
If memory serves, in tightVNC you can exit fullscreen mode by going:
ctrl+esc
esc

I think that would work. For linux-to-linux remote view/control, VNC is a good choice. Note, however, that you have lots of viewers (and servers) to choose from. I use tightVNC as the server, but would xvncviewer as the viewer. You can try different viewers until you find the one that works for you.

---

### Post by fourthirtysix on 2007-02-03
Hi kebes, I've used Ctrl-Esc Esc using windows, and it works there, but it doesn't seem to work in xtightvncviewer in linux.

Just some extra info, I start the server with:

[I]
tightvncserver -geometry 1152x768 :2[/I]

and connect to it with:

xtightvncviewer -fullscreen 192.168.1.3:2

and I cannot get the F8 popup menu to work at all :( 

Thanks for any help/suggestions...

---

### Post by kebes on 2007-02-03
Hmm... F8 should definately bring up the option menu. (Does it work when you are not in fullscreen mode?) In the [vncviewer manpage]("http://www.die.net/doc/linux/man/man1/vncviewer.1.html"), it says that you can use the option "-MenuKey" to set the key to the keystroke of your choosing. Maybe setting it to something else will make it work?

---

### Post by bmt on 2007-02-12
Any solution to this?  I have run into the same problem.

It appears that the vncviewer remote desktop is on top of everything else, possibly including the pop-up menu.  With the remote screen set to a smaller-than-maximum size, full-screen leaves a small border of the local desktop around the edge.  Windows or icons visible in that edge area can be manipulated with the mouse, but remain behind the remote picture.

---

### Post by bmt on 2007-02-20
Okay, my solution is to use xvnc4viewer (from the repos.) instead of the tighntvnc viewer.

F8 works all the time and the window scrollbars work in a more consistent fashion.  Browsing the bugs in launchpad shows quite a few for 'vncviewer', with a common solution being to change to xvnc4viewer -- it worked for me.

---

### Post by triwave on 2007-12-15
I have the same problem, the server I connect to is a windows VNC server.

My solution when finished my VNC session is to use the disconnect client command on the windows VNC server (right click -> disconnect clients). This ends the sessions you are running and terminates your full screen session, but doesn't shut down the remote server so it's ready for you to log into again. 

Doesn't solve the ability to switch between modes, but I find tightvnc very fast and stable on my system so I like to continue using that viewer.

---

### Post by jerinjoy on 2008-06-27
I tried installed xvnc4viewer and it works great.

---

