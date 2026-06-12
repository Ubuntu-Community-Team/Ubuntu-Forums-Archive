---
title: "Beryl Cube help"
date: 2008-03-10
forum: Desktop Effects &amp; Customization
---

### Post by MaX PL on 2008-03-10
For some reason, either a feature i enabled or something else, my desktop cube(in beryl) is all messed up now.  

Every cube face besides the main default one is crashed.  I open an application and its as if a dozen windows are open of the same app.

I tried removing beryl and putting it back on, but the settings remain.  Is it possible for me to remove it along with any settings?

---

### Post by Immolatus on 2008-03-10
I think you need to root out and remove any remaining config files. Also make sure you choose to "completely remove" beryl before you reinstall. Probably what is happening is when you reinstall it's picking up the old config files and using them. do in terminal 
code: 

locate beryl

and you'll have to weed them out manually. Or you could just run Compiz Fusion like the rest of us. I was a Beryl over compiz person myself but I think compiz fusion is much more like beryl than compiz.

---

### Post by MaX PL on 2008-03-10
yeh i just tried installing compiz fusion and am having difficulty with that as well.

says its already on my computer when i try to install it, but i dont really know where to find it.

and yeh, theres no way a nub like me  can find and remove old config files.  no idea how to do that.

---

### Post by billgoldberg on 2008-03-10
In ubuntu gutsy gibbon (7.10) compiz fusion installed by default.

You just need to go to "system -> preferences -> appearance", go to visual effects and select custom.

No open up a terminal (applications -> accessories) and copy/past this:

```
sudo apt-get install compizconfig-settings-manager
```

You can now change settings in "system -> preferences -> advanced destkop effects settings"

The "cube caps" button is somewhere in the bottom, don't change it in "desktop cube" as you did with beryl, it won't work.

note: to change the number of virtual desktop, go to "general options -> desktop size -> horizontal virtual size" in the advanced desktop effects settings.

Please post if this fixes the problem with compiz fusion.

---

### Post by MaX PL on 2008-03-10
well actually i'm using feisty thru Wubi so i'm not sure if the instructions you posted work.

now i've removed all beryl and compiz files using synaptic.  apparently the compiz stuff was already on there but i didnt know how to access it.

i guess now i have to reinstall some of these compiz files in order to get compizfusion to work?

[IMG]http://farm3.static.flickr.com/2184/2325453204_617d4ab4e5_b.jpg[/IMG]

---

### Post by MaX PL on 2008-03-10
man i'm seriously confused.  is compiz fusion just the default manager on feisty?

how do i access the settings for it?  

all i am trying to do is get the animation effects and desktop cube options i got with beryl manager.  i'm done with beryl i guess so how do i go about getting this with compiz or compiz fusion(are these two the same things?)?

---

### Post by billgoldberg on 2008-03-10
No, compiz fusion isn't installed by default on feisty.

Follow this guide to install compiz fusion on ubuntu fiesty fawn.

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

---

### Post by MaX PL on 2008-03-10
ok thanks alot.  

i guess beryl wasnt working correctly due to the fact that my video drivers were not updated.  oh well...  :)

---

### Post by Immolatus on 2008-03-13
so.....did this solve your problem?

---

