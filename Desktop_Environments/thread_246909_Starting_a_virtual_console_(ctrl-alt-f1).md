---
title: "Starting a virtual console (ctrl-alt-f1)"
date: 2006-08-29
forum: Desktop Environments
---

### Post by bugnotme on 2006-08-29
On other Linux systems I have, pressing ctrl-alt-f1 drops me to a terminal. What do I have to do in inittab to do this in Ubuntu?

---

### Post by hopstah on 2006-08-30
that should do it for you.
edit:  i mean that ctrl-alt-f1 to f6

---

### Post by danderson3 on 2006-08-30
> **bugnotme said:**
> On other Linux systems I have, pressing ctrl-alt-f1 drops me to a terminal. What do I have to do in inittab to do this in Ubuntu?

This does not work for me either...  I have searched but found no
solution.

David

---

### Post by Atomic Dog on 2006-08-30
Well ctrl-alt-f1 worked for me.  But seeing I'm a point & clicker and not versed well in prompt commands I couldn't figure out how to bring the Gnome GUI back.

Anybody wanna clue me in? :)

---

### Post by max_dingemans on 2006-08-30
ctrl+alt+f7 should do the trick.

---

### Post by bugnotme on 2006-08-30
> **max_dingemans said:**
> ctrl+alt+f7 should do the trick.

I want to switch to a text terminal on another virtual console, not to get back to the X terminal.

---

### Post by hopstah on 2006-08-30
> **bugnotme said:**
> I want to switch to a text terminal on another virtual console, not to get back to the X terminal.
max's comment was in reference to how to get gnome back after going to a virtual terminal.  i have no idea why ctrl+alt+f1 wouldn't get you to a terminal.  the only thing i could think of is that maybe you have a non-english keyboard layout, and your alt key is actually mapped to an alt-gr function instead of a standard alt.

---

### Post by bugnotme on 2006-08-30
> **hopstah said:**
> max's comment was in reference to how to get gnome back after going to a virtual terminal. 

Oops. Sorry, my fault. I didn't read the previous comment properly.

>  i have no idea why ctrl+alt+f1 wouldn't get you to a terminal.  the only thing i could think of is that maybe you have a non-english keyboard layout, and your alt key is actually mapped to an alt-gr function instead of a standard alt.

I have the standard US keyboard layout. I guess I should elaborate more. When I press ctrl-alt-f1 it does do something, it brings me to a black screen (no terminal, no text, nothing). My guess is the terminal is not started on that virtual console (maybe the runlevel is not correct). I'm using NVidia closed source drivers.

---

### Post by danderson3 on 2006-08-30
I have the exact same problem.  I use Matrox drivers and a 
std American keyboard.

-d

---

### Post by xtknight on 2006-08-30
Is tty1 started?

ps ax | grep getty

---

### Post by danderson3 on 2006-08-30
yes, the gettys are there...

-d

---

### Post by bugnotme on 2006-08-30
Here is my inittab if someone can find something wrong


# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
id:2:initdefault:

# Boot-time system configuration/initialization script.
# This is run first except when booting in emergency (-b) mode.
si::sysinit:/etc/init.d/rcS

# What to do in single-user mode.
~~:S:wait:/sbin/sulogin

# /etc/init.d executes the S and K scripts upon change
# of runlevel.
#
# Runlevel 0 is halt.
# Runlevel 1 is single-user.
# Runlevels 2-5 are multi-user.
# Runlevel 6 is reboot.

l0:0:wait:/etc/init.d/rc 0
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
l3:3:wait:/etc/init.d/rc 3
l4:4:wait:/etc/init.d/rc 4
l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/rc 6
# Normally not reached, but fallthrough in case of emergency.
z6:6:respawn:/sbin/sulogin

# What to do when CTRL-ALT-DEL is pressed.
ca:12345:ctrlaltdel:/sbin/shutdown -t1 -a -r now

# Action on special keypress (ALT-UpArrow).
#kb::kbrequest:/bin/echo "Keyboard Request--edit /etc/inittab to let this work."
# What to do when the power fails/returns.
pf::powerwait:/etc/init.d/powerfail start
pn::powerfailnow:/etc/init.d/powerfail now
po::powerokwait:/etc/init.d/powerfail stop

# /sbin/getty invocations for the runlevels.
#
# The "id" field MUST be the same as the last
# characters of the device (after "tty").
#
# Format:
#  <id>:<runlevels>:<action>:<process>
#
# Note that on most Debian systems tty7 is used by the X Window System,
# so if you want to add more getty's go ahead but skip tty7 if you run X.
#
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

# Example how to put a getty on a serial line (for a terminal)
#
#T0:23:respawn:/sbin/getty -L ttyS0 9600 vt100
#T1:23:respawn:/sbin/getty -L ttyS1 9600 vt100

# Example how to put a getty on a modem line.
#
#T3:23:respawn:/sbin/mgetty -x0 -s 57600 ttyS3

---

### Post by Atomic Dog on 2006-08-30
> **max_dingemans said:**
> ctrl+alt+f7 should do the trick.

Thanks. :D

---

### Post by Alabaster on 2007-01-21
I have this same problem.

I know all the keys are working, the gettys are there, and when I crtl-alt-backspace GNOME restarts, but I can´t exit gnome into a virtual terminal using ctrl-alt-F1 (or F2 or F3...)

xev shows that when I press ctrl-alt-f1, it sees it as keycode 245, as shown here:

