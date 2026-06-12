---
title: "No sound after installing Beryl"
date: 2007-03-09
forum: Desktop Environments
---

### Post by loopeando on 2007-03-09
I have installed Beryl on my Lenovo 3000 N100 and my audio has died.

Before installing Beryl, and the modifications in the xorg.conf file to install it, my audio worked great.

Can anyone help me?

---

### Post by zeny on 2007-03-13
me too, I tried setting default card and everything

---

### Post by PaulFXH on 2007-03-13
In my experience, the first thing to do before trying any more elaborate sound problem fix is to make sure your alsamixer settings are correct.
Type
```
alsamixer
```
in a terminal and make sure EVERYTHING is unmuted (use the "m" key) and turned up to at least 50 (up/down arrows) where appropriate.
In my case at least, one setting MUST be muted. This is the Analog/Digital Output Jack.
Good luck
Paul

---

### Post by tetu81 on 2007-03-13
This was my exact problem...xorg.conf changes on Edgy while installing Beryl.  PaulFXH hit the nail on the head :KS...I used alsamixer to unmute everything except the line out.

The question (from this kinda-newbie) is why changes to that file would have caused my audio to get messed up?  Can bad/misplaced entries in xorg.conf allow X to work ok but cause other problems (like this one) to occur?

For what it is worth, I was following these instructions: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

All is well now and I quite like Beryl.

---

### Post by szantaii on 2007-03-30
Hi!

I have the same problem with my Lenovo 3000 N100 laptop too. After installed Beryl sound has just disappeared, no sound at all and I am not sure what to do. I've used the same guide as above to install Beryl.
Here are some screens from alsamixer (if this helps):

[http://img382.imageshack.us/my.php?image=alsamixer1if3.png](http://img382.imageshack.us/my.php?image=alsamixer1if3.png)
[http://img238.imageshack.us/my.php?image=alsamixer2en0.png](http://img238.imageshack.us/my.php?image=alsamixer2en0.png)
[http://img238.imageshack.us/my.php?image=alsamixer3vh1.png](http://img238.imageshack.us/my.php?image=alsamixer3vh1.png)

Thanks for the help in advance.

---

### Post by PaulFXH on 2007-03-30
What I did in my case was to first make sure EVERYTHING in alsamixer was turned on and set to at least 50% setting.
Then when that didn't restore my sound, I went through every one of the items in alsamixer and muted it. If muting it didn't restore the sound, I turned it on again and moved to the next item. As I had mentioned earlier, my analog/digital output jack HAD to be muted to give me sound.
I seem to remember seeing in another thread that the EXTERNAL item needs to be muted in some cases. Maybe you can try this.

---

### Post by szantaii on 2007-04-08
I don't know what happened, it just works now, nothing is muted. Mystery... :)

---

