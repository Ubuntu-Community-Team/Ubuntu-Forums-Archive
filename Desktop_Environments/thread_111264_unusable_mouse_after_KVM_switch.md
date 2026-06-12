---
title: "unusable mouse after KVM switch"
date: 2006-01-01
forum: Desktop Environments
---

### Post by ChrisC on 2006-01-01
I'm running Ubuntu 5.10 on my new machine and Windows on my old machine, and have them both connect to the same keyboard, video and mouse via a 2-way KVM switch.

I've found that if I boot the Ubuntu machine with the KVM set to it, then the mouse works fine.  However, If I KVM-switch away to the Windows machine and then switch back, the mouse is then no longer usable.  If I move it, the onscreen pointer jumps around, context menus open, and the mouse is totally unusable.  I quickly became familiar with the Alt-F1 keyboard shortcut to open the Gnome menu :)

Can anyone suggest some way to fix this?  Someone on IRC suggested looking into "gpm" and "repeater" mode, but I think that has something to do with capturing mouse data ... if that's the solution, can you explain further?

If not permanent fix, is there a command I can run to "resync" the mouse after I switch back to the Ubuntu machine?  I tried logging out and back in (which I assume restarts X) and that didn't fix it.  Right now my only recourse is reboot the machine.

---

### Post by Mike_N on 2006-01-01
This might be of no use but... I've heard of problems with KVM's that if you have a USB mouse and have to use an adaptor to plug it into a PS2 KFM port, it might have problems... So... Are you using an adaptor to plug your mouse into the KVM?

If so, you might need a new mouse or KVM that is native to one another...

---

### Post by DaMasta on 2006-01-01
I always had this problem too. If you switch to a different screen (ctrl-alt-F2 or F3, etc) then switch back, it should work fine.

---

### Post by ChrisC on 2006-01-01
... and I should have searched this site before posting, not right after.

I searched for "kvm" which didn't get me anywhere, but searching for "kvm mouse" led me to [this post]("http://www.ubuntuforums.org/showpost.php?p=607292&postcount=4") that says if you just unplug/replug the mouse it works again, and I've confirmed that.

OK, awesome, I've got a workaround.  Any permanent fix ideas?  Or a software workaround? (to resync the mouse)

---

### Post by ChrisC on 2006-01-01
Wow, replies already!

I am indeed using a PS/2 KVM switch, and my favored mouse is USB with an adapter.  The old machine is PS/2 only, as is the keyboard.  I guess I'll look for adapters ...

The Ctrl-Alt-F1/F2/... switching trick did not fix it for me.

---

### Post by ChrisC on 2006-01-02
Any ideas about how to "resync" the mouse without physically replugging it?

---

### Post by lgmdaniel on 2006-01-03
I've got the same problem.. I'll have to have look tonight a try a few things myself. My mouse is a USB into a PS/2 adapter, I have some spare ones laying about but I would rather keep the opti 5 button mouse.

---

### Post by Vernominon on 2006-01-05
Hi. I've had the same problem using a 5 button + wheel USB mouse via a PS/2 adapter and a KVM switch.
The fix i found was to boot up the ubuntu box with the switch turned to another PC. Switch back to login, and i can switch too and fro afterwards with the mouse remaining erratic behaviour free :)

---

### Post by phoenixleo on 2006-01-08
I've had the same problem for some time and the only thing that have fixed it configuration-wise is to:

```
sudo gedit /etc/modules
```

find the line that says psmouse and change to:
```
psmouse proto=bare
```

Then it's no problem, except that the wheel and any middle/extra buttons will cease to function. Now I'm using remote desktop instead...

---

### Post by ChrisC on 2006-01-09
[QUOTE=Vernominon]The fix i found was to boot up the ubuntu box with the switch turned to another PC. Switch back to login, and i can switch too and fro afterwards with the mouse remaining erratic behaviour free :)[/QUOTE]

Didn't work for me -- at first it worked but only one scroll wheel direction, and then after a KVM switch the mouse was jumpy again.

As for the proto=bare suggestion, I do want the scroll wheel to work.

So, I'm still re-plugging the mouse every time I do a KVM switch (and minimizing KVM switch events by using VNC).  Any other ideas for a software reset method, like the console switching method (Ctrl-Alt-F2), but not that? :)

