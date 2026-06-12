---
title: "How can I run Sancho ?"
date: 2006-01-11
forum: Desktop Environments
---

### Post by Zonkle on 2006-01-11
Hi,

I installed MLDonkey Server from Synaptic with the GTK GUI. As I found, to run the server I have to type in the terminal "mlnet" so it will start the server with its files (settings and others) at the place where I executed the command (ex home folder).
The GTK GUI doesn't look good at all ..... so I found that there is a nice GUI called Sancho, so I downloaded. So how can I make it run ?? I tried a lot but it didn't work .... when I tried ./sancho then I get the error:
./sancho: line 7: 13065 Segmentation fault      ./sancho-bin "$@"


So my question please ... how can I have Sancho in the "Internet Menu" and when I click on it - it loads MLDonkey and Sacnho .. becasue as I remember I didn't have the "Launch at start" option for MLDonkey.

Thanks.

---

### Post by Zonkle on 2006-01-14
No reply :(?

---

### Post by Zonkle on 2006-01-14
No reply :(?

---

### Post by MiKom on 2007-05-25
Same problem here, why it's not in repositories?

---

### Post by wladston on 2007-06-12
agreed .. they should put that one the repos ...

---

### Post by rcmn on 2007-06-26
ok here is how i did it ,
download the linux binaries - gtk and the version with the gnu head (avoid any java stuff it's bad for your heart and bad for your brain,)
[http://sancho-gui.sourceforge.net/files/2i866qudvmaqa/sancho-0.9.4-58-linux-gtk.sh](http://sancho-gui.sourceforge.net/files/2i866qudvmaqa/sancho-0.9.4-58-linux-gtk.sh)

then save it to your home directory:
# cd ~
# chmod 775 sancho-0.9.4-58-linux-gtk.sh
# ./sancho-0.9.4-58-linux-gtk.sh
Extract to directory [<sancho-0.9.4-58-linux-gtk>]: enter/the/path/you/want or just type <enter> key(it will create the folder in your home directory.
# cd sancho-0.9.4-58-linux-gtk
# ./sancho

and sancho will launch.

after you can create a shortcut depending of the distribution you are using.ubuntu/kubuntu/xubuntu/touroudoudoupoilaucoup.

good luck

Because Sancho is so wildly use in the other OS it should be added to the repository.
Also mldonkey-gui is a heavy/clumzy/ugly/bugy joke vs sancho or kmldonkey.Packaging that was/is an obvious wast of time ,Sorry for the devellopers of this project and the maintainer of the package but it has to be said.Even if you want to keep maintaining that thing(for diversity purposes) at least allow people the comfort of using a nice clean gtk apps.Andale!!! or maybe it in the process of been incorporated in that case =>[exit].

---

### Post by wladston on 2007-11-23
I just got the tar.gz, extracted it, and then right-clicked the sancho file, and there is a tab where you can check "allow execution of this program" or somthing like. then whenever I need to run it, I have to go to that folder, and double click sancho.

I'm going to find out how to have sancho as a normal program on the applications -> internet, and how to have a deb file to properly install it.

---

### Post by wladston on 2007-11-23
guys, I looked up and found no information on how to make a binary .deb package that I could understand...

can someone here  help ?

I can't stand to that stupid sancho folder on my desktop, just making clutter...

---

