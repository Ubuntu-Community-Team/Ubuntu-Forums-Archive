---
title: "Beryl &amp; Compiz both freeze computer on loading"
date: 2007-03-18
forum: Desktop Effects &amp; Customization
---

### Post by StevenX on 2007-03-18
I was checking out some settings on Beryl this afternoon (after having had it succesfully installed and working great for 2/3 days), when I ticked the option which has something to do with trails (windows not used for a while become transparent). Suddenly, the computer froze and only the mouse cursor could be moved.
The only way to boot the computer normally was to remove Beryl via the failsafe terminal after pressing CTRL-ALT-Backspace at startup (the desktop wouldn't load at all - plain brown screen). I then removed beryl-manager from the session startup list so that if it had any more problems on reinstall it wouldn't stop the computer booting up. Then I reinstalled Beryl, and upon trying to start it the same thing happened every time - everything froze, but the cursor could still be moved (although nothing on screen could be clicked upon). Deciding I'd maybe broken Beryl, I tried to install Compiz. Upon trying to run that (activating the GL desktop), the exact same thing happened once again, producing the following error messages in the terminal (Beryl didn't seem to produce any before crashing). Does anyone have any idea what they are and how to fix them? This is really frustrating!

I'm using Ubuntu Edgy, and have the latest NVidia drivers installed (the same ones installed when Beryl was working before).

(compiz-tray-icon:5405): GLib-GObject-WARNING **: invalid (NULL) pointer instance 

(compiz-tray-icon:5405): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 

(compiz-tray-icon:5405): GLib-GObject-WARNING **: invalid (NULL) pointer instance 

(compiz-tray-icon:5405): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

Thanks in advance for any advice.

---

### Post by StevenX on 2007-03-18
I've got this working myself eventually - Beryl must have messed up the xgl conf file when it crashed as there were a couple of things missing from it. Since putting those back in/out, it's all better.

---

### Post by edam on 2007-04-05
Hmm, I'm having the same problem, also with an NVidia card. I've had an old version of compiz installed previously and I've just upgraded to Edgy and compiz at the same time. It took me several minutes to get the window-decorator working again, and now it freezes when I enable "GL desktop"...

What did you do to fix yours? Would you mind posting your xorg.conf  (or whatever you fixed)?

Thanks!

---

