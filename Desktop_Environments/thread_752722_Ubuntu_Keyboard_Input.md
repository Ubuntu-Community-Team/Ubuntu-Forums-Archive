---
title: "Ubuntu Keyboard Input"
date: 2008-04-11
forum: Desktop Environments
---

### Post by guardianangelz on 2008-04-11
I'm still really new at this posting thing, so please cut me a huge hunk of slack.

I've seen many a forum thread about Ubuntu refusing to accept keyboard input before login, after login, from the start of a program, or after an error.  None of these helped me, because my problem is a little different.

On Firefox, whenever I hit the Enter key on a window other than the main browser (ie Save image, Save file) the main browser subsequently refuses to accept <i>any</i> keyboard input.  PageUp, PageDown, Ctrl+W, Up, Down, Ctrl+S don't work.  Incidentally, Alt+F4 does, but I think that's because Alt+F4 is sent to the window manager, not Firefox itself.  The thing is, it doesn't happen all the time - once in awhile I can still use the keyboard after an Enter keypress.  Also, (I think) I've observed the same effect on GAIM.  I can't do anything until I killall firefox-bin in a terminal, then start Firefox again.

At first, I thought it was a maximum number of keypresses that any one program can accept before dying because of memory problems or a config thing, but a newly started Firefox causes the same problem (sometimes) as soon as I press the Enter key in a Save Image dialog (if not the first time, then the second).  Thank god for the new Restore Session in Ff2, but I'd really like it if it didn't do that.

When I came to the Ubuntu forum to post this, I saw the link to the Desktop Effects category next to Desktop Environments, and went to test if Compiz was to blame.  It was not.

Has anybody had the same problem?  Anybody have a fix, or suggestions for a fix?  Thanks.

---

### Post by tamoneya on 2008-04-12
are you using firefox 2 or 3?  What version of ubuntu are you using?  Try to run firefox through terminal and then replicate this error.  Then post any terminal output.  Just type ```
firefox
``` in terminal and you will be all set.

---

### Post by guardianangelz on 2008-04-12
My terminal just sits there and blinks happily at me.  Does Firefox usually paint anything to the terminal when started from there?  Also, I'm using Gutsy Gibbon running FF 2.0.0.13 - the original one that came preinstalled in Ubuntu, plus, I suspect, updates from apt.

I found out I can start a new Firefox with key inputs and everything without killall firefox-bin; all I have to do is close every Firefox window and start over.  The reason I killed the process every time is because I usually leave the Downloads dialog open in the back, that I then promptly forget about; this dialog left firefox-bin running, and didn't do an ounce of good for a new browser window that clicking the Firefox icon opened.

---

### Post by tamoneya on 2008-04-13
hmm thats odd.  When you type firefox into terminal it should launch the application like normal.  The only difference should be that any errors and such are outputted to terminal.

---

### Post by guardianangelz on 2008-04-13
Oh I'm sorry.  Yeah, Firefox starts and all that.  I can browse normally and even reproduce the problem.  After Firefox not accepting anymore keyboard input, though, the terminal hasn't stdouted any error information.  I'm actually starting to think it's a problem with Ubuntu, rather than Firefox, partly because Pidgin has also been affected.  That doesn't explain, though, how Alt+F4 still works, or why the problem only occurs in one program at a time.

ADD: I'd also forgotten: The same problem also occurred on and off on Nautilus.  I don't usually use Nautilus, preferring to ls in a terminal, but when I need to collate pictures I need a file browser that can do things like display images.  Sometimes I find myself unable to type stuff into the address bar that hides behind the breadcrumbs, and I don't remember what I was doing before it happened (I don't think I was really pressing Enter on a non-main window - Delete confirmation, maybe?).

---

### Post by tamoneya on 2008-04-13
are you sure that the window isnt just losing focus due to some hotkey that you assigned to enter?

---

### Post by guardianangelz on 2008-04-14
No.  I mean, even if it is, I keep clicking on the window to return focus to it because that's my first suspicion, too.  Yet no keyboard input.  The scrollwheel on mice work, as well as the Grab and Drag plugin I use because it's a tablet PC, but since I usually use the touchpad when I use the computer, but not the up/down or pageup/pagedown keys.

ADD: This is funny.  GNOME was causing a lot more problems than just the above keyboard one - on some boots, it refused to load, leaving me staring at an orange screen - so I installed Kubuntu-desktop, being a KDE person at heart.  Firefox doesn't seem to produce the same keyboard-ignorant effect on KDE.

Now if only I can figure out how to make SKIM work, and wean myself off of the tight integration with Compiz that Gnome offered.

---

