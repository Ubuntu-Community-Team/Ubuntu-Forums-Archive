---
title: "Remote execution of a single application"
date: 2005-10-05
forum: Desktop Environments
---

### Post by Rounan on 2005-10-05
Hi,

I'm running Ubuntu on two machines: an AMD64 desktop, and an AthlonXP server. I'm having difficulties getting Java and Flash plugins to work in Firefox on my AMD64 machine - Flash is just impossible and the blackdown plugin just hangs firefox. The lack of w32 codecs for mplayer is also an annoyance with some files.

Because I have an always-on 32-bit server, I'd like to avoid all the malarky of a chroot - these are applications with low performance requirements that I usually don't even need. Instead, I'd like to just run the applications on the server, and display them on my desktop. Currently I'm doing this with vncviewer - but that chews about 50% of the server's CPU and 2-5MB of network bandwidth to give me control of the entire running desktop. That's overkill, and expensive overkill at that.

What I really want is to be able to ssh into the server, and run firefox but have the head pop up on my desktop for that app only. I know this is possible - I did it every day at work from a Windows box using Exceed. But when I try to set my DISPLAY, I get:

```
$ export DISPLAY=<my IP>:0
$ firefox

(firefox-bin:10480): Gtk-WARNING **: cannot open display:
```

So it's either that I haven't set the right variable, or that my desktop X server isn't accepting a connection. I've enabled XDMCP on both machines, but the more I read the more I'm convinced that isn't the solution.

How do I fix it?

---

### Post by cwaldbieser on 2005-10-05
[QUOTE=Rounan]Hi,
I'm running Ubuntu on two machines: an AMD64 desktop, and an AthlonXP server. I'm having difficulties getting Java and Flash plugins to work in Firefox on my AMD64 machine - Flash is just impossible and the blackdown plugin just hangs firefox. The lack of w32 codecs for mplayer is also an annoyance with some files.
Because I have an always-on 32-bit server, I'd like to avoid all the malarky of a chroot - these are applications with low performance requirements that I usually don't even need. Instead, I'd like to just run the applications on the server, and display them on my desktop. Currently I'm doing this with vncviewer - but that chews about 50% of the server's CPU and 2-5MB of network bandwidth to give me control of the entire running desktop. That's overkill, and expensive overkill at that.
What I really want is to be able to ssh into the server, and run firefox but have the head pop up on my desktop for that app only. I know this is possible - I did it every day at work from a Windows box using Exceed. But when I try to set my DISPLAY, I get:
```
$ export DISPLAY=<my IP>:0
$ firefox
(firefox-bin:10480): Gtk-WARNING **: cannot open display:
```
So it's either that I haven't set the right variable, or that my desktop X server isn't accepting a connection. I've enabled XDMCP on both machines, but the more I read the more I'm convinced that isn't the solution.
How do I fix it?[/QUOTE]
You should just be able to
```

$ ssh -l <username> -X <hostname or IP>

```
You can also use -Y instead of -X.  Then when you run an X app, it will display on your local X display server.

---

### Post by Rounan on 2005-10-05
Well that did something unexpected....

