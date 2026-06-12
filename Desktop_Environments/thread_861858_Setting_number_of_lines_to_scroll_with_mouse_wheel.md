---
title: "Setting number of lines to scroll with mouse wheel"
date: 2008-07-17
forum: Desktop Environments
---

### Post by JKoltner on 2008-07-17
There's a thread with this exact same topic in the old archives here: [http://ubuntuforums.org/showthread.php?t=628725](http://ubuntuforums.org/showthread.php?t=628725) ... but I'm starting a new topic because the advice given in that thread (which boils down to adding 'option "VertScrollDelta" 6' in xorg.conf) doesn't work for me -- or some of the other posters -- and the thread was started back before Hardy was released.

(I've found that unfortunately many solutions that worked for Feisty or Gutsy don't in Hardy.  Since Hardy is a long-term support edition, it seems like this is work getting nailed down.  This is under Gnome -- with KDE supporting a variable number of lines scrolled with the mouse wheel can be set through the GUI and I haven't found any messages suggesting it doesn't work as designed.)

Anyway... any idea why, with the following (snippets of my) xorg.conf, my mouse wheel still only scrolls shell text or Firefox windows 3 lines at a time?  I've tried setting the VertScrollDelta to lots of numbers between 6 and 100, and it just seems to be completely ignored.  I don't suppose X can be made to keep a log somewhere of what it's ignoring/doesn't like?

```

[Lots of sections deleted]

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
        Option          "VertScrollDelta"       "6"
EndSection

[More sections deleted]

Section "ServerLayout"
	Identifier	"Default Layout"
	screen "Default Screen"
	Inputdevice	"Configured Mouse"
EndSection

[I'm assuming "ServerLayout" is a reserved name and hence X really should pick up the "Configured Mouse" section settings.]


```

Thank you very much for your help.

---Joel Koltner

---

### Post by kaibob on 2008-07-17
> **JKoltner said:**
> Anyway... any idea why, with the following (snippets of my) xorg.conf, my mouse wheel still only scrolls shell text or Firefox windows 3 lines at a time?  I've tried setting the VertScrollDelta to lots of numbers between 6 and 100, and it just seems to be completely ignored.  I don't suppose X can be made to keep a log somewhere of what it's ignoring/doesn't like?
Firefox has a mousewheel scroll setting that MAY override any other setting. I don't know if that's the case, but you may want to check. The Firefox setting is controlled by the following about:config entries:

> Mousewheel.*

These fall into two groups, vertical and horizontal scroll. The general form is:

    * mousewheel.(modifier key).(type)
    * mousewheel.horizscroll.(modifier key).(type) 

Type is then one of:

action 
    integer value that determines the type of action: 

    * 0 - Scroll document by a number of lines (given by the numlines property)
    * 1 - Scroll document by one page
    * 2 - Move back/forward in history
    * 3 - Make text larger/smaller
    * 4 - Scroll document by a number of pixels (given by the numlines property) 

numlines 
    number of lines to scroll by, or pixels if action is set to value 4 
sysnumlines 
    use system preferences to determine how many lines to scroll by 

BTW, I tried to link to the above information, but the link wouldn't work.

---

### Post by JKoltner on 2008-07-18
Thanks Kaibob... FireFox can be set to scroll a page at a line with the mouse wheel, although overriding the number of lines to scroll doesn't appear to work (and I've confirmed with Googling that this is apparently the intended behavior -- when FireFox can successfully interface to a desktop manager, the manager's setting for the number of lines to scroll has priority).

Hmm...

---

### Post by kaibob on 2008-07-19
> **JKoltner said:**
> Thanks Kaibob... FireFox can be set to scroll a page at a line with the mouse wheel, although overriding the number of lines to scroll doesn't appear to work (and I've confirmed with Googling that this is apparently the intended behavior -- when FireFox can successfully interface to a desktop manager, the manager's setting for the number of lines to scroll has priority).
Hmm...

I changed Firefox preference settings as follows:

settingsmousewheel.withnokey.action - value 0

mousewheel.withnokey.numlines - value 1

mousewheel.withnokey.sysnumlines - value false

With the above settings, the mousewheel scrolled one line at a time in Firefox. I then changed the numlines setting to 10, and the mousewheel scrolled 10 lines at a time. I also tried 20 lines, and it also worked. 

I don't completely understand the reference to desktop manager in your post. I thought the sysnumlines preference allowed the user to override any system mouse settings, but perhaps that's not true. In that case, I can't be of any help.

---

### Post by JKoltner on 2008-07-20
Ah, thanks Kaibob -- I was missing the mousewheel.withnokey.sysnumlines setting!  (Which makes me feel rather ignorant, given that it's immediately below the mousehweel.withnokey.numlines setting...)

That probably fixes about 90+% of the time I use the middle wheel on the mouse... the rest of the time would be in, e.g., a shell or OpenOffice, so hopefully one of these days I can learn how to get Gnome in general to configure the number of lines to scroll.

---

### Post by Nowaker on 2010-04-02
Firefox isn't the whole system. Please tell how to change the wheel scroll lines system-wide as VertScrollDelta in xorg.conf does not work. (Ubuntu 9.10)

---

