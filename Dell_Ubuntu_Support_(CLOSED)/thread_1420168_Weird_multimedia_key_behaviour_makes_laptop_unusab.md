---
title: "Weird multimedia key behaviour makes laptop unusable"
date: 2010-03-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by osterchrisi on 2010-03-02
Hi!

I got my Dell Studio 1558 today and I come across a weird problem: The "Mute" button and the "Eject" button work perfect, but as soon as I press a "Volume Down" or "Volume Up" button, it seems to repeat the call as long as until the slider reaches either end of the scale.

The message window on the top right is then popping around like crazy and after some seconds of popping around there the mouse and the keyboard won't work anymore. I can still move the mouse but I cannot click anything and the keyboard doesn't react at all.

Not to mention that I don't have sound at all... But ok, that problem seems more fixable to me...

Does anyone have a clue about this?
Thanks for any help!!!

---

### Post by osterchrisi on 2010-03-03
Ok, at least I have sound now! As obviously with a lot of Dell laptops it helped with mine to add
```
options snd-hda-intel model=dell-m6
```
to my alsa-base.conf file.

I can now hear, that the buttons have an effect on the volume (goes either way all up or all down) but still my input devices (mouse, keyboard) won't work properly after using them as described in the above post.

Is there any special call where I could start looking at or something??

---

### Post by lz1dsb on 2010-03-12
Strange, I have Dell 1555 running 64-bit Karmic and haven't encountered that problem so far. I'm wandering if 1558 is so much different from 1555... For me that worked just out of the box.

Cheers,
Boyan

---

### Post by coatzin on 2010-03-12
I have the same issue with function keys in Dell Studio 1557, don't have a clue on a real solution... what I did was change in bios to function keys first... then in keyboard configuration set the function keys to have the multimedia function...

of course you loose the function of function key :-|

---

### Post by lz1dsb on 2010-03-12
Did you also had the problem that when the multimedia keys were active, you're unable to use the function keys? It's quite uncomfortable when you need for example to start a tty session. Ctrl+Alt+F1 for example doesn't work... I read in the forums that disabling the multimedia keys functionality solves this. I just haven't had the time to try this though...

Cheers,
Boyan

---

### Post by coatzin on 2010-03-12
> **lz1dsb said:**
> Did you also had the problem that when the multimedia keys were active, you're unable to use the function keys? It's quite uncomfortable when you need for example to start a tty session. Ctrl+Alt+F1 for example doesn't work... I read in the forums that disabling the multimedia keys functionality solves this. I just haven't had the time to try this though...

Cheers,
Boyan

No... well, **Ctrl+Alt+F1** doesn't work but **Ctrl+Alt+Fn+F1** works just good

---

### Post by lz1dsb on 2010-03-13
Thank you! It really works. I was searching for that and even looking for a ways to remap that key combination. Now I know what the Fn key is used for :P

Greetings,
Boyan

---

### Post by osterchrisi on 2010-03-15
Hey I found a solution here: [http://ubuntuforums.org/showthread.php?t=974723&page=6]("http://ubuntuforums.org/showthread.php?t=974723&page=6")

---

### Post by coatzin on 2010-03-19
> **osterchrisi said:**
> Hey I found a solution here: [http://ubuntuforums.org/showthread.php?t=974723&page=6]("http://ubuntuforums.org/showthread.php?t=974723&page=6")

Thanks, works fine!

---

