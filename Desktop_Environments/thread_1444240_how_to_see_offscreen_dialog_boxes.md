---
title: "how to see offscreen dialog boxes?"
date: 2010-04-01
forum: Desktop Environments
---

### Post by gregconquest on 2010-04-01
I'm running Ubuntu Netbook 10.04 Beta 1. In using Thunderbird, the bottom of the options under Edit -- Account Settings -- Server Settings the bottom line I can see is "Local Directory" and then the next line is not showing, nor are any of the other lines down there being shown. So my questions:

1) How do I get to these options? Is there a way to grab the window somewhere other than the top and drag it around? Do I have to change my resolution to be able to see these settings?

2) Is this specific problem for Thunderbird going to be addressed? Or is this a more general problem that will be fixed in the beta?

Thanks,
Greg

UPDATE:
<ALT><F7> moves the window, even off screen.
<ALT><F8> resizes the window.

---

### Post by mcduck on 2010-04-01
1) Just hold down the Alt key and you'll be able to move a window from any point inside the window. (Alt+left click = move, Alt+middle click = resize)

2) No, it's not going to be fixed. A display with a certain resolution will only be able to display certain amount of stuff at once. No software trick can fix that. (of course it would be possible to redesign a program's user interface for small-resolution displays, but that would in most cases result in user interface that wouldn't work well on normal display resolutions any more..)

So no, it's not Thunderbird-specific, but it's not a bug either and it's not going to be fixed. Actually it *can't* be fixed (apart from changing your display to a higher-resolution one, or by rewriting the programs specifically for the netbook use).

---

### Post by gregconquest on 2010-04-01
> **mcduck said:**
> 1) Just hold down the Alt key and you'll be able to move a window from any point inside the window. (Alt+left click = move, Alt+middle click = resize)
Thanks, mduck. That works great.
> 2) No, it's not going to be fixed. A display with a certain resolution will only be able to display certain amount of stuff at once. No software trick can fix that. (of course it would be possible to redesign a program's user interface for small-resolution displays, but that would in most cases result in user interface that wouldn't work well on normal display resolutions any more..)
But this **is** ubuntu netbook. It is designed for smaller displays. That would make this a GUI bug in my book. If this quirk can't be fixed, then a workaround would be to include these keyboard and mouse move and resize commands in a ubuntu netbook intro screen that flashes several times upon first use.

Many people will try ubuntu netbook, not be able to re-size the dialog boxes and not be able to figure out what keywords to search for/ask about to get the answer. Then they'll not be able to use the OS. That would be disappointing.

---

### Post by mcduck on 2010-04-01
> **gregconquest said:**
> But this **is** ubuntu netbook. It is designed for smaller displays. That would make this a GUI bug in my book. If this quirk can't be fixed, then a workaround would be to include these keyboard and mouse move and resize commands in a ubuntu netbook intro screen that flashes several times upon first use.

Many people will try ubuntu netbook, not be able to re-size the dialog boxes and not be able to figure out what keywords to search for/ask about to get the answer. Then they'll not be able to use the OS. That would be disappointing.

I meant the *program*, not the operating system. :D

o make Thunderbird's user interface work properly on small resolution you'd need to edit the Thunderbird, not your operating system. And since it's unlikely that Mozilla would decide to target netbook users over the normal desktop users, you'd actually have to fork the project and create your own mail reader to replace Thunderbird... Or ask Mozilla to design their program to work better on small resolutions.

The point was that the operating system and desktop environment can't change how a program's user interface was designed, that's up to the program's developers to do. And it often simply is either really hard, or impossible, to build the user interface in a way that would work well on both large and very small resolutions. So if you need to use a small resolution display your only options are to either learn to work around the possible issues, or start using another program that works better on that resolution.

---

