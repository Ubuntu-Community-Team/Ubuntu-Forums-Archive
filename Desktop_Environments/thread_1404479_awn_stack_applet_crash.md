---
title: "awn stack applet crash"
date: 2010-02-11
forum: Desktop Environments
---

### Post by gabrielcik on 2010-02-11
Hola,

It crash giving this error: "Whoops! the applet crashed. Click to restart it"
while i set Layout "curved gui"

and then i try to change its setting by clicking on "Layout settings".

Sometimes im able to get inside "layout settings" but then it crush when i switch
to another tab.

What to do for to solve this issue? Is some other way to configure it (maybe through terminal)

Or exist some better stack applet (mac like)

thank you!

---

### Post by mannigill1 on 2010-04-09
It happens to me aswell. where ever I tries to click on layout settings it crashes

---

### Post by eg0n on 2010-04-30
Same problem here, I tried to use configuration editor to change the curved gui properties manually but I only found the stacks that I used before updating. Does anybody know where we can find the configuration files of running applets?

---

### Post by mahdif62 on 2010-08-04
Same problem here!

---

### Post by Covi on 2010-09-25
BUMP! here too :(
**Avant Window Navigator 0.4.0*

Error without backtrace (*output with line breaks for readability*):
```
/usr/share/avant-window-navigator/applets/stacks/stacks_glade.py:44: GtkWarning: 
IA__gtk_radio_button_set_group: assertion `!g_slist_find (group, radio_button)' failed
  wtree = gtk.glade.XML(self.glade_file)
/usr/share/avant-window-navigator/applets/stacks/stacks_glade.py:44: GtkWarning: 
GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  wtree = gtk.glade.XML(self.glade_file)
*** glibc detected *** python: double free or corruption (out): 0x0994e8a0 ***
```

Reproduce:
Add stack applet -> Configure -> Folders backend -> Stack Layout (curved gui) -> Layout settings -~~~-> CRASH

---

### Post by kerry_s on 2010-09-26
don't click on layout settings. :)
you can change those settings in gconf-editor, but you shouldn't need to, not much choice in the layout anyways.

make sure you use the ppa version its faster & more stable than the repo version.
[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

---

### Post by Covi on 2010-10-02
Thx Kerry_s but is crashed anyway, click or not on settings:
> The program 'stacks_applet.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadLength (poly request too large or internal Xlib length erro'.
  (Details: serial 5791 error_code 16 request_code 1 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
** (avant-window-navigator:26133): DEBUG: AwnPanel: DBus object :1.535 didn't call UninhibitAutohide!
from latest or ppa :(

...i'll trying to reinstall from ppa...

---

### Post by empty_spaces on 2010-10-05
I'm having issues with the stacks applet crashing as well.
AWN version is the default one for lucid
Any solutions yet?

---

### Post by ewyn on 2011-01-09
Same problem here... but has solved :)

i think this because python-gnome2-desktop not installed.

try this : sudo apt-get install python-gnome2-desktop

or try manual install. It's works for me.


Thank u

---

### Post by Frogs Hair on 2011-01-09
I have been using this Awn ppa in 10.04 and 10.10 and it's been problem free. If you try it remember to purge the current version of Awn as shown in the instructions. [http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html#more](http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html#more)

---

