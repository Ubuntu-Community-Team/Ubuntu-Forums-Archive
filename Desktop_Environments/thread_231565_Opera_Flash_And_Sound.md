---
title: "Opera Flash And Sound"
date: 2006-08-07
forum: Desktop Environments
---

### Post by Sethro on 2006-08-07
So I have Opera installed and flash works great, but when I try to watch online video from YouTube etc. I get no sound. I searched the forums and tried a bajillion things.

Is there a fool proof method of getting sound to work??

So far tried the following :

-install the alsa-oss package
-reinstalled the flash plugin manually

---

### Post by Ramses de Norre on 2006-08-07
> **Sethro said:**
> 
-install the alsa-oss package

You also loaded opera with "aoss opera" then? (or whatever the command is to launch opera, I don't have it myself)

---

### Post by Sethro on 2006-08-07
Yeah tried just about everything..

I wanted a low CPU/Resource web brower.
I noticed alot of people said that Firefox was a hog and decided to use Opera. Are their any low CPU web browers out there for ubuntu??

---

### Post by Ramses de Norre on 2006-08-07
Epiphany should be pretty lightweight, and it's very firefox/mozilla like.

---

### Post by Sethro on 2006-08-07
Thanks for this, anybody here using Opera know how to get sound to work??

---

### Post by rudiz on 2006-08-07
sudo aptitude install kaffeine

---

### Post by telperion on 2006-08-08
Yes 
```
aoss opera
```


work!!!!

Tnx

---

### Post by Claus7 on 2006-11-09
Hallo,

So, in order to racapitulate, so as to make flash work in opera we have to install :
   -the alsa-oss package
   -the flash plugin 
   -kaffeine 
and type in command line:
   $aoss opera

Could we avoid the command line and still have sound? Because when I open opera from my panel, I cannot have sound from flash (you tube is my example web site).

---

### Post by dannyboy79 on 2006-11-09
> **Sethro said:**
> Yeah tried just about everything..

I wanted a low CPU/Resource web brower.
I noticed alot of people said that Firefox was a hog and decided to use Opera. Are their any low CPU web browers out there for ubuntu??

you want a low cpu/resource web browser but yet you want to run websites that have flash in them, sounds like an oxymoron. i run opera in xubuntu on an old pentium with mmx 266mhz and 128mb ram, i installed flash 9 and when I go to youtube, my computer can't do it obviously it just ain't powerful enough. i think there is also  dillo. that's a pretty small browser. or what about epiphany. (i think that's what it's called)

---

### Post by dannyboy79 on 2006-11-09
> **Claus7 said:**
> Hallo,

So, in order to racapitulate, so as to make flash work in opera we have to install :
   -the alsa-oss package
   -the flash plugin 
   -kaffeine 
and type in command line:
   $aoss opera

Could we avoid the command line and still have sound? Because when I open opera from my panel, I cannot have sound from flash (you tube is my example web site).

you can simply edit the command that runs from your panel. if you have ubuntu, just use alacarte menu editor and then find opera, then hit poperties, then simply change whatever the command states to aoss opera and you should be golden. if you run xubuntu like me, it should be similar but it doesn't use alacarte menu editor, i think the menu editor is under accessories instead. let us know if that works.

---

### Post by Claus7 on 2006-11-09
Hello again,

Many thanks for your answer dannyboy79. You just cought me before I submit a similar answer to yours. I do not know what alacarte menu editor is. What I did, is that I went to opera icon and then I did right click.
Then I went to properties and in command I changed the opera u% (I think it was something like that) and I typed aoss opera.
It works like a dream. Thanks again!

---

### Post by Claus7 on 2006-11-09
I found out what alacarte command editor is. The truth is that even though I had changed the command to aoss opera to my shortcut, in alacarte editor it was unchanged (it was left as opera %u). I changed that also. I have to say that if I type opera in the command line (and only that) I still cannot hear any sound. If only I type aoss opera I have sound. Of cource if I click on my shortcut I have sound too.

I must also say that installing that kaffeine (and some codecs before that) I can play even m4a music files (they are similar to mp3), that I couldn't play before using rhythmbox. That's all. 

I hope that in the next edition of opera this issues will be solved.

---

### Post by raovq on 2006-11-14
i have the same issue. i have alsa-oss.

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

anyone have any ideas?

---

