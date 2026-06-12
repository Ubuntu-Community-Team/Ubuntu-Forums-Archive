---
title: "setting &quot;tilde&quot; key in gconf-editor??"
date: 2008-03-09
forum: Desktop Environments
---

### Post by sindyr on 2008-03-09
In gconf-editor, under apps/metacity/global_keybindings there is a setting for "panel_main_menu".  I want to set this to Windows-tilde (techincally, Mod4-grave or Mod4-backquote).  However, while I can set that function to a lot of different keys, including "<Mod4>q"  (I hit windows-q and my ubuntu "start" menu comes up.), nothing I have tried seems to work - <Mod4>Backquote, <Mod4>Tilde, <Mod4>Grave - nothing.

How can I assign this to the windows-tilde combination?

---

### Post by sindyr on 2008-03-10
Still need to know...

---

### Post by sindyr on 2008-03-10
*This* is an impossible question??

---

### Post by sindyr on 2008-03-12
Well, I still don't have the answer to this question - do you?

---

### Post by sindyr on 2008-03-22
I still need this.

---

### Post by sindyr on 2008-03-25
So I guess I am gonna assume that this thread is dead and that there is absolutely no way to set the tilde key as a shortcut..

Can someone email me @ [email]benn@4efix.com[/email] if theres any further to be done, as I am not going to keep monitoring this thread after no action for a week.

Thanks.

---

### Post by crocowhile on 2008-03-26
what about simply:
<Control>grave
?
it works for me.

---

### Post by sindyr on 2008-03-27
Thanks for confirming that usage.  Once I had the confirmation, I was able to investigate further and determined that Control-grave was being used by a Compiz shortcut.  Removing that shortcut fixed the problem and allowed Gnome to take control of that combo.

Thanks.

---

