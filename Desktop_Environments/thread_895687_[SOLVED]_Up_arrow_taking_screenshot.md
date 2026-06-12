---
title: "[SOLVED] Up arrow taking screenshot"
date: 2008-08-20
forum: Desktop Environments
---

### Post by RicJD on 2008-08-20
Hi Guys

Recently my keyboard has started acting straingly.  When i press the up arrow it takes a screen shot.  Also the down key don't seem to work.  Some of the media keys which used to work aren't working any more.  Below is the set up of my /etc/X11/xorg.conf:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

```

The keyboard i'm using is a logitech s510.

If anyone has any ideas or help it would be greatly appreciated.

Thanks

Rick

---

### Post by Potatoj316 on 2008-08-20
have you looked in 
System->Prefrences->Keyboard shortcuts?

---

### Post by RicJD on 2008-08-20
Just have now, and it's set to "Print" which is correct.  But to see if anyelse was set to "Up Arrow" I set some top use the up arrow and got:

The shortcut "Print" is already used for:
 "Take a screenshot"

So it seems that for some reason Ubuntu has my arrow keys set as something else.

My down is Super R
My left is ISO Level 3 shift
And my right is "0x72"

any more ideas would be helpful!

---

### Post by RicJD on 2008-08-20
And if any one is interest, the print key is "Delete"  If fact apart for the numbers on the number pad, all the keys on the right hand side of my keyboard are messed up!

Getting really confused now.

---

### Post by Potatoj316 on 2008-08-20
maybe its your keyboard?  Is it new? Has it worked before?  does it work on windows? (if you dont have windows then it doesnt really matter)

---

### Post by RicJD on 2008-08-20
Ok wierdness ahoy!

unplugged it, tried it in my laptop work fine.  Pluged back into my computer.  Now works fine!! mayve been a lose connection.  Will monitor it and see how we go...

Thanks for your help!

---

### Post by vahnx on 2008-10-12
Not solved. I'm using Sabayon and same is happening to me. It was fine earlier.

---

### Post by engineer on 2008-10-27
same here!
i'm using the intrepid beta on a dell m1330 and noticed this problem today. but that doesn't necessarily mean that the problem is here since today.

it's the same for the built-in and external keyboards.
the shortcuts in the gnome settings are set correctly.

---

### Post by PeteJ on 2008-10-29
Solved again?

See my note here:  [http://ubuntuforums.org/showpost.php?p=6061199&postcount=5](http://ubuntuforums.org/showpost.php?p=6061199&postcount=5)

Bottom line:  on the server, System, Preferences, Keyboard Shortcuts, under the Desktop section, Take a screenshot--it had just "Print", I held the Ctrl key and tapped the PrtSc/SysRq key, which changed the Take a screenshot value to Ctrl+Print, and now ALL the nav keys work fine!

---

### Post by engineer on 2008-10-30
for me it disappeared after rebooting. i can't tell why, i didn't install any updates in between. at least that's what i think

---

### Post by britton on 2008-11-03
Brilliant. I had the same issues, fixed to normal after using the above.

---

### Post by daqron on 2009-02-06
> **PeteJ said:**
> Solved again?
System, Preferences, Keyboard Shortcuts, under the Desktop section, Take a screenshot--it had just "Print", I held the Ctrl key and tapped the PrtSc/SysRq key, which changed the Take a screenshot value to Ctrl+Print, and now ALL the nav keys work fine!
Cheers, this worked for me (Ubuntu 8.10 on a Dell c600).

---

### Post by Francewhoa on 2009-07-17
Another way of taking screenshot is with Shutter. Read more at [http://ubuntuforums.org/showthread.php?p=7629179#post7629179](http://ubuntuforums.org/showthread.php?p=7629179#post7629179)

---

### Post by Rytron on 2011-05-15
The odd time this weird activity of the **up arrow button** taking screen shots and the **Print Screen** button not working (even though Print Screen is set to take screen shots in my Keyboard Shortcut setup) occurs. A reboot usually fixes it. I am using Ubuntu 10.10 and presume this is the fault of the OS rather than my old PS2 keyboard.

---

### Post by gmbutler on 2012-04-08
As I am typing this the problem is alive and well. The above methods work only every now and then, but it reverts back to the problem after every boot. I have changed the keyboards from USA to some other generic keyboards and back, remapped the shortcuts, etc, and nothing seems to make it stick. I did all the steps as root, so it should stick, but for me this remains unsolved. ](*,)

I am on Natty, using the Microsoft Natural Multimedia 1.0A Keyboard. None of my extended and media keys have ever worked, even after following numerous forum posts on the matter. However, I doubt that it has relevance on this issue.

Any more ideas?

---

