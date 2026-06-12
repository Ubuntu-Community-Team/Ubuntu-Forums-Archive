---
title: "return to running application from script command"
date: 2009-08-12
forum: Desktop Environments
---

### Post by eleach on 2009-08-12
I want to be able to return to a running application with a command after I have gone to a different application.

I'm editing html files in vim. I have a vim command that loads the page being edited in Firefox. Looks like:

map tr :w<Enter> :execute "!/usr/bin/firefox  -new-tab [http://weather.yahoo.com](http://weather.yahoo.com) & "


However, after it loads in Firefox, I want to be returned to vim automatically - as if I hit Alt-Tab. This way, I can keep editing and testing without my hands even leaving the keyboard. Would be very helpful.

Thanks.

---

