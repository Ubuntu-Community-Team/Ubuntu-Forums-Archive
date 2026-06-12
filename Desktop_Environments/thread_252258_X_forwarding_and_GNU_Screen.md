---
title: "X forwarding and GNU Screen"
date: 2006-09-06
forum: Desktop Environments
---

### Post by grough on 2006-09-06
Is there an X equivalent of GNU Screen?

When running an X application over ssh, I&#8217;d like to be able to close the program and have it continue to execute (much like with Screen in a terminal) so I can resume (or "re-attach" in screen-speak) the session later. As far as I know, closing a remote X window closes the session altogether.

An example of this would be to run a graphical P2P client remotely. You could leave the application running, uploading, downloading, doing its thing, and re-attach when you need to interact with the program.

I can do all of this in a terminal quite happily using screen, but there are some X apps that I&#8217;d really like to use too.

Is there a way to do it?

Thanks - Gavin

---

### Post by mssever on 2006-09-06
I've never used screen, but I do use X forwarding over SSH. Of course, that means that if I close the program's window, the program closes--just like on the local machine. The other thing I use is vncserver. You can close and re-open the vnc window without affecting the behind-the-scenes session. Of course, in this setting all your programs are confined to the vnc window.

---

### Post by kaefert66014235 on 2008-03-03
so does that mean you cant reatach an x window application that was run over ssh tunnel when the connection brakes down?

that would be a great feature if someone knows how or if that works...

---

### Post by Skerit on 2008-03-23
I'm looking for the exact same kind of program myself.

Someone suggested the "screen" program, but unfortunately it's only useful for command-line programs (which isn't what we're after.)

VNC isn't an option, indeed, as I want the program on my desktop, not another X-desktop on my desktop.

---

### Post by Skerit on 2008-03-23
Aha, I've found it! A program called "xmove", it acts as a "pseudo-x-server", it doesn't do the work of a real x-server but just relays it to the real one.

I'll try to explain in my own words, but it all happened rather hasty, so excuse me!
I found this information on this wiki: [http://wiki.archlinux.org/index.php/Allow_a_program_to_continue_after_logoff](http://wiki.archlinux.org/index.php/Allow_a_program_to_continue_after_logoff)

First of all you need to run xmove as a server. 

First of all, I'll establish an ssh connection (using X-forwarding) to the server.

$ ssh -X 192.168.1.2 -l <LOGIN>

Now we'll start the xmove server. We'll use "localhost:10" as the screen, X uses this screen to forward applications over SSH by default. The "-port 9" is the screen number xmove uses.

 $ xmove -server localhost:10 -port 9 &

Let's start dolphin using xmove now (My server is running kubuntu, you can easily use nautilus or gedit or whatever)

$ env DISPLAY=:9 nohup dolphin

Now we get a problem, Xmove isn't authorised to connect to our client-X.

Luckily there was a Russian guy who was able to sort it out.
[http://lists.debian.org/debian-russian/2006/05/msg00465.html](http://lists.debian.org/debian-russian/2006/05/msg00465.html)
(and no, I don't speak Russian, luckily there is only 1 language for commands!) Apparantly we need a key ...

Open another terminal on the CLIENT and type:
$ xauth list

Now you'll get your running X-session with the needed key

KIP-DU-SKER/unix:0  MIT-MAGIC-COOKIE-1  <KEY>

Go back to your SSH session and type:

$ xauth add localhost:10 MIT-MAGIC-COOKIE-1  <KEY>

Now we can run dolphin over xmove:

$ env DISPLAY=:9 nohup dolphin

It does take a while to load, though.
Let's move the screen somewhere else now!

On the server, type:

$ export DISPLAY=:9
$ xmovectrl -list
3     (no name)            localhost:10                                        

This will give you a list of applications which are currently being handled by xmove. For some reason the name is not showing on my machine, and 1 application spawns multiple entries in the list. (Even though only number 3 works)

$ xmovectrl -move -suspend 3

The screen on my client disapears. When I type this in on the SSH session:

$ xmovectrl -list
3     (no name)            suspended    

Now to move the window back to the client:

$ export DISPLAY=:9
$ xmovectrl -move localhost:10 3

And it's back (even though it took a while...)

If only xmove had some kind of gui... :P

---

