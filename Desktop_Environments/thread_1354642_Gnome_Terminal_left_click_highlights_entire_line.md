---
title: "Gnome Terminal left click highlights entire line"
date: 2009-12-14
forum: Desktop Environments
---

### Post by shaibn on 2009-12-14
Hi,

When I click anywhere, where there is a blank space (either to the right of text or on lines that text has yet to be shown), the entire line to the right of the text (ie. white space) to the end of the line on the very right of the screen, gets highlighted.

This is kind of annoying since it then also enters that blank to my clipboard manager and makes it so my previous and much needed clipboard needs to be retrieved again from the clipboard manager.

How can I make a single-left-click copy mode disabled? So that only if I double click a word or 3 clicks highlight an entire line or path or what not?

Thanks in advance!
Shai

---

### Post by fixitdude on 2009-12-14
I use "gnome-terminal" all the time and it doesn't do that at all. I just looked through the settings and there's nothing for that, you have to select a profile then select "edit" to get to the settings.

You may want to get the latest version, I'm running a default Hardy install. Or if it already is the latest, reboot (just in case) and/or remove it and then re-install using your synaptic manager.

The only time I've seen it select a whole line is if it's a URL starting with http and so on.. or if I double click it will select a word.

You might also want to check your mouse settings, I don't know how but maybe it's sending a double click for any left click?

And make sure it's actually gnome-terminal that's running, there was another terminal I tried once but it sucked.

---

### Post by shaibn on 2009-12-14
Thanks for the prompt response :)

It is Gnome Terminal (according to the Help->About).
The only thing I can think of, is that this is actually a virtual machine inside virtualbox.

I actually just tried it, and from remote desktop connection to the box over virtualbox's VRDP, this didn't happen.

I guess this is VirtualBox related...

---

### Post by Psy-Q on 2009-12-21
I have the same issue here with Ubuntu 9.04 inside VirtualBox 3.1.0.

I found out that if I hold left CTRL, it doesn't happen. But that's useless too :)  In all other cases, whenever I click in the gnome-terminal window, the exact same behavior you described is visible.

Ubuntu is running inside VirtualBox in full-screen mode, with the matching VirtualBox guest additions installed.

---

### Post by shaibn on 2009-12-21
Exactly the same situation as mine :)
Thanks for the Ctrl tip ... but that's useless as you said.I too run it in Full screen inside a VM.

---

### Post by provoko on 2010-10-09
So what's the fix???  Hold left ctrl all the time?  There's gotta be a better solution...

---

