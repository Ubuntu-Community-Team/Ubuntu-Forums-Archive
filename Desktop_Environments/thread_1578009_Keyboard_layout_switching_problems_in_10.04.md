---
title: "Keyboard layout switching problems in 10.04"
date: 2010-09-19
forum: Desktop Environments
---

### Post by CaspianCanuck on 2010-09-19
Hi,

A few months ago I upgraded one of my Ubuntu boxes to 10.04.1 and haven't been able to switch keyboard layouts ever since.  I have US and Russian Phonetic keyboards and used to be able to switch between them using the keyboard switching panel applet back when I was using Karmic Koala.  Now the applet is gone and not even available in the list of applets.  

I understand the applet has been removed in the new Ubuntu.  But why?  And what other means of switching keyboard layouts are available now?

The trouble is that I have never been able to switch layouts without the applet -- none of the keyboard shortcuts I tried under Preferences > Keyboard > Layouts ever worked in any version of Ubuntu.  Now I can't even test the Russian layout inside the Layouts tab, i.e. when I select Russian Phonetic and type something in the test box below I keep getting US layout characters.  

Any ideas what might be wrong with my system?

---

### Post by CaspianCanuck on 2010-10-05
It's been a couple of weeks since I posted my question and there have been no replies. 

What's with the dead silence?

---

### Post by CaspianCanuck on 2010-10-05
Perhaps I need to clarify my issue:

It's not so much about the keyboard layout applet. The problem is, I cannot switch the layout at all even with the Alt+Shift combination that is configured in the options.

Any thoughts?

---

### Post by Raugturi on 2010-10-05
Try running gnome-keyboard-properties and on the Layouts tab click Options.  Then go to the "Key(s) to change layout" section and set the binding to whatever you want.  If that still doesn't work maybe something else is conflicting with it.

---

### Post by CaspianCanuck on 2010-10-06
Raugturi, thanks for your reply!  Perhaps I wasn't clear enough in my post, but I had been doing exactly what you said and it just doesn't work for me.

Any idea what might be conflicting and how I could fix it?  I would hate to have to reinstall the OS but ability to switch between keyboard layouts is very important for me.

---

### Post by simosx on 2010-10-08
Try to change the shortcut that switches layouts. Try, for example, Shift+Shift instead. You can change in the Layout Options in the Layout tab of the Keyboard Preferences.

---

### Post by CaspianCanuck on 2010-10-15
I have tried all sorts of suggestions but none seem to work.

It's not just that I cannot switch the layout with a key combo but I can't even seem to get a non-English layout to work inside the Layouts window (Preferences > Keyboard > Layouts).  What I mean is, before the upgrade I was able to test a layout by switching to it in the Layouts window, then typing in the test box below, and the letters would be in the selected language.  But now it doesn't happen (i.e. I'm getting English characters no matter which layout I select in the list, which makes me think that the entire keyboard layouts module in my Ubuntu is somehow broken.

Is there a way to completely reinstall the keyboard subsystem (for the lack of a better term) in Ubuntu?

---

