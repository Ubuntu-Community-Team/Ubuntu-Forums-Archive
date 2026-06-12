---
title: "Batch processing 1000+ photographs"
date: 2006-08-01
forum: Desktop Environments
---

### Post by xp_newbie on 2006-08-01
After installing Ubuntu, I noticed the impressive image editing program, GIMP.

Now I need to process 1000+ photos in batch: auto color correction (as named in Photoshop), resizing - and cropping.

Does GIMP allow this kind of batch processing? If so, where do I find the documentation for how to accomplish that?

If not, is there a program or a software package that does batch processing of images?

Thank!
Alex

---

### Post by Bagnaj97 on 2006-08-01
not sure about colour correction but install the imagemagick package from the repositories and use the convert tool for cropping and rotating. It's a command line tool that I can't remember how to use but typing "man convert" into a terminal should give you instructions.

---

### Post by reclusivemonkey on 2006-08-03
> **xp_newbie said:**
> 
Now I need to process 1000+ photos in batch: auto color correction (as named in Photoshop), resizing - and cropping.

Does GIMP allow this kind of batch processing? If so, where do I find the documentation for how to accomplish that?

If not, is there a program or a software package that does batch processing of images?


As Bagnaj97 says, ImageMagick is the program to do this, however you will need to be able to write some scripts to take full advantage. A good place to start learning this is;

[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

If you take a look on the ImageMagick site there are also some example scripts, and a good preview of the effects you can do;

[http://www.imagemagick.org/](http://www.imagemagick.org/)

---

### Post by xp_newbie on 2006-08-10
Thanks everybody. I just discovered an amazing resource for ImageMagick help:

[URL="http://studio.imagemagick.org/discussion-server/"]
http://studio.imagemagick.org/discussion-server[/URL]

I hope this will help others, too. :)

---

### Post by oss_monkey on 2006-08-22
Thanks! This was really helpful. I even learned how to write a simple shell script for batch processing. :)

Now, can anyone point me to the direction as to how I can run a script from anywhere? For now I copy the script in every directory I want to process, run it, then delete it. :(

TIA.

---

### Post by reclusivemonkey on 2006-08-22
> **oss_monkey said:**
> 
Now, can anyone point me to the direction as to how I can run a script from anywhere? For now I copy the script in every directory I want to process, run it, then delete it. :(


Well there are a number of ways to do this. You can either copy the script to somewhere in your PATH, or add where you keep your script to your PATH. For ease, I would just copy it to /usr/local/bin, then you should be able to run it as long as you set it to be executable. You can read more about the PATH variable here;

[http://www.faqs.org/docs/Linux-mini/Path.html](http://www.faqs.org/docs/Linux-mini/Path.html)

HTH.

---

### Post by oss_monkey on 2006-08-23
> **reclusivemonkey said:**
> Well there are a number of ways to do this. You can either copy the script to somewhere in your PATH, or add where you keep your script to your PATH. For ease, I would just copy it to /usr/local/bin, then you should be able to run it as long as you set it to be executable. You can read more about the PATH variable here;

[http://www.faqs.org/docs/Linux-mini/Path.html](http://www.faqs.org/docs/Linux-mini/Path.html)

HTH.

Thank you so much! This is exactly what I've been looking for. =D>

---

### Post by reclusivemonkey on 2006-08-23
> **oss_monkey said:**
> Thank you so much! This is exactly what I've been looking for. =D>

No problem, us Monkeys should stick together ;-) I had a quick read of your blog and you might want to look at the "nice" command for your scripts. The man page should tell you all you need to know. If you have a "always-on" internet connection too, try looking at [www.pandora.com](www.pandora.com) for new music. :)

---

### Post by oss_monkey on 2006-08-24
I agree. To paraphrase the chorus of the Mighty Ducks:

*Monkeys swing together!*

Anyway, I decided to study using arguments to note search terms for the script.

Something like "smallify.sh jpg l 1024", which will run the smallify script on files with:
1) a jpg (not JPG) extension
2) landscape orientation

...to the long side being scaled to 1024 pixels and the other side scaled to ratio. :)

On Pandora, it was interesting to see something like that. Too bad my internet connection's not the greatest. Even if this is a DSL line, it's not that fast to maintain radio streaming. Or maybe I have too many apps running too. Or too little RAM. :D

Again, thanks reclusivemonkey.

---

### Post by asplode on 2006-08-24
might want to check this out too... its a nautilus script for resizing a ton of images.  I like it a lot.  No CLI typing involved.

[http://www.gfiles.org/gtk/download/nis-nautilus-image-script/268/](http://www.gfiles.org/gtk/download/nis-nautilus-image-script/268/)

---

### Post by Tankard on 2006-10-30
> **asplode said:**
> might want to check this out too... its a nautilus script for resizing a ton of images.  I like it a lot.  No CLI typing involved.

[http://www.gfiles.org/gtk/download/nis-nautilus-image-script/268/](http://www.gfiles.org/gtk/download/nis-nautilus-image-script/268/)

I installed the script and went to resize some images and I get this error;

"You must select at least one image to resize".

D'oh!

---

