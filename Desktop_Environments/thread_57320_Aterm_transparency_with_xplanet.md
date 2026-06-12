---
title: "Aterm transparency with xplanet"
date: 2005-08-16
forum: Desktop Environments
---

### Post by phazer on 2005-08-16
Running fluxbox with xplanet with the rss-xplanet script ([http://home.arcor.de/mdoege/rss-planet/](http://home.arcor.de/mdoege/rss-planet/))

Now whaat I want is aterm to be tranparent with some shading, problem is, if I comment the shading line out of my Xdefaults file aterm works perfectly and transparency works, but no shading, if I turn shading on, no transparency.

Seeing as shading breaks transparency I commented the tranparency line out, until I can get this working.

Anyone have any idea on how to fix this?

Here's my aterm entries of my Xdefaults file :

aterm*loginShell:true
#aterm*transparent:true
#aterm*shading:90
aterm*background:Black
aterm*foreground:White
aterm*scrollBar:true
aterm*scrollBar_right:true
aterm*transpscrollbar:true
aterm*saveLines:32767
aterm*font:*-*-fixed-medium-r-normal--*-140-*-*-*-*-iso8859-1
aterm*boldFont:*-*-fixed-bold-r-normal--*-*-140-*-*-*-*-iso8859-1

---

### Post by MaXqUE on 2007-02-18
> **phazer said:**
> Running fluxbox with xplanet with the rss-xplanet script ([http://home.arcor.de/mdoege/rss-planet/](http://home.arcor.de/mdoege/rss-planet/))

Now whaat I want is aterm to be tranparent with some shading, problem is, if I comment the shading line out of my Xdefaults file aterm works perfectly and transparency works, but no shading, if I turn shading on, no transparency.

Seeing as shading breaks transparency I commented the tranparency line out, until I can get this working.

Anyone have any idea on how to fix this?

Here's my aterm entries of my Xdefaults file :

aterm*loginShell:true
#aterm*transparent:true
#aterm*shading:90
aterm*background:Black
aterm*foreground:White
aterm*scrollBar:true
aterm*scrollBar_right:true
aterm*transpscrollbar:true
aterm*saveLines:32767
aterm*font:*-*-fixed-medium-r-normal--*-140-*-*-*-*-iso8859-1
aterm*boldFont:*-*-fixed-bold-r-normal--*-*-140-*-*-*-*-iso8859-1

In Ubuntu Xdetaults is called Xresources. Aparently changing the name of the file will get Ubuntu to read it. I found [this answer here]("http://ubuntuforums.org/archive/index.php/t-8244.html").

I haven't tried it yet, but I want several litres of that transparency myself!.

And I just tried it... this sollution doesn't work. The filename change works but not transparency. :(

Mq

cheers,
MaXqUE

---

