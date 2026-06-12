---
title: "Ubuntu freezing all the time!"
date: 2009-03-22
forum: General Help
---

### Post by SlingerXL on 2009-03-22
I run 8.04 on a dell inspiron 1525. Recently Ubuntu starts freezing every 30 seconds or so for about 30 seconds then comes back to life. It freezes more often after hibernating or being suspended and gradually the freezes become more and more intermittent but it still happens a lot even at its best. 

I believe this started happening after Ubuntu really ****** up on me. Giving me blank error messages for everything and unending theme options for cairo dock. I just ran fsck at the boot and that seemed to clear things up. But that's when this freezing stuff started happening I think. 

Anyone know why?

---

### Post by dodle on 2009-03-22
I'm just guessing, but I would say it sounds like a video card/driver issue.  What video card are you using?

See if there is another driver available for it.
Try using the "vesa" driver, see if the freezing still occurs.

I am currently using vesa, becuase I have a Via Unichrome IGP, and none of the available drivers work 100% correctly for me.

---

### Post by SlingerXL on 2009-03-22
How do I find out what drivers I have?

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

---

### Post by dodle on 2009-03-22
To list/change your graphics card drivers you can do the following from the terminal:```
gksu displayconfig-gtk
```Select the "Graphics Card" tab.  I hope this helps.

---

### Post by SlingerXL on 2009-03-22
[IMG]http://img.photobucket.com/albums/v484/SlingerXL/SSvideodriver.jpg[/IMG]

---

### Post by dodle on 2009-03-22
That's strange.  I have no idea why it shows you two graphics cards.  Have you tried changing the top one to vesa?

---

### Post by SlingerXL on 2009-03-25
I tried but when I click it it already has vesa selected and when I hit OK it just says none again like in that screenshot. I have written this post several times now because Firefox is randomly closing now!

---

### Post by SlingerXL on 2009-03-26
Anyone know?

---

