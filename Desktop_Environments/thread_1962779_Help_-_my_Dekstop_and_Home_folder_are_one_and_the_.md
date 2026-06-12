---
title: "Help - my Dekstop and Home folder are one and the same"
date: 2012-04-21
forum: Desktop Environments
---

### Post by Digital_Man on 2012-04-21
I'm running Ubuntu 11.10 with Unity and somehow, I managed to make my Desktop and Home folder one and the same. Not sure how I did that....

But the result is, anything on my Desktop is also in my Home Folder and anything in my Home folder is on my Desktop. If I delete an item from one, it also deletes it from the other.

Any suggestions as to how on earth I can separate the two again?

Any guidance appreciated.

---

### Post by metulburr on 2012-04-21
I had the same problem when i accidently mounted a dir to my home. I rebooted and then the two were separate again.

---

### Post by raja.genupula on 2012-04-21
[http://www.simplehelp.net/2008/08/26/how-to-use-your-home-folder-as-your-desktop-in-ubuntu/](http://www.simplehelp.net/2008/08/26/how-to-use-your-home-folder-as-your-desktop-in-ubuntu/)


look at that , the selected area check box was selected , un select it for your case .

---

### Post by Digital_Man on 2012-04-21
Still struggling here. A reboot didn't help, and going to the dconf-editor, nautilus, there were not any other options to unlink Desktop and Home folder.

Again, I'm using 11.10 with Unity - any help?

Anything would be greatly appreciated!

---

### Post by Digital_Man on 2012-04-21
Solved. The first answer on this page did it:

[http://askubuntu.com/questions/44449/ubuntu-desktop-suddenly-points-to-home-folder#44467](http://askubuntu.com/questions/44449/ubuntu-desktop-suddenly-points-to-home-folder#44467)

---

### Post by raja.genupula on 2012-04-21
> **Digital_Man said:**
> Still struggling here. A reboot didn't help, and going to the dconf-editor, nautilus, there were not any other options to unlink Desktop and Home folder.

Again, I'm using 11.10 with Unity - any help?

Anything would be greatly appreciated!

Hey its gconf not dconf see in the link i have given to you . glad you have solved it .

---

### Post by Digital_Man on 2012-04-22
> **raja.genupula said:**
> Hey its gconf not dconf see in the link i have given to you . glad you have solved it .

I wasn't able to run gconf on 11.10 Unity, but maybe that's my fault....
But still, thanks very much for your reply, and yes, thankfully it's solved.

---

### Post by Krytarik on 2012-04-22
> **raja.genupula said:**
> Hey its gconf not dconf see in the link i have given to you .
No, it's not ;-) - since Oneiric 11.10, thus Gnome 3, Nautilus stores its settings in DConf.

Regards.

---

