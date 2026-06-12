---
title: "Problem with Thunderbird Account Settings Window"
date: 2009-02-28
forum: General Help
---

### Post by -kg- on 2009-02-28
I have a problem with Thunderbird's Account Settings that I have searched for but been unable to find anything posted.  I am running Hardy 8.04 on both computers; 64 bit on my desktop and 32 bit on my laptop.

I am attempting to transfer primary control of my POP email accounts from my desktop to my laptop, keeping it switchable between the two.  To accomplish this, I am storing my email files and folders on my external hard drive.

I have long been in the habit of putting my mail files in a separate set of folders and changing the "Local Folders" setting under "Server Settings" at the bottom of the screen.  On my desktop this is not a problem, since the Account Settings window is fully visible, including the "Local Folders" window, but this is not so on my laptop.

On my laptop the "Server Settings" window is cut off just under "Empty Trash on Exit" and I have tried everything I can think of to make "Local Folders" appear, to no avail.  When first launched, the Account Settings window is unmaximized and extends below the bottom of the visible screen.  The "Advanced" button is shown, but the "Cancel/OK" buttons aren't there.  I can only see the "Add Account" button on the left; the others are invisible.  When I maximize it, the "Cancel/OK" buttons are shown, as are the other two buttons to the left..."Set As Default" and "Remove Account," but "Local Folders" is hidden with no way to scroll down and access it.

I can change this by resizing the unmaximized window until I bring the bottom into view.  I do this by lowering the top of the window and moving the window up until the bottom of the window is in view.  Then, all the buttons on the left are visible, and the "Cancel/OK" buttons, but the "Empty Trash on Exit" checkbox is half cut off and the "Advanced" button is no longer visible, and naturally, at no time under any circumstance is the "Local Folders" window visible.  This is the case whether the window is maximized or unmaximized.

I'm at my wit's end with this; I have tried everything I can think of.  I feel sure that, when the window is unmaximized and extends below the visible area of the screen, everything is there but hidden below the viewable area.  There is no way I can think of to move it up into the visible area.

The settings window is not displayed on the taskbar, so I can't select "Move" from a right click on the button so that I can move the whole window to visibility.  The only window I can move thusly is the Thunderbird window, which moves nicely below the settings window. I found that I can right-click the top bar of the window and select move from there, but in no way can I move the window up above the viewable screen; only below it.

I've tried changing screen resolution to no avail.  It's already at max resolution (the same resolution as the pre-installed Vista) and any lower hides more of the window.

The only thing I'm really concerned with is getting to the "Local Folders" window so I can change it to the location on the external hard drive instead of the default for each account.  That way, I can access my mail files no matter what computer I'm on.  All I have to do is install Thunderbird, set up my accounts, and point them to the files on my external hard drive.  I don't even know where default is, to tell the truth, and I have several accounts set up and load them to separate folders.

Any suggestions?

---

### Post by -kg- on 2009-03-02
Bump

I may have found a solution, but still no real success.

---

### Post by emarkay on 2009-03-02
Boiling this down to issue IMHO - there's an issue on getting a full window visible?

Can you post an annotated screenshot?

I have had annoying issues in Ubuntu where for some reason I am at a lower display resolution (don't get me started on getting my ATI card working on a HDTV set...) and there is no way that I can "pull" the bottom part of a dialog box "up" to get to the darn "OK" button.

Is this something similar?

---

### Post by muddywater on 2009-03-31
had same problem with tb 2.0.0.21 on ubuntu intrepid. adjusted setting in about:config layout.frames.force_resizability to true. fixed layout issue but still doesn't work with lightning.

---

### Post by jo4hnc on 2009-03-31
Have you looked into IMAP? Seems like it might do what you need it to do.

[http://www.imap.org/](http://www.imap.org/)

You can probably check the Thunderbird or Mozillazine sites for info on how to set it up.

---

