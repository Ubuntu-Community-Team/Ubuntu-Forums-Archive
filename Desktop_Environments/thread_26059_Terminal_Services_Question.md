---
title: "Terminal Services Question"
date: 2005-04-11
forum: Desktop Environments
---

### Post by Chris_Durham on 2005-04-11
Anybody have any ideas on how to get Terminal Services to just launch? Without first prompting the user for information? From a command line? 

I'm new to linux, so please go easy. Or is this something over a newbie's head?

---

### Post by panzer77 on 2005-04-11
You should just be able to use rdesktop, it its not installed you can install through snaptic.  Once you launch it you will be prompted for the ip address of the server. :smile:

---

### Post by Chris_Durham on 2005-04-11
I can do that. And I can save the settings as a file. What I want is to load the file automatically and connect to the server without any input from the user. Just as a command in the startup options.

---

### Post by spartas on 2005-04-11
You may also look into VNC for what you're trying to do.  I use [TightVNC](http://www.tightvnc.com) for my purposes.  If you decide to do this, make sure you have vncviewer on ubuntu.

---

### Post by Chris_Durham on 2005-04-11
We use Windows Terminal Server at work for many of the staff and will be expanding its use later this year to include all of our sales staff (with a second server in the farm). I've been speaking with our VP and our head administrator about using Ubunto on the desktops instead of Windows 2000. The users would never use Ubuntu themselves, it would just be a platform from which to run the TS client.

I know this isn't the most noble use of open-source software, but I'm trying to worm technology I believe in into our infrastructure. Of course I'm selling them on it as a way to repurpose Win2K licenses.:wink: It's funny what kind of fast-talking you have to do in a windows shop to get them to buy into Macs or Linux, even if they do admit they're more stable, less problematic options.

---

### Post by cwaldbieser on 2005-04-12
Terse as they may be, I think the man pages for rdesktop give you all the info you need to pass options to the rdesktop command so the user does not have to type a thing.

---

### Post by Chris_Durham on 2005-04-12
Okay, next question. It's been a long time since I used Unix commands for anything, and being incrdibly new to Linux/Ubuntu I couldn't figure out how to get the man pages. I know the cmmand is Man, but what is the rest of the syntax?

---

### Post by yanik on 2005-04-12
```
man tsclient
```

---

### Post by shakin on 2005-04-12
[QUOTE=yanik]```
man tsclient
```[/QUOTE]

And once you find the command, you can go into System / Preferences / Session and insert it as a startup program. Or I suppose you could do a forum search to find out how to automatically login a user and just set tsclient to come up with that user's session, that way the computer would boot directly into the tsclient window.

Sounds like an excellent way to use Open Source Software to me :)

---

### Post by Chris_Durham on 2005-04-12
Thanks.

Okay, so now I can run the command "tsclient -x Dalts01" at startup and it opens the client and loads the settings file. The last step is getting it to connect automatically. Any ideas? nothing on this in the Man pages. I suspect that there're some sort of keystroke commands I can do, or something; but I have no clue how or what.

---

### Post by shakin on 2005-04-12
[QUOTE=Chris_Durham]Thanks.

Okay, so now I can run the command "tsclient -x Dalts01" at startup and it opens the client and loads the settings file. The last step is getting it to connect automatically. Any ideas? nothing on this in the Man pages. I suspect that there're some sort of keystroke commands I can do, or something; but I have no clue how or what.[/QUOTE]

I don't mean to undo the work you've done so far, but have you looked into using rdesktop instead of tsclient? I don't know much about either one, but 'man rdesktop' shows a lot more options and you can even do domain authentication on the session. It looks like rdesktop will automatically connect if you give it the paramaters it needs.

---

### Post by shakin on 2005-04-12
[QUOTE=shakin]I don't know much about either one, but 'man rdesktop' shows a lot more options[/QUOTE]

Well, a bit of research and it turns out that tsclient is just a front end for rdesktop. Since you just want it to connect right away, you don't need the front end at all.

This is a good, short read: [http://www.linuxquestions.org/questions/answers/425](http://www.linuxquestions.org/questions/answers/425)

---

### Post by yanik on 2005-04-12
You might be better off using plain rdesktop.  TS Client is a pretty app for gnome.  rdesktop is a command line app, see:

```

yanik@nixbox:~$ rdesktop
rdesktop: A Remote Desktop Protocol client.
Version 1.3.1. Copyright (C) 1999-2003 Matt Chapman.
See http://www.rdesktop.org/ for more information.

Usage: rdesktop [options] server[:port]
   -u: user name
   -d: domain
   -s: shell
   -c: working directory
   -p: password (- to prompt)
   -n: client hostname
   -k: keyboard layout on server (en-us, de, sv, etc.)
   -g: desktop geometry (WxH)
   -f: full-screen mode
   -b: force bitmap updates
   -e: disable encryption (French TS)
   -E: disable encryption from client to server
   -m: do not send motion events
   -C: use private colour map
   -D: hide window manager decorations
   -K: keep window manager key bindings
   -S: caption button size (single application mode)
   -T: window title
   -N: enable numlock synchronisation
   -X: embed into another window with a given id.
   -a: connection colour depth
   -r: enable specified device redirection (currently: sound)
   -0: attach to console
   -4: use RDP version 4
   -5: use RDP version 5 (default)
```

Find what options you need, then make it load automatically in gnome by going in system--preferences---session

---

### Post by Chris_Durham on 2005-04-14
Thanks. I can get RDesktop to work with the proper options from a command line in Terminal. When I place the same command in System > Preferences > Session > Startup, though, Nothing happens at startup. When I run TSClient, I at least get the client to pop up. Why doesn't the RDesktop command work? Does it have anything to do with the order? It's the only command I have in there, but does the order have anything to do with time before the command is executed? I've tried  setting it to 50 and 100 with no change in my results. Please help.

---

### Post by Chris_Durham on 2005-04-14
Wierd. I just booted up and it booted to TS. I'll have to play with this some more.

---

### Post by Chris_Durham on 2005-04-14
Okay, so it works. Thanks everybody for the help.

---

### Post by OlympicSoftworks on 2007-08-29
Ok, I am having some issues with my attempts here.  I am trying to use RDesktop as well, TSClient would be fine, I really don't care what the front end is or if there is one...I'd be happy just to login remotely at this point.  I am running Ubuntu/Gnome on the machine I want to log into remotely and am on the same network connected via a router/gateway and at the far end a switch to branch off a bit more to different machines in my shop.  We are both on the lan side of the gateway.

I set it's login manager to allow remote logins and even installed Firestarter just so I could absolutely drop the firewall/ipchains to rule out that interfering.  Still no go.

Let me get this right: Set login manager to allow remote logins, and then run TSClient to actually get a login screen and 'presto'.  Does not sound like there is anything to do extra...what bugs me is I had this set up with either 6.06 or 6.10 and had some minor issues but it worked.

Any help or pointers to more data would be great!

---

