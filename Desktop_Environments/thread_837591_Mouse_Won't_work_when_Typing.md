---
title: "Mouse Won't work when Typing"
date: 2008-06-22
forum: Desktop Environments
---

### Post by jose158 on 2008-06-22
Like the title says,  the cursor won't move when i'm typing (e.g arrow keys, letters). it will freeze and move when im done typing.  it gets annoying when im trying to type and move the cursor at the same time.  Any ideas would be appreciated.

---

### Post by spupy on 2008-06-22
There is a program that does exactly that; it is very useful for touchpads on laptops. The programs is called **syndaemon**. See if it is running.

---

### Post by issih on 2008-06-22
Taking a bit of a stab in the dark, but do you have a process called syndaemon running?

That program is specifically designed to do what you say is happening, as it is intended to avoid unintentional mouse input from the touchpad whilst typing on a laptop.

doing "ps -eaf | grep syn" in a terminal should let you see if you have syndaemon running.

I doubt it is that unless you are using a laptop, and I'd have thought you would probably have to have enabled it at some point, but its worth checking.

Hope that helps

---

### Post by issih on 2008-06-22
Heh, 41 minutes with no response then bang 2 at once, we are like buses round here :)

---

### Post by overcyn on 2008-06-22
Jumping in here. Ive got the same problem. how do i turn syndaemon off/keep it from turning on?

---

### Post by issih on 2008-06-23
To stop it starting at boot time go to:

System->Administration->System Monitor

Then go to the processes tab, select syndaemon and end it.

To stop it starting at boot, go to:

System->Preferences->Sessions

Find the startup entry that is launching syndaemon, and remove it.

Hope that helps

---

