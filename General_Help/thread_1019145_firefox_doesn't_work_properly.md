---
title: "firefox doesn't work properly"
date: 2008-12-22
forum: General Help
---

### Post by i_heart_pandas on 2008-12-22
firefox has been playing up to the point it's almost unusable

basically all of a sudden it's stopped doing alot of things

[LIST]
[*]when i start it it doesn't go to home screen it just goes to a blank screen(i can click on home to get there though)
[*]i can't go back or go forward(there greyed out the whole time, same for refresh and stop)
[*]it doesn't save url's, when i type in a url it doesn't give me history, so i have to type in everything
[*]when i go to another link the url stays the same as the first one i typed in (eg if i go i type in [www.google.com](www.google.com) then follow a link the url says [www.google.com](www.google.com) the whole time
[*]sometimes when i type in something like gmail.google.com it says "can't find www.gmail.google.com" 
[*]pretty shore it's slower as well
[/LIST]

I don't know what it's doing, I've reinstalled it but it didn't work, also I've fully uninstalled it then installed it again

this is firefox 3.0.5 on ubuntu 8.04 x64

any ideas?

thank you for your time
x

---

### Post by i_heart_pandas on 2008-12-22
also all my tabs have gone

---

### Post by Dr Small on 2008-12-22
When you uninstalled/reistalled, did you happen to delete or move ~/.mozilla in your Home directory?

---

### Post by i_heart_pandas on 2008-12-22
> **Dr Small said:**
> When you uninstalled/reistalled, did you happen to delete or move ~/.mozilla in your Home directory?

k let me try that, brb

---

### Post by i_heart_pandas on 2008-12-22
cheers, "sudo rm -r /home/g3rc4n/.mozilla/firefox" done the trick

---

