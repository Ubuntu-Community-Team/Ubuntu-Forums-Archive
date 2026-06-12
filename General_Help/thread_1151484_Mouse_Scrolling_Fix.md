---
title: "Mouse Scrolling Fix?"
date: 2009-05-07
forum: General Help
---

### Post by joeyknuccione on 2009-05-07
Has anyone found a way to adjust the number of lines scrolled on a mouse yet?

I have this in my xorg.conf, but nothing seems to change:

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
    Option         "VertScrollDelta" "20"
    Option         "SHMConfig" "true"
EndSection

Why does Ubuntu hate mouse scrolling?

---

### Post by BslBryan on 2009-05-07
Hello, joeyknuccione. :-)

Firefox apparently has a mousewheel setting that overrides any other setting. :-?

So, check [this thread]("http://ubuntuforums.org/showthread.php?t=861858"), and I think you might get it working right. :-)

I hope I've helped.  Keep me posted.  :-)

Best to you, and good luck.

---

### Post by joeyknuccione on 2009-05-07
> **BslBryan said:**
> Hello, joeyknuccione. :-)

Firefox apparently has a mousewheel setting that overrides any other setting. :-?

So, check [this thread]("http://ubuntuforums.org/showthread.php?t=861858"), and I think you might get it working right. :-)

I hope I've helped.  Keep me posted.  :-)

Best to you, and good luck.

'Preciate the tip, but it was a no go.

I guess maybe I can try KDE, but I sure like gnome a whole lot better.

Maybe someone from Gnome will see this thread and realize how disappointing it is to scroll one line a week.

---

### Post by BslBryan on 2009-05-07
Hmm.  Well, here's my xorg.conf, if it helps.  It includes the line that you've entered in yours.

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"VertScrollDelta" "6"
EndSection
```

Mine works very well.  After changing options, you did restart the gdm, right?  Ctrl+Alt+Backspace. 

You probably did, but just making sure. :-)

---

### Post by joeyknuccione on 2009-05-07
> **BslBryan said:**
> Hmm.  Well, here's my xorg.conf, if it helps.  It includes the line that you've entered in yours.

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"VertScrollDelta" "6"
EndSection
```

Mine works very well.  After changing options, you did restart the gdm, right?  Ctrl+Alt+Backspace. 

You probably did, but just making sure. :-)
Yeah, still a no go.

You wouldn't happen to know of a linux distribution that allows mice to be configured do you?

---

### Post by BslBryan on 2009-05-07
This one, I thought. ;-)

If you really are thinking about switching distros over this, I'm quite a big fan of Fedora, myself. :-)

---

### Post by joeyknuccione on 2009-05-07
> **BslBryan said:**
> This one, I thought. ;-)

If you really are thinking about switching distros over this, I'm quite a big fan of Fedora, myself. :-)
I'll give Fedora a try. This mouse scrolling is a deal breaker, and I've spent over a year waiting for ubuntu to fix it. I suppose my priorities are not theirs :)
It's hard trying to convince folks that Linux/Ubuntu is the way to go when it takes a month to scroll through a file or folder.

---

