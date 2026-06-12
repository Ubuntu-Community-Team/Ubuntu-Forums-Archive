---
title: "Xgl and Compiz problem"
date: 2006-06-13
forum: Desktop Environments
---

### Post by johso on 2006-06-13
Hiya people!

I've searched both this forum and Google thin, but I haven't found a solution.
I'm trying to start my Xgl server, and it is just not working out for me!
I had it working on Breezy, but it was too buggy, and I wasn't able to update (since everything was made for Dapper). So when I upgraded to Dapper I couldn't wait to try out the newer versions, and---guess what?---it doesn't work.

My initial method was this: [http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916)
But since that didn't really work, I added this to my gdm.conf-custom:
```

[servers]
# Override display 0 to use Xgl.
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel xv -accel glx:pbuffer
flexible=true

```
But uhm, that didn't work eiter. Had to change back to the standard X server.

When I restart gdm (with the Xgl server enabled), I can see the default ubuntu thinker-curser (or whatever you'd call it) and move it around. Nothing happens for 10 seconds, then it restarts X 5-7 times, and tells me that X could not be started.
I've added GdmXserverTimeout to 50, but it seems like this option is totally ignored, though.
Just about an hour ago, I tried to open my .Xsession from nautilus to edit it, and instead I, by mistake, executed it, which---to my surprise, I might add---worked!
So, now I'm quite lost. It works, but can't use gnome, since it already is launched. So what I have is a Xgl server in a 1400x1050 (my screen resolution) window, and nothing but a blue background.
This leads me to believe that the .Xsession file is **not** executed when I login. Otherwise Xgl shold be launched, right?
And btw, just to make sure I've tried to run 'thefuture' (which is the script that should launch Compiz), and it only returns "compiz.real: No composite extension".

Any help would be appreciated.

Thanks in advance, Johs

EDIT:
My graphics card is an ATi Mobility Radeon 9700.

---

### Post by fargoth on 2006-06-13
try adding 
```

Section "Extensions"
    Option "Composite" "true"
EndSection

```
in the end of xorg.conf

and if you use nvidia add 
```

Option   "AllowGLXWithComposite" "On"
Option   "RenderAccel" "true"
``` 
in the device section.

WARNING: The RenderAccel option is EXPERIMENTAL. Set this option to false if you experience lockups. NOTE: RenderAccel has become a lot more stable using nivida 1.0.8178 or 1.0.8756 drivers

---

### Post by johso on 2006-06-13
Tried it, but it didn't help. The composite manager tries to run the Compiz command (which it can't), which results in windows with no decorations.
I knew it wouldn't work, but tried it anyway.
From [http://en.opensuse.org/Xgl_Troubleshooting](http://en.opensuse.org/Xgl_Troubleshooting):
> 
Xgl does not need the Composite extension enabled in xorg.conf - in fact this is counter-productive, as e.g. the NVIDIA driver disables OpenGL by default when Composite is enabled. The Composite extension is provided by Xgl itself, without the need to configure anything.


Any ideas on the .Xsession issue? Is there a way that I can verify it's executed?

---

### Post by johso on 2006-06-19
Hi again.

I finally found the reason why the Xgl server wouldn't start - GdmXserverTimeout was set twice, and ignored second time (50 seconds).
But uhm, now I've got a new problem:
```

compiz.real: Support for non power of two textures missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :1.0

```
And I haven't got a clue how to solve it.
Anyone...?

---

### Post by rafalr on 2006-08-08
Hi,

You say that the problem was "GdmXserverTimeout was set twice, and ignored second time (50 seconds)."

where (path/file) is this option being set ?

I got the same problem and am a bit stuck ...

Rafal

---

### Post by johso on 2006-08-08
The "GdmXserverTimeout" option it set on line 198 in /etc/gdm/gdm.conf

If you open /etc/gdm/gdm.conf with gedit (as root), you can push CTRL+I and then type in 198 to go to line 198.

I hope it works for you! :-)

---

### Post by rafalr on 2006-08-09
thanks, will try that

rafal

---

### Post by Rever75 on 2006-08-09
If you are using an ATI card make sure you have the fglrx driver installed and working. Log into a regular session non XGL and run fireglcontrolpanel the OpenGl section should say ATI. If you are using Nvidia make sure you have the latest libglizt1.

---

