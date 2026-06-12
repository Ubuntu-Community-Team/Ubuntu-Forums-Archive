---
title: "mplayer plugins"
date: 2006-09-13
forum: Desktop Environments
---

### Post by moon_dog on 2006-09-13
i've followed numerous HOWTOs and i still can't see certain video formats on firefox (quicktime, etc.).  i've compiled mplayer from source and installed the essential codecs package to /usr/local/lib/codecs.  when i run mozilla and go to help-->about plugins, it says that the mplayer plugins are installed.  and yet when i test it by going to [www.apple.com/trailers](www.apple.com/trailers), i can't see anything, all i get is a blank screen saying no picture.  can anyone help?

---

### Post by reclusivemonkey on 2006-09-14
> **moon_dog said:**
> i've followed numerous HOWTOs and i still can't see certain video formats on firefox (quicktime, etc.).  i've compiled mplayer from source and installed the essential codecs package to /usr/local/lib/codecs.  when i run mozilla and go to help-->about plugins, it says that the mplayer plugins are installed.  and yet when i test it by going to [www.apple.com/trailers](www.apple.com/trailers), i can't see anything, all i get is a blank screen saying no picture.  can anyone help?

I've installed the stock mplayer and mplayer plugin from the repos and can see quicktime fine. Can you paste the contents from about:plugins from Firefox?

---

### Post by distroman on 2006-09-14
I compiled mplayer as well. 
Then I installed the plugins from here.
[http://mplayerplug-in.sourceforge.net/install.php](http://mplayerplug-in.sourceforge.net/install.php)

As it says you don't have to install after make.

For Debian/Ubuntu
```
cp mplayerplug-in*.so /usr/lib/mozilla-firefox/plugins
```
Works great here.

---

