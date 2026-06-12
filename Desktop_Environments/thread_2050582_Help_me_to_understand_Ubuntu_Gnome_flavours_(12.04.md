---
title: "Help me to understand Ubuntu Gnome flavours (12.04)"
date: 2012-08-31
forum: Desktop Environments
---

### Post by Trompette83 on 2012-08-31
Hi,

For few days I try to understand what are the difference between the Ubuntu gnome DE with 12.04 before switching to one of them.

I wrote a table attached. Could you help me to fully fill the table and add links, etc...
I will add info to complete it.
The info and links are mainly based on Ubuntu 12.04.

BTW, is it possible to display this table directly in the thread, not in a file? How?

Thanks a lot

---

### Post by tartalo on 2012-08-31
Gnome 3 has 2 official "front-ends", Gnome Shell and Gnome Classic. Unity is another unofficial "front-end".

gnome-session-fallback or Gnome Classic is NOT Gnome 2, it's Gnome 3 arranged to look like Gnome 2.

Gnome 2 is a dead project.

Gnome-panel worked on top of Gnome 2, has been replaced by Gnome shell in Gnome 3

---

### Post by Trompette83 on 2012-08-31
Sorry but more I read more I get lost.

> gnome-session-fallback or Gnome Classic is NOT Gnome 2, it's Gnome 3 arranged to look like Gnome 2.

So, I don't understand this [_link_]("http://askubuntu.com/questions/179376/how-to-remove-gnome-fallback"):
> Some time ago I've upgraded my Ubuntu 11.04 to 12.04. Now I have Gnome2 as well as Gnome3. It's a bit useless to have them both, so could u please tell me how can I remove Gnome2 safely?
You can remove the session using this command:

sudo apt-get remove gnome-session-fallback


Does he say "Gnome2" instead of "Gnome2 look like"?


> Gnome-panel worked on top of Gnome 2, has been replaced by Gnome shell in Gnome 3 
Does that mean that if I install gnome-panel pkg, I install gnome2 (the desktop environment) to run it?

The question is:
What is the difference between the 2 pkg, gnome-session-fallback and gnome-panel?
I didn't find any answer in the Net.

---

### Post by tartalo on 2012-08-31
Sorry, I was wrong about Gnome panel, there is a Gnome panel for Gnome 3

---

### Post by Trompette83 on 2012-08-31
Found part of answer [_here_]("http://ubuntuforums.org/showthread.php?t=1994637")

> Gnome Session Fallback depends on Gnome Panel, and Gnome Panel "recommends" Gnome Session Fallback.

Therefore, no matter which one you install, you'll end off with the other one too. No difference.

I tested with Software Center:
Install gnome-panel will install gnome-session-fallback
Install gnome-session-fallback will install gnome-panel

Remove gnome-panel will remove gnome-session-fallback
Remove gnome-session-fallback will NOT remove gnome-panel

Now next question:
What is the difference when I login with
Gnome Classic or Gnome Classic (No effects)?

---

### Post by Trompette83 on 2012-08-31
Found important info after lot of reading.

From [_here_]("http://ubuntuforums.org/showthread.php?t=1984091&page=2"), [_here_]("http://ubuntuforums.org/showthread.php?t=1914841") and [_here_]("https://answers.launchpad.net/ubuntu/+source/gnome-session/+question/190813"):

- Unity and Gnome Classic uses Compiz as window manager
- Unity-2D and Gnome classic (no effects) use Metacity

So, I have now more info to choose the good one

Thanks

---

