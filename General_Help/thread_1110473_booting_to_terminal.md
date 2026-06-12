---
title: "booting to terminal?"
date: 2009-03-29
forum: General Help
---

### Post by williane on 2009-03-29
Ok so I've googled this. theres a billion and one articles on how to do it changing X file, or X config setting. But the problem is I cant log in, I need boot to terminal to edit soemthing so I'm able to log in again. I though recovery mode might allow me to do this but that didn't work either. Any ideas?

---

### Post by Bakon Jarser on 2009-03-29
Do you have a live cd?

---

### Post by williane on 2009-03-29
Yeah, tried that. Permissions issues with that though. Can't save the file after I edit it.

---

### Post by Bakon Jarser on 2009-03-29
You opened the file as root?

gksu gedit (filename)

---

### Post by williane on 2009-03-29
Oh, no, sorry I'm pretty nub at this still. I was trying sudo. Let me try that. Thanks for your help.

---

### Post by williane on 2009-03-29
Yeah, that worked great. Thanks again for the help. Back in ubuntu now. :)

---

### Post by Bakon Jarser on 2009-03-29
Glad you got it fixed.  Just so you know, sudo is for root on command line, gksu is for root with graphical programs.

---