It does, indeed, open firefox on my local display when I do that. However, the firefox that opens is the AMD64 version, running on my local machine - even though the command was issued on the remote machine. (Yes, the ssh was successful, I'm issuing the command from the remote environment.)

On the server, DISPLAY is set to localhost:10.0 after the ssh -X. When I change that to <myIP>:0 (or : 0.0, or :10.0, tried that too), I get the "cannot open display" error, as above. Change it back, local firefox executed by a remote command. Weird....

---

### Post by cwaldbieser on 2005-10-06
[QUOTE=Rounan]Well that did something unexpected....

It does, indeed, open firefox on my local display when I do that. However, the firefox that opens is the AMD64 version, running on my local machine - even though the command was issued on the remote machine. (Yes, the ssh was successful, I'm issuing the command from the remote environment.)

On the server, DISPLAY is set to localhost:10.0 after the ssh -X. When I change that to <myIP>:0 (or : 0.0, or :10.0, tried that too), I get the "cannot open display" error, as above. Change it back, local firefox executed by a remote command. Weird....[/QUOTE]
If you run "top" on the remote machine, isn't Firefox running there?  How do you know the version you are seeing is the AMD64 version?

---

### Post by Rounan on 2005-10-06
No, it isn't. It's definitely the AMD64 version, because flash/java don't work and the "about Firefox" menu says v 1.0.5, x86_64, not 1.0.7 i386.

Incidentally, I'm typing "firefox", not "firefox &", but I'm returned to the command prompt (still on the remote system) after it executes locally.
I'm doing this through gnome terminal, if that makes a difference.

---

### Post by cwaldbieser on 2005-10-06
[QUOTE=Rounan]No, it isn't. It's definitely the AMD64 version, because flash/java don't work and the "about Firefox" menu says v 1.0.5, x86_64, not 1.0.7 i386.

Incidentally, I'm typing "firefox", not "firefox &", but I'm returned to the command prompt (still on the remote system) after it executes locally.
I'm doing this through gnome terminal, if that makes a difference.[/QUOTE]
That is weird.  

Typing "firefox" at the terminal returns you to the prompt regardless of whether you are running locally, though.  I think the front end launches the backend browser program and returns immediately, or something like that.

Earlier you mentioned that you had XDMCP enabled-- maybe it has something to do with that.  For doing X-forwarding over ssh, you should not need XDMCP enabled.  And you should see the process running on the remote machine, not the local one.

---

### Post by Rounan on 2005-10-07
XDMCP is now disabled on both machines - same result.

I agree with you completely: This is not what should be happening. However, it is what's happening. I ssh -X into the i386 server, run firefox, and it launches the AMD64 firefox on my machine.

Somewhere along the line, either Gnome Terminal or ssh or X is doing something "intelligent", and saying "oh, he wants firefox! Might as well launch it from his own machine". How do I avoid this?

---

### Post by cwaldbieser on 2005-10-08
[QUOTE=Rounan]XDMCP is now disabled on both machines - same result.

I agree with you completely: This is not what should be happening. However, it is what's happening. I ssh -X into the i386 server, run firefox, and it launches the AMD64 firefox on my machine.

Somewhere along the line, either Gnome Terminal or ssh or X is doing something "intelligent", and saying "oh, he wants firefox! Might as well launch it from his own machine". How do I avoid this?[/QUOTE]
I suppose you could try uninstalling the local firefox and see what happens...

---

### Post by Quirky on 2005-10-08
[QUOTE=Rounan]But when I try to set my DISPLAY, I get:

```
$ export DISPLAY=<my IP>:0
$ firefox

(firefox-bin:10480): Gtk-WARNING **: cannot open display:
```

So it's either that I haven't set the right variable, or that my desktop X server isn't accepting a connection. I've enabled XDMCP on both machines, but the more I read the more I'm convinced that isn't the solution.

How do I fix it?[/QUOTE]

Have you tried typing `xhost +' on the machine whose X you are using? i.e. on the machine with <my IP>?

---

### Post by jimcooncat on 2005-10-08
In my experience, X forwarding over ssh automatically adds 10 to the display number of localhost (not your IP address).

I don't know why, but firefox did not take the $DISPLAY variable from the environment. I have to start it with "firefox --display=localhost:10.0". Otherwise I get the local firefox. I verify this by going to the URL "file:///home/" or something like that which will tell me what machine I'm on.

I agree this is weird behavior. I haven't a clue why a remote command would run a local executable.

p.s. Probably would be better to use "firefox --display=$DISPLAY". I just tested this and it works for me. This would be a bit more flexible.

So "ssh -X *me*@*apphost*" then "firefox --display=$DISPLAY" is all you need. You don't need the "xhost +" command. 

p.s.s. The "xhost +" command bypasses your X server's security by allowing any computer to use your display. If you're trying to get around tunnelling the X to increase performance, you can use the IP address or host name of the remote machine to limit what you're exposing your x server to. Your traffic can still be sniffed by any computer in the middle, though.

For example, you're on *mycomputer* and you want to run firefox on *apphost*.
"xhost + *apphost*", "ssh *me*@*apphost*", "firefox --display=*mycomputer*:0.0"

Even better performance and security can be gained by using FreeNX instead.

---

### Post by DeathOnJuice on 2005-10-08
I'm just posting so I can find this topic later.

---

### Post by Zwack on 2005-10-08
[QUOTE=DeathOnJuice]I'm just posting so I can find this topic later.[/QUOTE]

Did you consider searching for SSH Firefox?

Z.

---

### Post by Rounan on 2005-10-08
Thanks for the replies, I think I'm making some progress.

I'm still not able to run firefox remotely:

```
me@desktop$ xhost +
access control disabled, clients can connect from any host
me@desktop$ ssh -X server
Last login: Sat Oct  8 17:25:27 2005 from 192.168.1.2
me@server$ echo $DISPLAY
localhost:10.0
me@server$ firefox --display={$DISPLAY}

(firefox-bin:11993): Gtk-WARNING **: cannot open display: {localhost:10.0}
me@server$ firefox
(opens local AMD64 firefox on desktop)
me@server$
```


This seems to be specific to firefox though. I can launch mplayer and XMMS, and they connect to the localhost:10.0 server fine. Relevant line from Mplayer:
```
vo: X11 running at 1600x1200 with depth 24 and 32 bpp (":10.0" => remote display)
```

The display on the server is 1024x768, and the window pops up on the desktop just fine - definitely remote process, local display.

Why is firefox, alone, unable to connect to the :10.0 display?

On a related note, how can I get XMMS/MPlayer to play sound on my local machine? Right now, they complain about not being able to access hw:0. I know ESD has some network magic - how do I access that? Does ALSA have something similar? I've had far better success using ALSA directly. Sound daemons always make me wary...

Thanks,
--Rounan

---

### Post by jimcooncat on 2005-10-08
[QUOTE=Rounan]
me@server$ firefox --display={$DISPLAY}
[/QUOTE]

Did you try it without the braces?
firefox --display=$DISPLAY

---

### Post by Rounan on 2005-10-08
Heh. wow, I'm a moron.
Yeah, that worked perfectly. Thanks!! Great response time. ;)

Next question: How would I go about tying all of these commands (xhost +; ssh -X server; firefox --display=$DISPLAY) into a nice, iconified desktop icon or menu item? Just stringing them together like that doesn't do the job.

---

### Post by Zwack on 2005-10-08
[QUOTE=Rounan]How would I go about tying all of these commands (xhost +; ssh -X server; firefox --display=$DISPLAY) into a nice, iconified desktop icon or menu item? Just stringing them together like that doesn't do the job.[/QUOTE]

Well ssh can be run with a command as an argument so the last part is

ssh -X <server> firefox --display=$DISPLAY

xhost + is a BAD idea as it opens your XServer up for anyone to connect to it.  Much better is xhost +<server> which only allows <server> to talk to you.

Given that ssh -X forwards X across the ssh connection I am not sure that you need the xhost + anyway.  Testing on my system it tries to run xauth on the remote host (and fails as xauth doesn't exist over there) but xhost + does jack to help...

So try the ssh line above and see what error message you get.

Preferably on a fresh login so your previous xhost + doesn't get in the way.

Z.

---

### Post by Rounan on 2005-10-08
you're right, xhost + doesn't matter. Thanks anyway for the security tip.

ssh -X <server> firefox --display=$DISPLAY

doesn't work, fails on "Can't connect to display :0.0" - this is because my local bash$ is expanding $DISPLAY, rather than the remote environment. When I change it to localhost:10.0 in the above line, it works.

Now working on getting FreeNX up and running (mplayer is chewing 7MB/s +), as well as sound forwarding. Any pointers or links would be appreciated!

---

### Post by Zwack on 2005-10-08
[QUOTE=Rounan]

ssh -X <server> firefox --display=$DISPLAY

doesn't work, fails on "Can't connect to display :0.0" - this is because my local bash$ is expanding $DISPLAY, rather than the remote environment. When I change it to localhost:10.0 in the above line, it works.
[/QUOTE]

Glad to be able to help... you might try excaping the $DISPLAY as \$DISPLAY or \\\$DISPLAY to pass it through ssh.

Z.

---

### Post by juhani on 2007-02-24
There's still one thing that keeps bugging me: I can only use firefox from either machine, not both at the same time. If I first start firefox locally and then remotely, both firefoxes are run locally and if the first one is started remotely, both firefoxes are run remotely. Naturyally playing around with --display hasn't got anything to do with this, because with wrong setting firefox won't start at all.

Is there a simple way to run different firefoxes simultaneously? (Why would someone want to? It's always slower to use browser remotely, but there are some pages I need to access from remote ip and I don't want to set up any proxy. Using firefox remotely is much more simple.)

---

