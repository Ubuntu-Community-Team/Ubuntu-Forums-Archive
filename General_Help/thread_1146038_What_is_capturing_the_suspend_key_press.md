---
title: "What is capturing the suspend key press?"
date: 2009-05-02
forum: General Help
---

### Post by icedfusion on 2009-05-02
Hi,

I want to re-map my suspend keypress, but this particular key does not appear to be disabled.

What I have tried so far:

1. System->Prefs->KeyBoard Shortcuts. Key is already disabled, so is being captured by Ubuntu somewhere else
2. CCSM (Compiz Config Settings Manager) - Cant seem to find anything relating to suspend key here

3. Added:
# Screensaver
"gnome-screensaver-command --activate"
   XF86Sleep
To my xbindkeys file - no joy as the keypress is caught before xkeybinds gets it. Also, xbindkeys does not give me the keycodes as the key is captured before it gets to xbindkeys-config. I have also tried 'xev' to capture the key.

If I go to: System->Prefs->Power Management, I can set what happens when I press the suspend key (I have changed it to nothing) so this proves that the keypress is being caught, but where oh where is the mapping for this?

Any pointers greatly appreciated.

Cheers

ice.

---

