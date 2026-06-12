---
title: "emacs not offered for opening from nautilus"
date: 2011-12-27
forum: Desktop Environments
---

### Post by gleedadswell on 2011-12-27
This looks like a bug.  I just thought I'd see if anyone else has noticed it before I submit it as a bug.  Also, I think it needs more diagnosis before I can make a useful bug report because the behavior is inconsistent.

In Nautilus I've set the default application for opening .tex files to be Emacs 23.  When I right click on a .tex file, however, it offers me, in order

Open
Open with Text Editor
Open with Other Application

Just clicking "Open" seems to do nothing, as does just double clicking the file in Nautilus.  "Open with Text Editor" opens it in gedit.  "Open with Other Application" brings up the usual dialogue window and offers Emacs 23 as the only option.  So I can open it in emacs either via the Open with Other Application dialogue (which is a bit annoying compared to having it in the right click menu) or of course I can just do it from a terminal.

The thing that's particularly strange is that it is inconsistent.  Some .tex files offer Emacs as the top option in the right click menu and others don't.  Going into the properties on those files I see that emacs is already set as the default application for them, so that's not the problem.  I haven't yet figured out whether there is any pattern to which files offer emacs and which don't.

If I create a new .tex file by opening emacs from the command line then close it, Nautilus offers emacs as the default application on right click for that file.

---

