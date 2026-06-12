---
title: "Gedit sometimes seems to randomly paste copied text"
date: 2008-07-31
forum: Desktop Environments
---

### Post by Max Williams on 2008-07-31
Sometimes, when i copy some text (with ctrl&c) in gedit, it is silently pasted somewhere else in the same text file, without me realising.  When i say silently, i mean that the page view doesn't jump to the paste location, so there's no signal that anything's happened.  It happened to me just now when i selected some text to copy into a different file, and it happened at the point of ctrl&c'ing the text.

I know that the first reaction when hearing this is that i'm being an idiot and pasting it without realising, and maybe that is the case.  But it happens to me fairly frequently - maybe 3% of the time, ie 1 in every 30 or so copies.  Most of the time, because it's silent, i don't notice, until my app breaks and i go looking, to find a big wodge of text randomly inserted into the middle of a method call.  

If i am accidentally doing it, i'd love to know how, so i can avoid it.  As far as i know i'm not doing anything out of the ordinary.  One possibility is that there's some sequence of 'copy-pageup-paste-pagedown' happening, i have no idea how i would trigger that though.  If i am just mashing ctrl-v down at the same time as ctrl-c i'd expect the text to appear in the same place, not somewhere else in the doc.

I'm using gedit 2.22.3 in Ubuntu 8.04, but i used to have the same problem when i was running gutsy in a virtual machine in windows.

Has anyone else seen this?  Can anyone think of a way i might be doing this without realising?   It's really annoying and i really like gedit for development, besides this issue.

thanks
max

---

### Post by undecidable on 2008-07-31
Separate two terms:
cursor:  where your cursor is pointing on th screen;
edit pointer:  where your editing cursor is located within the document;

Two possibilities I can think of:

1.  things are pasted where your edit pointer is, not where you are looking.  Your edit pointer could be anywhere, not just on the screen where you are looking or where your cursor is.  

2. Dont forget text an be selected by just highlighting it,
 and then pasted with a middle-click.  If youredit pointer happens to be not on the present screen, this of course can lead to unexpected results.  

Hope this helps.

---

### Post by Max Williams on 2008-07-31
Doh, it was me being an idiot after all!  Although in my defence, i wasn't aware of either of those two facts, both of which contribute to cause my problem - i must have been accidentally clicking the middle mouse button.  I'm off to go and disable that function - i only ever use it to scroll web pages up and down.

Many many thanks!
max

---

### Post by undecidable on 2008-07-31
When you get used to it,
selecting text, then using the middle mouse button to paste it
is much faster and nicer than ^c / ^v.
I didn't like it at first, but now use it all the time.

---

### Post by Max Williams on 2008-07-31
I hate it - maybe i'd get used to it, but i find middle-mouse click quite awkward, possibly because i use a small wireless mouse (getting used to THAT took i while but i did it).  That awkwardness probably explains why i was hitting it accidentally.  I'd rather it's just not an issue. :)

Switching it off wasn't as easy as i thought but i found the answer thanks to this thread - [http://ubuntuforums.org/archive/index.php/t-431712.html](http://ubuntuforums.org/archive/index.php/t-431712.html)

In case anyone else wants to do this, the best way seems to be to turn your middle-mouse click into a left-mouse click (scroll up and down still works):   

in the "ConfiguredMouse" section of xorg.conf (in my case, /etc/X11/xorg.conf), add the following lines to the bottom of the section:

Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 1 3 4 5"

thanks again
max

---

### Post by Keyper7 on 2008-07-31
> **undecidable said:**
> When you get used to it,
selecting text, then using the middle mouse button to paste it
is much faster and nicer than ^c / ^v.
I didn't like it at first, but now use it all the time.

I completely agree.

It's like everyone says, Windows will never be truly ready for the mainstream desktop until it gets rid of that keyboard typing rubbish and becomes more suited for point-and-click. ;)

---

### Post by undecidable on 2008-07-31
One caution so you don't run into a 'gotcha' later:

you cannot ^c / ^v in a terminal window. 
And you can't ^c from somewhere and then ^v into the terminal window.
To paste (eg a dir path) into the terminal window (eg gnome-terminal or tilda) 
you have to use the middle-click.

---

### Post by alphane on 2008-07-31
or shift-insert ;)

---

### Post by undecidable on 2008-07-31
I didn't know that - thanks.  
Any similar key combination to do a ^c in a terminal?

---

