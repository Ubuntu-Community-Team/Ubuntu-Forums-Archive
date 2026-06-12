---
title: "Help! Cant run unity with a window manager."
date: 2011-05-15
forum: Desktop Environments
---

### Post by gnomeout on 2011-05-15
Hi folks. I've managed to completely ruin my system for like the millionth time. 

Basically my story is this. I cannot seem to run both unity and a window manager/decorator at the same time. Perhaps it is partially because I am not entirely sure what the current window manager is these days.

I thought it was metacity since that has been the default in the past. I ran a ```
metacity --replace
``` though and unity disappeared, although my regular window theme did reappear and I was able to move windows again but i couldnt launch anything because unity was gone. So I then ran ```
unity --replace
``` and then I got unity back but the metacity window decorator crashed. So it seems these to not work well together? I also noticed there was a "unity-window-decorator" but no matter how I tried running this I got no output from the terminal.

Can someone help me?? I would really like to be able to move windows. I am typing this from my web browser which is permanently stuck in the position it launched in on my screen.

---

### Post by mikewhatever on 2011-05-15
Unity uses Compiz as its window manager, and Metacity is the default Gnome2 window manager. Launching metacity will kill compiz/unity and vice verse, they are not supposed to work together.

---

### Post by 3ar1 on 2011-05-15
As far as I know the window manager used depends on the mode you choose when logging in. You have various options: "Ubuntu", "Ubuntu Classic" and "Ubuntu Classic (no effects)". Read [this thread]("http://ubuntuforums.org/showthread.php?t=1741293&highlight=ubuntu+classic") for a short overview.

If you choose "Ubuntu" the window manager is compiz. So maybe a 

```
compiz --replace
```

does help.

---

### Post by gnomeout on 2011-05-15
thank you both for the fast replies. 

Here is a small development. 2 things. 
I forgot to mention i also tried ```
compiz --replace
``` but it had basically the same output as ```
unity --replace
``` which was a bunch of repetitive opengl errors.

Second is that article inspired me to look at my compiz settings since thats probably what caused all of this. and "Window Decoration" was disabled. So I enabled it and now I can min/maximize and close windows. But very strangely I cannot move them. Which is totally weirding me out.

Any ideas?

PS: 3ar1, I do not seem to have that session manager menu on my login screen mentioned in that article you referenced. which is also weirding me out. however I went to my system setting-> login settings and it says to choose the "Ubuntu" setting by default... not sure if its being successful though.

---

### Post by mcduck on 2011-05-15
> **gnomeout said:**
> thank you both for the fast replies. 

Here is a small development. 2 things. 
I forgot to mention i also tried ```
compiz --replace
``` but it had basically the same output as ```
unity --replace
``` which was a bunch of repetitive opengl errors.

Second is that article inspired me to look at my compiz settings since thats probably what caused all of this. and "Window Decoration" was disabled. So I enabled it and now I can min/maximize and close windows. But very strangely I cannot move them. Which is totally weirding me out.

Any ideas?

PS: 3ar1, I do not seem to have that session manager menu on my login screen mentioned in that article you referenced. which is also weirding me out. however I went to my system setting-> login settings and it says to choose the "Ubuntu" setting by default... not sure if its being successful though.

If you had the Window Decoration-plugin disabled, then perhaps some of the other essential ones are disabled as well? Make sure the "Move" plugin is enabled... ;)

What comes to the Session option in the login screen, it only appears after you have selected a user (or typed in the username) but before you type in your password.

(and yes, the others are right, Unity only works with Compiz, it's a Compiz plugin so you can't use it with other window managers)

---

### Post by mikewhatever on 2011-05-15
You should be able to reset unity to its original state wit the **unity --reset** command.

---

### Post by gnomeout on 2011-05-15
once again, thank you BOTH. A rather embarrassingly simple problem. 

You are right. my Move plugin got disabled along with  like a billion others. And just when I was thinking "hmm, how can I reset it back to default settings?..." I came online and mikewhatever had the command I needed. What luck.

Thanks everyone once again. Also very useful to know about the various window manager options. And boy do I feel silly not catching when the session manager appears, but you are right mcduck, it appears after ive selected my username (D'oh).

I'm embarrassed at how simple it was, but it was late last night and frustratingly difficult to google for anything without my normal window manager abilities.

---

