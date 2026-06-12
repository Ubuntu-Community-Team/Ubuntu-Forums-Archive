---
title: "system keys"
date: 2008-05-19
forum: Desktop Environments
---

### Post by phoenix5002 on 2008-05-19
Sometimes the system keyboard shortcuts don't work when certain applications are active.  Particularly games.
This is a big issue for me, not only does it not allow me to minimize the game, or change the volume while playing, it sometimes causes me to have to restart X, or even do a hard restart.
An example is the game Cube2.  Sometimes it starts, but it for some reason fails to recognize keyboard input, so I can look around with my mouse and I can shoot, but I can't move, and worst of all, I can't exit the game!!  because I can't press escape so I can't bring up the menu to leave the game, and my system keys don't work, so even though I have binded the "system monitor" to ctrl+alt+delete, I can't bring that up to close the game, so I'm stuck in the game :(  I think this is ridiculous, my system is perfectly responsive and I'm getting 60+fps in game its running fine, but I get stuck inside a game with no way out.
In windows even when an application is really messed up or freezes ctrl+alt+delete always seems to bring up the task manager, I don't see why I can't do this in Ubuntu.

It would just be nice for my system keys to always work, so if I'm playing Tremulous for example, and I hear the little noise notifying me that someone sent me a chat message, I can actually minimize and read it without having to close the entire game and then start it up again when I'm done.

NOTE: alt+f4 doesn't work with these applications either.
Sometimes ctrl+alt+backspace works, and sometimes it does not.  Wine sometimes crashes for me and not even that works, I have to do a hard restart.

**EDIT:** in some games like tremulous, even though I run it in a window I can't get off the window, so in order to respond to that chat message someone sends me, (even though I can read it because the game is in a window) I still have to close the entire game just to activate the other window because alt+tab doesn't work to respond to the message.

---

### Post by gnivler on 2008-05-19
> **phoenix5002 said:**
> Sometimes the system keyboard shortcuts don't work when certain applications are active.  Particularly games.
This is a big issue for me, not only does it not allow me to minimize the game, or change the volume while playing, it sometimes causes me to have to restart X, or even do a hard restart.
An example is the game Cube2.  Sometimes it starts, but it for some reason fails to recognize keyboard input, so I can look around with my mouse and I can shoot, but I can't move, and worst of all, I can't exit the game!!  because I can't press escape so I can't bring up the menu to leave the game, and my system keys don't work, so even though I have binded the "system monitor" to ctrl+alt+delete, I can't bring that up to close the game, so I'm stuck in the game :(  I think this is ridiculous, my system is perfectly responsive and I'm getting 60+fps in game its running fine, but I get stuck inside a game with no way out.
In windows even when an application is really messed up or freezes ctrl+alt+delete always seems to bring up the task manager, I don't see why I can't do this in Ubuntu.

It would just be nice for my system keys to always work, so if I'm playing Tremulous for example, and I hear the little noise notifying me that someone sent me a chat message, I can actually minimize and read it without having to close the entire game and then start it up again when I'm done.

NOTE: alt+f4 doesn't work with these applications either.
Sometimes ctrl+alt+backspace works, and sometimes it does not.  Wine sometimes crashes for me and not even that works, I have to do a hard restart.

**EDIT:** in some games like tremulous, even though I run it in a window I can't get off the window, so in order to respond to that chat message someone sends me, (even though I can read it because the game is in a window) I still have to close the entire game just to activate the other window because alt+tab doesn't work to respond to the message.

Are these all games you are playing with wine?  Or native linux apps?

---

### Post by phoenix5002 on 2008-05-20
they are native linux apps.
I mentioned that wine does it sometimes too, I can cut wine some slack, but I'd really like the native apps to work.

---

### Post by gnivler on 2008-05-20
> **phoenix5002 said:**
> they are native linux apps.
I mentioned that wine does it sometimes too, I can cut wine some slack, but I'd really like the native apps to work.

Hmmm.. what version is your kernel and which release are you running?  On a wild guess maybe it is related to the keyboard driver - if you lsmod | grep -i keyboard does it show HID or USB (or ps2?).  Also in your /etc/X11/xorg.conf is there anything specific for the keyboard defined or just InputDevice    "Generic Keyboard" "CoreKeyboard"

Going to try these games myself and see if I can replicate the issue but that could take some time.

---

### Post by phoenix5002 on 2008-05-20
**lsmod | grep -i keyboard**
gives me absolutely no output...

and I have this for the keyboard input device in my xorg.conf:
[b]Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection[/b]

---

### Post by gnivler on 2008-05-20
> **phoenix5002 said:**
> **lsmod | grep -i keyboard**
gives me absolutely no output...

and I have this for the keyboard input device in my xorg.conf:
[b]Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection[/b]

Woops sorry my mistake, I was doing and typing different things - I did dmesg | grep -i keyboard.  As for lsmod, I did lsmod | grep -i hid since I've got a HID driver (not sure on the proper technical terms here) for my particular keyboard and I got 3 entries:

usbhid                 35168  0 
hid                    44992  1 usbhid
usbcore               169904  5 lmpcm_usb,usbhid,ehci_hcd,ohci_hcd

The entry in my xorg.conf is identical to yours.  Are you running Hardy?  Was it an upgrade from a previous release or a fresh install?  Just probing the topic really to see if anything jumps out as an issue to look at...  I am good at troubleshooting but this is over my pay grade :)

edit:
Just occured to me maybe compiz is interfering, too.  Have you tried running metacity --replace & in a terminal before gaming?  Maybe it will have more luck cooperating with the games.  I have heard wine doesn't like compiz very much either (or pulse audio).

---

### Post by VMC on 2008-05-20
Have you check Preferences > Keyboard > Layout. Or anything in there that looks out of the ordinary? Like under General repeat keys, what sliding value?

---

### Post by phoenix5002 on 2008-05-20
Here is what my settings look like...

System > preferences > Keyboard:

**General**  tab
key presses repeat when key is held:  checked
Delay:  about 25% from the left
Speed:  about 20% from the left

Cursor blinks in text fields: checked
Speed:  about 60% from the left


**Layouts**
Keyboard model:  Generic 105-key (intl) PC
layout:  USA   *<--the button under Default for this is unchecked... could that be the problem?*

under that, "separate layout for each window" is checked  *<-- This could be the problem as well*

**Accessibility**
everything is unchecked

**mouse keys**
allow to control the pointer using the keyboard:  unchecked

**Typing break**
all unchecked

---

### Post by VMC on 2008-05-20
No, that's exactly how mine is. 
If its only on games and it doesn't happen anywhere else, you might want to investigate the sames.
 Are their any games that this doesn't happen?

---

### Post by phoenix5002 on 2008-05-21
Yes, It does not occur on UrbanTerror, and wine games.  it sometimes occurs with wine games though, but that only happens when wine locks up.  When it's running correctly it works.

I'm sure it's the games fault, it seems to take control away from my system.  But that's the whole point of my post, I want my system keys to work regardless of what applications are running.  Maybe I should have stated it this way from the beginning.

---

