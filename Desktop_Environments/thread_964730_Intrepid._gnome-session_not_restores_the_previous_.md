---
title: "Intrepid. gnome-session not restores the previous session"
date: 2008-10-31
forum: Desktop Environments
---

### Post by erlguta on 2008-10-31
Hello community.
I have just upgraded to Intrepid from Hardy and i see this annoying bug:
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/249373](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/249373)

It seem like gnome-session does no restores the previous session and you must be starting every time: pidgim, rhythmbox, skype, ekiga, evolution, etc...

Is there any workaround to solve this untill this bug is solved?

Accepting suggestions to solve this annoying bug. 
Thank you very much.

---

### Post by constrictor on 2008-10-31
You could put then in your auto start applications in the sessions window. If you click on system ->preferences -> sessions. Click on the applications that start automatically tab and click on add and fill in the fields. To help you fill out the bit with command if at the command line you type in "whereis" <appname> it will give you the right spelling and the right path. This is what you put in the command field and then Put in a good description. Be careful with this though as it is very possible to mess up your GNOME session.

---

### Post by erlguta on 2008-10-31
Thank you Constrictor.
The problem is that if you do in this way it does not remember the windows position. As i had evolution in Hardy in Desktop nº2 and terminal maximized in Desktop nº3.
If i do in this way it always start all applications one on top of each other in desktop 1...and it is very annoying :(

PD: I am surprised that this very annoying bug:
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/249373](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/249373)

is known for some time and nobody has done anything about it.
And ironically is marked as low :confused:

---

### Post by ScottMinster on 2008-11-18
I feel your pain, erlguta.  I too am annoyed by this bug.  Even more when combined with bug 272247 that causes problems with booting (and suspending, resuming, hibernating, etc.) on my laptop.  This means I'm more likely to be (re)booting and being annoyed by this Gnome bug.  I think [http://bugzilla.gnome.org/show_bug.cgi?id=552387](http://bugzilla.gnome.org/show_bug.cgi?id=552387).  It's listed as urgent, but I don't know if it's actually being worked.

However, we really cannot complain to Ubuntu about this.  It is clearly a major regression in Gnome itself.  As I understand it, Gnome released 2.24 with a partially re-written session manager.  This re-write is missing major functionality, such as the ability to save and restore sessions.  Personally, I think that since those are pretty must the only things that a session manager has to do, Gnome should not have put the partial re-write in a released version of Gnome.  They could have easily held off until 2.26 when the functionality would be finished.

<rant>
I'm not too surprised, though.  Gnome has been busy removing functionality since 2.0 when they took away the ability to have different backdrops on different virtual desktops.  More recently, they decided to severely limit screensavers by writing their own screensaver engine and configuration dialog that doesn't support any actual configuration except for what screensaver to run.  And now a session manager that doesn't actually save or restore sessions.
</rant>

Sorry about that, I just get upset when I think about some of the dumber things the Gnome developers have done.  I really do prefer the look and feel of Gnome and the GTK widgets.  Maybe it's time for a Gnome fork?  If only I had the time...

---

### Post by Wolki on 2008-11-18
Yes, this is incredibly annoying. I've already missed some important IMs because I forgot to start pidgin manually.

I think I have most things in my autostart now, but it's a bad workaround.

---

### Post by erlguta on 2008-11-18
> **ScottMinster said:**
> However, we really cannot complain to Ubuntu about this.  It is clearly a major regression in Gnome itself.  As I understand it, Gnome released 2.24 with a partially re-written session manager.  This re-write is missing major functionality, such as the ability to save and restore sessions.  Personally, I think that since those are pretty must the only things that a session manager has to do, Gnome should not have put the partial re-write in a released version of Gnome.  They could have easily held off until 2.26 when the functionality would be finished.

Yes. you're right. I think exactly the same. I understand mistakes and bugs happen and I do not complain about that. But upload a new version of Gnome that is known have errors like this because ubuntu must always be on pair with Gnome it is not a solution.
What if gnome do serious mistakes and regressions in one release?.
Has Ubuntu the necessary resources to continue and resolve it?.
This is something that worries me.

It is a known bug since the RC! and nobody did nothing to solve it. This indicates Ubuntu in a style of improvisation and let it go.

---

### Post by roderikk on 2008-12-01
Well, if we all register at the gnome bugzilla and comment on this bug maybe we will get noticed.

So, go here: [http://bugzilla.gnome.org/createaccount.cgi](http://bugzilla.gnome.org/createaccount.cgi)

Create an account, click on the email link (it takes a while to come... hasn't come for me yet).

Then go here: [http://bugzilla.gnome.org/show_bug.cgi?id=552387](http://bugzilla.gnome.org/show_bug.cgi?id=552387)

And give your (constructive) criticism.

Lets hope that if enough of us respond to this bug somebody with time and coding skills will notice and code a solution. Until then I will keep most of my PCs on Hardy.

---

### Post by Wolki on 2008-12-01
> **roderikk said:**
> Lets hope that if enough of us respond to this bug somebody with time and coding skills will notice and code a solution. Until then I will keep most of my PCs on Hardy.

Honestly, please don't do that. I'm really pissed off about the stupid decision to include the new gnome-session when it obviously isn't ready, but doing that would be absolutely counter-productive. Think about it this way: every comment you do sends a ton of mails and adds noise to the bug report, and having to read them will take developer time away from actually coding the fix for the bug.

If you want to send the message that you're interested in that bug, add yourself to the cc (this will also send a mail, but not add to the bug). Keeping the bug tracker in good shape and free from noise will get us to a solution quicker.

---

### Post by slowtrain on 2008-12-02
Another option:  Use Hibernate rather than shutting down your machine.  On my computer, this leads to a growing use of RAM till the computer is virtually unusable.  However, I've learned I can keep going indefinitely if I run the following code to clean out my swap out of hibernation and if I occasionally restart Firefox (on which I have the Session Manager add-on, so I can't lose my last session.


free -m
sudo swapoff -a -v
sudo swapon -a -e -v
free -m

---

### Post by jis on 2008-12-15
Another option is to install xubuntu-desktop and login Xfce session, since session management works better there.

---

