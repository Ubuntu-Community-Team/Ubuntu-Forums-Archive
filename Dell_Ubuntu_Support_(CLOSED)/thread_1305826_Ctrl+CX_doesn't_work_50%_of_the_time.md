---
title: "Ctrl+C/X doesn't work 50% of the time"
date: 2009-10-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Wilbefast on 2009-10-30
I've always had the problem but it's annoying me more and more - when I want to copy/cut a file I can't just hit Ctrl+C/X because half the time it won't actually copy/cut the file: nothing is added to the clipboard.

Thus I have to hit the command several times in a row just to make sure it's registered that I'm trying to copy something. I can't count the number of times I've had to come back to the file I was trying to copy having pasted thin air :(

Is there a fix for this?

Dell Vostro 1510
AZERTY keyboard
Ubuntu 9.04


Thanks,


William

edit: on a side note, I also lose the clipboard whenever I close an application - say I open my source code in Kate, grab a chunk I want to pastebin, copy and then close Kate: I lose the source I wanted to paste and have to open Kate again. Is there an option to turn on a sort of persistent clipboard?

---

### Post by hellocatfood on 2009-10-30
I've had this problem too and still have it on 9.10. I don't believe there's a workaround so I've submitted a bug about it.

---

### Post by teward on 2009-10-30
I've got a Dell Latitude E6500, with a QWERTY keyboard, and clipboard works fine on 9.04 Jaunty.  The only time it doesn't work is when I'm using Wine to run Windows programs, where as I close it, and I lose the data, but that's what the gedit text editor is useful for.

---

### Post by hellocatfood on 2009-10-30
It's not that it doesn't work at all but that there's a slight delay in it recognising the key press. I've had a similar problem with the [caps lock](https://bugs.launchpad.net/ubuntu/+bug/438447) and nothing's been sorted yet.

I filed the bug against Nautilus but I'm not sure what component it could be.

---

### Post by Wilbefast on 2009-10-30
> **hellocatfood said:**
> It's not that it doesn't work at all but that there's a slight delay in it recognising the key press. I've had a similar problem with the [caps lock]("https://bugs.launchpad.net/ubuntu/+bug/438447") and nothing's been sorted yet.

I filed the bug against Nautilus but I'm not sure what component it could be.

That may be it: when I do Ctrl + C I do it really fast, but with absurd amounts of memory and the ability to perform several billion calculations per second I really don't think a modern operating system should have a problem picking up a split-second key-press.

That said, I am NOT going back to Windows  [-(

---

### Post by spongypants23 on 2009-10-31
Install glipper and add it to a panel (assuming you use GNOME).

```
sudo apt-get install glipper
```

It's a great clipboard app. Works wonderfully.

It may solve some of your problems.

---

### Post by Wilbefast on 2009-10-31
I've installed it, but how does one perform this "adding to panel" procedure you speak of? I'm trying to run "glipper" in terminal but the computer says no.

---

### Post by Bucky Ball on 2009-10-31
?

Copy cut? One or the other.

Control+X will cut AND copy the cut contents to the clipboard.

Control+C. Delete. Copy material and then delete it.

Cut=cut from here but DON'T delete. Should be on the clipboard until you put something else in there.

Curious to know if just control+x is working. If not, that would be a bug.

Consequently, control+x then control+v should cut (and copy) then paste to the new location.

---

### Post by Wilbefast on 2009-10-31
I'd always thought it was:
"Copy" + "paste" = cp
"Cut" + "paste" = mv
So the "cut" copies the file to the clipboard and then deletes it when it is pasted, whereas "copy" only copies it. But that's not really the question. 

Both "cut" (ctrl + x) and "copy" (ctrl + c) don't register about half the time I use them, so when I go to paste (ctrl + v) what I just tried to cut/copy I don't have anything to paste, because the previous cut/copy didn't work.

It's the_ keyboard shortcuts_ that aren't being registered - if I right click and select copy or whatever and right click to paste it works fine, it's just that I'd like to do things a little faster than that :-S

---

### Post by hellocatfood on 2009-10-31
> **Wilbefast said:**
> That may be it: why I do Ctrl + C I do it really fast, but with absurd about of memory and the ability to perform several billion calculations per second I really don't think a modern operating system should have a problem picking up a split-second key-press.

That said, I am NOT going back to Windows  [-(

Do you think this could be registered as part of the [one hundred papercuts](https://launchpad.net/hundredpapercuts) project?

---

### Post by spongypants23 on 2009-10-31
> **Wilbefast said:**
> I've installed it, but how does one perform this "adding to panel" procedure you speak of? I'm trying to run "glipper" in terminal but the computer says no.

Again, I'm assuming you run GNOME. I don't know how/if this works in KDE/XFCE/any other desktop environment.

Simply right-click a panel, click "Add to panel", and add "Clipboard Manager".

---

### Post by Wilbefast on 2009-10-31
> **hellocatfood said:**
> Do you think this could be registered as part of the [one hundred papercuts]("https://launchpad.net/hundredpapercuts") project?

It's certainly a small but annoying problem...

> **spongypants23 said:**
> Again, I'm assuming you run GNOME. I don't know how/if this works in KDE/XFCE/any other desktop environment.

Simply right-click a panel, click "Add to panel", and add "Clipboard Manager".

:o Oh

Well, that was easy :)

Man - this thing is awesome! Pretty much exactly what I needed for part 2 of the problem!

---

### Post by hellocatfood on 2009-11-13
Looks like the root of the problem has been found. Please add your +1's to this bug report [https://bugzilla.gnome.org/show_bug.cgi?id=517639](https://bugzilla.gnome.org/show_bug.cgi?id=517639)

---

### Post by Wilbefast on 2009-11-13
Cool - I went and posted on the bug report ;)

Was hoping this would be fixed in 9.10, apparently they have the same problem :-k

---

### Post by ryecomp on 2009-12-04
I have the same problem in or between kate, ff, terminal.

Specially in kate, my main notepad, it occurs too frequently, may be about 50%..

If i enter few lines into kate and select and copy them and
paste to the **SAME** kate text box, it says there is nothing to 
copy. 

It is not about delay. It is about copy action not working.

Sometimes copy action is possible after restarting kate,... 

This problem started after upgrading to ubuntu 9.10!!! This is the first ubuntu version
that is unusably unstable. 

os : ubuntu 9.10
kate 3.3.2
ff 3.5.1
terminal 2.28.1

---

### Post by hellocatfood on 2009-12-04
As mentioned in the bug report above ([https://bugzilla.gnome.org/show_bug.cgi?id=517639](https://bugzilla.gnome.org/show_bug.cgi?id=517639)) it's a problem with Nautilus. I've had this problem since 9.04 and not sure if it's something that'll be fixed with Gnome Shell coming in 10.10.

*sigh* We can only hope

---

### Post by billharris on 2009-12-12
I'm having a problem with X copy (or whatever it's called -- when you select text with the mouse and then middle-click to paste it.  It's always worked up until Karmic.  Now I usually can't copy and paste using that or Ctrl-c / v.  :-(

---

### Post by ukblacknight on 2009-12-14
> **Wilbefast said:**
> edit: on a side note, I also lose the clipboard whenever I close an application - say I open my source code in Kate, grab a chunk I want to pastebin, copy and then close Kate: I lose the source I wanted to paste and have to open Kate again. Is there an option to turn on a sort of persistent clipboard?

I've just realised this tonight - I've been using Ubuntu since 7.10 and had just thought it was me not copying properly, or something to do with non-GTK apps.

It was only until I tried copying an address from Chrome, closing it, then trying to paste it into Firefox and it couldn't that I realised it wasn't working.

This seems like such a basic bug it's insane that it's not been fixed!

---

### Post by Uadebisi on 2009-12-23
> **spongypants23 said:**
> Again, I'm assuming you run GNOME. I don't know how/if this works in KDE/XFCE/any other desktop environment.

Simply right-click a panel, click "Add to panel", and add "Clipboard Manager".

Hello all,
I tried this & it didn't seem to work. The terminal reported some install info but resulted in something about searching for Python. Now what?

 What about "Parcellite" clipboard manager? That's the only "Clipboard Manager" that I can find in the software repository. Would that work too?

Ever since the update a few days ago, I too am having copy,cut & paste problems via right-clicking on a mouse. I am also noticing since that time, that when I try to access my Thunderbird account via the launcher, that I sometimes need to click more than once for the program to open. Perhaps there is a correlation:?:

---

### Post by spongypants23 on 2009-12-25
> **Uadebisi said:**
> Hello all,
I tried this & it didn't seem to work. The terminal reported some install info but resulted in something about searching for Python. Now what?

 What about "Parcellite" clipboard manager? That's the only "Clipboard Manager" that I can find in the software repository. Would that work too?

Ever since the update a few days ago, I too am having copy,cut & paste problems via right-clicking on a mouse. I am also noticing since that time, that when I try to access my Thunderbird account via the launcher, that I sometimes need to click more than once for the program to open. Perhaps there is a correlation:?:

Post the output of ```
sudo apt-get install glipper
```

---

### Post by Uadebisi on 2009-12-25
Thank you spongypants23! 

> Post the output of      Code:
     sudo apt-get install glipper
:~$ sudo apt-get install glipper
[sudo]: 
[COLOR=Navy]Reading package lists... Done
Building dependency tree       
Reading state information... Done
glipper is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
:~$ 
[/COLOR] 

However, this result is not exactly the same as the one I received last night (that I should have copied). Also, I just realized that I am in a Dell forum & I have a Gateway built for Windows :eek: I hope that we can still get a work around for my problems. And remember, there is Parcellite in the repository. Perhaps that will do the trick.

I look forward to your reply.
MERRY CHRISTMAS!

---

### Post by spongypants23 on 2009-12-25
So, what happens when you try to add Glipper to the GNOME-Panel?

---

### Post by Uadebisi on 2009-12-25
> **spongypants23 said:**
> So, what happens when you try to add Glipper to the GNOME-Panel?

Glipper is not an option in "add to panel"... Glipper is no where to be found by running a search nor is it a program in the "installed" or "uninstalled" repository.

---

### Post by spongypants23 on 2009-12-26
> **Uadebisi said:**
> Glipper is not an option in "add to panel"... Glipper is no where to be found by running a search nor is it a program in the "installed" or "uninstalled" repository.

It's not called Glipper in the Add To Panel menu, it's called "Clipboard Manager", not sure if that helps.

I'm not sure what you mean by installed and uninstalled repositories, since those aren't repos in the first place.

Just for kicks, you can try running ```
sudo dpkg-reconfigure glipper
``` and see if that helps at all.

---

### Post by Uadebisi on 2009-12-26
Well, I ran 

> sudo dpkg-reconfigure glipper& there was a few second pause where the machine was working on something but there were no results from the terminal to actually post here. So, I again right clicked in the panel, clicked "add to panel" & still no Glipper/Clipboard Manager.

> I'm not sure what you mean by installed and uninstalled repositories, since those aren't repos in the first place.Just saying that I looked for "Glipper" by running a search for the name from "Places" - "Search for files" & that I also searched "Applications" - "Ubuntu Software Center" for anything named "Glipper" or "Clipboard Manager". All I found there was "Parcellite" Clipboard Manager.

So, by running what I have so far in the terminal, did I change anything to my system & if so, how do I change it back to the way it was? And...what next? :)

---

### Post by spongypants23 on 2009-12-28
I have to admit I'm not sure how to solve your problem. Sorry.

You might have more luck if you post in the "General Help" section. I suspect more people read that category than this Dell one.

---

### Post by hellocatfood on 2009-12-28
> **spongypants23 said:**
> I have to admit I'm not sure how to solve your problem. Sorry.

You might have more luck if you post in the "General Help" section. I suspect more people read that category than this Dell one.

That wont help this situation. It's a problem with Gnome or nautilus and has already been reported on Launchpad/bugzilla. A friend of mine who used to be an Ubuntu developer confirmed the bug but I suspect it wont get fixed any time soon Gnome are busy working on the Gnome Shell, which is due to appear in Ubuntu next October.

---

### Post by spongypants23 on 2009-12-28
> **hellocatfood said:**
> That wont help this situation. It's a problem with Gnome or nautilus and has already been reported on Launchpad/bugzilla. A friend of mine who used to be an Ubuntu developer confirmed the bug but I suspect it wont get fixed any time soon Gnome are busy working on the Gnome Shell, which is due to appear in Ubuntu next October.

I was talking about the Glipper problem in the last few posts, rather than the OP's problem.

---

### Post by hellocatfood on 2009-12-28
Ah, I see. Sorry for assuming! :oops:

---

### Post by Uadebisi on 2009-12-28
Fair enough...but what about this question,

> So, by running what I have so far in the terminal, did I change anything to my system & if so, how do I change it back to the way it was?

---

### Post by spongypants23 on 2009-12-29
> **Uadebisi said:**
> Fair enough...but what about this question,

No, you haven't made any major changes to your system that would need to be rolled back.

---

