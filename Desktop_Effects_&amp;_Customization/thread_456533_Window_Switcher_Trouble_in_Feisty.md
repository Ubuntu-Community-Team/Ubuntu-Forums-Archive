---
title: "Window Switcher Trouble in Feisty"
date: 2007-05-27
forum: Desktop Effects &amp; Customization
---

### Post by RelativelyQuantum on 2007-05-27
Hi all.

I'm having a bit of trouble with the Desktop effects in Feisty. I have it set so that a click in my lefthand corner activates the window selector, but this stops working every other time I mount the hard drive. This is a fairly recent problem, as I have used Feisty since its release with no trouble. The only thing I could think of which might be causing it are some residual settings that Beryl may have left behind after I removed it; I had downloaded and installed it just to try it out, and found that it did not allow me to use the window selector. As I said before, Beryl is no longer on my machine; I would imagine that the problem stems from some residual program files left behind.

Any comments would be greatly appreciated.

---

### Post by nevernamed on 2007-05-28
I would love to help you... but I was a little confused by the problem that you're having.
You are trying to use the built in desktop effects that come with fiesty? But you had beryl on there before.. and think that there might be something left from it messing with compiz? Why are you mounting your hard drive after startup? Shouldn't the harddrive me mounted when the computer is booted??

Please eleborate on what exactly is wrong and I will do my best to help you!

---

### Post by RelativelyQuantum on 2007-05-28
Sorry to be vague. I may have botched the terminology - by 'mounted' I meant that I booted up. This is exactly what happened: 
     I upgraded to Feisty two days after it was released. Since then I have used the built-in desktop effects which come as a preview (the window selector was particularly valuable :D). I also had my 3 desktops rapped around a triangular prism, with the switcher in my bottom right hand corner. About two weeks ago I began to read some interesting things about Beryl, and downloaded it shortly afterward. I removed it later that day because I couldn't do what I wanted to with it (so I thought at the time - still don't know for sure). After I removed it, every other time I booted up my window switcher did not work. I would open Desktop Effects, and the "desktop effects" button would be depressed, but I had to click it to turn desktop effects off, then click it again to reactivate my window switcher.

     A bit of a complex problem, to say the least. Again, I don't know weather it had anything to do with the fact that Beryl was once on my machine. What I do know for sure is that it seems to have resolved itself - I unchecked the "workspaces on a cube" box, and have had no problems since then.

     Thanks for the help, in any case, and sorry to have confused.

---

### Post by nevernamed on 2007-05-29
I really don't know enough about obscure linux commands to be able to help you that much.. but my advice to you would be to try and find out what dependencies beryl needs specifically, and try to disable them and if it doesn't mess with the rest of your system to just then remove it. I'm sure that there is an apt-get variation to just remove the application and all dependencies.

From what you said you had gotten beryl working? Also, what is the problem that happens on startup?

I am also having a problem that nobody seems able to help me with:
I was trying to use the built in desktop effects that come with Fiesty, and it asked me to activate the nvidia driver. I said yes, it downloaded the necesary files. It said that I had to run desktop effects again when the new nvidia driver was running. I rebooted. Everything worked fine until the login screen was supposed to come up. The screen went totally black. I still heard the African drums, but I was unable to do anything. control+alt+backspace restarted x and nothing happened. I can boot to the recovery mode... but I really don't know what to do. Do you know why this has happened (i heard something about a bug in the nvidia driver in a different thread) and how to correct it?

---

