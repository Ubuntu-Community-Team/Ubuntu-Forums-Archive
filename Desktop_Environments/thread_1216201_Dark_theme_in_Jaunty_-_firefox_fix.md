---
title: "Dark theme in Jaunty - firefox fix"
date: 2009-07-18
forum: Desktop Environments
---

### Post by prince.buster on 2009-07-18
Yo - took me a bit of time to fix this, so thought I'd post the experience.
Using one of the default dark themes included in Jaunty (New Wave, which is lovely btw), the Firefox menu bar appeared black on a black background - unreadable. It's to be expected that a highly portable non-gnome-specific browser isn't going to follow the themes exactly. So here's the fix to change the menu (file, edit, view etc) to the light gray it should be.

1. navigate to ~/.mozilla/firefox/*.default/chrome
2. edit userChrome-example.css
3. append this to the bottom of the file:
```
menu#file-menu {color: LightGray ! important;}
menu#edit-menu {color: LightGray ! important;}
menu#view-menu {color: LightGray ! important;}
menu#history-menu {color: LightGray ! important;}
menu#bookmarksMenu {color: LightGray ! important;}
menu#tools-menu {color: LightGray ! important;}
menu#helpMenu {color: LightGray ! important;}
```
4. save it
5. rename the file to userChrome.css
6. restart firefox
7. you will have to undo these changes manually if you switch back to a light theme

cheers!

---

### Post by dilomo on 2009-07-18
You could also install the FF theme that gives some extra candy and coolness.:

[https://addons.mozilla.org/en-US/firefox/addon/11239](https://addons.mozilla.org/en-US/firefox/addon/11239)

P.S. There is version 0.3 available when you click All versions that is for FF 3.5.

---

### Post by prince.buster on 2009-07-18
installed & looking good
a much better solution - cheers!

---

