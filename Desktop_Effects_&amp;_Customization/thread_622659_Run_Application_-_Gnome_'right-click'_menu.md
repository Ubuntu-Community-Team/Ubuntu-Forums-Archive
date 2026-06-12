---
title: "Run Application - Gnome 'right-click' menu"
date: 2007-11-25
forum: Desktop Effects &amp; Customization
---

### Post by thecapuchin on 2007-11-25
A little preface here, given that the other posts, that were so helpfully provided (thanks ubuntuforums - you've helped me so often) when I created the title for this one, were completely unhelpful in and of themselves, here I go into territory likely tread by many a Gnome user.

Ok, what I'm looking for is this:  

I want to be able to right click on the desktop and in the menu that pops up, have an option that gives me the "Run Application" dialog box.  

I use my home computer from work a lot of the time via NX and using Alt-F2 doesn't cut it for me since the local machine tries to override the shortcut.  Before you tell me that I can just add the Run Application icon to the panel, let me say just this, I don't bloody want to.  It is there right now because I've yet to find an answer that avoids adding unnecessary icons to the panel.

I've read that the Gnome devs removed this option a while back and I'd love to know what the justification for that was.  A keyboard shortcut is easier?  Whatever, I like my menus and I'd like to know how to get this option back if possible.

Thanks in advance and sorry about any potential snideness lurking in my post, I'm just frustrated at this particular issue.

---

### Post by Forlong on 2007-11-25
I guess this should be possible with nautilus-actions.
Unfortunately, I don't know if the Run Application menu has a command on it's own... it's part of the gnome-panel.

---

### Post by thecapuchin on 2007-11-25
Dang it, I was hoping there was more to it than that.  I've tried to sort out what process might be running it, but it does seem to be purely a part of the panel rather than a separate process.

I've tried using the '--run-dialog' parameter when setting up a Nautilus action, but it didn't seem to like it.

Guess I'll keep hunting.

Thanks for the response in any case.

---

