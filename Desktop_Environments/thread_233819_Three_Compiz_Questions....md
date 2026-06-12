---
title: "Three Compiz Questions..."
date: 2006-08-10
forum: Desktop Environments
---

### Post by richardq on 2006-08-10
I'm running the Compiz-Quinn packages on Dapper. I've got a few quick questions:

1. The cube now seems to 'step back' or retract and then rotate when I switch desktops. This is slower and more cumbersome feeling than when it just rotated. Is this something that changed recently or is everyone elses just rotating smoothly from desktop to desktop.

2. Also, manipulating the cube with the mouse (ctrl-alt-drag) used to be very easy and smooth on my system but now it seems quite jerky and overly mouse-sensitive. I've played with the compiz settings to no avail. Could 1 and 2 be related?

3. What is the difference between the quinn and vanilla packages? I've installed the quinn packages and maybe they are making the differences. Maybe I should reinstall compiz with the vanilla packages.

Can anybody shed any light on these issues?

---

### Post by jstueve on 2006-08-10
I experience the same hesitation and jerky manipulations, I'm running on a Intel 855gm, and those effects have been present since quinn13 (12 worked fine), it has gotten better (something changed upstream that broke how rotate worked, and it hasn't really be investigated more, as far as I know)

Vanilla is basically CVS compiled for Dapper, with no custom plugins or patches.  Quinn is heavily modifed with customr plugins and patches, but the basic engine stays in sync with upstream.  Plugins from quinn's aren't meant to work with Vanilla.  I tried swapping vanilla in for quinn and experience jerkiness on both.

---

### Post by KFASheldon on 2006-08-10
The same happens here with cube.  I thought it was something I had ticked in settings.

Other issues recently haunting me !!

Top left corner of display sometimes updates out of synch to rest of screen when rotating, or moving windows - very noticable with F12 tile display of open windows.

Windows programs running in wine often leave a window frame from cgwd for any error dialogs that show. Even quiting wine and killing any process associted does not remove these windows - very annoying.

Oh but I do love the new Blur plugin - I wish the default setting was on when it was installed as it took me a while to discover it was disabled ion GSetCompiz ?? works great though and is just like Vista. But I prefer OSX look with slight opaque borders.

---

### Post by Anduu on 2006-08-10
1. To fix the stepping back open gconf editor...

 Go to apps>compiz>plugins>rotate>screen0>options and set the zoom key to 0.

2. Dunno maybe...:p

3. Well vanilla is vanilla and quinn is superfunkalicious ;)

---

### Post by murataht on 2006-08-10
for question 2: you may change the sensitivity of the rotate plugin. use gset-compiz or gconf-editor. after changing mine is working well. but i somehow feel compiz is getting slower. maybe i am wrong. maybe because of the plugins...

---

### Post by richardq on 2006-08-10
> **Anduu said:**
> 1. To fix the stepping back open gconf editor...

 Go to apps>compiz>plugins>rotate>screen0>options and set the zoom key to 0.

2. Dunno maybe...:p

3. Well vanilla is vanilla and quinn is superfunkalicious ;)


You da man Anduu. :) Got rid of that annoying step back. Also I played around with the rotate sensitivity while I was in gconf-editor as murataht suggested and got the cube rotation a little more controllable. But it's still quite choppy compared to a couple of weeks ago. Let's hope they address whatever the problem is.

And yes, superfunkalicious would be the correct term. :)

Thanks for the help.

Richard

---

### Post by Anduu on 2006-08-10
No sweat :D

---