### Post by jose158 on 2008-06-23
> **spupy said:**
> There is a program that does exactly that; it is very useful for touchpads on laptops. The programs is called **syndaemon**. See if it is running.
No I don't have that program... I don't even have a laptop:(. I think it is a big in Gnome or something....

---

### Post by jose158 on 2008-06-23
I think it might be something I did in my xorg.conf file. I was trying to get a Wiimote to move my cursor and I added: ```
Section "InputDevice"
        Identifier      "Wiimote"
        Driver          "evdev"
        Option          "Name"          "Nintendo Wiimote"
EndSection
```After the last InputDevice section
and ```
  InputDevice     "Wiimote" "AlwaysCore"
```in the serverLayout section.
Would that be causing the problem?

---

### Post by spupy on 2008-06-23
Can you try backing up your current Xorg.conf and do a reconfigure?
```
dpkg-reconfigure xserver-xorg
```
was the command, i think.

---

### Post by jose158 on 2008-06-23
> **spupy said:**
> Can you try backing up your current Xorg.conf and do a reconfigure?
```
dpkg-reconfigure xserver-xorg
```was the command, i think.
No, It still does it.

---

### Post by jose158 on 2008-06-29
Anybody?:-\"

---

### Post by jose158 on 2008-07-03
*whistles Jeopardy song*:-\"

---

### Post by jose158 on 2008-07-09
sorry, but: bump

---

### Post by spupy on 2008-07-09
If you have the Ubuntu LiveCD, try with it? Maybe with a "virgin" xorg.conf you wont have the problem.

---

### Post by jose158 on 2008-07-09
ok I'll try it

---

### Post by jose158 on 2008-07-09
Yeah, the mouse works like it normally would in the Live CD

---

### Post by spupy on 2008-07-10
Then backup your current xorg.conf and replace the "Input Device" section for the mouse with the one from the live cd.  But only the section for the mouse.

---

### Post by jose158 on 2008-07-10
> **spupy said:**
> Then backup your current xorg.conf and replace the "Input Device" section for the mouse with the one from the live cd.  But only the section for the mouse.
The "Input Device" section for the mouse is exactly the same for the live cd and for the normal one. What do i do?

---

### Post by spupy on 2008-07-10
> **jose158 said:**
> The "Input Device" section for the mouse is exactly the same for the live cd and for the normal one. What do i do?

[http://pastebin.com/](http://pastebin.com/)

Paste both xorg.conf there and post the two links.

---

### Post by jose158 on 2008-07-11
> **spupy said:**
> [http://pastebin.com/](http://pastebin.com/)

Paste both xorg.conf there and post the two links.
my current xorg.conf: [http://pastebin.com/m595e51af](http://pastebin.com/m595e51af)

live cd: [URL="http://pastebin.com/m72372bb2"]http://pastebin.com/m72372bb2
[/URL]

---

### Post by spupy on 2008-07-11
[COLOR="Red"]BACKUP YOU XORG.CONF[/COLOR]
and replace the ServerLayout section with this one:

```
Section "ServerLayout"
	Identifier      "Default Layout"
	screen 0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard" "CoreKeyboard"
	InputDevice	"Configured Mouse" "CorePointer"
#	InputDevice     "Wiimote" "AlwaysCore"
EndSection
```

If it works like that, uncomment the Wiimote line and try again.

---

### Post by jose158 on 2008-07-11
I did that and rebooted and it still does it!

---

### Post by spupy on 2008-07-12
> **jose158 said:**
> I did that and rebooted and it still does it!

If the LiveCD xorg.conf works, back up your current and replace it with the livecd one?

---

### Post by jose158 on 2008-07-12
> **spupy said:**
> If the LiveCD xorg.conf works, back up your current and replace it with the livecd one?
Nope:(. It still does it...

Obviously it's not the xorg.conf...

---

### Post by spupy on 2008-07-12
> **jose158 said:**
> Nope:(. It still does it...

Obviously it's not the xorg.conf...

That is a step forward! At least we know it's not in xorg.conf. Lets think where to look next.

I guess the mouse still wont work when typing? Could you paste (here or in a pastebin) the output of 
```
ps aux
```

It shows what programs are running and with arguments were they started.

---

### Post by jose158 on 2008-07-12
[http://pastebin.com/f3408bdf1](http://pastebin.com/f3408bdf1)

---

### Post by spupy on 2008-07-12
> **jose158 said:**
> [http://pastebin.com/f3408bdf1](http://pastebin.com/f3408bdf1)

I am sorry to bother you again - could you resize your console before "ps aux", the ends of the lines are trimmed. There is a program running "/usr/sbin/mouse", but I can't see the rest of the line.
Another possible culprit might be hald. As you can see, hald is running "hald-addon-..." for various devices. I for example had problem with hald and my touchpad, so I guess that hald could be a possible reason. If you wish, in the meantime, you can try to stop hald-addon for keyboard:
```
killall hald-addon-keyboard
``` (might require sudo)
BUT! I don't know what will happen when you do that. A (hard) restart might be needed if killing hald doesn't go well.

---

### Post by jose158 on 2008-07-13
> **spupy said:**
> I am sorry to bother you again - could you resize your console before "ps aux", the ends of the lines are trimmed. There is a program running "/usr/sbin/mouse", but I can't see the rest of the line.
Another possible culprit might be hald. As you can see, hald is running "hald-addon-..." for various devices. I for example had problem with hald and my touchpad, so I guess that hald could be a possible reason. If you wish, in the meantime, you can try to stop hald-addon for keyboard:
```
killall hald-addon-keyboard
``` (might require sudo)
BUT! I don't know what will happen when you do that. A (hard) restart might be needed if killing hald doesn't go well.
Oh.. sorry here: [URL="http://pastebin.com/f50897c17"]http://pastebin.com/f50897c17
[/URL]

---

### Post by spupy on 2008-07-13
Well, you have /usr/sbin/mouseemu running:

> Mouseemu is a daemon to emulate mouse buttons on trackpads with only one button.
[...]
It was initially developed for Apple PowerBooks and iBooks...


Do you need this - you said your computer is not a laptop, right?

Try
```
sudo killall mouseemu
```

EDIT: Hehe, see what we have here:
[http://ubuntuforums.org/showthread.php?t=545244](http://ubuntuforums.org/showthread.php?t=545244)
In this case, try:
```
sudo /etc/init.d/mouseemu stop
```

---

### Post by jose158 on 2008-07-13
Yes! finally! it works! thank you!
And to think it was such an easy solution!:lolflag:

---

### Post by spupy on 2008-07-13
> **jose158 said:**
> Yes! finally! it works! thank you!
And to think it was such an easy solution!:lolflag:

I am glad it is working! :D

It's strange though, why would Ubuntu install this if you don't need it. Probably an issue with hardware detection. If you don't need "3mouse button emulation for iBooks" (or whatever mouseemu was doing), you should deinstall mouseemu from synaptic, so it won't start on the next boot.

---

### Post by jose158 on 2008-07-13
yeah ok!

---

