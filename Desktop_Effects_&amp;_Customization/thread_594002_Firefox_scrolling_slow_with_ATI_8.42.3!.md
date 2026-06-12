---
title: "Firefox scrolling slow with ATI 8.42.3!"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by MicroChris on 2007-10-27
Hey all,

I just installed the new ATI 8.42.3 drivers, and after much hacking and tweaking I got them working, with AIGLX and Compiz. 

Everything is fast (enough) and I haven't come across any bugs yet, except for one.

The scrolling in Firefox is painfully slow with the new drivers. Is there a fix for this or anyway to make it faster? It doesn't sound like a big deal but I spend a lot of time surfing and scrolling.

Thanks!

---

### Post by praxis22 on 2007-10-27
AIGLX is slow at present, use XGL That'll work properly.

---

### Post by MicroChris on 2007-10-27
Bah, the reason I put the new drivers on was so I didn't have to go through the XGL crap..

Noooo! :(

---

### Post by Melcar on 2007-10-27
All ATI users are experiencing slow scrolling with Compiz enabled.  Screen flickering is another big one.  Hopefully most of these issues get resolved by the next release.

---

### Post by sp0onman on 2007-10-27
and slow downs with some compiz effects. i uninstalled them and put the 8.40 ones back on with xgl. simple enough to do, dont know what you mean goin through all the xgl crap. you type one line in the terminal and with gutsy just restart. easy.

---

### Post by NoVista on 2007-10-27
ATI released these simply to give us all a peek at what's to come. The drivers are immature.

---

### Post by raul_ on 2007-10-27
It doesn't happen with Opera. Weird

---

### Post by riverfr0zen on 2007-10-27
> **sp0onman said:**
> and slow downs with some compiz effects. i uninstalled them and put the 8.40 ones back on with xgl. simple enough to do, dont know what you mean goin through all the xgl crap. you type one line in the terminal and with gutsy just restart. easy.

Besides CPU consumption, XGL works pretty well - however, there are one or two really annoying things with it - for example, the gnome screensavers don't work for me, regardless of their settings - by default the screen just goes black after a few minutes.

---

### Post by praxis22 on 2007-10-27
You can get around that with Xscreensaver, the screen going black is a driver issue, not gnome, mine kicks in, then straight back out again.

---

### Post by mastercho on 2007-10-27
i got the same issues, but different hardware, using xgl i think. intergrated intel graphics chip. scrolling in FF or even nautalis trying to browse my home folder or other drives is painfully 1 frame per second.

---

### Post by MicroChris on 2007-10-27
I reverted back to the restricted driver with 7.10 and installed XGL. I didn't realize it was so painless. It didn't always used to be!

Everythings fine again.

---

### Post by bergmanman on 2007-10-28
How do I go back to the restricted drivers and XGL and still have direct rendering?

Ubuntu 7.10 with ATI/AMD Radeon Xpress 1100.

---

### Post by raul_ on 2007-10-28
i just switched to Opera :P everything else is very snappy

---

### Post by NoVista on 2007-10-28
Fusion is "snappy"?
What's your setup?

---

### Post by raul_ on 2007-10-29
I confess that maximizing is not so snappy :P (restore is though). But scale, expo, minimize and close animations, etc, it's all good

What do you want to know about my setup?

I think using Arch also helps, because in Ubuntu my animations were laggy.

---

### Post by zealotbr on 2007-11-13
so...     no way to get things ok with ATI 8.42.3 ?

i cant go back to restricted drivers coz i wanna play wow and need direct rendering.

my contact -> [email]rafael.gidra@gmail.com[/email]

tnksss

---

### Post by manuelg on 2007-11-13
Maybe this can help.....(found it on OS novice)

If you are using firefox in Ubuntu Linux, you might have wondered how you can change mouse scroll speed.
To do that, you should roll up your sleeves and go to the hidden firefox settings. In address bar type:

about:config

You will see a textbox and a long list of options and settings. In the "filter" textbox type:

mousewheel.withnokey.sysnumlines

Change the default value to "false". Then type:

mousewheel.withnokey.numlines

The default value is "1". Increase this number to have faster scroll speed in firefox. I personally prefer "6".
You don't even need to restart firefox to see the changes. They take effect on the fly.

):P

---

