---
title: "Pidgin - I cannot use my B key, PLEASE HELP!!!"
date: 2009-02-10
forum: General Help
---

### Post by solvision on 2009-02-10
Hey Guys

Wasn't sure where to post this.

I've just recently switched in Ubuntu 8.04. Loving it a lot. Just wish i could get my external monitor to full widescreen.

ANYWHO...i am using pidgin for IM and about 5 days ago, my B button stopped working when i am typing messages. Now it only controls the toggle for logging on/off.

This is driving me crazy, i use it for work a lot and cannot find ways to say a lot of things without using the letter B. I have tried the following to fix it:

- Remove a global shortcut i had that was using Alt+B. Rebooted.
- Reinstalled Pidgin. Rebooted
- Completely removed Pidgin and reinstalled. Reboot
- Completely removes Pidgin and depackaged 2.5.4 from Deb files. Reboot.
- Turned off logging completely in the preferences section and the chat window menu.

None of it had any effect.

Everything works fine, except this.

Someone PLEASE HELP ME, it seems no one has had this problem before, i have searched for the past few days and found NOTHING.

---

### Post by x C0MMAND0 x on 2009-02-10
Did you "completely" remove Pidgin using:

```
sudo apt-get purge pidgin
```

Because just using remove won't get rid of all settings and what-not which may be causing your issues...

---

### Post by solvision on 2009-02-11
I hadn't purged.

But isn't that the way it happens. You spend days searching for an answer. Then soon as i post in three linux forums i finally find the answer after all :) haha

OK The problem was, B is a binding key (i didn't know that term, which would limited my searching queries). Usually those kinds of keys are accompanied by Ctrl, Alt or Shift, etc. In this case it was only B, no special combination of keys.

I fixed the problem by using the following:

sudo gedit ./purple/accels    

then changed this line:

(gtk_accel_path "<main>/Options/Enable Logging" "b")

to this:

(gtk_accel_path "<main>/Options/Enable Logging" "<Control>b")

Problem Solved.

This was where i eventually found the solution: [http://developer.pidgin.im/wiki/shortcuts](http://developer.pidgin.im/wiki/shortcuts)

Thanks for the help anyways.

---

### Post by khc on 2009-02-12
you can also hover over the menu item and press backspace

---

