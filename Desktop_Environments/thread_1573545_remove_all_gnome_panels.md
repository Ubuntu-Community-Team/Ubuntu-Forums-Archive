---
title: "remove all gnome panels"
date: 2010-09-12
forum: Desktop Environments
---

### Post by nick_goodfate on 2010-09-12
Hello all! I'm trying to delete all gnome panels, following the method of deleting the panel value from gconf-editor->desktop->gnome->session->required_components. It doesn't work... I've made it successfully at the past several times, but now for some reason it doesn't work.

If it means something, when I'm killing gnome-panel process from system monitor it immediately restarts...

i miss something?

---

### Post by kerry_s on 2010-09-12
try logging out & back in

---

### Post by nick_goodfate on 2010-09-12
> **kerry_s said:**
> try logging out & back in

thanks for the reply, but I've already done it. I also want to note that i would prefer to remove the panels with the method i mentioned above. I don't want to remove the gnome-panel package for example...

---

### Post by stinkeye on 2010-09-12
Try removing panel from gconf-editor > /desktop/gnome/session/**required_components_list**

---

### Post by nick_goodfate on 2010-09-12
> **stinkeye said:**
> Try removing panel from gconf-editor > /desktop/gnome/session/**required_components_list**

Is it easy to restore it if i remove it from there? Can you give me an idea of what I'll have to do to restore it, if you know?

---

### Post by stinkeye on 2010-09-12
> **nick_goodfate said:**
> Is it easy to restore it if i remove it from there? Can you give me an idea of what I'll have to do to restore it, if you know?

When you double click in the value field you get a dialogue window.
Just remove **panel**.
Take a screenshot, before you remove, if you like to restore back to how it was.
Your panel preferences will remain so if you restore the panel it will look the same as before you removed it.

---

### Post by kgas on 2010-09-12
if iirc you can not remove both the panels  but you can hide them. see [this](http://ubuntuforums.org/showthread.php?p=4021498) thread.

---

### Post by nick_goodfate on 2010-09-12
> **stinkeye said:**
> When you double click in the value field you get a dialogue window.
Just remove **panel**.
you mean [that]("http://tinypic.com/r/29zzcp5/7")...?

> **stinkeye said:**
> 
Try removing panel from gconf-editor > /desktop/gnome/session/required_components_list

you mean [that]("http://tinypic.com/r/33b2wow/7")?

Anyway i tried both and no result...

---

### Post by nick_goodfate on 2010-09-12
> **kgas said:**
> if iirc you can not remove both the panels  but you can hide them. see [this](http://ubuntuforums.org/showthread.php?p=4021498) thread.

What is iirc? I don't want to hide them, i want to completely remove them. Thank you for the help!

---

### Post by stinkeye on 2010-09-12
> **nick_goodfate said:**
> 

Anyway i tried both and no result...

The only reason I can think of that it's not working is in 
startup applications > options
you have enabled 
**Automatically remember running applications when logging out**

Are logging out then in?

---

### Post by msrinath80 on 2010-09-12
> **nick_goodfate said:**
> you mean [that]("http://tinypic.com/r/29zzcp5/7")...?


you mean [that]("http://tinypic.com/r/33b2wow/7")?

Anyway i tried both and no result...

No he DID NOT mean that. He meant this: [http://i53.tinypic.com/2cmq8ti.png](http://i53.tinypic.com/2cmq8ti.png)

---

### Post by nick_goodfate on 2010-09-12
> **stinkeye said:**
> The only reason I can think of that it's not working is in 
startup applications > options
you have enabled 
**Automatically remember running applications when logging out**

No it's not enabled. As i told at my first post, when i kill gnome-panel process it restarts. Why is that happening? Until yesterday i had all panels removed and for some reason i restored them... Something changed since yesterday and i can't remove again

---

### Post by nick_goodfate on 2010-09-12
> **msrinath80 said:**
> No he DID NOT mean that. He meant this: [http://i53.tinypic.com/2cmq8ti.png](http://i53.tinypic.com/2cmq8ti.png)

ok, did that too, as i said...

---

### Post by msrinath80 on 2010-09-12
restart

---

### Post by stinkeye on 2010-09-13
Did you put gnome-panel in startup applications?

---

### Post by nick_goodfate on 2010-09-13
> **msrinath80 said:**
> restart

I don't think it's something so obvious... I've removed my panels several times before.

---

### Post by nick_goodfate on 2010-09-13
> **stinkeye said:**
> Did you put gnome-panel in startup applications?

nope

---

### Post by kerry_s on 2010-09-13
i don't know, when i did mine all i did was remove that 1 "gnome-panel" & log out & back in.(see pic)

are you removing it for a dock? you can put the name of the dock in it's place. remember just "right click-> unset" if you ever need to return it to default.

---

### Post by nothingspecial on 2010-09-13
This will work
```

sudo mv /usr/bin/gnome-panel ~/.panel
```

This will move the binary that gnome uses to run your panel from where gnome thinks it is to a hidden file in your home directory called .panel

It will not be able to run because it is not there.

If you want it back

```
sudo mv ~/.panel /usr/bin/gnome-panel
```

That will put it back.

You will not be able to use Alt F1 or Alt F2

---

### Post by nick_goodfate on 2010-09-13
> **kerry_s said:**
> i don't know, when i did mine all i did was remove that 1 "gnome-panel" & log out & back in.(see pic)

are you removing it for a dock? you can put the name of the dock in it's place. remember just "right click-> unset" if you ever need to return it to default.

I've tried that too. I replaced "gnome-panel" with avant-window-navigator" and nothing happened...

---

### Post by nick_goodfate on 2010-09-13
> **nothingspecial said:**
> This will work
```

sudo mv /usr/bin/gnome-panel ~/.panel
```

This will move the binary that gnome uses to run your panel from where gnome thinks it is to a hidden file in your home directory called .panel

It will not be able to run because it is not there.

If you want it back

```
sudo mv ~/.panel /usr/bin/gnome-panel
```

That will put it back.

You will not be able to use Alt F1 or Alt F2

As far as i know the first update of something i don't remember now will restore the panel, if I've removed them with this method. Have you tried that, is it true? 

I've replaced Alt+F2 with gnome-do;)

---

### Post by nothingspecial on 2010-09-13
> **nick_goodfate said:**
> As far as i know the first update of something i don't remember now will restore the panel, if I've removed them with this method. Have you tried that, is it true? 

I've replaced Alt+F2 with gnome-do;)

It works, I do it all the time.

---

### Post by nick_goodfate on 2010-09-13
Thank you all for your help!

> **nothingspecial said:**
> It works, I do it all the time.
Yes it works nothingspecial, thank you!

---

