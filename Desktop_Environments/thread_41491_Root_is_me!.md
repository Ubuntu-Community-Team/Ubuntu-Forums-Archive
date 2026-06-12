---
title: "Root is me!"
date: 2005-06-13
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-13
I'm trying to listen to advice not to log is as root. It's bad for some reason (even tho on windows i always have full access to everything). So I'm logged in as me - settng everything up all over again. Now, next time i need log in as root i'd like it to know that root setting = dave settings. Can I use those posh shortcut/alias things to link roots er... 'application data' to mine?

Not urgent, but would be nice
Thanks

---

### Post by desdinova on 2005-06-13
[QUOTE=Dave_is_sexy]I'm trying to listen to advice not to log is as root. It's bad for some reason (even tho on windows i always have full access to everything). So I'm logged in as me - settng everything up all over again. Now, next time i need log in as root i'd like it to know that root setting = dave settings. Can I use those posh shortcut/alias things to link roots er... 'application data' to mine?

Not urgent, but would be nice
Thanks[/QUOTE]
 Not easily no - the best is to use sudo - you can run nautilus with sudo to get a gui root privilege'd nautilus.....

Its bad for two major reasons

1) Root isn't a normal account, its for sys admin purposes only

2) As root can do anything and everything - its phenomenally easy to trash your machine - hence why you run as a user. Windows has only recently tried to move away from the "always root" - for example Win XP Home only allows admin in safe mode.

The point is, the *nix philospohy is to only have as much permission as necessary to complete the job at hand. It makes for good security - wait till you've run a "rm " command in the wrong directory ;-) !

---

### Post by Dave_is_sexy on 2005-06-13
Oh cool. Man, why don't they put a button on the (now vanished) Nautilus task bar that says "root powers". then you push it and enter the password and yau have a new root window.

Can I make a script to open a root nautilus? That really is a huge huge thing they should print in tips or something. Another idea would be to have tips  :smile: 

With root nautilus and terminal, i don't think i'll need the root accunt at all. Although, everything works there. My log on is crap.

---

### Post by desdinova on 2005-06-13
[QUOTE=Dave_is_sexy]Oh cool. Man, why don't they put a button on the (now vanished) Nautilus task bar that says "root powers". then you push it and enter the password and yau have a new root window.

Can I make a script to open a root nautilus? That really is a huge huge thing they should print in tips or something. Another idea would be to have tips  :smile: 

With root nautilus and terminal, i don't think i'll need the root accunt at all. Although, everything works there. My log on is crap.[/QUOTE]
 If you install via backports repository the SMEG menu editor, you could create a launcher (or even just right click on your desktop and select Create Launcher)

command line 

gksu nautilus

then perhaps a root terminal one

gksu gnome-terminal

---

### Post by Dave_is_sexy on 2005-06-13
Wicked! I have power on my account... AND it's in browser mode! but not when started without the launcher

---

### Post by Takis on 2005-06-13
[QUOTE=Dave_is_sexy]Oh cool. Man, why don't they put a button on the (now vanished) Nautilus task bar that says "root powers". then you push it and enter the password and yau have a new root window.[/QUOTE]
But what happens when you come back after ten minutes away and have forgotten that you're browsing under the root account? You need to be very careful of this. Where I work (I'm a Windows admin), I have two accounts: a normal and an admin. Although I usually am aware, sometimes I don't realise I'm looking at something with write priviledges when I don't need to - even though I can any time I want to.
The only time you should go in with write priviledges is when you know exactly what it is you're going to change. Accomplish that change and then stop using that priviledge. It's a very sensible way to administrate your system.

---

### Post by Dave_is_sexy on 2005-06-13
Cool that's the plan. I was already talked out of using root, athough i'd like the machine to acknowlede that if i try to change something it doesn't want me to it should ask for a password rather than daring to tell me, it's owner that i don't have permission.

---

### Post by Takis on 2005-06-14
Dave, you need to learn to let the machine wear the pants in your relationship. I know the following is hard to believe when moving from Windows  :grin: , but sometimes our OSs know more than we do.

---

### Post by PeP on 2005-08-11
[QUOTE=Takis]But what happens when you come back after ten minutes away and have forgotten that you're browsing under the root account? You need to be very careful of this. Where I work (I'm a Windows admin), I have two accounts: a normal and an admin. Although I usually am aware, sometimes I don't realise I'm looking at something with write priviledges when I don't need to - even though I can any time I want to.
The only time you should go in with write priviledges is when you know exactly what it is you're going to change. Accomplish that change and then stop using that priviledge. It's a very sensible way to administrate your system.[/QUOTE]

there is a solution:
Have a very different ( I mean flashy and ugly)  gtk/kde theme for root so that you don't confuse an app run as root with the same app without special privileges.

Change the colors of the shell prompt it's easier to notice than a $/>% ...

---

### Post by wmcbrine on 2005-08-12
[QUOTE=PeP]there is a solution:
Have a very different ( I mean flashy and ugly) gtk/kde theme for root so that you don't confuse an app run as root with the same app without special privileges.[/QUOTE]
That's what I do, in Windows. (I don't even use root in Ubuntu, just sudo.) My normal backdrop is the tranquil moon-over-mountains pic, while my root backdrop is the moon-over-the-Sahara -- it says "don't stay here long, or you'll regret it". (But I guess I should really have a blazing-sun-over-the-Sahara.)

Dave: running as admin is a bad idea in Windows, too, even though it's the default (and there are quite a few poorly-written apps that require it). Try a limited account for your daily usage and see if it doesn't work for you.

Desdinova: "Win XP Home only allows admin in safe mode" -- huh? Sounds like a good idea, but it's not what I've seen.

Sorry for all the Windows talk.

---

