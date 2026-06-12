---
title: "Firefox is killing me"
date: 2009-02-09
forum: General Help
---

### Post by airjaw on 2009-02-09
Thread title says it all. Flash player works 80% of the time. Firefox will freeze my entire system an average once every 12 hrs. (no force kill, no shortcuts work, have to power down + restart).  Firefox will hang on opening a new page and I'll have to force quit.  Or Firefox will simply close without warning and I have to restart it.
I don't know how many "previous sessions" i have restored. Probably 100+ now.

Yea this was more of a rant than anything, but I wanted to know if OTHER people were also having the same problems. Is this an Ubuntu issue? or a Firefox issue?

---

### Post by 2hot6ft2 on 2009-02-09
I was just reading about others having the same or similar problems in another forum here [http://forumubuntusoftware.info/viewtopic.php?f=46&t=2719](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2719) so you're not alone. Apparently it's a firefox problem and not just in ubuntu. Some other browsers were recommended like:
seamonkey ver 1.1.14
Swiftweasel
and the new beta Firefox:[http://www.mozilla.com/en-US/firefox/all-beta.html](http://www.mozilla.com/en-US/firefox/all-beta.html)

Personally I haven't been having problems and I also have swiftfox installed.

---

### Post by unplugged23 on 2009-02-09
Open synaptic, mark firefox for complete removal, and install it again.

---

### Post by Yashiro on 2009-02-09
It's a Flash Plugin issue.

---

### Post by unplugged23 on 2009-02-09
> **Yashiro said:**
> It's a Flash Plugin issue.

Ahhh...

---

### Post by airjaw on 2009-02-09
Hmm.. what about the random shutdowns and freezes? Those happen even without youtube open. They are s-c-a-r-y. I could be in the middle of doing something important and have to power down my computer..

I will give swiftweasel a try. hopefully I have more luck with it.
thanks guys.

---

### Post by Yashiro on 2009-02-10
Is this ubuntu 64 bit?

---

### Post by Ripose on 2009-02-10
If this is Firefox 64 bit you have to have ia32libs installed, or least have the Community-Maintained Repository enabled. Or disable flash.

---

### Post by Yashiro on 2009-02-10
Nope. You uninstall **all** flash plugins and remove nspluginwrapper. Then install the 64bit beta plugin .so into /home/YOU/.mozilla/plugins

---

### Post by Ripose on 2009-02-10
Where might we find this beta?

---

### Post by gilloz on 2009-02-10
Hi:  I am using Ubuntu 64 and it is not a beta.  I downloaded the ISO file and burned the image unto a CD, then installed it.  I have noticed that it is faster than the 32 bit program.  See link below.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

