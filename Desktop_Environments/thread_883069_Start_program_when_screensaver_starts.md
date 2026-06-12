---
title: "Start program when screensaver starts"
date: 2008-08-07
forum: Desktop Environments
---

### Post by mock on 2008-08-07
I would like to start motion (motion detektion when the screen saver starts (ie when i'm away from the keyboard) and END when the screen saver ends.

That way i can have a motion detektor while i'm away from the computer.

Now is that possible? (i have search the forum and haven't found anything) but i think i could be possible to do this.

---

### Post by mock on 2008-08-09
I found a way to do this:

make a file name screensaverchange.pl

```

#!/usr/bin/perl
my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSaver',member='SessionIdleChanged'\"";

open (IN, "$cmd |");

while (<IN>) {
    if (m/^\s+boolean true/) {
        #when screensaver activates, run the following commands
        system("motion -n &");
    } elsif (m/^\s+boolean false/) {
        #when screensaver deactivates, run the following commands
        system("killall -9 motion");
    }
}



```

then

```

chmod +x screensaverchange.pl

```

to start you just have to 

```

perl screensaverchange.pl

```

which you can put in your session starter,

---

