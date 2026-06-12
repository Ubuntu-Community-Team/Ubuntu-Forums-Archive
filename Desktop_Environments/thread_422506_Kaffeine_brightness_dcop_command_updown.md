---
title: "Kaffeine brightness dcop command up/down"
date: 2007-04-25
forum: Desktop Environments
---

### Post by dentaku65 on 2007-04-25
Hi,
I'm seaching a way to set the dcop command for manage the up/down brightness in Kaffeine (to use with lirc remote control); even if this command is supported 

[http://docs.kde.org/development/en/extragear-multimedia/kaffeine/dcop-functions.html](http://docs.kde.org/development/en/extragear-multimedia/kaffeine/dcop-functions.html)

there is not a way to implement it different that setting straightly int number (instead to use incremental/decremental mode like for volume or channels).

Here my lircrc of Kaffeine 

```

## KAFFEINE ##
begin
        prog = irexec
        button = 0
        config = dcop kaffeine KaffeineIface playDvb
end

begin
        prog = irexec
        button = pause
        config = dcop kaffeine KaffeineIface pause
end

begin
        prog = irexec
        button = SOURCE
        config = dcop kaffeine KaffeineIface dvbOSD
end

begin
        prog = irexec
        button = stop
        config = dcop kaffeine KaffeineIface stop
end

begin
        prog = irexec
        button = forward
        config = dcop kaffeine KaffeineIface posPlus
end

begin
        prog = irexec
        button = rewind
        config = dcop kaffeine KaffeineIface posMinus
end

begin
        prog = irexec
        button = CH+
        config = dcop kaffeine KaffeineIface next
end

begin
        prog = irexec
        button = CH-
        config = dcop kaffeine KaffeineIface previous
end

begin
        prog = irexec
        button = TV
        config = dcop kaffeine KaffeineIface quit  
end

begin
        prog = irexec
        button = VOL+
        config = dcop kaffeine KaffeineIface volUp
end

begin
        prog = irexec
        button = MUTE
        config = dcop kaffeine KaffeineIface mute
end

begin
        prog = irexec
        button = VOL-
        config = dcop kaffeine KaffeineIface volDown
end

begin
        prog = irexec
        button = FULL_SCREEN
        config = dcop kaffeine KaffeineIface fullscreen
end

begin
        prog = irexec
        button = up
        config = dcop kaffeine KaffeineIface zoomIn
end

begin
        prog = irexec
        button = down
        config = dcop kaffeine KaffeineIface zoomOut
end

begin
        prog = irexec
        button = 1
        config = dcop kaffeine KaffeineIface setNumber 1
	repeat = 0
end

begin
        prog = irexec
        button = 2
        config = dcop kaffeine KaffeineIface setNumber 2
	repeat = 0
end

begin
        prog = irexec
        button = 3
        config = dcop kaffeine KaffeineIface setNumber 3
	repeat = 0
end

begin
        prog = irexec
        button = 4
        config = dcop kaffeine KaffeineIface setNumber 4
	repeat = 0
end

begin
        prog = irexec
        button = 5
        config = dcop kaffeine KaffeineIface setNumber 5
	repeat = 0
end

begin
        prog = irexec
        button = 6
        config = dcop kaffeine KaffeineIface setNumber 6
	repeat = 0
end

begin
        prog = irexec
        button = 7
        config = dcop kaffeine KaffeineIface setNumber 7
	repeat = 0
end

begin
        prog = irexec
        button = 8
        config = dcop kaffeine KaffeineIface setNumber 8
	repeat = 0
end

begin
        prog = irexec
        button = 9
        config = dcop kaffeine KaffeineIface setNumber 9
	repeat = 0
end

begin
        prog = irexec
        button = 0
        config = dcop kaffeine KaffeineIface setNumber 0
	repeat = 0
end

```

As far as you can see the problem is regarding the use of Kaffeine as DVB-T player (or maybe as video player too) that there is a lack of command line for video settings (contrast/brightness/hue); I'm not using KDE applications (I'm on Gnome env but for DVB-T I needed to use Kaffeine) and maybe some guru of K can give me some specific hint (dcop stuff...)...

TIA

---