```
KeyPress event, serial 29, synthetic NO, window 0x2600001,
    root 0x5c, subw 0x0, time 1200824634, (405,-51), root:(542,535),
    state 0x14, keycode 245 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x2600001,
    root 0x5c, subw 0x0, time 1200824634, (405,-51), root:(542,535),
    state 0x14, keycode 245 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

The ¨NoSymbol¨ remark looks ominious... what does this mean and how can I fix it???

---

### Post by melusyne on 2007-01-24
I have the same problem since i upgraded from Dapper to Edgy :
I'm still able to restart X with <Ctrl><Alt><Del>, but not any more to switch to any tty terminal.

there are 3 of them active, but i don't get any response to the switch command.
root      4086     1  0 15:58 tty1     00:00:00 /sbin/getty 38400 tty1
root      4087     1  0 15:58 tty2     00:00:00 /sbin/getty 38400 tty2
root      4088     1  0 15:58 tty3     00:00:00 /sbin/getty 38400 tty3

I don't think it comes from the keyboard layout, since <Ctrl><Alt><Del> or <Ctrl><F2> work,
There is no disabled option related to this in my xorg.conf (saw something related in old breathy thread) 

Is there any way to get back to a terminal session once GDM + X + Gnome is launched ?
when i kill x i just come back to the session log-in windows which doesn't allow a terminal login...
when i kill GDM it just freezes...

Edit : just stopping GDM works way better than killing it : sudo /etc/init.d/gdm stop
then i can log in a terminal mode, and achieve my Nvidia driver installation (which was the reason i needed to get rid of x)

BUT the driver doesn't works out-of-the-box (ok, that's another story), and Ctrl Alt F1-6 don't work either !

Thanks for any hints!

(Dell Inspiron 9400, Ubuntu Edgy 6.10, Kernel 2.6.17-10.34 generic )

---

### Post by melusyne on 2007-01-24
well, actually i DO have a problem with my keyboard layout, (but only for <alt gr> things or a few special characters)
so it might come from it that <Ctrl><Alt><Fx> don't work...

I'm looking in that direction...

---

### Post by tonyr1988 on 2007-01-25
For me, editing /boot/grub/menu.lst did the trick. I added " vga=792" to the end of the kernel line (after splash) and it now works perfectly.

I'm not sure why it works for me or if it'll work for you - I had gotten it from someone else on the forums, so all credit goes to him / her. :)

---

### Post by melusyne on 2007-01-25
Well, after all it was a "simple" keyboard lay-out problem for me :
after struggling a few hours against gnome's configuration (there are minimal 2 different config ways in there, one of them outdated but still accessible) , X' configuration (through xorg.conf), and the general config (what you get in Terminal mode), i just saw that it was just Latin9 and not Latin09 that i had to use as variant... stupid !

with good keyboard configuration everything works well now.

I suppose that your trick corrects a display problem once you're running the terminal mode, mine was just key-combination not acknowledge !

Bye, i'm done with this !

---

### Post by gaillard on 2007-01-25
> **tonyr1988 said:**
> For me, editing /boot/grub/menu.lst did the trick. I added " vga=792" to the end of the kernel line (after splash) and it now works perfectly.

I'm not sure why it works for me or if it'll work for you - I had gotten it from someone else on the forums, so all credit goes to him / her. :)

Does anyone know if this is the correct way to get rid of this bug or to do what tselliot suggest in his how to at the bottom of the page.  He says to remove the word splash.  What is this vga line statement do?

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

Thanks for the help!

---

### Post by Foxmike on 2007-02-12
> **gaillard said:**
> Does anyone know if this is the correct way to get rid of this bug or to do what tselliot suggest in his how to at the bottom of the page.  He says to remove the word splash.  What is this vga line statement do?

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

Thanks for the help!
> Does anyone know if this is the correct way to get rid of this bug or to do what tselliot suggest in his how to at the bottom of the page. He says to remove the word splash. What is this vga line statement do?


The VGA statement "tells" to the virtual console to use VGA resolution instead of default 640x480 resolution when using the console.  I am not sure but that bug seems to have something to do with video card drivers and usplash.  Can someone confirm?

Thank you!

---

### Post by addisor on 2007-02-14
Got this problem myself and have tried those suggestions, anyone got a good fix?

---

### Post by Zamber on 2007-02-21
Got it too ;/ Maybe it's something with GNOME. Gotta google more and try, try, try...
From gdm it works well, GNOME - no change.

---

### Post by dom on 2007-02-25
I'm not sure if I have the same problem.....

I have a Dell Inspiron 9400, the graphics card is a ATI Radeon Mobility X1400, 256MB. 

Note that this bloody thing is actually a 128 megabyte card that can take some system memory to be kinda pseudo 256mb! 

Anyway, I have the 1440x900 working with the fglrx driver used in the xorg.conf.

I have been using gnome fine.

My problem is that when I try to use CTRL-ALT-Fx to change to a virtual console, or check log output etc, I don't see anything nice, just a bad screen. Looks like resolution issues.

I am going to try the vga boot option...

using option "vga=792" on boot works :) 

thanks for the help folks.

---

### Post by medomedo on 2007-03-07
Hi, 

I would like to tell you that I have the same problem. When ctrl-alt-f1 is pressed noting happens (no black screen). I am using Kubuntu Edgy on i855 video card. Using vga=792 did not solve the problem for me. This missing feature is crucial to me because I am using some unstable applications therefore I need the terminal window.

---

