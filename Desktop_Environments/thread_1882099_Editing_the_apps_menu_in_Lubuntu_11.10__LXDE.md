---
title: "Editing the apps menu in Lubuntu 11.10 / LXDE"
date: 2011-11-16
forum: Desktop Environments
---

### Post by dajare on 2011-11-16
Is there an idiot-proof guide on how to remove items from the apps menu in Lubuntu? 

I installed Digikam from Synaptic Package Manager. It is a very nice photo-management suite, but it brought a lot of dependencies with it. One of them is "Akonaditray", which is now showing up twice in my "Accessories" menu. I don't even want it to show up once. 

How do I get rid of it from the menu? I thought to simply remove it using Synaptic, but Digikam (which looks quite useful) wants it kept. So can I at least get it off my menu? BOTH of the entries?

(The closest I could get for this question was a [thread on a missing menu item]("http://ubuntuforums.org/showthread.php?t=1837321"), but it didn't quite answer my question.)

Thanks!

---

### Post by Rodney9 on 2011-11-16
Open PCmanFM navigate to
 ```
/usr/share/applications
``` 
go to 'Tools' 'Open Current Folder as Root'
and you should see two "Akonaditray" there, then delete one.

Rodney

---

### Post by dajare on 2011-11-17
Thanks Rodney. This will have to wait until this evening now, but will report back on how it goes.

I actually found my way to that directory, but then didn't know what to do next! ;)

---

### Post by MG&amp;TL on 2011-11-17
Hello!

I'll try and make this as simple as possible. Open your file manager (known as pcmanfm), then click Tools, then 'open current folder as root'

Now enter your password. You are now root, so be CAREFUL. Now go to /usr/share/applications as before. You should see a load of icons that look like the ones in your menu (screenshot provided!). Now, delete the ones you don't want. Carefully, otherwise you might have to reinstall something.

Now close the window. You should not be root, and if you look in your menu, the offending items should be gone. :D

---

### Post by BobMarleyy on 2011-11-17
Try searching this forum without specifying you are using Lubuntu, because other ubuntu's can also use the lxde or xfce desktop as in lubuntu. Anyway check this thread:
[http://ubuntuforums.org/showthread.php?t=1875258](http://ubuntuforums.org/showthread.php?t=1875258)

I hope this helps you.
Cheers,
Bob

---

### Post by dajare on 2011-11-17
@Rodney9 & @MG&TL - thanks for those nicely complementary sets of instructions. Worked very nicely! The offending item is gone.

@BobMarleyy - thanks for the pointer to that thread, and the reminder that LXDE queries can come up in other contexts than Lubuntu. I'd overlooked that completely! (Still quite new to the whole "DE" thing.)

---

### Post by oboedad55 on 2012-04-18
Here's an easier way, install lxmed. You get a nice gui menu editor;
[http://lxmed.sourceforge.net/](http://lxmed.sourceforge.net/)

---

### Post by Adrian98 on 2012-04-19
i was just starting from the Lubuntu and now I got the solutions to remove the apps from the menu thanks!!

---

### Post by kelleychambers on 2012-11-18
I've been with Ubuntu on-and-off since 2003... but this is my first experience with Lubuntu & XFCE. I've got it running speedily on my Asus 1001PX netbook.

I wanted to thank not just the people who answered the question (which was super duper helpful!!!) but to the poster of the question as well.  I wouldn't have found the solution so quickly without you both!  Thank you!!!
:guitar:

---

### Post by dralaroc on 2012-12-02
Thank you very much!

---

