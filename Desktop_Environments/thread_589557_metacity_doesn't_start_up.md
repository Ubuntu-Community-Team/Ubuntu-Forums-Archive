---
title: "metacity doesn't start up?"
date: 2007-10-24
forum: Desktop Environments
---

### Post by Mr. Tos on 2007-10-24
So, I updated to 7.10 on both my computers. Both were running beryl before, but I decided to go back to metacity. So I uninstalled compiz(-fusion), beryl, emerald, xserver-xgl, all that. On one computer, all is fine. On the other however, Ubuntu starts up without a window manager. I have to manually open a console and type 'metacity' (not even --replace), then it works. I tried adding metacity to the startup programs and when that didn't work exec metacity to xinitrc, but it didn't work either. Creating another user has the same problem, as does loading a failsafe session.

What should I do? I'm a bit confused, since the other computer has no problems even though I did the same thing to it.

Another problem I noticed, that may or may not be related, is that pressing Quit does nothing, I have to ctrl-alt-backspace out (which doesn;'t cause problems). On my old user Quit makes the system unresponsive and the computer seems to be doing things, on my new one the button just doesn't do anything.

Thanks!

---

### Post by Mr. Tos on 2007-10-24
Ah, I found it. For those with the same problem: the gconf key /desktop/gnome/applications/window_manager/default was still at the now non-existing /usr/bin/compiz window manager. Just changed it to /usr/bin/metacity and it worked.

Didn't solve the Quit problem though...still hangs there.

---

### Post by Mr. Tos on 2007-10-24
..and after some searching in this forum the Quit problem is now also solved by enabling gnome-power-manager in Preferences->Sessions .

Even though no one replied, the forum was of use and I hope someone with a similar problem will stumble upon this thread and not waste so much time resolving it as I did :)

---

### Post by ma_chowdhury on 2007-10-26
I have (had) the same problem. Now that you mention compiz, I can recall that the problem started when I removed the compiz packages in synaptic. More details - the initial user in which I had set/unset compiz has no problems with metacity starting up. In another user with administrative privileges, metacity starts up after some 3 minutes. The rest of the users, and any new users, metacity does not start up at all, just like you said.

I could not find the gconf file where the key you mentioned is located. What I did was create a symlink for compiz pointing to metacity in /usr/bin. That solved the problem.

I don't have the problem with the exit button with the existing users (which were created before compiz was removed). New users did have that problem though. but symlinking compiz has solved that also.

---

### Post by Mr. Tos on 2007-10-30
> **ma_chowdhury said:**
> 
I could not find the gconf file where the key you mentioned is located. What I did was create a symlink for compiz pointing to metacity in /usr/bin. That solved the problem.

Glad you solved your problem as well, but for future reference: gconf-editor is what allows you to edit the key directly, rather than having to do the symlink workaround.

---

