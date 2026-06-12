---
title: "Multimedia keyboard shortcuts for use with LIRC"
date: 2007-07-05
forum: Desktop Environments
---

### Post by pointone on 2007-07-05
I am running Ubuntu 7.04 on a Dell Inspiron 6400 (E1505), which has a set of multimedia buttons on the front panel. These keys work fine out of the box--no problems here.

I have a remote control that came with my laptop (Windows XP MCE) which I successfully set up using LIRC, but only for a specific program (Rhythmbox, specified in my lircrc file). I was wondering how I could go about configuring LIRC to use the same features as the laptop multimedia buttons. For example, I know I could configure volume up and down to work at the system level using irexec and amixer, but this method doesn't show the on-screen volume display that accompanies the multimedia buttons. Similarly, I could configure a play / pause command for each program in lircrc, but the multimedia buttons seem to work universally (Rhythmbox, Totem, etc.)

Essentially, what I'm asking is how to access the multimedia button functions from the command line, or if it's possible to assign more than one key to these functions.

```
# LIRC
#
# lircrc configuration file

begin rhythmbox

begin
        prog = Rhythmbox
        button = Play
        config = play
end

begin
        prog = Rhythmbox
        button = Pause
        config = pause
end

begin
        prog = Rhythmbox
        button = Stop
        config = stop
end

begin
        prog = Rhythmbox
        button = VolUp
        config = volume_up
end

begin
        prog = Rhythmbox
        button = VolDown
        config = volume_down
end

begin
        prog = Rhythmbox
        button = Mute
        config = mute
end

begin
        prog = Rhythmbox
        button = Forward
        config = seek_forward
end

begin
        prog = Rhythmbox
        button = Rewind
        config = seek_backward
end

begin
        prog = Rhythmbox
        button = Skip
        config = next
end

begin
        prog = Rhythmbox
        button = Replay
        config = previous
end

end rhythmbox
```

---

### Post by viperet on 2008-02-24
You can access the functions of some multimedia buttons by running shell scripts in /etc/acpi/*.sh

For example to control volume, you can use:
```

begin
  prog=irexec
  button=vol-
  config=/etc/acpi/voldownbtn.sh
end
begin
  prog=irexec
  button=vol+
  config=/etc/acpi/volupbtn.sh
end

```

---

