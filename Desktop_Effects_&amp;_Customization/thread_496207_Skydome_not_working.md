---
title: "Skydome not working"
date: 2007-07-08
forum: Desktop Effects &amp; Customization
---

### Post by fycloops on 2007-07-08
Using Compiz Fusion. It is all working fine except for the skydome. I have this lovely 2048 x 1024 jpg that I'd like to use. I use compizconfig settings manager which has been great to change all my other settings but just doesn't do anything for skydome!?!?!?! I can change the colours of the default skydome...

Any ideas?

I start fusion with:

compiz --replace -c emerald &

in my gnome session start up.

Any help would be appreciated!

Fyc

---

### Post by ajmorris on 2007-07-08
can your card handle textures as high as 2048??

post the output of this command :```
 glxinfo -l|grep GL_MAX_TEXTURE_SIZE
```

---

### Post by fycloops on 2007-07-08
Hi AJMorris.

Here is the output:

GL_MAX_TEXTURE_SIZE = 4096


Fyc

---

### Post by ajmorris on 2007-07-08
You can definitely get 2048x1024 then... 
what format is the skydome in?.....   .jpg do not work at this time...  .png is the best.

---

### Post by fycloops on 2007-07-08
Thanks AJ. 

The file format was the issue. Changed it to PNG and it works good as gold!

Kia Ora mo to awhi!

Fyc

---

### Post by juamez. on 2007-11-01
AGAIN a save from the person called ajmorris. Thank you very much. I was trying to use a nice file with a +3000x2000 resolution, but it seems my graphics card (intel GMA900) can only handle up to 2048.

I resized the pic to 2048x1024 and now it works. Yay, really!

/edit: I know this thread is old, but I really needed to express my joy and gratitude for tackling such painstaking "problems" - let's call them glitches - in our neverending quest to finetune EVERYTHING we can, and even further than that.

---

### Post by ricochet1269 on 2008-05-03
Hey, I just wanted to say thanks as well.  I had a png file, but it was more than the 2048 my computer handles.  I only found out because of this handy command!

---

### Post by Drakkor on 2008-05-06
How to adjust skydome picture ? All my skydomes seem too large or zoomed in on the screen. Thanks :)

---

