---
title: "X/Gpdf customization"
date: 2005-11-10
forum: Desktop Environments
---

### Post by cbpxy on 2005-11-10
Hi all,

I'm a longtime unix/linux user, and I've been using Ubuntu for about 6-8 months.  It's very nice!

Here's my question:  I would like to configure gpdf (or xpdf) to open fullscreen and "Fit Width" (that is, as if I'd clicked the "Fit Width" button).  Can I do this?  Is this just a matter of editing an .Xresources file, or is there some modern way to do this?

It's not  extremely important, but it would be nice (as I always make the two clicks when opening a PDF from the web).

Thanks very much,

cbpxy

---

### Post by cbpxy on 2005-11-10
Hi,

I'm responding to my own post, but I still can't do all I want.  :???: 

I added this to my .Xresources file: 
```

xpdf*Geometry: 1270x956+0+0
xpdf*initialZoom: width
```

After running the command 
```
xrdb -merge .Xresources
```
this will do what I want for xpdf.  Alas, for some reason I prefer gpdf (it's prettier, what can I say?) and the analagous thing doesn't work for gpdf.  

Can you help?  Thank you!

---

