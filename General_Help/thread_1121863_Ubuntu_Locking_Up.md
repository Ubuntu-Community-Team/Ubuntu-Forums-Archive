---
title: "Ubuntu Locking Up"
date: 2009-04-10
forum: General Help
---

### Post by Carpe Guitarrem on 2009-04-10
So, issue here, I've been using Ubuntu for a long time. Out of the blue, though, it started regularly locking up and refusing to load beyond booting up, flashing the Caps Lock light and the Scroll Lock light. I even tried Alt+SysRq+s, Alt+SysRq+o, in every possible combination on my laptop keyboard, and it's not working to shut it off.

I'm using Ubuntu 8.04, and the most recent thing that I've been working with is the pygame package. It seems to have issues with a number of the libraries which I've been installing on Ubuntu to provide for dependencies.

At startup, I boot up Pidgin, Gruler, and a Gmail notifier, along with Screenlets and the default programs. Gruler, Pidgin, and the notifier are the most recent additions, and it seems to be locking up as Gruler loads.

I'm currently dual-booting Ubuntu and XP, albeit not optimally, because I used the "install Ubuntu through Windows" option on the LiveCD, the Wubi installer, that is.

Any suggestions? I'm particularly wondering if there's any way I can use the command line to fix this.

---

### Post by utnubuuser on 2009-04-10
Have you tried removing Gruler to see if it actually is the cause?

---

### Post by Carpe Guitarrem on 2009-04-10
Well, I'm not quite sure how to manage that, because it's a Ruby script that runs on startup. And I don't have access to the files on my main user from my "sandbox" user (which I set up for an entirely random reason, but I'm very glad I have it, now).

So there's another bit of info. It logs in on another user just fine, but not my main one. I'm also not sure how to alter the session startup or how to move the gruler folder (thus breaking the link and interrupting the startup load), unless it be by logging on as root, but I really don't want to do that.

A quick update, I was mistaken on my version, I'm running 8.04, and that's under a Wubi install on Windows XP.

EDIT: Okay, so a bit of digging around, I found out that after using "su" to temporarily log in as root, it's possible to change a folder name from the command line. Been, done, and it interrupted gruler, which apparently has been what's causing this ruckus. I fortunately also now have a backup user, in case this goes awry again. So, problem solved.

---

