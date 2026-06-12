---
title: "How to make gvbam"
date: 2008-10-27
forum: Gaming &amp; Leisure
---

### Post by Tonieddy69 on 2008-10-27
My friend has been trying to help me make gvbam, but every time the end result is vbam its self.. Does anyone know what we are doing wrong? If so, please help. :)

---

### Post by disturbedite on 2008-10-27
> **Tonieddy69 said:**
> My friend has been trying to help me make gvbam, but every time the end result is vbam its self.. Does anyone know what we are doing wrong? If so, please help. :)
you need to post the output of your compilation.

i compiled it from svn myself about a month ago but the result wasn't very functional: it wouldn't render video. :confused:

---

### Post by wingnux on 2008-10-27
I compiled it from svn this weekend and it worked like a charm! Here are the steps I did:

sudo apt-get install cmake
sudo apt-get build-dep visualboyadvance
svn co [https://vbam.svn.sourceforge.net/svnroot/vbam](https://vbam.svn.sourceforge.net/svnroot/vbam) vbam 
cd vbam/trunk
cmake .
make (I'm not sure if it's needed, can't remember atm)
sudo make install

All done! =)

---

### Post by wingnux on 2008-10-27
How do I delete a post?:confused:

---

### Post by Tonieddy69 on 2008-10-27
Ive tried those steps, though my friend said it should come out as gvbam, but never does, I always get vbam, will it still work, even if its vbam???

---

### Post by Perfect Storm on 2008-10-28
Sounds like you're missing to -dev packages like libgtk2 (and maybe others). Please as stated above post in/out-put of you actions.

---

### Post by Tonieddy69 on 2008-10-28
I will post them next time I am in Linux, right now I am in Windows XP to play Final Fantasy XI since my ATI card wont allow me to play in wine..

---

