---
title: "Google Talk VoIP Client for Feisty?"
date: 2007-05-14
forum: Desktop Environments
---

### Post by adityanag on 2007-05-14
Hi,

I want to be able to voice chat on the Google Talk network. I have tried installing Tapioca, but it does not work. The error I get is

tapiocaui: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory

EDIT--  I followed [http://ubuntuforums.org/showthread.php?t=291089&page=2](http://ubuntuforums.org/showthread.php?t=291089&page=2), and now Tapioca runs, but I cannot voice chat.. I  don't hear anything, nor does the other party. I tried all the volume settings too, nothing works

I also tried install Landall, but here it says that I have an unsatisfied dependency of libdbus1-2. But I already have this installed.

If anyone can either help me install these two, or point me to some other client that works well, I would be very grateful. All I need is Voice Chat to work

Thanks,
Aditya

---

### Post by loell on 2007-05-15
try gizmo 3.0 beta, it can talk with gtalk 

[http://download.gizmoproject.com/jasmine/gtk-gizmo-3.0.1.67/gizmo-project_3.0.1.67_i386.deb]("http://download.gizmoproject.com/jasmine/gtk-gizmo-3.0.1.67/gizmo-project_3.0.1.67_i386.deb")

add the gtalk user as your contact.

---

### Post by adityanag on 2007-05-15
Hmm,

This is an interesting workaround, but ineffective for a large number of contacts. Thanks though, at least I can do some VoIP now.. 

If anyone else has any suggestions, bring em on!

Thanks again, loell, your reply is much appreciated!

---

### Post by loell on 2007-05-15
np :) , another option is to install 

[Jabbin]("http://www.jabbin.com/int/configure-jabbin-for-google-talk/")

---

### Post by adityanag on 2007-05-15
so i tried jabbin.. and this is what i get., chat works, but not VoIP. sigh

nag@nagmobile:~$ jabbin
/home/nag/.psi
/usr/share/jabbin
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by flickerfly on 2007-08-22
Jabbin has improved since this post. They now claim support for libjingle, meaning GoogleTalk audio support. It might be worth checking out.

---

### Post by anindya.baruah on 2007-08-22
I was looking for something using which I can send files. But for people who just want to use voice, you don't need to install anything. Just go to [http://talk.google.com/](http://talk.google.com/). Click on Launch Google Talk and you will see a flash based version of Google Talk. It has the voice chat feature. :)

---

### Post by adityanag on 2007-08-23
No, it does not. 

The website does not mention it anywhere, and I tried. There is a call button, but you can't click it.

---

