---
title: "Firefox error in ubuntu 7.04"
date: 2007-08-09
forum: Desktop Environments
---

### Post by ekwok on 2007-08-09
I am using ubuntu 7.04 live CD. When I boot up to the Gnome desktop, I start the firefox and the error come out.

I had no problem with the ubuntu 7.04 live iso in vmware virutal pc environment but it happen when I use a CD to boot in a real machine.

---

### Post by 1/0 on 2007-08-09
Does it go away if you restart firefox? Is there a lock file in .mozilla/firefox/whatever.default/ ?

If the file is there and firefox is not started, delete it. In worst case try to rename .mozilla to .mozilla-old or something and see if that helps.

---

### Post by ekwok on 2007-08-09
It is still the same.
The whole flow is like, when I start firefox, I get an error message. I close the err windows and start firefox again. It shows the same error again.

Then I rename the .mozilla to .mozilla.old and start firefox again, but this time, I could event see an error message. In fact, nothing happen after I click it.

attached a sreenshot about the .mozilla directory.

I also take a video clip of this error at youtube.com
[http://www.youtube.com/v/YqFVspSc7PE]("http://www.youtube.com/v/YqFVspSc7PE")

---

### Post by 1/0 on 2007-08-12
Sorry for the late response, I've been to a festival. 

What if you start firefox from a shell? What error messages do you get then? Can you start it with the -safe-mode flag. Try -g for debug if necessary.

---

