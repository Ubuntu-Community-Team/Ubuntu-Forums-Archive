---
title: "[SOLVED] xscreensaver"
date: 2007-10-17
forum: Desktop Environments
---

### Post by k33bz on 2007-10-17
I cant bring up my xscreensaver, i get this when i run the command.

```
keebler@K33bz-mobile:~$ xscreensaver
xscreensaver: 15:59:29: already running on display :0.0 (window 0x2800006)
 from process 5524 (keebler@K33bz-mobile).
keebler@K33bz-mobile:~$ 

```

---

### Post by tkon1567 on 2007-10-17
I get a very similar output response, I just posted about ten minutes ago.  Did your default screen saver work, when it was randomly selected.  Now that  I changed the setting the screen saver hasn't turned on since?

---

### Post by k33bz on 2007-10-17
> **tkon1567 said:**
> I get a very similar output response, I just posted about ten minutes ago.  Did your default screen saver work, when it was randomly selected.  Now that  I changed the setting the screen saver hasn't turned on since?

yep, when i first installed xscreensaver I got the configurations, didnt choose yet cause i wanted to install more. Installed more screen savers for it, but am unable to get the config screen back up for it. I have even tried rebooting.

---

### Post by k33bz on 2007-10-17
Just found a way to bring the screen back up. Hoping there is another way though.

I went to System/Administartion/system monitor  and chose to end the process.

---

### Post by tkon1567 on 2007-10-17
I went to task manager and it was up in the processes but was not using any cpu usage?  I'm still very green on linux, and this seems like a trivial problem yet it is very persistent and I am throughly clueless on it as well.  It sounds from your post that you installed an extra program?  If this is so did you ever come across this before you tried any other programs?

---

### Post by kellemes on 2007-10-17
You're trying to run the daemon, this daemon is already running..
You need to run "xscreensaver-demo" to configure xscreensaver.

---

### Post by k33bz on 2007-10-17
> **kellemes said:**
> You're trying to run the daemon, this daemon is already running..
You need to run "xscreensaver-demo" to configure xscreensaver.


awwww, yep, that works better. Thank you

---

### Post by tkon1567 on 2007-10-17
That's the thing I've already configured from here.... now it won't turn as expected?  Should kill the daemon from the file tab....?  Or is there something else I'm missing ?

---

### Post by kellemes on 2007-10-17
> **tkon1567 said:**
> That's the thing I've already configured from here.... now it won't turn as expected?  Should kill the daemon from the file tab....?  Or is there something else I'm missing ?

You don't need to kill the daemon.. the daemon needs to be running to have xscreensaver functioning.
If you type "xscreensaver-demo" in the terminal it will start the daemon if needed.
Not sure how Ubuntu handles this but probably it's automatically added to the startup-daemonlist, so at boot the screensaver-daemon is started.
So.. you don't need to do anything..probably.. feel free to ask if you have trouble.

---

### Post by tkon1567 on 2007-10-17
Yeah thats the thing ever since I've customized to a single screen saver.... instead of having the random selector on, it never turns on anymore?

---

### Post by kellemes on 2007-10-17
> **tkon1567 said:**
> Yeah thats the thing ever since I've customized to a single screen saver.... instead of having the random selector on, it never turns on anymore?

So you configured it to start after X minutes? And it doesn't come up?

---

### Post by tkon1567 on 2007-10-17
Yeah........ thats why its strange.  Its not like it wasn't working before either.

---

