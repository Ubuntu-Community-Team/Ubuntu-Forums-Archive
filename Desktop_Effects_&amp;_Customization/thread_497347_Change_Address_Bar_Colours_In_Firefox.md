---
title: "Change Address Bar Colours In Firefox ?"
date: 2007-07-10
forum: Desktop Effects &amp; Customization
---

### Post by gidra on 2007-07-10
I just installed a dark theme and it looks really nice except for firefox. The address bar has white text on a black background. Tried to mess up with usercontent.css but no luck. Any ideas how to invert the colours please ?

---

### Post by crimesaucer on 2007-07-10
You should try userChrome.css, ask how to do it in the Theme Development section of this forum: [http://forums.mozillazine.org/index.php](http://forums.mozillazine.org/index.php)

Mozilla Theme Development: [http://forums.mozillazine.org/viewforum.php?f=18](http://forums.mozillazine.org/viewforum.php?f=18)


This is about userChrome.css: [http://www.mozilla.org/support/firefox/edit#css](http://www.mozilla.org/support/firefox/edit#css)

and here is an example of some things you can do in Firefox with userChrome.css: [http://www.mozilla.org/support/firefox/tips](http://www.mozilla.org/support/firefox/tips)

---

### Post by crimesaucer on 2007-07-10
This might work, it was in the Mozilla Forum:

```

#urlbar {
background-color: #FFFFFF !important;
color: #000000 !important; }

```

just try and add that to your userChrome.css file, and if it doesn't work you can always edit it out. You can also change the colors to your liking.

---

### Post by gidra on 2007-07-10
Thank for your reply. I'll try it later cause i'm a bit busy right now, keep ya posted

---

