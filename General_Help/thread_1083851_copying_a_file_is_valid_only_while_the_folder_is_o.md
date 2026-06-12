---
title: "copying a file is valid only while the folder is open"
date: 2009-03-01
forum: General Help
---

### Post by chriskin on 2009-03-01
ok the title is not the best i could find

what i mean is that, once i copy something, for example some text from firefox, and i close firefox, then i cannot paste the text anywhere because it is automatically deleted. 

can i not make it be kept until i copy something else?

---

### Post by taurus on 2009-03-01
Try highlighting text that you want to copy with the right button of the mouse and wherever you want to paste, press the little scroll ball or both right and left buttons at the same time.

---

### Post by chriskin on 2009-03-01
it didn't work, it just vanished once i closed firefox, even though it worked perfectly while firefox was on

strange, does it happen to any pc or just mine? i remember it happened on every ubuntu installation i have tried

---

### Post by cariboo on 2009-03-01
That could be called a bug, the problem is well known. Paste what you have copied before you close the application and you should have no problems.

Jim

---

### Post by chriskin on 2009-03-01
seems one cannot have everything he wants :)


thanks for your time :)
:popcorn:

---

### Post by Zimmer on 2009-03-01
> **chriskin said:**
> ok the title is not the best i could find

what i mean is that, once i copy something, for example some text from firefox, and i close firefox, then i cannot paste the text anywhere because it is automatically deleted. 

can i not make it be kept until i copy something else?

When you close Firefox you are releasing the Firefox clipboard buffer, hence no text to paste. There may be a standalone clipboard app that will get you over those problems and I have an inkling I came across one once in KDE .... I may Search for a GNOME app and get back to you...
EDIT:
Glipper,  it is in the repositories, it may do what you require...
See [http://blogs.howtogeek.com/jatecblog/posts/glipper-clipboard-management-for-gnome](http://blogs.howtogeek.com/jatecblog/posts/glipper-clipboard-management-for-gnome)
[http://glipper.sourceforge.net/](http://glipper.sourceforge.net/)
[http://ubuntuforums.org/showthread.php?t=8868](http://ubuntuforums.org/showthread.php?t=8868)

---

### Post by doug1212 on 2009-03-01
There is a utility called parcellite available from getdeb that is quite useful for holding cut or copied text etc:

[HTML]http://parcellite.sourceforge.net/[/HTML]

Doug.

---

### Post by s_raiguel on 2009-03-10
I'm always running up against this extremely annoying behavior, not just in Firefox, but in Thunderbird as well. Why on earth doesn't Mozilla use the Ubuntu clipboard, what was the logic, if any, in having it maintain a  private clipboard? The Windows versions of the Mozilla programs don't seem to have this strange glitch. At any rate, I'll give the Parcelite program a try; but I shouldn't have to, this is one of those things that should just work.

---

