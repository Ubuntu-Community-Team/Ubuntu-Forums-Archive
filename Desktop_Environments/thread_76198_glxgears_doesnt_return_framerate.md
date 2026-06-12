---
title: "glxgears doesnt return framerate"
date: 2005-10-14
forum: Desktop Environments
---

### Post by snipes420 on 2005-10-14
I upgraded to breezy a few days before the release date and have upgraded again just now. ever since upgrading, glxgears does not return a framerate and seems to be VERY slow. just a guess but does this mean i need to install my nvidia drivers again? 
glxgears does show the gears but nothing is returned to the console.

---

### Post by mlomker on 2005-10-14
That's a new "feature."  Add this alias to the bottom of your /etc/bash.bashrc file.

```

alias glxgears='glxgears -printfps'

```

---

### Post by StinkyPete on 2005-10-14
Thank you !

I was wondering about this...:razz:

---

### Post by Takis on 2005-10-14
Incidentally, I noticed that in Breezy my framerate increased by about 10%. :D

---

### Post by Segovia on 2005-10-14
[QUOTE=Takis]Incidentally, I noticed that in Breezy my framerate increased by about 10%. :D[/QUOTE]
As you can see by the new option, it's not a benchmark.  So how would you know your framerate increased?  :confused:   ;)

---

### Post by snipes420 on 2005-10-15
thanks for clearing that up mlomker :)

---

### Post by ltmon on 2005-10-15
[QUOTE=mlomker]That's a new "feature."  Add this line to the bottom of your /etc/bash.bashrc file and that'll square it away.

```

alias glxgears='glxgears -iacknowledgethatthistoolisnotabenchmark'

```[/QUOTE]

Hey... and I thought for a while you were just being facetious!!!

I have been mucking around for an hour with nvidia-glx and nvidia-glx-legacy to see why my OpenGL seemed so slow!!!  I just use glxgears as a quick test to make sure it's working - and when the gears turned so slowly I was sure something was wrong.

Turns out there was nothing wrong at all... just that glxgears has changed the way it works.  I started up a 3d game it played fine ... better than Hoary.

I think this should be made a little more public so that simpletons like me don't think that their graphics is screwed up. :oops:

L.

---

### Post by mlomker on 2005-10-15
> I think this should be made a little more public so that simpletons like me don't think that their graphics is screwed up. :oops:


I'm going to link it in the Video & Sound forum's sticky.

---

### Post by Takis on 2005-10-15
[QUOTE=Segovia]As you can see by the new option, it's not a benchmark.  So how would you know your framerate increased?  :confused:   ;)[/QUOTE]
Although it's not a hard benchmark, it can definitely be used as a guide. I was getting FPS of about 3,600 before and now I'm hitting just over 4,100. Although I wouldn't say I've had a 13% increase, there's definitely been something, and a ballpark figure is 10%.

---

### Post by BLTicklemonster on 2005-10-15
Oh, ~$ sudo gedit /etc/bash/bash.rc
[I]
then add[/I]

```
alias glxgears='glxgears -iacknowledgethatthistoolisnotabenchmark' 
```

at the bottom. ;)

I keep forgetting to do that. Nice if people would just take the time to put that for the newbsters who come in. (like me :) )

Here's mine:

578 frames in 5.0 seconds = 115.511 FPS
578 frames in 5.0 seconds = 115.511 FPS



but that's with the window maximized.




6429 frames in 5.0 seconds = 1285.613 FPS
6115 frames in 5.0 seconds = 1222.990 FPS
6678 frames in 5.0 seconds = 1335.475 FPS
6680 frames in 5.0 seconds = 1335.881 FPS
6677 frames in 5.0 seconds = 1335.344 FPS

This is what it was at first. 


About time!!! I was getting those first numbers at first in Hoary.

---

### Post by berserker on 2005-10-15
[QUOTE=mlomker]That's a new "feature."  Add this line to the bottom of your /etc/bash.bashrc file and that'll square it away.

```

alias glxgears='glxgears -iacknowledgethatthistoolisnotabenchmark'

```[/QUOTE]

Or you could do ```
alias glxgears='glxgears -printfps'
```

---

### Post by arcanistherogue on 2005-10-15
funny, I was just about to ask about this exact thing!  Thanks for the help.

Once again, the Ubuntu community is quite possibly the best GNU/Linux community I have ever seen :KS

---

### Post by mlomker on 2005-10-16
[QUOTE=berserker]Or you could do ```
alias glxgears='glxgears -printfps'
```[/QUOTE]

Less to type.  I'll update my how-to's with that.

Thanks.

---

### Post by Segovia on 2005-10-16
[QUOTE=Takis]Although it's not a hard benchmark, it can definitely be used as a guide.[/QUOTE]
Yes, yes.  I was only joking of course.  :cool:

---

### Post by BLTicklemonster on 2005-11-18
[QUOTE=mlomker]That's a new "feature."  Add this alias to the bottom of your /etc/bash.bashrc file.

```

alias glxgears='glxgears -printfps'

```[/QUOTE]


You rock. Did anyone ever tell you that? You rock.

---

### Post by goslackware on 2006-03-10
current glxgears options:

-display
-info
-stereo
-fullscreen
-iacknowledgethatthistoolisnotabenchmark
-printfps

example:
glxgears -info -fullscreen -printfps

use, ctrl-c to exit glxgears while in fullscreen mode

---

### Post by siennalizard on 2007-02-16
> **goslackware said:**
> current glxgears options:

-display
-info
-stereo
-fullscreen
-iacknowledgethatthistoolisnotabenchmark
-printfps

example:
glxgears -info -fullscreen -printfps

use, ctrl-c to exit glxgears while in fullscreen mode

That's definitely man page material. Sadly, glxgears has neither a man page, or usage instructions with the --help or -h switches. This is not the first time I've googled around for this, either!

---

