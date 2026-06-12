---
title: "Quake 4 &quot;Segmentation fault&quot; running Dapper and XGL"
date: 2006-04-05
forum: Gaming &amp; Leisure
---

### Post by MetalMusicAddict on 2006-04-05
I just got this when I tried to play Quake 4 on Dapper. I also have all the XGL and Compiz eye-candy installed. I get the same thing with and without compiz running. I am running a nVidia 6800 card.

```
X..GL_ARB_texture_compression not found
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully.
```.

Ideas?

---

### Post by SlCKB0Y on 2006-04-05
Well firstly, you have zero chance of running quake4 under xgl/compiz. You need to make sure neither are running. It wont work just to stop compiz.

---

### Post by MetalMusicAddict on 2006-04-07
WOW. That was helpful.

---

### Post by Jedeye on 2006-04-08
I get the same message. Anybody have any ideas? I also have a nvidia 6800

---

### Post by SlCKB0Y on 2006-04-08
[QUOTE=MetalMusicAddict]WOW. That was helpful.[/QUOTE]


Are you being sarcastic?

I Was being about as detailed as I need to be. let me help you out again. WITH XGL/COMPIZ RUNNING, OTHER OGL APPS WILL FAIL TO RUN. This is what I said in my first post. IT IS NOT YET POSSIBLE.

Since you didnt mention anything about turning off XGL I cam only assume it is still running. Change gdm.conf-custom back to normal (or by whatever means you start Xgl).

Does this help?

](*,)  ](*,)

---

### Post by Jedeye on 2006-04-11
Hey MetalMusicAddict this got Quake4 working for me by disabling xgl, got it from another topic from ubernoob:

[QUOTE=ubernoob]If you do this, you will lose all unsaved data (since you are restarting the x-server) You might want to log out before doing this:

disabling:

ctrl + alt + f1
sudo mv /etc/gdm/gdm.conf-custom /root/
sudo /etc/init.d/gdm restart

enabling:

ctrl + alt + f1
sudo mv /root/gdm.conf-custom /etc/gdm/
sudo /etc/init.d/gdm restart[/QUOTE]

The problem you have/had was that xgl was enabled, it may have not seemed like it since you didnt have compiz on, but its still in the background.

Good luck!

---

### Post by MetalMusicAddict on 2006-04-11
Nice. :) I did know XGL was running but wasnt sure how to disable it. Too bad its a kinda hackish way to get games to work. Right now that is.

---

