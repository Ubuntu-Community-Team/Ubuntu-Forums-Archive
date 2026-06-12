---
title: "compiz: alt button makes current window minimize"
date: 2006-07-28
forum: Desktop Environments
---

### Post by hotani on 2006-07-28
As much as I hate to start yet another frakking Compiz thread... and as much as I want to swear off it once and for all, I just can't let this one go. 

On 2 machines I'm running it seems the latest update has --ONCE AGAIN-- locked my 'ALT' key to minimizing the current window. This is on two completely separate systems, one running nvidia the other a Dell box running aiglx.

Did I mention that this has happened before?

I really, really, really hate compiz - and yet I can't stop using it. I seriously need counseling. Can we start a support group or something?

---

### Post by hotani on 2006-07-28
ZOMG!!111 It's a miracle! I fixed all my Compiz problems with one command (bookmark this page so you don't lose this ever-so-important HOWTO):

```

metacity --replace

```

so... nobody else is getting the alt key problem eh?

---

### Post by rdd on 2006-08-03
I have that problem too. My shift key doesnt work either, which is worse. Have you found a solution{questionmark}

rdd

---

### Post by rdd on 2006-08-07
Just to wrap this up: 

I fixed this on my computer by adding the -kb in my /etc/gdm.conf-custom like so

```
[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer **-kb**
flexible=true
```

This is on an Acer TM 8100 with an ATI X700

Maybe it helps. 

rdd

---

### Post by hotani on 2006-08-07
Thanks for the fix, maybe when my faith in compiz returns I'll give it a shot. Until then, as mentioned above, I fixed all my compiz problems on all 3 of my ubuntu machines with: "metacity --replace" which worked wonders.

---

### Post by hotani on 2006-10-04
Here is the cause (and fix) for my very irritating problem that keeps coming back.

I always set F9 to be play/pause for whatever audio app I'm using (Rhythmbox or Amarok). Compiz likes to default to using Alt+F9 to.... you guessed it: Minimize. Since the F9 key is otherwise occupied, for some reason it uses 'Alt' by itself for that function. 

The fix is: go to System -> Preferences -> Compiz Settings Manager. In the General Options section, under the Keyboard tab, disable (or reassign key combinations) the Minimize function keyboard shortcut.

---

