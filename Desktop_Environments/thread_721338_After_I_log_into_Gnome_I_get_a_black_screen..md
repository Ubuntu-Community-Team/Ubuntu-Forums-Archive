---
title: "After I log into Gnome I get a black screen."
date: 2008-03-11
forum: Desktop Environments
---

### Post by AceRimmer on 2008-03-11
Hello.  I had a perfectly running Gnome setup but then I ran the Spinrite disk 
maintenance package.  But after I log in the screen briefly shows the end of the text that scrolls by when you are booting up but then goes all black and nothing happens. The drive spens for a few seconds and then it just sits there.  I can log in with failsafe Gnome session but 3d effects are disabled.

---

### Post by {BzF}~JOKesTER on 2008-03-13
Try This:

At The Login Screen Press:

Ctrl+Alt+F1 {The F1 Key} At The Same Time:

Now It Will Ask For Your Username And Password - 

Enter Them And Hit Enter.

Now I Will Warn You That Doing This WILL RESET ALL DESKTOP EFFECTS To Defualt.
{Such As Your Backround - Fonts -Icons Toolbars - Etc....}

Ok Now Type:

sudo rm -rf .gnome .gnome2 .gconf .gconfd .metacity

And Hit Enter.

Now Type:

restart

And Hit Enter - Your Computer Will Restart And You Should Be Set!!!:)

Tell Me How It Goes!!!:popcorn:

---

