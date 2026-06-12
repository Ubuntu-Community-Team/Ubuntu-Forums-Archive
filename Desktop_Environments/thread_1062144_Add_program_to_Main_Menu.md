---
title: "Add program to Main Menu?"
date: 2009-02-06
forum: Desktop Environments
---

### Post by MR2Quick on 2009-02-06
I just installed via the cli a program.  Now, when i have to launch the program, i have to navigate to the installation folder then type ./program for it to run.

Is there a way to add it to the main menu list?  I'm not sure what i need to do to the launcher properties to get it to work correctly.

I know this is total n00b question, but what does ./ mean in this situation?

Any and all help is greatly appreciated! Thanks!

---

### Post by mikewhatever on 2009-02-06
There isn't a line for properties when creating a launcher. You get the following:
Type: Application
Name: Name of the program
Command: ./program
Comment: anything

---

### Post by arvevans on 2009-02-06
Last question first...that "./program" means look in the current directory to find the program.  This is necessary if your pre-defined search path does not include the directory where the program resides (this is changable by tweaking your .profile settings).

If you are running Ubuntu with Gnome desktop, you go to:

[INDENT]System->Preferences->Main Menu[/INDENT]

In the Main Menu editor you have the option to add new applications.  In the Add New editor you will see a selection box labeled "Type".  Click on this and select "Application in Terminal".  Then in the box labeled "Command" you enter the full path name to your new application.

This will add your new application to the selected sub-menu, and when clicked it will open a terminal session and run the application there.

Hope this helps.

Arv
_._

---

