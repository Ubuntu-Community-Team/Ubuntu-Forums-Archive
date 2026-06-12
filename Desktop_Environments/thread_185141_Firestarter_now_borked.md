---
title: "Firestarter now borked??"
date: 2006-05-31
forum: Desktop Environments
---

### Post by Caseyjp on 2006-05-31
Just did a reboot after the latest updates, and firestarter now refused to run.

Attempted to fire it up from the command line and the following error came up:

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:5530): Gtk-WARNING **: cannot open display:

Also, running :   sudo firestarter -s   will start the firewall, but no icon or other indication that its running.

okay 2nd edit:  the terminal SAYS its running but system monitor has NO process with the name firestarter running (all, mine or active)

---

### Post by Caseyjp on 2006-05-31
quick bump.

---

### Post by bruce89 on 2006-05-31
Did you do ```
gksu firestarter
```?

---

### Post by Caseyjp on 2006-05-31
Now why would I have to do that "NOW", when it has NEVER been a requirement  prior to today?  Firestarter normally should start when the icon is clicked to start, or started with the boot up process. (using sudoers change).

Even in a terminal, a sudo firestarter prior to this last round of updates starts the application. (brings up the sudo password dialogue).

and yes, I just tried it with the same Gtk-WARNING as the sudo command.

---

### Post by Caseyjp on 2006-05-31
Just uninstalled, reinstalled and rebooted.  Same problem.
gksu doesn't work, nor does sudo to get it started.  The installation indicated that it 'started' the application, but a ps shows no process running. system monitor shows no process running.

---

### Post by SeanTater on 2006-05-31
it is unnecessary to have the gui on.

There is no firestarter process, but thet is because there is no need for one, all firestarter does is tell the kernel what to do.

if you want to know what the kernel is doing, type the following into a terminal and give your password where needed: 
```
sudo iptables -L
```

if it gives you more than say, 5 lines of text, firestarter is working, and for me it gave ~75 lines of text..

---

### Post by Caseyjp on 2006-05-31
[QUOTE=SeanTater]it is unnecessary to have the gui on.

There is no firestarter process, but thet is because there is no need for one, all firestarter does is tell the kernel what to do.

if you want to know what the kernel is doing, type the following into a terminal and give your password where needed: 
```
sudo iptables -L
```

if it gives you more than say, 5 lines of text, firestarter is working, and for me it gave ~75 lines of text..[/QUOTE]

I appreciate that info...however, firestarter DOES run as a process when it is invoked.  It DOES have a gui that shows 'events' rules and tabs.  It no longer starts and errors out with the info I showed in the first message, and this is a NEW thing as of today.

Yesterday this application was working, today it is not, and the ONLY difference  to this box is the updates that were applied.

I've submitted a bug report 47662 to launchpad.

---

### Post by PhilOSparta on 2006-06-02
[QUOTE=Caseyjp]I appreciate that info...however, firestarter DOES run as a process when it is invoked.  It DOES have a gui that shows 'events' rules and tabs.  It no longer starts and errors out with the info I showed in the first message, and this is a NEW thing as of today.

Yesterday this application was working, today it is not, and the ONLY difference  to this box is the updates that were applied.

I've submitted a bug report 47662 to launchpad.[/QUOTE]

A follow up on this at the launchpad bug report 47662 indicates that Caseyjp found a work around.

In a terminal type    ***[SIZE="4"]host +local:[/SIZE]***<enter>
He also indicates that it has to be done for each power up.

It has worked for me. 
Thanks to Caseyjp for the research.

---

### Post by Yleeyas on 2006-06-04
Hi folks,

I'm having the exact same problem, but the work around doesn't seem to work!
(by the way that should be "xhost +local:" from the bug report)
When I then type "sudo firestarter -s" it says it started up, but there is no icon, or any indication that it starts up???

What next?

Yleeyas

---

### Post by Anduu on 2006-06-04
I have been down this road many,many times.

In my experience it is ***NOT*** possible to get the GUI to load properly at startup.If you have modified your sudoers file and added firestarter to your startup script I highly recommend you undo these changes because this method can break other things like sudo and gksu.

Firestarter ***DOES*** run in the background when installed and functions correctly.You will then be able to launch the GUI and modify your settings.

---

### Post by Yleeyas on 2006-06-04
Hello Anduu,

As Caseyjp pointed out, it DID work under Breezy, for us, and he got it to go with a 'workaround', which didn't work for me. So I'll stay the course 'til I find a suitable fix, thanx.

Yleeyas

***EDIT*** With apologies to Caseyjp (if your still monitoring)

After entering in terminal; " xhost +local:"
I can then start it up from the menu selection
Applications>System Tools>Firestarter

Being a noob, is there a standard startup script we can add the xhost line to, then maybe get the auto startup working?

---

### Post by KrazyPenguin on 2006-06-04
[QUOTE=Yleeyas]Hello Anduu,

As Caseyjp pointed out, it DID work under Breezy, for us, and he got it to go with a 'workaround', which didn't work for me. So I'll stay the course 'til I find a suitable fix, thanx.

Yleeyas

***EDIT*** With apologies to Caseyjp (if your still monitoring)

After entering in terminal; " xhost +local:"
I can then start it up from the menu selection
Applications>System Tools>Firestarter

Being a noob, is there a standard startup script we can add the xhost line to, then maybe get the auto startup working?[/QUOTE]

I have posted a HowTO on Firestarter and it is also included in my guide.

[http://www.ubuntuforums.org/showthread.php?t=187899](http://www.ubuntuforums.org/showthread.php?t=187899)

Good luck!!!

;-)

---

### Post by Yleeyas on 2006-06-04
Hi KrazyPenguin,

I've seen your excellent HowTo for firestarter before, and had it all set up and working under Breezy.

The only step which I don't have was replacing the 'Defaults' line, and the subsequent fixes for 'broken' administrative apps. (I did have the ALL=NOPASSWORDS line, which seems to work still, cuz I'm not asked for a pwd even when I start fstarter from the menu)

Just to clarify, are you saying that replacing that 'Defaults' line will have the same effect as Caseyjp's " xhost +local: " fix? 

Thanx for your attention,
Yleeyas

---

### Post by Anduu on 2006-06-05
I have no doubt it can be *made* to work...however what happens with the next update...does it break again?Does the "workaround" completely bork something else?

Like you said it worked in Breezy then broke.
It worked for a short time in Dapper then broke again and messed up gksu.

Ive given up trying to make Firestarter work in ways it wasn't intended.

Just my two cents.

---

