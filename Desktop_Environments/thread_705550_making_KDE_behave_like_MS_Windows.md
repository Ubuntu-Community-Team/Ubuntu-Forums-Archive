---
title: "making KDE behave like MS Windows"
date: 2008-02-23
forum: Desktop Environments
---

### Post by john_spiral on 2008-02-23
Does anyone know any good HOWTO's / blogs that detail how to configure KDE so it behave exactly like MS Windows from the keyboard.

I've tried the System Settings -> Keyboard & Mouse -> Keyboard Shortcuts.... settings but I'm unable to configure basic Window keyboard shortcuts like (alt + space bar +N) to minimize a window?

---

### Post by mrsteveman1 on 2008-02-23
There is a program in KDE called kpersonalizer (i think), that lets you set how the environment works. I know it works to change single click to double click, window behavior etc.

Not sure about keyboard combinations though.

---

### Post by samwyse on 2008-02-23
I don't think it's possible to set a weird combination like that.  You can press the modifiers you want (ctrl/shift/alt/win) + one key.

---

### Post by john_spiral on 2008-02-23
thanks mrsteveman1!

kpersonalizer seems to have done the trick.

The Windows key doesn't work by default but I'm sure google will hopefully turn up some joy.

---

### Post by john_spiral on 2008-02-23
I got the left Windows key to work from the below site:

[http://opengecko.wordpress.com/2008/02/20/make-the-windows-key-on-your-keyboard-open-kmenu-in-kde/](http://opengecko.wordpress.com/2008/02/20/make-the-windows-key-on-your-keyboard-open-kmenu-in-kde/)

note you will need to go to:

KDE Control Center -> Keyboard & Mouse -> Keyboard Shortcuts-> Global Shortcuts -> Panel -> Popup Launch Menu 

Choose custom & assign an alternate shortcut by pressing the left Windows key.

Does anyone know how to assign 3 keyboard shortcuts to the same action?

My right Windows key doesn't get assigned in the above screen ;-(

---

### Post by john_spiral on 2008-02-24
Another question, does anyone know how to assign as the key combination (F13 + M) in the below screen?

[IMG]http://www.safewaytobank.com/snapshot1.gif[/IMG]

---

### Post by john_spiral on 2008-02-24
FYI:

The below file contains the KDE key bindings

~/.kde/share/config/kdeglobals

Adding the below edit to the file doesn't allow me to minimize all Windows via the (Windows Key + M)?

**Toggle Showing Desktop=Win+D;F13+M**

any ideas?

---

