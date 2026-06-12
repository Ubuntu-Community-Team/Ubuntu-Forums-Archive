---
title: "What The Hell?! Where Did My Desktop Go?!"
date: 2005-07-28
forum: Desktop Environments
---

### Post by D-Boy on 2005-07-28
ok...this is odd. a few minutes ago my desktop went kaput. I have no idea what I was doing at the time (short term memory loss.) so please. Anyone know what this is? I think I was adding repositories with synaptic..

---

### Post by varunus on 2005-07-28
Try opening a terminal and typing "killall nautilus".  If this command returns a "no process killed" message, try typing "nautilus&" into the terminal.

---

### Post by D-Boy on 2005-07-28
THANK YOU VERY MUCH! So it is true what they say. The Linux Community is the most helpful.  :smile:

---

### Post by Dogmeat on 2005-07-28
I had to randomly kill it on boot if the desktop didn't load, thats really annoying. I think it happens if you add remote shares to fstab, because when i commented it out I stopped having to kill nautilus every time. Its better just to make a shell script to mount all your drives and run it when needed, after this I never had to kill nautilus again. The side effect is you don't get the share's icons on the desktop, but I think the trade off is worth it.

---

### Post by dtfinch on 2005-07-29
I've been having this same problem (desktop often freezes when it tries to load) for a couple months. No fstab mounts to remote shares, but I do have some network paths in my bookmarks. It's been such a problem that I just put a launcher to "killall nautilus" in my panel.

Another problem I encountered while trying to debug the nautilus freezing problem is that the System Monitor fails to properly monitor per-process cpu usage. It's almost entirely broken. Sorting by cpu usage shows idle processes at both the top and the bottom. Scrolling through the list, all I see are zeros. But if I scroll over a process that I know has high cpu usage, several seconds later it'll jump from the incorrect value of 0% to the 90+% usage I expected.

---

### Post by varunus on 2005-07-29
Sounds like you should post bug reports on both of those at the gnome website...Unless of course they already are bug reports on them there.  Though, I think GNOME 2.12 is in a feature freeze, but it wouldn't hurt to post a bug report, they'll probably fix it for 2.12.1 at least...

---

### Post by dtfinch on 2005-07-29
Bugzilla is a nightmare for end users who only need to submit a single bug report. Figuring it out and going through all the prerequisite rituals can take like an hour or more if it's their first time. If developers wanted to hear about bugs, they'd make it easy, like a text box, a version dropdown, and a submit button, with no forced registration or other pointless hassles.

This problem in particular has been around for months:
[http://ubuntuforums.org/showthread.php?t=37696](http://ubuntuforums.org/showthread.php?t=37696)

It's certainly worthy of a bug report, but nobody wants to deal with bugzilla when they can just post in a forum and let someone with more free time deal with it. There's no guarantee you'll get a positive response from them either. Having seen bug and annoyance reporters get flamed and treated like trolls by developers on their mailing list, I submitted my last set of criticisms via paypal, figuring they might get more consideration that way, and got a nice mug in return.

---

