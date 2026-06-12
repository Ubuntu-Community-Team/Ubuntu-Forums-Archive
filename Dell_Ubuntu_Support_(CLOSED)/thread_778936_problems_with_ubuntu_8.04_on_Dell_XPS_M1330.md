---
title: "problems with ubuntu 8.04 on Dell XPS M1330"
date: 2008-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Apertotes on 2008-05-02
hi, i am a new linux user. i installed ubuntu 7.10 three months ago on my Dell XPS M1330, and this week i upgraded to 8.04

since the change i am having some issues that i havent found solution for.

1. Multimedia keys do not work, or work badly. the only ones that work are play/pause, stop and mute. next, previous, volume up/down do not work at all. they do not work on the built in keyboard, nor on the logitech MX5000, nor on the dell remote control.

trying to configure them on "key combinations" (dont know the proper English name, in spanish is "Combinaciones de teclas") does not work either. out of the 7 different keys (play/pause, stop, next, previous, volume up, volume down, mute) only 3 are recognized. for example, the "stop" key and the "next" key are both recognized as "XF86AudioNext". the "play/pause" and the "previous" key are both recognized as "XP86AudioPrev".

this means that i can not give a different function to those keys.

the volume keys are recognized all right, but nevertheless, they do not work. again, they do not work on any of the three devices i have. i tried opening the sound control to see if those keys affected the volume on a different channel other than "Master" or "Front", but apparently they do not affect any device or channel at all.

oddly, the mute key works perfectly, on the "Front" channel.

2. keyboard brightness control has only 3 positions, instead of the 10 it had previously.

3. window shadows (emerald setting) do not work, or if they do, they appear on strange colours. it seems quite random. every time i restart the comp the shadows are a different colour or they do not appear at all, but they are never black, as they should. playing with emerald settings does nothing at all.

4. the system needs quite a longer time to start. and sometimes it says it can not start the graphic client, and it works only on text mode. restarting usually solves this problem.

also, i have observed how while starting the system appear a lot of text lines while the different drivers, modules and devices are being loaded. i remember this happening also during the first days after i installed ubuntu 7.10, and then it went away and only the splash screen was shown. can anybody explain to me why those text lines are appearing again?

-------------------------------------------------------------------

i think this is all for now. of course, all those issues worked perfectly fine last week with ubuntu 7.10, without need of any additional program (with this i mean that i would love to make them work again without any external utility).

can anybody help out with them?

---

### Post by ethanay on 2008-06-04
0.  Sorry no one has even replied to you yet...that's bad.  Have you resolved any of the problems?

1.  is hotkey-setup installed?  it should detect the keys and produce codes which allow you to assign them to keyboard shortcuts menu in > system > preferences

what bios version do you have?  try updating to the latest, a10.  also, it is possible that you have broken hardware :confused:

2. this is a common problem, it is annoying but i am waiting for a fix.  you can try to blacklist "video" module -- people say it works for them but i tried it and it gave me some worse problems with video (disappearing/graphical corruption) and touchpad not working well.  so i tolerate it right now.

3. don't know anything about shadows...what video card do you have?  what driver?

4.  are you sure ubuntu isn't restarting with the kernel in recovery mode?  i think that is a text prompt.  i don't know why it switches back and forth, though.

---

### Post by Apertotes on 2008-06-04
> **ethanay said:**
> 0.  Sorry no one has even replied to you yet...that's bad.  Have you resolved any of the problems?

1.  is hotkey-setup installed?  it should detect the keys and produce codes which allow you to assign them to keyboard shortcuts menu in > system > preferences
[COLOR="Red"]
yes, it is installed. the problem is that it doesnt creates as many codes as keys. for example, both "next" and "play/pause" are recognised as 00xnext (or something like that, but the same code), and the same happens with "previous" and "stop".

this behaviour is the same on the laptop keyboard, on the remote control and on the external logitech MX5000[/COLOR]

what bios version do you have?  try updating to the latest, a10.  also, it is possible that you have broken hardware :confused:

[COLOR="Red"]yes, my bios is a10. i do not think it is a matter of hardware, for 2 things. first one, the problems appear on 3 different places. and second, somedays (it seems random), suddenly media keys work allright. and suddenly they stop working again[/COLOR]

