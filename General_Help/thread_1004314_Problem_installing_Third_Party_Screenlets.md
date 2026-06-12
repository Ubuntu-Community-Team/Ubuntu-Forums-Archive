---
title: "Problem installing Third Party Screenlets"
date: 2008-12-07
forum: General Help
---

### Post by Rohatgir on 2008-12-07
I'mmmm Baaack!!! With more problems again!

Once again, I'm a little new, but I'm learning kind of fast. I was having a problem installing some screenlets that I downloaded from their website at [http://screenlets.org/index.php/Category:UserScreenlets](http://screenlets.org/index.php/Category:UserScreenlets).

Now after I download them, I get a zipped file which I take the folder out of. I tried going through the application and when I navigate to the folder it doesn't recognize the screenlet, in the sense I have nothing to click on. 

Then when I try the "hard way" which I read in the faqs, when I try to copy to the folder itself, it won't let me due to lack of permissions.

I don't know what to do, could someone help me out, as well as, point me to a good Note-screenlet as I do not like the one that came bundled with the software. I would love to use TomBoy notes if the notes stayed in widget layer only.

Also, which widgets from other companies (google gadgets, etc) can I convert?

Thanks for the help!

---

### Post by Bakerconspiracy on 2008-12-07
Hey there is google gadgets for linux. You should google it haha.

As far as changing your permissions on the directory, you should navigate to the directory in terminal and type "sudo chmod -R 755 ./"directory_name" ".

---

### Post by Rohatgir on 2008-12-07
Thanks :) After a tad more research, I found out that I needed to add it to a hidden folder! But after doing that, Pandora wouldn't add due the fact that it needs..

"You need Gtkmozembed to run this Screenlet , please install it"

Yet, I couldn't find that. Also, my main purpose is a good note program where I can have multiple notes with different things on them. I didn't like either Simple Notes or Clear Notes. Any suggestions about the putting up Pandora or a good Note Dealio?

---

### Post by Rohatgir on 2008-12-08
Bump! anyone? Pandora! Good notes program for widget layer?

---

### Post by Wartender on 2008-12-08
did you try dragging the compressed file (the .tar or .tar.gz) onto the screenlets manager? that's what you're supposed to do to install them you know...

---

### Post by Rohatgir on 2008-12-08
When I do that I don't have the permissions to add it? how do I change the permissions in detail?

---

### Post by Wartender on 2008-12-08
```
sudo nautilus
```
then drag? not sure just throwing ideas out there and i'm done for the day i'll check back tomorrow

---

### Post by Rohatgir on 2008-12-09
Hmmm, I just type sudo nautilus in terminal and then what do I do? Just try to drag it then?

---

### Post by Wartender on 2008-12-09
yeah give it a shot if it's a permissions problems maybe it'll work

---

### Post by curtiswtaylorjr on 2009-05-15
After I did some research, I found out that I need to do this:

sudo apt-get install python-gnome2-extras
or just search for and install the python-gnome2-extras package.

This also works for the youtube screenlet.

---

### Post by siabost on 2009-07-16
Thanks. Worked for me too.

:D

---

