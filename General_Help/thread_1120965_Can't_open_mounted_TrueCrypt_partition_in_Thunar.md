---
title: "Can't open mounted TrueCrypt partition in Thunar"
date: 2009-04-09
forum: General Help
---

### Post by peyre on 2009-04-09
I'm running Xubuntu 8.10 and have installed TrueCrypt.

I previously had Nautilus installed for connecting to other computers over the network (since Thunar doesn't have that capability), but I uninstalled it because it would hijack my Desktop on every reboot--I had to go back into settings and recheck Let Xfce manage my desktop.

So now when I try to open a mounted volume in TC, it errors out saying it can't find Nautilus.

I removed TC, then reinstalled it, hoping it would notice that Nautilus wasn't there.  No dice; it still insists on using Nautilus, and errors out.

Now don't get me wrong; I like Nautilus and would *like* to put it back on my system, but it's unacceptable that it %$#@s with my Desktop settings on every reboot.  Anyone have a solution?  I'd be happy with either getting TC to open partitions in Thunar, or better yet, persuading Nautilus to leave my settings alone.

---

### Post by rakzor on 2009-04-09
Use ```
nautilus --no-desktop
``` 

and it won't take over your desktop.

---

### Post by peyre on 2009-04-10
> **rakzor said:**
> Use ```
nautilus --no-desktop
``` 

and it won't take over your desktop.

Whoa-whoa.  Sorry to be a noob, but where do I insert that?

---

### Post by fireworld2406 on 2009-04-10
I think (please correct me if I'm wrong) he means to type it into a Terminal window. Unfortunately I've only used Xubuntu once, so I don't quite remember how to open a terminal window in Xubuntu, but I believe you open the applications menu and goto accessories.

Hope that helps!

---

### Post by peyre on 2009-04-10
> **fireworld2406 said:**
> I think (please correct me if I'm wrong) he means to type it into a Terminal window. Unfortunately I've only used Xubuntu once, so I don't quite remember how to open a terminal window in Xubuntu, but I believe you open the applications menu and goto accessories.

Hope that helps!

Oh, the Terminal!  Yeah, I know how to open that--I'm not [i]that[/] big a noob.  I tried it, but no good so far.  I tried once with just that command, and then again using sudo, but each time it grabbed my Desktop after a reboot.  Thanks for trying though!

---

### Post by fireworld2406 on 2009-04-10
But it works properly when you open nautilus using that command though, right?

All that you are doing with that command is opening nautilus with some options added to it. That is why it won't stick once you reboot.

---

### Post by peyre on 2009-04-10
> **fireworld2406 said:**
> But it works properly when you open nautilus using that command though, right?

All that you are doing with that command is opening nautilus with some options added to it. That is why it won't stick once you reboot.

Oh, I see what you mean.  Well, the problem isn't that Nautilus messes with the Desktop settings when I open it for the first time.  It resets them immediately on bootup, before I've opened anything.  The system comes up normally for a second, then suddenly switches back over to the Gnome desktop, or whatever it is that Nautilus wants it to be.  I won't have even opened Nautilus at that point.

---

### Post by fireworld2406 on 2009-04-10
Try some of these solutions here:

[http://bugs.launchpad.net/ubuntu/+source/xfce/+bug/73844](http://bugs.launchpad.net/ubuntu/+source/xfce/+bug/73844)

[http://answers.launchpad.net/ubuntu/+source/nautilus/+question/6044](http://answers.launchpad.net/ubuntu/+source/nautilus/+question/6044)

The tip about gTweakUI in the second link looks like the easiest and most promising (you can download it from the repositores using the package manager that comes with Xubuntu or by opening a terminal and typing
```

sudo apt-get install gtweakui

```
)

Hope that helps!

---

### Post by peyre on 2009-04-10
> **fireworld2406 said:**
> Try some of these solutions here:

[http://bugs.launchpad.net/ubuntu/+source/xfce/+bug/73844](http://bugs.launchpad.net/ubuntu/+source/xfce/+bug/73844)

[http://answers.launchpad.net/ubuntu/+source/nautilus/+question/6044](http://answers.launchpad.net/ubuntu/+source/nautilus/+question/6044)

The tip about gTweakUI in the second link looks like the easiest and most promising (you can download it from the repositores using the package manager that comes with Xubuntu or by opening a terminal and typing
```

sudo apt-get install gtweakui

```
)

Hope that helps!

Hey, that did it!  At least on my test system here.  Next to try it at home tonight.

For anyone else with this issue who may come across this thread, this is what you do:

[LIST=1]
[*]Open a terminal and run [FONT="Courier New"]sudo apt-get install gtweakui[/FONT] (as fireworld suggested)
[*]Open the File System, then go to /usr/bin
[*]Double-click on gtweakui-nautilus
[*]Deselect "Use nautilus to draw _d_esktop", and click _C_lose.
[/LIST]

---

### Post by ryu kun on 2010-08-27
> **peyre said:**
> Hey, that did it!  At least on my test system here.  Next to try it at home tonight.

For anyone else with this issue who may come across this thread, this is what you do:

[LIST=1]
[*]Open a terminal and run [FONT="Courier New"]sudo apt-get install gtweakui[/FONT] (as fireworld suggested)
[*]Open the File System, then go to /usr/bin
[*]Double-click on gtweakui-nautilus
[*]Deselect "Use nautilus to draw _d_esktop", and click _C_lose.
[/LIST]

I use Xubuntu 10.04.  I have the same issue with you. I get the same error message from Truecrypt: "No such file or directory: nautilus"

When I run gtweakui-nautilus I see that option is already "deselected".  Any suggestions please?

I can access the files through /media/truecrypt1 , but it would be nice if the drive appears on the Places menu after its mounted.

Any suggestions, please?

---

