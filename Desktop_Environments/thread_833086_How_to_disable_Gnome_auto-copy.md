---
title: "How to disable Gnome auto-copy"
date: 2008-06-18
forum: Desktop Environments
---

### Post by karlwilbur on 2008-06-18
I have somehow managed to enable some auto-copy feature of gnome and I cannot turn it off. It is driving me nuts.

When I select a block of text, it automatically gets copied to the clipboard. I can see how this _could_ be a good thing, but not for me since I usually select another block of text to be replaced from the clipboard contents only to find the Ctrl+v now pastes the unwanted text. I am a programmer and I usually stick to the keyboard; a "keyboard-centric" user. For me, copying a block of code from a file usually involves holding shift while manipulating the arrow keys. But with this feature enabled, as soon as something is selected (a character, a word, a line) it gets copy to the clipboard and a new select process begins. This just does not work for me.

This is happening in more than one application (GEdit, Komodo, Firefox, Thunderbird...just to name a few) so it is not application specific. Must be a gnome feature.

I am running Ubuntu 8.04.

I know that there must be something that I am doing to enable it (hot-key, kybd & mouse combo, etc.), I just don't know that is. This is not the first time that this has happened. I have had it come and go, sometimes weeks between instances. Meaning that I accidentally enabled this feature and just as accidentally disabled it. So based on this I know that it can be disabled. 

I think that this all started when I upgraded to Hardy. FWIW.

I am a fairly competent Linux user and have been using Linux exclusively on all my my laptops and desktops for years. I switched to Ubuntu for everything (laptops, desktops, servers) about at 6.10.

That said, this is only happening on my primary desktop. Everything else is just moving along normally.

I have looked though gconf-editor and cannot see a key that would disable this feature.

I am usually able to sort this kind of thing out but I am totally at a loss here.

Any help would be greatly appreciated.

---

### Post by arrix on 2008-09-07
I'm having exactly the same problem. Selecting text by dragging mouse always overwrites clipboard. 

I know there are 2 (actually 3) "clipboards" in ubuntu, one managed by x window (PRIMARY or selection) and the other by the desktop environment (CLIPBOARD or Ctrl+c clipboard). see [http://www.jwz.org/doc/x-cut-and-paste.html](http://www.jwz.org/doc/x-cut-and-paste.html) for details.

The two clipboards should be independent.

---

### Post by arrix on 2008-09-07
I found ctrl+c automatically "pressed" each time after I selected some text in GNOME.
Try select some text in the terminal prompt to see if it goes to a new line (ctrl+c doesn't copy anything in terminal but it interrupts current command and start a new line).

I am running Ubuntu 8.04 in VMWare workstation 6.0.4.
I suspect it's vmware who sends ctrl+c automatically.
Uninstalling VMWare Tools doesn't solve the problem.

---

### Post by arrix on 2008-09-07
I was wrong again. VMWare didn't do anything bad. It was my Lingoes translator's zoned word translator auto sending Ctrl + C.  Disabling the feature solves the auto copy problem.

---

### Post by kindzal on 2009-08-21
same problem. In my case it is the nx client the automatically sends ctrl +c on selected text. Very annoying.

---

### Post by Goatrancer on 2010-04-21
Yes, how does one turn this feature off? It's very annoying.

---

