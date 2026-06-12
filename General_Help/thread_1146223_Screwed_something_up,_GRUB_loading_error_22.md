---
title: "Screwed something up, GRUB loading error 22"
date: 2009-05-02
forum: General Help
---

### Post by bubbagumper6 on 2009-05-02
Well I decided to try and give Ubuntu another shot and in the end once again decided it wasn't for me.  Unfortunately I then decided to boot windows and just format the hard drive that Ubuntu was installed on :(

Now when I try to boot it says:

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 22

Then it just sits until I hit the power button and shut down the computer...what should I do?  I just want to go back to being able to boot windows...

---

### Post by vishy1618 on 2009-05-02
Ok...I assume you are able to boot up using the Windows Install CD.
When It asks you whether you want to install windows or not, press 'R' to enter the Windows Recovery console.
After some time it will take you to a command line. There, you type:

fixmbr

There you go, GRUB is removed. Now restart.
BTW, sorry to hear that you find Ubuntu inadequate for your needs. I hope you give it an other try later. Ciao!

---

### Post by bubbagumper6 on 2009-05-02
I always seem to have trouble installing drivers.  And the driver support for my laptop isn't very good so I just don't think it's cut out for Ubuntu.  I do still have it on my desktop though :)

Thanks for the help!

---

