---
title: "special characters &amp; the sad story of a lost xterm window"
date: 2008-10-09
forum: Desktop Environments
---

### Post by drew boardman on 2008-10-09
Dear All

I am having a problem with the following:
"Linux / NetBSD: Using the dead-keys. In an xterm window first press the (´) or (`) key. The character should not appear on the screen. Now press a letter, such as "e". The e is given an accent, é or è. If not, then check in the XF86Config file if a "nodeadkeys" XkbdVariant has been loaded there and replace it. You may also have set the environment variable SAL_NO_DEADKEYS, which deactivates the dead-keys." 

1.  How do I know if I am using an "xterm window"?
2.  Anybody know where I can find the XF86Config file?
3.  "If not, then check in the XF86Config file if a "nodeadkeys" XkbdVariant has been loaded there and replace it."  With what?

Thanks for your help.

Drew

ps For those who are interested I can send you my completed CV, in French, with accents, so that you may see the practical results of your advice and help!

---

### Post by cwsnyder on 2008-10-09
1. xterm is a generic term for a terminal window, such as xterm, gnome-terminal, or Konsole.  

2. Can't help here.

3. When someone helps you find the XF86Config file, open it with an editor (gedit, nano, kate, emacs, vim, etc.) and there should be an entry called 'XkbdVariant', which entry might be set to 'nodeadkeys'.

---

### Post by cwsnyder on 2008-10-10
Something of interest on the XF86Config:

Open konsole (or in gnome, gnome-terminal) and type ```
find / -name "XF86C*"
```This should enable you to find if you have an existing XF86Config file.  I found only a sample file which had been gzipped in /usr/share/doc/nvidia-glx-new/examples/XF86Config.sample.gz for my copy of Ubuntu Hardy.  There is no indication where you might put such a config file if you create one, but it probably would be either in the /etc folder or in the ~ home directory folder.

Under the Input devices, you could probably add an option line in the input device section for XkbdVariant.  The following is that section from my sample: ```
#
# Keyboard section
#
Section "InputDevice"

    Identifier "Keyboard1"
    Driver     "Keyboard"
    Option     "AutoRepeat"  "250 30"

    Option "XkbRules"  "xfree86"
    Option "XkbModel"  "pc105"
    Option "XkbLayout" "us"

EndSection
```

---

