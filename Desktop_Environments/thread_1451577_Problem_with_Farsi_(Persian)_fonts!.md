---
title: "Problem with Farsi (Persian) fonts!"
date: 2010-04-10
forum: Desktop Environments
---

### Post by gagea on 2010-04-10
Hello friends,

I have problem with Farsi fonts on the ubuntu. The Mozilla Firefox can not show the Farsi website properly. I have already installed all Farsi fonts available Synaptic Package Manager. Anybody know hoe to solve the problem.

Thanks a lot in advance

Gagea:confused:

---

### Post by quixote on 2010-04-11
I assume if you installed the fonts with Synaptic, everything should be in the right place and the cache updated, but check just to make sure.

Judging by my system, where Synaptic shows only one installable Farsi font, that's a truetype font.  So it would normally go in this directory: ```
/usr/share/fonts/truetype/*farsi-font-file-or-directory*/
```If it's not there, then that's the problem.  Either download again or, if it's already somewhere else on your system, copy it there: ```
sudo cp /current/location/your-farsi-file.ttf /usr/share/fonts/truetype/your-farsi-file.ttf
```.  Then you need to update the font cache: ```
sudo fc-cache
```(You don't have to use synaptic.  Download ttf, put it in the right /usr directory, and update the font-cache, is all you need.  It's what synaptic should be doing for you, but apparently isn't.)

---

### Post by mehdi_mfs on 2010-09-02
hi dear`
i had this problem but i solved it :
first i create a folder in my home directory and named it *.fonts*
then i copeid windows(bfonts) fonts in this folder 
```

cd~
mkdir .fonts
cp /my_font_folder  ~/.fonts

```

---

### Post by quixote on 2010-09-03
That's interesting know.  I bet that would work for any fonts you wanted to use, and on a one-user machine, it's easier than the whole /usr/share/fonts route.  Did you have to update the font cache afterward or not?

---

