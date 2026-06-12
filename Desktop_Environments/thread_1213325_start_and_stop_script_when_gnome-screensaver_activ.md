---
title: "start and stop script when gnome-screensaver activates and deactivates"
date: 2009-07-14
forum: Desktop Environments
---

### Post by anlayne on 2009-07-14
I'm trying to run the Folding@Home GPU2 client on my Jaunty box under wine. It runs fine, but makes my display sluggish, so I want to only run it when I'm away from the computer. I figured the easiest way was to run it when the screen saver is activated. I found a perl script [here]("http://www.linuxquestions.org/questions/fedora-35/start-and-stop-script-with-screensaver-728498/") that is supposed to do this, and have modified it to look like this:

```
#!/usr/bin/perl
my $cmd = q[dbus-monitor --session "type='signal',interface='org.gnome.ScreenSaver',member='SessionIdleChanged'"];
open (IN, "$cmd |");
while (<IN>) {
    if (/^\s+boolean true/) {
        system '~/gpufolding/gpufah.bash';
    }
    elsif (/^\s+boolean false/) {
        system 'kill `pgrep gupfah.bash`';
        system 'kill `pgrep Folding.*home`';
    }
}
```

The reason for the two kill commands is that the bash script starts a program called [email]Folding@home-Win32-GPU.exe[/email] which in turn starts another program which seems to die if I kill [email]Folding@home-Win32-GPU.exe[/email]. Everything starts up fine, but when the screen saver goes off. The programs don't get killed like they should. I'm don't have any experience with perl, so help is appreciated.

---

### Post by anlayne on 2009-07-16
I answered my own question, though I'm sure this isn't the best way to do this. The problem was that since the gpufah.bash script never terminates, the script didn't execute the elseif statement until I manually killed it. The solution is to use screen so the script can execute the bash script and still continue. And when the screensaver exits and the kill command goes through, screen finishes and exits automatically. Here's the code:

```
#!/usr/bin/perl
my $cmd = q[dbus-monitor --session "type='signal',interface='org.gnome.ScreenSaver',member='SessionIdleChanged'"];
open (IN, "$cmd |");
while (<IN>) {
    if (/^\s+boolean true/) {
        system 'screen -A -m -d -S GPUFAH ~/gpufolding/gpufah.bash';
    }
    elsif (/^\s+boolean false/) {
        system 'kill `pgrep FahCore_1` `pgrep Folding`';
    }
}

```

---