---

### Post by jaranguren on 2006-01-12
I have the same problem and my workaround is to unload and load psmouse module.

```
sudo rmmod psmouse;sudo modprobe psmouse
```

This makes my mouse fully functional including wheel.

P.S. I saved this in a script called fixmouse so I just call fixmouse everytime I switch.

---

### Post by Soda Ant on 2006-01-24
I fixed this on my system by changing my mouse device in /etc/X11/xorg.conf from

/dev/input/mouse0

to

/dev/input/mice

---

### Post by ChrisC on 2006-02-04
[QUOTE=jaranguren]sudo rmmod psmouse;sudo modprobe psmouse[/QUOTE]

YES!  That's exactly what I needed.

In order for the script to Just Work, and be easy enough to use so that the Significant Other could use it, I had to do the following things:

1.  Put the above into a script called "fixmouse".
2.  Run "sudo visudo" and add the following lines
```
# allow mouse reset; used after doing a KVM switch
chris   ALL = NOPASSWD: /sbin/rmmod psmouse
chris   ALL = NOPASSWD: /sbin/modprobe psmouse
```
3.  Test it by running /path/to/script/fixmouse .   You should NOT be prompted for the sudo/root password.
4.  Edit the application menu and add a "FixMouse" item at the bottom that calls fixmouse.

Now, after switching the KVM back, I can hit Alt-F1 to pull up the Applications menu, arrow up to FixMouse, and hit enter to run the script and fix the mouse.

---

### Post by nix4me on 2006-02-04
Your issues with erratic mouse is a flaw in your kvm switch.  I had the same problem a couple of years ago.  I had a gwc kvm and a belkin and they both exhibited this behavior.  I finally did some research and I bought an IOGear kvm and all has been well for a couple years.

nix4me

---

### Post by sysko on 2006-03-05
I had my load on this one too. I read your post earlier today and I wanted to post in this thread what worked for me.

My PS/2 mouse (A Logitec USB mouse converted to PS/2 with an adapter) wasn't resynching properly with my 'Mini PS/2 KVM switch'  once I switched from computer B (Windows) back to Computer A (Ubuntu Breezy, with psmouse loaded as a module). 

At first I was running the *'rmmod psmouse; modprobe psmouse'* command, evertime I was switching... how painfull!

After reading tons of different posts about the topic I started to play with the parameters for the psmouse module. When I loaded the psmouse module with proto=bare ( via the file /etc/modules at boot time) my mouse was able to resync properly when switching. Helas there was a cost, the lost of scroll wheel and also the fact that the mouse was slower to move on the screen. :cry:  

From there I experienced with the other protocols although I did not know what they were. I eventualy came across 'psmouse proto=exps' and It was a GREEN, everything was fully operationnal. But still... I kept trying with other protocols just for the heck of It and I found-out that the proto=imps was also working very well.

Here is what I did:

1)     *sudo gedit /etc/modules*
       modify the line
          *psmouse* 

       to reflect 
          **psmouse proto=imps2**

**Save** file and **Exit** the text editor.

2)     *sudo gedit /etc/X11/xorg.conf*
          modify the protocol option under 'InputDevice'

   Section "InputDevice"
	    Identifier	"Configured Mouse"
	    Driver		"mouse"
	   Option		"CorePointer"
	   Option		"Device"		"/dev/input/mice"
	   **Option		"Protocol"		"ImPS/2"**
	   Option		"Emulate3Buttons"	"true"
	  ** Option		"ZAxisMapping"		"4 5"**
   EndSection

(but I beleive it was like that, above, by default under Breezy 5.10. ... I can't remember since I played with that file a bit.)

**Save** file and **Exit** the text editor.

3)   **Reboot** the computer.

4)   Test scrolling, middle mouse button and KVM switching. Worked for me.

Thanks for the insight folks.

---

### Post by AdrianTM on 2007-07-17
Same problem here, it seems like 

```
 psmouse proto=imps
```

saves the day. I will add that in **/etc/modprobe.d/options** (I think it can be added in kernel line too)
```

#Fix mouse for KVM
options psmouse proto=imps

```

Thanks guys for the solution.

---

