---
title: "Firefox not saving bookmarks?"
date: 2009-04-20
forum: General Help
---

### Post by sjprice on 2009-04-20
Just as the title says, I have all my bookmarks, but if I save a new one, it is gone after restarting Firefox. Disabled all my extensions, same issue. Checked Home permissions and I own everything, and Others is access only.

Thoughts?

---

### Post by chriskin on 2009-04-20
i would suggest installing the foxmarks plugin as a workaround, but i do not know a real solution

---

### Post by sjprice on 2009-04-20
I actually have Foxmarks, now xmarks, and that was the first thing I did was disable it to see if that was the issue. It wasnt. For some reason, I think it is a permissions issue, but really dont know...

---

### Post by sjprice on 2009-04-20
Solved by exporting bokmarks, removing Bookmarks.html from .mozilla folder and bookmarksbackup folder. Opened firefox with no bookmarks, and imported the file. 

Works fine now.

---

### Post by joshh88 on 2009-04-25
I'm having the same problem, but I am confused on how to find the bookmarks.html folder. I can't even find firefox; how and where????

---

### Post by imran65 on 2009-05-13
:-$:-({|=> **joshh88 said:**
> I'm having the same problem, but I am confused on how to find the bookmarks.html folder. I can't even find firefox; how and where????

Any one facing xmarks not sync. problem, or fiire fox crashing, just open the fire fox from shell using root passward instead of calling the program from menu list, or from user profile.

sudo firefox

it will open with the current saved book marks. and u can sync. without any problem. i did not understand that why it is happening, but i m very much sure that it is working;)

---

### Post by cottfcfan on 2009-05-13
I had the same issue, and had to keep reinstalling Firefox, in the end I realized it was only after I`d used Bleachbit, that it happened. Bleachbit also cleared all my Album Art in Banshee.
 Since I`ve stopped using Bleachbit, the problem has never reoccured.

---

