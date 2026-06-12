---
title: "Blank Screen when using NoMachine NX"
date: 2009-02-05
forum: Desktop Environments
---

### Post by kopolov on 2009-02-05
I have a PC at home with Ubuntu 8.10 and a PC at work with Ubuntu 8.10.
Until 2 days ago I was able to connect from home to work using NoMachine NX (not freenx).
Now When I connect I get a blank screen. The authentication process goes well and I see the NocMachine logo but then I get a blank screen.
I went over all the posts, tried to delete everything from /tmp.
Reinstalled NX on both client and server.
Nothing.
Except for praying, is there anything else I can do?
I am using NX client 3.3.0-3 at home and NX server 3.3.0-3 at work.
I am a NB, so please be clear if you have suggestions.

---

### Post by lnoland on 2009-06-18
I know that it's been quite a while since you posted this -- is this still a problem for you?  Are you using KDE4?

I was having the same problem and spent over a week searching for answers on the web and experimenting with different configurations trying to get it working again.  I finally tracked it down to a problem with Plasma not starting when I tried to launch NX in fullscreen mode.  If I tried to start Plasma manually I got a whole slew of errors (I don't remember the exact errors but they all contained the phrase "could not convert").  I deleted the plasma configuration files and tried it again and KDE launched on the first try.

If you want to see if you are having the same problem, you can try the following:

1. First, open the command  launcher (on my system, that is done with Shift-Alt-F2 -- I have read several posts where others indicated using just Alt-F2, but that doesn't work on my system -- perhaps I remapped something).

2. In the command launcher enter "xterm" to open an X-terminal window.

3. In xterm, type:

   # ps aux | grep plasma

If plasma is not running only one line will be returned and it will be the entry corresponding to the grep command you just launched.  If plasma is running than perhaps your problem is different than mine was.

4. If plasma isn't running you can try launching it manually with:

     # plasma&

In my case, I got a whole mess of error messages from that.

5. Next, remove (or, at least, move to somewhere not on your PATH) your plasma configuration files:

    # rm /home/<username>/.kde/share/config/plasmarc
    # rm /home/<username>/.kde/share/config/plasma-appletsrc

5. At that point you can exit the black-screen session and launch a new NX session.  In my case, that got me right in.

Good luck.

- Les

---

### Post by marvec on 2009-07-23
Hello, I had exactly the same problem and this helped me a lot. Many thanks!

---

### Post by lnoland on 2009-07-27
> **marvec said:**
> Hello, I had exactly the same problem and this helped me a lot. Many thanks!

You're welcome.  I am so glad to hear that someone else was able to profit from the days of searching and experimenting it took me to find the solution to the problem.

 - Les

---

### Post by fred_bertie on 2011-07-02
Hi all,

I am aware this thread is really quite old but the symptoms (nearly) exactly manage my problem and my setup. 
Only differences are that I'm running NX client from a Windows PC and I'm using Gnome.

this portion of the previous post is exactly the same as mine:
"
Until 2 days ago I was able to connect from home to work using NoMachine NX (not freenx).
Now When I connect I get a blank screen. The authentication process goes  well and I see the NocMachine logo but then I get a blank screen.
I went over all the posts, tried to delete everything from /tmp.
Reinstalled NX on the client.
"

I cannot work out the issue, with my limited knowledge of both NX and Linux machines; nor do I have direct access to the Linux machine, for the time being. I wondered if there was anything I could try from the client end?

Many Thanks for any and all advice.

---

### Post by lnoland on 2011-07-08
> **fred_bertie said:**
> Hi all,

I am aware this thread is really quite old but the symptoms (nearly) exactly manage my problem and my setup. 
Only differences are that I'm running NX client from a Windows PC and I'm using Gnome.

this portion of the previous post is exactly the same as mine:
"
Until 2 days ago I was able to connect from home to work using NoMachine NX (not freenx).
Now When I connect I get a blank screen. The authentication process goes  well and I see the NocMachine logo but then I get a blank screen.
I went over all the posts, tried to delete everything from /tmp.
Reinstalled NX on the client.
"

I cannot work out the issue, with my limited knowledge of both NX and Linux machines; nor do I have direct access to the Linux machine, for the time being. I wondered if there was anything I could try from the client end?

Many Thanks for any and all advice.

I wish I could help you out but since you are using Gnome, it seems unlikely that your situation is related to the one I encountered (except to the extent that NX has reacted to the two situations in the same manner).

Is there anything you could try from the client end?  Undoubtedly, but what you could accomplish with it, particularly if you have limited knowledge of Linux, is somewhat questionable.  Your best bet would probably be to connect to the machine using SSH via a shell or even by forwarding X-windows (though it is unlinkely that the machine is currently set up to allow forwarding X-windows even if you had the capacity and knowledge of how to do it).  It is likely set up for SSH however as NX generally uses SSH as the conduit over which it transmits its own forwarding of the remote screen, etc.  If you do access the machine that way, though, you are going to have to know enough about the shell to find your way around and then there is the question of what to look for.  I would probably start by looking in /var/logs and examining any log files related to NX, X-windows, or even system and kernel logs just to try to find out what might be happening at the times when you attempt to connect with NX.  If you find something which looks suspicious, hopefully, you can research it on the Net and perhaps someone else has had similar problems and found a cure.  There probably aren't enough users of NX to hope to find the exact problem (or you might have found it already just by researching the symptoms) but by looking at the logs, you at least might find more symptoms to research.  I think the NX client does some logging on the local machine as well -- you should probably examine any of those logs and see if they give you clues.

Good luck.

 - Les

PS
By the way, it might not be all that obvious why what I did fixed my system.  While I am only speculating, my guess is that whatever it was in those Plasma configuration files which was causing the Plasma errors resulted in X-Windows starting in some configuration which NX wasn't equipped to handle so when it tried to analyze and forward the screen data, it didn't know how to handle it and just transmitted a black screenn instead.  If that is what actually happened, that may be how your problem and mine are alike -- it could be that some component of Gnome has done something similar and created an X-Windows configuration which NX cannot handle.

---

### Post by fred_bertie on 2011-07-09
Thank you for your advice inoland; the dude at the server end managed to find out that some process had crashed whilst trying to run some sort of system scan and had bugged at 100% of CPU and so was essentially not responding to anything until the process was killed.

I can only assume it was as you said, that the server couldn't figure out what to transmit or something and so just sent a black screen instead.

Many thanks all the same.

---

### Post by helpdeskdan on 2011-08-03
There has to be a gnome answer.  If you login the local machine, and then connect with the nomachine client, gnome comes up fine.

---

### Post by Tabsc on 2011-09-15
I had the same problem and this came from the local .Xauthority file that did not belong to my user.

You can try to ssh the server with X11 Forwarding (-X) and lauch an X application (xcalc for instance). If this does not work then you could have the same problem.

The solution is there:
[http://www.cyberciti.biz/faq/x11-connection-rejected-because-of-wrong-authentication/](http://www.cyberciti.biz/faq/x11-connection-rejected-because-of-wrong-authentication/)

---

