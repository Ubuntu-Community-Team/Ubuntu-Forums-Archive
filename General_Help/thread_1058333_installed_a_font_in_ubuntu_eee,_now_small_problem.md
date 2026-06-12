---
title: "installed a font in ubuntu eee, now small problem"
date: 2009-02-02
forum: General Help
---

### Post by Fenris_rising on 2009-02-02
Hi all

I have an eee pc running ubuntu eee 8.04.1. I installed a couple of fonts today. I followed a short tut on here to install them and the refresh the cache so they were known to the OS. Now I went to a post on here that had a link to a website to 'measure your geekness' To my surprise the text of the site was in one of the font styles I had downloaded. Because the font in question is based on the Dr Who new series daleks ID tags its illegable :D. I tried deleting the relevant ttf then running the code to refresh the cache again but the web page stayed the same. Now I have just been to another site and odd bits of text were in the same Dalek Font. The font is called 'logo code' and works only in upper case. So how do I correct the problem or if this isn't  possible clean it out of my system so that I don't have this problem. I believe the logo code font was created in windows by the provider of the font. I have not selected it as a font to use anywhere except in Open Office. See sample :)

regards

Fenris

---

### Post by Fenris_rising on 2009-02-04
Anyone? :)

---

### Post by lswest on 2009-02-04
Can you go to firefox's preferences and see what settings you're using for fonts, and make sure that sites are allowed to choose their own fonts.  Also, make sure you restart firefox before refreshing a page. Can't think of anything else that might help.

Hope that helps,
Lswest

---

### Post by Fenris_rising on 2009-02-04
Hi there

Thanks for the reply. Having checked the firefox font preferences it seems to be the 'serif' family of fonts throughout. The allow websites to pick their own was ticked. I unticked it and now the font on the website is in a standard english text :) . I presume something has gone slightly awry as I really dont think the sites creator would have picked a font I just happened to download. So is there something wrong with the downloaded font that causes this problem? I think the font in question 'logo code' was modified from a standard serif font IIRC so has despite it's current name could there be a fault that still identifies it to the PC as serif?
At least for now I can read the web pages but how, once I remove the font, do I reset the system so it does not continue to use it?

thanks again

regards

Fenris

---

### Post by redilyn on 2009-02-04
I thought you just had to delete the font, update the cache, then logout/login to remove a font.

Delete The Font

Then Run
```

sudo fc-cache -f -v

```

Then Logout & Login

Maybe this will shed some light on the problem
[http://ubuntuforums.org/archive/index.php/t-215955.html](http://ubuntuforums.org/archive/index.php/t-215955.html)

---

### Post by Fenris_rising on 2009-02-04
Ahhhhhhhhhhhhhhh! :) It would be the log out log in that I didn't realize I had to do to complete the change. Thankyou Gentlemen much appreciated.

regards

Fenris

---

