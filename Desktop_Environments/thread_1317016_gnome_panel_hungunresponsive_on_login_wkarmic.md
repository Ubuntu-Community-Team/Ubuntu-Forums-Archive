---
title: "gnome panel hung/unresponsive on login w/karmic"
date: 2009-11-06
forum: Desktop Environments
---

### Post by Steve Roscio on 2009-11-06
Howdy -

Upgraded Ubuntu desktop from Intrepid thru Jaunty to Karmic 9.10.

Now when I login, more than half the time my gnome-panel is unresponsive.
It looks fine, the icons are there, etc, but it is hung - does not respond to mouse or keyboard input.  Workspace switching does not work either.

Too, if it's working when I login, and then I do something to the panel like try to move launchers or change the icon size (I'm not sure the trigger), it will then hang.  Open windows are responsive, but the panel is not, including Application/Places/System menu items.

This occurs on both an x86 32-bit box, and an x86 64 bit box.

I can clear it (sometimes) by logging out (ctrl+alt+del responds, select Logout) and back in.

Suggestions?

- Steve

---

### Post by surfincrow on 2009-11-06
I've got the same problem. When I select restart, the message appeares 'gnome panel does not respond, do you still wan't to restart'
This is also after an upgrade scenario.

---

### Post by PTo on 2009-11-07
I'm having the same problem, but in my case restarting gives no improvement. I solved it a few days ago but it started again yesterday. 

Today I typed 'gnome-panel' in synaptic and reinstalled everything that was green. That did the trick for me. Let's hope it stays this way...

---

### Post by PTo on 2009-11-08
This morning it happened again... I reinstalled gnome-applets and did a reboot, but still hanging. Then I entered 

pkill gnome-panel

in the terminal. Now its working again. Does anybody have a more durable solution?

---

### Post by TomG on 2009-11-08
Have same problem. Windows List applet does not always respond.
Seems only occur with Metacity in my case. Switching to Compiz workarounds the problem but I would prefer not use Compiz.

---

### Post by w0lv3n on 2009-11-08
I have had a similar problem in that gnome-panel has not started at all after upgrading to Karmic.

Also Conky was no longer loading. Thinking about this I loaded the Startup Programs configuration and removed all entries of both conky and gnome-panel from the list. After a restart I then ran both programs via terminal, opened the startup config, added both to the list then enabled the "auto remember" function and clicked the "remember these programs" button. After closing everything and restarting I have had no issues!

Seems long winded but this is just what I had done at work, hadnt even searched for a solution on the forums.

Hope it works for you, let me know how you go.

---

### Post by Steve Roscio on 2009-11-09
Thanx [w0lv3n]("http://ubuntuforums.org/member.php?u=805795"),

I think I did what you suggested but it did not work for me.

I was able to reproduce the hang again by going into Panel Properties and changing the icon size.  As soon as I click up (or down) on the size arrows, the panel hangs.

- Steve

---

### Post by ode on 2009-11-10
gnome-panel is pushing my cpu to 100% and taking my memory.

I filed a bug:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/479826](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/479826)

I'm also having the message surfincrow is getting when logging out.

Contribute/subscribe to the bug if you can.

I tried reinstalling all the panel packages and killing the panel but the problem is still there.
I also tried switching to compiz and it doesn't kill the problem.

Thanks

---

### Post by Steve Roscio on 2009-11-10
Hi Ode -

In my case, the panel just becomes non-responsive.  CPU and memory do not increase.  I can reproduce it by going to panel properties, and increasing the icon size.  As soon as I click the little size arrow, it hangs.  If I kill my X-server and log back in, then the new panel behaves OK.  However the original gnome-panel is still in my process list, stuck there (sleeping).  A SIGHUP kills it.

Regardless, I subscribed to your bug.  They do seem related.

Thanx,
- Steve

---

### Post by joohaan on 2009-12-02
I'm stuck with the same problem. After every login panel is non-responsive and I can only get out of this with following commands:

> rm -r ~/.gconf/apps/panel
gnome-session-save –kill

The first one resets the panel configuration and the second command sends me back to the login screen. After this login everything works again till the next reboot.

I'm pretty sure there must be a solution for this annoying problem. Hopefully somebody from this resourceful Ubuntu community can provide one.

Many thanks!

---

### Post by spencerg on 2009-12-10
I have a similar problem......... on reboot the panel hangs.  The applications, places,system menus show but the rest of the icons don't populate.  The panel is non responsive.

When I kill the gnome-panel process from a terminal session it respawns and the panel comes back ok.

I am running 9.10 AMD-64 and GNOME 2.28.1

---

### Post by Steve Roscio on 2009-12-15
(bump)
Latest round of patches, including some for gnome, yet problem still occurs.

---

### Post by UbuntuNerd on 2009-12-15
> **joohaan said:**
> I'm stuck with the same problem. After every login panel is non-responsive and I can only get out of this with following commands:



The first one resets the panel configuration and the second command sends me back to the login screen. After this login everything works again till the next reboot.

I'm pretty sure there must be a solution for this annoying problem. Hopefully somebody from this resourceful Ubuntu community can provide one.

Many thanks!
instead of this code try this one, you shouldn't have to log out and back in. It should reset your panels automatically right then and there:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```
let me know if it helps

---

### Post by joohaan on 2009-12-20
Thanks a lot, UbuntuNerd, your code worked like a charm.

After doing some research on the net I was even able to make this into a script restoring the backup of my panel settings.

I'll explain quickly. 

First create a backup of your panel settings:

```
gconftool-2 --dump /apps/panel > ~/Settings/panel_settings
```

Then to create the script, you just open a terminal and type:

```
gedit restorepanel.sh
```

This will open gedit with a blank file named restorepanel.sh. In the file, type the following and save:

```
#!/bin/sh
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
gconftool-2 --load ~/Settings/panel_settings
```

Next, run this command to make the file executable:

```
chmod 777 restorepanel.sh
```

Now, to run the script, type this:

```
./restorepanel.sh
```

Maybe there is someone out there who finds this useful.

---

