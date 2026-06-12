---
title: "how to set geometry of &quot;open file&quot; dialog window??"
date: 2008-04-20
forum: Desktop Environments
---

### Post by quixote on 2008-04-20
Where can I set the size of the "open file" "save as" and similar dialog boxes that list directories? ?? This is driving me nuts!  I tend to have complex dir trees and EVERY SINGLE TIME I either have to scroll to get to where I need, or resize the window so it's longer from top to bottom.

Why won't it remember what size I made it? Why doesn't the menu at top left include a window-geometry setting?  Why isn't there a right-click option?  Why won't they at least tell me where this setting is stored so I can deal with it?  :mad:  Linus is right: Gnome's lack of customizability can be maddening. 

 I've looked through gconf-editor, but don't know which setting to change or even if it would do any good.  I'd be glad to text edit /usr files or do anything, so long as I can make this problem go away! :-?

---

### Post by x1a4 on 2008-04-20
Hi,

I've never tried this but it might just work.

Open a terminal, then the application, then its dialog.  In the terminal run **xprop** then click the dialog window.  This will tell you a whole bunch of information about the window.  

Find the WM_NAME property and edit your ~/.Xdefaults file like so: 

name*resource: value

Where name is the name of the window which is set in WM_NAME and resource is the resource you wish to set.  In the case of size it will be **geometry** and the value is WIDTHxHEIGHT.  Optionally you may also set the X and Y offsets like so: WIDTHxHEIGHT+XOFF+YOFF

EDIT: If name doesn't work try the class, which is specified in WM_CLASS, or both:

Name*Class*geometry: value

---

### Post by quixote on 2008-04-20
x1a4:  I saw your intriguing answer both here and on the default window size thread.  So far, I haven't quite got there.

1) I assume if I have no ~/.Xdefaults I just make one, right?  That's what I did, so if that's not what you meant, could you tell me what the file should be called and where it goes?  I don't think I  have anything named that anywhere on my system.

2) I'm not sure about the syntax.  WM_NAME="Save As..."  WM_CLASS is "gedit"
How do I write Save As... ?  "Save As..." (ie with quotes)?  Save\ As...  ?? (with escaped space?)  Or just plain Save As...  (that doesn't seem plausible) ?

Since I'd like all "Save As..." dialogs to be a longer window, should I write (for instance):
"Save As...".*.geometry: 600x732+50+25

Or have I misunderstood the placement of periods?  Should it be:
"Save As..."*geometry: 600x732+50+25

Thanks for your help!

---

### Post by x1a4 on 2008-04-21
> **quixote said:**
> x1a4:  I saw your intriguing answer both here and on the default window size thread.  So far, I haven't quite got there.

1) I assume if I have no ~/.Xdefaults I just make one, right?

Yes

> 2) I'm not sure about the syntax.  WM_NAME="Save As..."  WM_CLASS is "gedit"
How do I write Save As... ?  "Save As..." (ie with quotes)?  Save\ As...  ?? (with escaped space?)  Or just plain Save As...  (that doesn't seem plausible) ?

Use backticks (`)

`Save As...`*geometry: value
OR
gedit.`Save As...`*geometry: value

> Since I'd like all "Save As..." dialogs to be a longer window, should I write (for instance):
"Save As...".*.geometry: 600x732+50+25

Or have I misunderstood the placement of periods?  Should it be:
"Save As..."*geometry: 600x732+50+25

No periods when using asterisks.

name.class.resource: value
OR
name*resource: value

> Thanks for your help!

You're welcome, although I haven't helped any. :sad:

Also, I don't think using .Xdefaults will not work.  I tried various ways with various applications and couldn't make it work.  At least not with Xfce's window manager, AfterStep, or Openbox.  When I used the Sawfish window manager however, I was able to use it's config tool to set all sorts of things for any window--even a theme that's different from the default. 

This doesn't mean that it's not possible, as I haven't tried various combinations.  You may want to try various combinations like: 

`Save As...`*geometry: value
OR
gedit.`Save As...`*geometry: value
OR
*`Save As...`*geometry: value

Also, you may want to try the **editres** tool to get the full class tree and use that.  Note: editres doesn't work with all applications. 

If all else fails, download, compile and use [xdotool]("http://www.semicomplete.com/projects/xdotool/") which fakes keyboard and mouse mouse events, which you could use in a script to resize the windows.

---

### Post by quixote on 2008-04-21
Well, you're right.  Futzing with .Xdefaults seems to have zero effect on anything, even now that I have the right syntax.  Ah well.

And you did help.  That trick with xprop is way cool! :D

---

### Post by zeltak on 2008-05-28
Hi

I would also love to get the open file dialog pop up larger, is there any progress with this?

thx

zeltak

---

