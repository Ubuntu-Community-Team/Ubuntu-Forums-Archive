---
title: "Rhyhmbox+LIRC? or best alternative"
date: 2009-02-17
forum: General Help
---

### Post by beattyml1 on 2009-02-17
Is there anyway to control rhythmbox with lirc?
If so can someone walk me through how to do so?

If not what would be the best media player to  use, with the main criteria being that it must have playlist support?

I like rhythmbox and banshee best as far as the interface goes, but if something else offers exceptional remote control options I am willing to forgo this preference.

---

### Post by Anonymousable on 2009-06-11
I originally used audacious with my remote control. It has playlist support, but runs slowly if you have too many songs in a playlist, which is why I switched to rhythmbox. 

Anyway, audacious does have a lirc plugin, but it didn't work for me so I just set up a lircrc file for it. Attached is my lircrc file. To control audacious, you will have to make some small changes to the file (eg. specifying your remote and setting up the buttons correctly), then put it as .lircrc in your home directory. Run irexec to start the script.

---

### Post by terry_gardener on 2009-08-02
it is possible to use rymthmbox with lirc you just need to activate the plugin and then close rymthmbox and then copy the folder and file to your home directory. 

i have attached the lirc file and folder to go with it.

extract to your home folder and then reopen rymthmbox and you will be able to use remote.

this assumes you use a windows media center remote

---

### Post by splattx_x on 2009-10-17
Hi! I'm having problems setting up LIRC with Rhythmbox as well. I have managed to configure Lirc properly and it's working (I get to see the codes when I run "irw") but Rhythmbox doesn't seem to recognize any commands :(

I activated the plugin in the plugins section but the "configure plugin" button is disabled (grayed out). I'm using the following text in my ~/.lircrc

```
##
# Rhythmbox key bindings.
##
begin
        prog = Rhythmbox
	remote = panasonic
	repeat = 0
        button = key_play
        config = playpause
end
begin
        prog = Rhythmbox
        button = key_stop
        config = playpause
end
begin
        prog = Rhythmbox
        button = key_stop
        config = stop
end
begin
        prog = Rhythmbox
	remote = *
        button = key_next
        config = next
end
begin
        prog = Rhythmbox
        button = key_previous
        config = previous
end
```

the "button" names are the same as in lircd.conf, I checked and here it is

```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.6(default) on Sat Oct 17 18:22:41 2009
#
# contributed by 
#
# brand:                       panasonic
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  panasonic
  bits           24
  flags SPACE_ENC
  eps            30
  aeps          100

  header       3434  1731
  one           392  1326
  zero          392   478
  ptrail        401
  pre_data_bits   24
  pre_data       0x400405
  gap          73994
  toggle_bit_mask 0x0

      begin codes
          key_play                 0x445011
          key_pause                0x446021
          key_stop                 0x440041
          key_next                 0x38526F
          key_previous             0x3892AF
          key_volumedown           0x008481
          key_volumeup             0x000401
      end codes

end remote
```

I think I might be close to get it working so if you could give me a hint of what could be going on I would appreciate it very much.

---

### Post by splattx_x on 2009-10-17
Hi! I was having problems setting up LIRC with Rhythmbox as well.

I'm using the following text in my ~/.lircrc

```
##
# Rhythmbox key bindings.
##
begin
        prog = Rhythmbox
	remote = panasonic
	repeat = 0
        button = key_play
        config = playpause
end

begin
        prog = Rhythmbox
	remote = panasonic
	repeat = 0
        button = key_pause
        config = playpause
end

begin
        prog = Rhythmbox
	remote = panasonic
	repeat = 0
        button = key_stop
        config = stop
end

begin
        prog = Rhythmbox
	remote = panasonic
	repeat = 0
        button = key_next
        config = next
end

begin
        prog = Rhythmbox
	remote = panasonic
	repeat = 0
        button = key_previous
        config = previous
end

begin
        prog = Rhythmbox
	remote = panasonic
	repeat = 0
	button = key_volumeup
	repeat = 1
	config = volume_up
end

begin
        prog = Rhythmbox
	remote = panasonic
	repeat = 0
	button = key_volumedown
	repeat = 1
	config = volume_down
end

```

the "button" names are the same as in lircd.conf, I checked and here it is

```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.6(default) on Sat Oct 17 18:22:41 2009
#
# contributed by 
#
# brand:                       panasonic
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  panasonic
  bits           24
  flags SPACE_ENC
  eps            30
  aeps          100

  header       3434  1731
  one           392  1326
  zero          392   478
  ptrail        401
  pre_data_bits   24
  pre_data       0x400405
  gap          73994
  toggle_bit_mask 0x0

      begin codes
          key_play                 0x445011
          key_pause                0x446021
          key_stop                 0x440041
          key_next                 0x38526F
          key_previous             0x3892AF
          key_volumedown           0x008481
          key_volumeup             0x000401
      end codes

end remote
```

Hope this helps

---

### Post by MeduZa on 2010-09-21
> **Anonymousable said:**
> I originally used audacious with my remote control. It has playlist support, but runs slowly if you have too many songs in a playlist, which is why I switched to rhythmbox. 

Anyway, audacious does have a lirc plugin, but it didn't work for me so I just set up a lircrc file for it. Attached is my lircrc file. To control audacious, you will have to make some small changes to the file (eg. specifying your remote and setting up the buttons correctly), then put it as .lircrc in your home directory. Run irexec to start the script.

audacious have a lirc plugin and works fine for me, you only need to add commands like this on the lircrc file:
> begin
prog = audacious
button = Play
config = PLAYPAUSE
end

begin
prog = audacious
button = Previous
config = PREV
end

begin
prog = audacious
button = Next
config = NEXT
end

begin
prog = audacious
button = Stop
config = STOP
end

begin
prog = audacious
button = Return
config = SHUFFLE
end
there is more commands:
> 
The following command list has been taken from lirc.c file from audacious-plugins source code.
Code: Audacious input commands (complete)

PLAY
STOP
PAUSE
PLAYPAUSE
NEXT
PREV
SHUFFLE
REPEAT
FWD
BWD
VOL_UP
VOL_DOWN
QUIT
MUTE
BAL_LEFT
BAL_RIGHT
BAL_CENTER
LIST
PLAYLIST_CLEAR
PLAYLIST_ADD


---

### Post by termin on 2010-09-21
i personally like banshee better than rhyhmbox because it can play better and it can stream. also, its more like windows media player on windows which in my opinion is the best media player for windows.

---

### Post by gamhead on 2011-02-22
Thanks Splatx_x!

---

