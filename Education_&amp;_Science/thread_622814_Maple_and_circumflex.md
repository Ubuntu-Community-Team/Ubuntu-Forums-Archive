---
title: "Maple and circumflex"
date: 2007-11-25
forum: Education &amp; Science
---

### Post by kvolden on 2007-11-25
Hi!
I've just installed Maple 11 on Gutsy, and I'm having problems typing the circumflex (^) character. Tilde (~) doesn't work either, but that doesn't matter as much as the circumflex. I had Maple 9 on a previous ubuntu version (feisty, I believe), and I had the same problem there. If I type the characters with another one that supports "modification" (like ô and õ) it works, but not as a standalone character. I don't believe it's a font problem, because I can copy/paste it in without problems.
Does anyone know how to fix this?
I'm fairly new to linux, so I may need to have things pretty thoroughly explained. Sorry about that. :)

---

### Post by ddrichardson on 2007-11-26
Do you only have problems with these keys in Maple?

---

### Post by kvolden on 2007-11-27
Hi, thanks for replying!
Yes, I only have this problem in maple. Maple runs on Java, by the way, and in case it's relevant "java -version" returns the following:

java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

---

### Post by SQuark on 2007-11-27
Not a fix, but a workaround: in Maple you can use ** instead of ^ to denote powers.

E.g.: 2**3; yields 8.

---

### Post by kvolden on 2007-11-27
> **SQuark said:**
> Not a fix, but a workaround: in Maple you can use ** instead of ^ to denote powers.

E.g.: 2**3; yields 8.

Thank you! :) A lot more practical than copy/paste.
Still, if anyone knows how to fix the problem, I'd appreciate it.

---

### Post by zoop on 2007-11-27
Also not a fix but a workaround:

The problem seems to be with dead keys, that is keys that don't print a character immediately but instead can be combined with other characters, like ~ and the a gives ã, and so on...

Many non-US keyboard layouts have such keys and the US International layout also has them.

So the workaround is to use a keymap that does not have dead keys.

In Gnome go to System->Settings->Keyboard (translated from German). Then switch to the "Layouts" tab. On the bottom you can select a secondary layout. Select one that has no dead keys, for instance the default US layout or the "Eliminate dead keys" variant of your usual layout. Make sure that you set the default keymap to the one you're normally using.

Another important option is the "Seperate layout for each window" which means that you can set the used layout seperately for each window. It's a matter of taste whether you want this option or not, but I always disable it because it tends to create confuse me :)

Now go to the "Layout Options" tab and go to "Group Shift / Lock" behavior and select a key combination to change the layout permanently (until you change it back) or temporarily (only as long as you press the key). I chose "Both Alt keys together change group."

I would also suggest to add the "Keyboard Indicator" (translated from German) applet to your Gnome panel. For this, right click on an empty area of the panel, select "Add to panel..." then select "Keyboard Indicator". This applet will show which layout you're currently using, which can help avoid confusion...

Now all you have to do is to open Maple or Matlab and when the Matlab / Maple window is active press your key combination to change the layout. You should see the change in the "Keyboard Indicator" applet. When the layout without dead keys is active you should have no problem entering ^, ~ and similar characters.

Hope this helps :)

---

### Post by kvolden on 2007-11-27
Thanks for your answer, but as the problem only affects one key, for my practical use, I think I'll stick with the ** workaround until I can fix the problem itself. But thanks! :) The trick might come in handy for later.

---

### Post by tuwe on 2007-11-30
hi,

i think this is a java related problem.
you might try the suggestions from this thread: [http://ubuntuforums.org/showthread.php?t=597890](http://ubuntuforums.org/showthread.php?t=597890)

hope this helps

---

