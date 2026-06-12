---
title: "Need help with &quot;start/ stop script ... thanx"
date: 2009-04-22
forum: General Help
---

### Post by lobo_blanco on 2009-04-22
Hi,

I'm new to script writing and could use a little help putting one together.

Background:
Ubuntu 8.04 host with Compiz Fusion installed
VirtualBox 2.2.0 with XP guest

VirtualBox seamless mode doesn't seem to work well with Compiz on so I found a nice little script called compiz-switch to turn compiz off so VB works in seamless.

1) What I'd like to do is have a script that will turn off compiz ...
("compiz-switch" will turn compiz on if it's off or off if it's on)

2) ... then open VirtualBox
("VBoxManage startvm WinXP" is the command line argument that I use to open VirtualBox)

3) ... then, if possible, turn compiz back on when exiting VirtualBox.
("compiz-switch")

I could probably make a script that will do #1 and #2 by using the echo command (permissions are owned by user so no sudo needed).

#3 may not be possible, I don't have a clue.


Thanks in advance for any help!
It's greatly appreciated!!

Dave

---

### Post by sdennie on 2009-04-22
My guess is that:

```

metacity --replace ; VBoxManage startvm WinXP ; compiz --replace

```

Is all you need.  You actually can just not bother with the script and put the following in a launcher:

```

sh -c "metacity --replace ; VBoxManage startvm WinXP ; compiz --replace"

```

---

### Post by lobo_blanco on 2009-04-22
Thanks Sdennie!

I'll just use the launcher since that's how I start Vbox now.
No need to make it more complicated than it needs to be.

Hey, I really appreciate the helpful hints!
Happy Earth Day!

Dave

---

### Post by sdennie on 2009-04-22
Actually, looking back, you probably need a & in there after metacity and compiz.  I think this will work:

```

sh -c "metacity --replace & ; VBoxManage startvm WinXP ; compiz --replace &"

```

But, I haven't tested it.  It's the general idea though.

---

### Post by lobo_blanco on 2009-04-22
Sdennie,

I wonder if it would be possible to call up the compiz-switch script, open Vbox then call up the compiz-switch again.
The reason I ask is that the little compiz-switch script works so well.

I think I messed up somehow 'cause when I rebooted I couldn't get a panel, just the background. I fixed it by replacing .gnome .gnome2 ,gconf .gconfd and .metacity with a clone backup ... so all is fine now.
I got a little spooked by messing with metacity as you could imagine.

I tried with the &'s but nothing happened.
I think the first one worked but I didn't give the launcher time to complete before I invoked another command.

Let me know if you think calling up the script would work.

Thanks for your time and patience.

Dave

---

### Post by sdennie on 2009-04-22
I see.  I'm not familiar with the compiz switch script but, if you understand how it works, you could probably substitute it for the "metacity --replace" and "compiz --replace" parts of the commands I've given.  Alternatively, you could try something like the following script:

```

metacity --replace &
sleep 10 # You could probably make this shorter
VBoxManage startvm WinXP
compiz --replace &
disown

```

That assumes that the VBoxManage command doesn't spawn something off and immediately return.  If it does, you'd need more complex stuff.  The "disown" at the end is just to make sure the compiz process isn't killed when the shell you are running terminates.  It may or may not be needed.

---

### Post by lobo_blanco on 2009-04-22
Cool, I'll experiment around and view the compiz-switch script to see what it consists of as you suggest.
You've given me some good things to try (and helped me with the syntax a great deal), I'll stick with it, try these out and learn something in the process. I'll keep you posted on what works for this particular situation.

Thanks ... :)

Dave

p.s. What a great forum, where else could you ask such a specific question and get numerous replies so quickly ... life is good, this forum (and whole ubuntu community) is great!

---

### Post by lobo_blanco on 2009-04-22
Hi again Sdennie,

I ended up using two launchers.

1) runs a script that:
   a) switches off Compiz (calls up compiz-switch.sh)
   b) launches VirtualBox (in Seamless mode)

2) runs a script that:
   a) initiates an acpi shutdown of XP (within VirtualBox)
   b) switches on Compiz (calls up compiz-switch.sh)

The problem was that I needed Compiz off the whole time, while using VirtualBox (in seamless mode) then needed Compiz back on when I closed VirtualBox down.

Using two launchers works well. I have to shut VirtualBox down one way or the other so it's just as easy to use a launcher button which also switches Compiz back on at the same time.
Problem Solved

I really do appreciate your help, you helped me think it through and we ended up with just what I needed.

Thank You,

Dave

---

### Post by sdennie on 2009-04-22
I'm glad to be able to help.  I don't have all the answers but, many times, a push in the right direction is just as good.

---

