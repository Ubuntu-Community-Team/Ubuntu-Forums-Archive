---
title: "more opera flash worries"
date: 2006-11-15
forum: Desktop Environments
---

### Post by raovq on 2006-11-15
ive no sound in flash. it worked pre flash 8, but now, nada.

running opera aoss gives me this.

```
ubuntu:~> aoss opera
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

#########and when i attempt to play something from youtube



(process:21729): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:21729): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `GDK_IS_DISPLAY (display)' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);

ALSA lib pcm_direct.c:1123:(snd_pcm_direct_open_secondary_client) unable to open hardware
(that last one repeats)

```

anyone have any ideas on what is going wrong?

---

### Post by dannyboy79 on 2006-11-15
i saw that you already posted this problem within the thread that I found this answer in, it stated:

I found out what alacarte command editor is. The truth is that even though I had changed the command to aoss opera to my shortcut, in alacarte editor it was unchanged (it was left as opera %u). I changed that also. I have to say that if I type opera in the command line (and only that) I still cannot hear any sound. If only I type aoss opera I have sound. Of cource if I click on my shortcut I have sound too.

I must also say that installing that kaffeine (and some codecs before that) I can play even m4a music files (they are similar to mp3), that I couldn't play before using rhythmbox. That's all. 

I hope that in the next edition of opera this issues will be solved.

now did you do the thing it stated at the very begining by actually installing opera aoss? per this Hallo,

So, in order to racapitulate, so as to make flash work in opera we have to install :
-the alsa-oss package
-the flash plugin 
-kaffeine 
and type in command line:
$aoss opera

this should work???? can't help more than this

---

### Post by raovq on 2006-11-15
kaffiene got rid of the alsa error message, but i seem to be no closer to getting sound working.

i restarted alsa, to no help.

perhaps a full reboot or something? im not sure.

---

### Post by soxs on 2008-05-21
Maybe you should try flashplugin 10 beta works fine for me (opera 9.50b2)

[http://ubuntuforums.org/showthread.php?p=5009236#post5009236](http://ubuntuforums.org/showthread.php?p=5009236#post5009236)

---

