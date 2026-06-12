---
title: "how do I delete .ttf files from /usr/share/fonts/truetype"
date: 2009-02-18
forum: General Help
---

### Post by ozguitarplayer on 2009-02-18
I guess this is the way some of us learn...

I followed a tutorial (well almost) that showed how to install .ttf font files into /usr/share/fonts/truetype/msttcorefonts however the /msttcorefonts folder dosen't exist and they ended up in 
/usr/share/truetype. 

I need to remove them and there isn't a delete/move to garbage bin/trash option when I right click....is is possible to remove the files and how would I do it?

---

### Post by Vaphell on 2009-02-18
launch terminal

sudo rm /usr/share/truetype/*.ttf (assuming you want to remove all .ttf files from that directory)
you are prompted for password, done.

sudo before rm command (rm=remove) means that you want to perform it with root proviledges (sudo=super user do) - you have to because you want to perform it in system directories and user accounts can't modify them freely.

alternatively you can run file browser with root privileges (probably better option if you are scared of using cryptic commands without understanding them)
sudo nautilus (in terminal of course, nautilus is the name of ubuntu file browser)

new window of system file browser pops up and you can delete anything using that window. Be careful and close it asap after performing the task, because you can delete anything as a superuser. In general avoid using sudo unless totally necessary.

---

### Post by ozguitarplayer on 2009-02-19
thanks Vaphell, being new to this I might try the Nautilus method first....but ummm how do I run a file browser with root privilages?.......hang on I'll go look first

---

### Post by ozguitarplayer on 2009-02-19
done....thanks again Vaphell...so much to learn it's scary...

---