2. this is a common problem, it is annoying but i am waiting for a fix.  you can try to blacklist "video" module -- people say it works for them but i tried it and it gave me some worse problems with video (disappearing/graphical corruption) and touchpad not working well.  so i tolerate it right now.

3. don't know anything about shadows...what video card do you have?  what driver?

[COLOR="Red"]nvidia 8400M GS. drivers... i am not sure. i just run ENVY and let it choose for me. anyway, this problem with emerald shadows has already resolved. i guess a patch/actualization did it.[/COLOR]

4.  are you sure ubuntu isn't restarting with the kernel in recovery mode?  i think that is a text prompt.  i don't know why it switches back and forth, though.
[COLOR="Red"]
i believe it is not in recovery mode, cause i have it set so that it always starts GRUB, and there, on the menu, there is the option for recovery (and memtest, and past kernels), but i always choose regular boot.

what bothers me is that it happened also the first weeks with 7.10, and suddenly it went away and only the splash screen was shown, and now it happens again, but it doesnt go away.[/COLOR]

thanks for your answers

---

### Post by JacquiOh on 2008-06-04
Hey, I have a 1330 and mostly it's working with 8.04. I had the "pink shadows" and yellow shadows but

[This worked.]("http://tombuntu.com/index.php/2008/04/28/workaround-for-pink-shadows-with-compiz/")

And I'm having the same issues with the brightness settings so let me know if you find the answer!

---

### Post by Technoviking on 2008-06-04
1. Unsure, the multimedia keys for great for me. I did do a clean install and not an upgrade.

2. This is how I fix it. [http://ubuntuforums.org/showpost.php?p=5009164&postcount=3](http://ubuntuforums.org/showpost.php?p=5009164&postcount=3)

3. I saw this during Hardy Alpha/Beta, but this problem went away for me in the Ubuntu 8.04 final.

4. Hmmmm...

If you are willing, I would try a clean install. I wondering if some of your xorg packages did not upgrade properly.

---

### Post by mikull on 2008-12-30
i have the same issue on my xps m1330 as well. the volume keys dont work at all. not even the mute,but u know what,when i press them,i get the volume meter on the screen,but the bar seems to be greyed out. 
the paus,next and stop work thou.
any ideas?

---

### Post by eyime on 2009-01-01
Hi everybody,

Well, I did a clean install of Ubuntu 8.04 and everything was fine. However recently I have noticed that the volume control doesn't work, there is a pop-up with a bar, but the volume doesn't change, but if I click the mute button and then the decrease volume, there is a change in the bar and also in the Mux 2 (in recording tab inside volume control).

So, it seems the system recognize the key but affect the wrong volume. I tried setting the keys in System->Preferences->Keyboard Shortcuts but nothing happens.

Any idea ??

---

### Post by nanog on 2009-01-01
The key binding problem is fixed in intrepid. In fact (for me) *everything* works in intrepid. Even the annoying nvidia window decorator artifacts have disappeared after a recent update:

```
$ dpkg -l | grep nvidia-glx-177
ii  nvidia-glx-177                             177.82-0ubuntu0.1 
```

---

### Post by eyime on 2009-01-01
Well,

after reading another solutions, I learned about the gconf-editor, so I opened a console ( [Ubuntu logo] Applications -> Accessories -> Terminal ), then I typed "gconf-editor", and in the new window I went to desktop -> gnome -> sound and I changed "default_mixer_tracks" to "[Master]". I really don't know why it was set to "[Mux 2]".

The others settings are:

default_mixer_device    alsamixer:hw:0
enable_esd             (clicked)
event_sounds           (clicked)

---

### Post by Yeti can't ski on 2009-03-16
> **mikull said:**
> i have the same issue on my xps m1330 as well. the volume keys dont work at all. not even the mute,but u know what,when i press them,i get the volume meter on the screen,but the bar seems to be greyed out. 
the paus,next and stop work thou.
any ideas?


Hey, I had exactly the same problem and this solved it form me!

[http://ubuntuforums.org/showthread.php?t=781084](http://ubuntuforums.org/showthread.php?t=781084)

---

