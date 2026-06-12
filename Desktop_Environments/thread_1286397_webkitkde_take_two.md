---
title: "webkitkde take two"
date: 2009-10-08
forum: Desktop Environments
---

### Post by dlenmn on 2009-10-08
I just wanted to share something I've learned. Maybe it isn't news, but it was the subject of an old (now read only) [thread]("http://ubuntuforums.org/showthread.php?t=651334") that was never completely resolved, and I haven't been able to find mention of it since then.

webkitkde installs the WebKit KPart -- it allows you to use [WebKit]("http://en.wikipedia.org/wiki/Webkit") (the power behind Apple's Safari and Google's Chrome) to render html instead of [KHTML]("http://en.wikipedia.org/wiki/KHTML") in applications like Konqueror.

KHTML has problems rendering a number of websites I frequent (and has other issues including content in background tabs bleeding through to the current tab), but WebKit seems free of these, so some of you might want to give it a shot. The WebKit KPart is described as a "work in progress," but what here isn't?

Anyhow, enough background. Here's how to do it:

1) Install webkitkde ('sudo apt-get install webkitkde' on the command line, or use your prefered graphical method)
2) Restart any browsers.
3a) If you just want to test it out without making it the default renderer then go to the View menu > View Mode > Webkit. That will make the current tab rendered with WebKit.
4a) To make this the default enter the command 'keditfiletype text/html'
and move "WebKit (webkitpart)" in the "Embedding" tab to the top.

The instructions were partially stolen from this [readme]("http://websvn.kde.org/*checkout*/trunk/playground/libs/webkitkde/README").

Enjoy.

---

### Post by dlenmn on 2009-10-09
I see now that there was a request on [another thread]("http://ubuntuforums.org/showthread.php?t=1238833") for a PPA with a newer version of the webkitkde package. For my own amusment, I've made a package for karmic from the latest source and put it in [my PPA]("https://launchpad.net/~leon-n-maurer/+archive/ppa"). This is the first time I've made a package, and I don't know the state of the source code (I am in no way associated with the development of the WebKit KPart), so there's the off chance that installing this package will blow up Pittsburgh. However, I followed the instructions and the package works on my computer. If there's interest, I can keep this package up to date since no one close to the project is regularly providing new packages.

---

