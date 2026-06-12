---
title: "Intrepid + Synaptics + Suspend"
date: 2009-01-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by u-foka on 2009-01-14
Hy there!

I have a dell vostro 1310, with a touchpad ident ifyed as alps and using the synaptics driver.

I configured hal to add SHMConfig for this device... and now I can adjust the touchpad settings from gsynaptics.

After login my settings restored fine with gsynaptics-init

BUT... **after a suspend/resume cycle, my settings lost**, and I haven't found a way to set them again :( is anyone there who can help me with this?

I looked how I can run gsynaptics-init from resume.d but it doesn't work, because this needs to run under my username and X11, and I don't want that kind of hack...

It would be a solution if gnome-screensaver can run a command after unlock, but I haven't found any way to do that.

Somewhere I read that this is because after suspend the touchpad get a new /dev/input/event device but mine uses the same event device as it has before suspend...

So I'm now out of ideas how to fix this ugly problem :(
The only solution for me now to run gsynaptics-init after suspend :(

P.S.: Sorry because my bad english!

---

### Post by psyeye on 2009-01-23
I'd like to chime in on this problem.

I can suspend/resume like 100 times - but I always need to disable tap-to-click after every resume.

Not that big an issue - but keeping the settings throughout suspend-cycles what be quite nice :)

---

### Post by Dirjel on 2009-01-26
> **u-foka said:**
> It would be a solution if gnome-screensaver can run a command after unlock, but I haven't found any way to do that.
Try this:
[http://ubuntuforums.org/showthread.php?t=1029704](http://ubuntuforums.org/showthread.php?t=1029704)

I tried it on my computer, and it works fine.

---

### Post by u-foka on 2009-01-26
Hy!

Truly it's a really interesting point of view :) But it may work, so I'l test it soon and post back with the results!

Thanks!!  :D

---

### Post by NTolerance on 2009-01-26
Launchpad bug report:

[https://bugs.launchpad.net/ubuntu/+source/gsynaptics/+bug/303595](https://bugs.launchpad.net/ubuntu/+source/gsynaptics/+bug/303595)

---

### Post by u-foka on 2009-01-29
Hy there!

I now put my script together based on the one that Dirjel suggested.
It seems to work but more testing is needed to be sure :D

Anyway i post that here so feel free to try it, and tell me the results :)

gsynaptics-sleep-fix.sh
```
#!/usr/bin/perl
my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSaver', member='SessionIdleChanged'\"";

open (IN, "$cmd |");

#input loop
while (<IN>) {
  if (m/^\s+boolean true/) {
    # if session is entered to idle state
    print "Idle: true\n";
  } elsif (m/^\s+boolean false/) {
    # if session is returned from idle state
    print "Idle: false\n";
    # run gsynaptics-init to make sure that the hw params are correct
    system("gsynaptics-init");
  }
}
```

---

