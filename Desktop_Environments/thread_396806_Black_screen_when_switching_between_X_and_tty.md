---
title: "Black screen when switching between X and tty"
date: 2007-03-29
forum: Desktop Environments
---

### Post by SBFC on 2007-03-29
Has anyone else had problems when switching from an X session to a tty session and back to X again?

When I do it with Beryl enabled my screen is black. Unless I disable Beryl from a tty session I am unable to get back into X.

I'd like to use Beryl but it makes it a lil hard when I can't switch out of my current X display. And it makes playing games on a separate X session impossible.

Just curious if anyone else had experienced this issue.

---

### Post by coolen on 2007-03-30
I get that when switching users. I just swap back to Metacity for a bit. Used to do it coming back from the screensaver, too, which was a little more annoying. That one's working fine for me now, though.
Beryl's still young. It'll only get more stable from here.

---

### Post by hearty on 2007-03-30
I am getting same problem with dist-upgraded feisty fawn. Every thing works well but X. Even gdm restart after doing a remote login doesn't work. Please SOS.:confused:

---

### Post by SBFC on 2007-03-30
> Beryl's still young. It'll only get more stable from here.

Aye. Was just curious if others were experiencing it as well. ;)

With beryl-manager you can at least choose a different WM from the right-click context menu, which makes switching fast enough.

---

### Post by Tiftof on 2007-04-11
I'm having the same problem using feisty... It's getting pretty annoying. Only thing I can do when I return back to the X session, is press the power button and let ubuntu shut down

---

### Post by Arko on 2007-04-13
Same problem here.

---

### Post by Dogmeat on 2007-04-22
I was having this problem too. When coming back from a VT or the screensaver X would be black and locked up. I fixed it by forcing AIGLX. I noticed some loss of performance but it should fix your problem. To force AIGLX do this:

- Right click Beryl Manager
  - Select Advanced Beryl Options
     - Rendering Platforms
        - Force AIGLX

---

### Post by Flare183 on 2007-04-22
Don't try this! This is one of the reasons that Beryl is unstable. It can't switch between tty's and the main virtual terminal (7).

---

### Post by Dogmeat on 2007-04-22
Flare183: It works everytime for me, after I force AIGLX, like I said above. My only issue with beryl now is the memory leak, which fills up my graphic's card memory, and window contents start getting black (due to lack of memory, not related in anyway to VT switching).

I'm using the nvidia binary drivers. I don't know if ATI users have this issue.

---

### Post by Flare183 on 2007-04-22
Yeah it might work for ndivda cards but for ati cards using aiglx you can't.

---

