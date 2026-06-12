---
title: "how to set screen to fade in/out"
date: 2006-03-29
forum: Desktop Environments
---

### Post by hezral on 2006-03-29
hi.in badger i can set it thru the screensaver settings but now in dapper its all gone. is there any other way to do this?

---

### Post by kurros on 2006-03-29
I'm not sure what you are asking. gnome-screensaver fades out/in for me automatically. Using popsquares at least.

---

### Post by hezral on 2006-03-29
okay. in breezy i set my screensaver to blank screen and there was an option on another tab to fade in/out the screen when it becomes active/inactive.
but as you know in dapper the screensaver settings is stripped out and last nite i noticed that it didnt fade in when i move the mouse. so are the settings gone? or is it hidden somewhere

---

### Post by aggiechemist on 2006-05-30
I'm going to second the need for more  obvious controls of fading. In breezy,  you could contol the fade time and whether or not it happened easily. Apparently in dapper, they tired to simplify the interface but took away all of my control. Now my screensaver has a very long fade time and I HATE it. 

Is there a config file somewhere? I'm also starting to notice on the forums there emight be two different screensaver managers...

Help?

---

### Post by graigsmith on 2006-05-30
im having this problem as well, isn't there just a way to disable that fade?  it's annoying. and it doesn't stop immediately when you move your mouse.

---

### Post by aggiechemist on 2006-05-31
OK, well I have a workaround. Apparently dapper uses the gnome screensaver system, which I personally find annoying. 

Kill it! I think you need to do something like:

sudo apt-get remove gnome-screensaver
sudo apt-get install xscreensaver
xscreensaver-demo

That should  give you a different system and let you configure it more. Also, if you search screensaver in synaptic it will find a bunch more options for you to download so you have lots of pretty movin pictures.

sudo apt-get install xscreensaver-data xscreensaver-gl

---

### Post by xplode_me on 2006-06-05
I managed to get to the xscreensaver configuration and disabled fade out and fade ir but they are still THERE!

Wich is quite annoying cause i want my screensaver to run a aplication without fading....

---

