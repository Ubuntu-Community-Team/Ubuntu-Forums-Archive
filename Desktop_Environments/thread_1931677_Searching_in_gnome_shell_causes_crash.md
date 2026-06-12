---
title: "Searching in gnome shell causes crash"
date: 2012-02-25
forum: Desktop Environments
---

### Post by dbbolton on 2012-02-25
If I bring up gnome shell (either by pressing the windows/meta key or moving the mouse cursor into the upper right corner of the screen) and start typing in the "Type to search" field, the session will crash immediately. All applications that were open stay up, but the panels and window decorations disappear.  The only way I can get out of it is to go to a tty and restart X, as no keybindings seem to work.

This does not happen if I bring up the run dialog via Alt+F2 though.

---

Edit: Here is the solution, explained below
```
echo "" > ~/.local/share/recently-used.xbel && chattr -i ~/.local/share/recently-used.xbel
```

---

### Post by flusi100 on 2012-03-04
Same Problem here.
Application search is one of the key features of Gnome3 and doesn't work. Very annoying!

Bug already reported [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/912798")

You could leave a comment there...

---

### Post by dbbolton on 2012-03-05
Strangely, it worked for awhile before it started crashing. 

I have another machine running linux mint 12 and it hasn't crashed at all.

---

### Post by phh on 2012-03-06
I re-installed my Nvidia driver to the (Recommended) version, and my Activities search is working now.

---

### Post by escentrix on 2012-03-06
I've been doing a bit of research/testing and it seems that most of the problem does indeed have to do with video drivers.
The actual crashing seems to be triggered by gnome-shell's recently used feature. I am not yet sure what type of recent file I open actually causes the crashing to start, but I'll let you know as soon as I can narrow it down. It might be something related to how gnome-shell displays images of recent pictures or movies in the app picker.

For now, if you want to use updated drivers, or it's just happening otherwise, you can remove/clear your ***~/.local/share/recently-used.xbel*** file. this ought to dump whatever recently used item is hanging gnome-shell. Obviously, this removes ALL of your recently used items, so if you rely on this feature to get to some things you may not want to do this.

Anyways, let me know if this helps you and if you can add to it please do!

_**EDIT:**_
Currently I only notice the crashing on recently opened videos. There is a good chance that whatever bug is causing this could be happing on differnet file types as well. This is just the only instance that I have found at this time. I should also note that my gnome-shell will only crash if whatever I search for brings up my video (AVI in this case).
For example: If I open a video named test.avi and then go to my activities; my gnome-shell will not crash if I avoid the letters "*test.avi*" or other keys that relate to the metadata that gnome uses to search by.

---

### Post by Dnyarri on 2012-03-09
If you can't upgrade / downgrade your nvidia-drivers, I suggest you to try this:

 ```
echo "" > ~/.local/share/recently-used.xbel && sudo chattr +i ~/.local/share/recently-used.xbel    
```First it clears the recently-used.xbel -file and then sets it to immutable. Eversince I did this, gnome shell hasn't crashed on my computer. I've heard that evolution can cause crash too if you get email. For further information, I suggest you to read these:

[URL="http://www.nvnews.net/vbulletin/showthread.php?t=174049&page=3"]http://www.nvnews.net/vbulletin/showthread.php?t=174049&page=3 
[/URL] [http://www.cyberciti.biz/tips/linux-password-trick.html](http://www.cyberciti.biz/tips/linux-password-trick.html)

---

### Post by escentrix on 2012-03-12
I like the immutable flag; had been looking for a way to do this! I actually open up certian programs that I need in my recent list (some wine programs) and then do your +i trick. Thanks!

---

### Post by saugatad on 2012-03-12
I am having same problem. Does nvidia driver creating this problem?

---

### Post by dbbolton on 2012-03-14
> **Dnyarri said:**
> If you can't upgrade / downgrade your nvidia-drivers, I suggest you to try this:

 ```
echo "" > ~/.local/share/recently-used.xbel && sudo chattr +i ~/.local/share/recently-used.xbel    
```First it clears the recently-used.xbel -file and then sets it to immutable. Eversince I did this, gnome shell hasn't crashed on my computer. I've heard that evolution can cause crash too if you get email. For further information, I suggest you to read these:

[URL="http://www.nvnews.net/vbulletin/showthread.php?t=174049&page=3"]http://www.nvnews.net/vbulletin/showthread.php?t=174049&page=3 
[/URL] [http://www.cyberciti.biz/tips/linux-password-trick.html](http://www.cyberciti.biz/tips/linux-password-trick.html)

This seems to do the trick, but I'm going to wait a day or two before marking this thread as solved.

Is "chattr -i" different from "chmod a-w"?

Also, why did you include sudo? Since I own the file, I shouldn't need root privileges to modify it (and just to make sure I tried it without sudo and there was no error).

---

