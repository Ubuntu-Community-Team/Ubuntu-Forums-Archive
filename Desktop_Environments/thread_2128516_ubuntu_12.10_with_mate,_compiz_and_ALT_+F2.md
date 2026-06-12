---
title: "ubuntu 12.10 with mate, compiz and ALT +F2"
date: 2013-03-23
forum: Desktop Environments
---

### Post by spezticle on 2013-03-23
I'm running Ubuntu 12.10 and wanted to switch to the mate desktop. I really like the gnome 2 style of desktop.
It's been a little bit of a chore and thought I would share with everyone the fixes I've found and what worked for me.

first, to get mate installed 
```
sudo add-apt-repository "deb http://packages.mate-desktop.org/repo/ubuntu quantal main" 
sudo add-apt-repository "deb http://repo.mate-desktop.org/ubuntu quantal main" 
sudo add-apt-repository "deb http://mirror1.mate-desktop.org/ubuntu quantal main"

sudo apt-get update
sudo apt-get install mate-archive-keyring -y
sudo apt-get update
# this install base packages
sudo apt-get install mate-core
# this install more packages
sudo apt-get install mate-desktop-environment

sudo apt-get install mate-conf-editor 



```
Now you should be able to log out of your current session and log in selecting mate as your desktop environment

Then to get compiz installed
```

sudo apt-get install compiz compiz-plugins compiz-plugins-default compiz-plugins-extra compiz-plugins-main compiz-plugins-main-default compizconfig-settings-manager

```

Now you need to tell mate to use compiz

press ALT + F2 and type ```
mateconf-editor
```
Click on desktop > mate > session> required_components > windowmanager and replace "marco" with "compiz" (without the quotation marks)

log out and back in again

You'll have to configure a bit of compiz to get window management and some other things to work properly.
**EDIT:** I just realized you can open a terminal and use the following command:
```
compiz --replace
```
**/EDIT**
Click on System > Preferences > CompizConfig Settings Manager

Click the check boxes next to:
Window Decoration
Resize Window
Move Window
Application Switcher

You shouldn't have to change any settings to get these things to work.

In order to get the ALT + F2 shortcut to call the run dialog to work was a little tricky.
We'll need the build-essential packages installed
```
sudo apt-get install build-essential
sudo apt-get install libx11-dev
```

take the following code and paste it into a new file called mate-run.c
```

#include <stdio.h>
#include <stdlib.h>
#include <X11/Xlib.h>

void die(const char *message)
{
   fputs(message, stderr);
   exit(1);
}

Atom get_atom(Display *display, const char *atom_name)
{
   Atom atom = XInternAtom(display, atom_name, False);
   if (atom == None)
      die("can't find an atom I need");
   return atom;
}

int main()
{
   Display *display;
   Atom gnome_panel_atom, run_atom;
   XClientMessageEvent event;

   display = XOpenDisplay(NULL);
   if (display == NULL)
      die("can't open display");

   gnome_panel_atom = get_atom(display, "_MATE_PANEL_ACTION");
   run_atom = get_atom(display, "_MATE_PANEL_ACTION_RUN_DIALOG");

   event.type = ClientMessage;
   event.window = DefaultRootWindow(display);
   event.message_type = gnome_panel_atom;
   event.format = 32;
   event.data.l[0] = run_atom;
   event.data.l[1] = (Time)(time(NULL) * 1000);

   XSendEvent(display, event.window, False, StructureNotifyMask,
              (XEvent *)&event);

   XCloseDisplay(display);

   return 0;
}
```

then compile with: (**note that /PATH/TO refers to wherever you saved the mate-run.c file to)**
```
gcc /PATH/TO/mate-run.c -o mate-run -L /usr/lib/X11/rstart/commands/x11r6 -lX11 
```

and then I put a sym link from the compiled path into /usr/bin/ so that I don't need to type the full path to access the newly created file
```
ln /usr/lib/X11/rstart/commands/x11r6/mate-run /usr/bin/ -s 
```

now we can go into the CompizConfig Settings Manager and in "Commands" under "General" I can add command 0 to be "mate-run" and then click key bindings and set it to alt+f2 or whatever you want it as.

Hope this helps.

---

