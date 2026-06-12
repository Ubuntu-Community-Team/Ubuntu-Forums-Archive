---
title: "[SOLVED] alt-tab is dead"
date: 2007-11-21
forum: Desktop Environments
---

### Post by Titi on 2007-11-21
hello
i've been playing a bit with Compiz (Advanced Desktop Settings) and now the alt-tab function is gone.
In Compiz, i had binded the combination to the ring switcher. Then i had to disable Copmiz because Matlab wouldn't work (a whole other story) and now without the advanced desktop settings, alt-tab doensn't work anymore. I've tried "Keyboard Shortcuts", but nothing changed.
would anyone now how i can get my beloved Alt-Tab function back?

---

### Post by jorgehumberto on 2007-11-26
HI!

The same happened to me...also while playing to compiz...
 besides" ALT-TAB" ive also lost" CTRL-ALT-ARROWS"... 

any sugestion on how to recover them?

Thanks in advance!

---

### Post by Znort_Ubern00b on 2007-11-27
Its only a guess but maybe if you remove the keystrokes in compiz and retry the keyboard shortcuts thing it may work. it might just be that those keystrokes are now used by compiz and need to be "released" for want of a better word.

---

### Post by jorgehumberto on 2007-12-02
hum.. i even removed compiz and nothing.... the only way i can seem to get this working is if i enter in Gnme failsafe mode... but as you might imagine it it not a perfect solution.. ;)

i do not know if it is related, but i also get a message saying "error activating XKB configuration"... does it help?

---

### Post by Titi on 2007-12-12
i've tried disabling the compiz shortkeys etc, even tried doing some things in the gnome configuration editor, but nothing helped. i could enable compiz again, but i don't like the ring switcher. i'd really like my alt-tab back!

---

### Post by Lostincyberspace on 2007-12-12
Okay this should only take a little bit.

first go to system>preferences>Keyboard Shortcuts

then for alt-tab go to "move between windows with popup" and set it to alt+tab

then go to "switch to workspace on the left" and set it to ctrl+alt+left

And finally go to "switch to workspace on the right" and set it to ctrl+alt+right

That should fix it. Let me know how it goes.

Edit: I just saw that you tried this but if someone else needs it I will leave it up.

---

### Post by Lostincyberspace on 2007-12-12
In keyboard preferences make sure alt win behavior is set to default.

---

### Post by Titi on 2007-12-17
i've noticed some strange things. in 'Keyboard Shortcuts', For "move between windows in popup", it had 'disabled' in italic, and for the other shortcuts, 'disabled' is not italic.
also in gconf-editor, in apps-metacity-global_keybindings, switch_windows is "not writable", so i can't change it at all. 
i guess that's got something to with it, but i can't solve it...

---

### Post by Lostincyberspace on 2007-12-17
If I were you I would reinstall just to make it all clean, since on first install I have almost no problems, at least with gutsy. Make sure to back up your home folder and any other things you need if you do reinstall though, I have forgotten to do it before and it was terrible.

---

### Post by Titi on 2007-12-18
isn't that a bit drastic? i could just reinstall gdm, no?

---

### Post by Titi on 2008-02-12
i have finally found the solution. for people who might have the same problem:
i had to run gconf-editor, then go to apps>metacity>global_keybindings and unset the key for switch_windows
that did the trick.

---

