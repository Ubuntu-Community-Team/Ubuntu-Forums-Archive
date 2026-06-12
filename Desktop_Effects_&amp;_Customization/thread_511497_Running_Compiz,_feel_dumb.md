---
title: "Running Compiz, feel dumb"
date: 2007-07-27
forum: Desktop Effects &amp; Customization
---

### Post by irel on 2007-07-27
Well, I feel less dumb after reading this thread:
[http://ubuntuforums.org/showthread.php?t=212941](http://ubuntuforums.org/showthread.php?t=212941)

But the problem is that I have it installed now, and I can not do anything with it.  I go to the settings manager and select what I think looks interesting, and nothing happens.  Same with the Emerald Theme manager. I find a theme I like, the only thing I can do with it is drag it around.  I am extremely new to this, having used windows for way to long, I felt like an idiot just not being able to do what should be simple things, and instructions are not to be found anywhere.  Thankfully, after reading that thread it seems like maybe it just is not installed properly.  Still, I can´t rule out the possibility that I´m just missing something.


Thanks,
-irel

---

### Post by irel on 2007-07-27
What I would like to do is just uninstall Compiz and reinstall it with a different method, but I am having a difficult time findout out how to uninstall it.  I think it is sudo apt-get remove, digging around the forums, but remove what I can not figure out.  I have already tried compiz, compiz-fusion, and, well, I guess that´s it.

Thanks,
irel

---

### Post by oldos2er on 2007-07-28
>What I would like to do is just uninstall Compiz and reinstall it with a >different method, but I am having a difficult time findout out how to uninstall >it. I think it is sudo apt-get remove

 Try these:
sudo apt-get remove compiz-gnome
sudo apt-get remove compizconfig-settings-manager
sudo apt-get remove compiz-core desktop-effects

 Hope this helps.

 I found some good info on using apt-get to its fullest here:
[https://help.ubuntu.com/community/AptGetHowto?action=show&redirect=AptGetHowTo](https://help.ubuntu.com/community/AptGetHowto?action=show&redirect=AptGetHowTo)

---

### Post by i3igTux on 2007-07-28
Perhaps you havent completed the last step, actually running the interface.

ALT+F2  (= Run fyi) and at the prompt type:   compiz --replace
ALT+F2 : emerald

If all was well, you should have wiggly windows, and a different theme installed for the window border.  I have heard it is not recommended to add these to the sessions list, but I have, and it works out fine.

If that doesnt work, I'm afraid I cant help you any further.

---

### Post by irel on 2007-07-28
You know, I´m not sure if I did that or not, I don´t think I did.  But I think I may have already uninstalled the compiz-gnome part, so it didn´t work.  But I think between the both of you I know what I need to do to get it working.  Thanks. :)

---

