---
title: "compiz - kiba-dock only displays on one desktop"
date: 2007-05-14
forum: Desktop Effects &amp; Customization
---

### Post by Ateo on 2007-05-14
I don't know if this is normal nor have I found the fix nor is there any option is the kiba-dock options panel but kiba-dock, when it loads, only appears on one desktop. It's missing from the other 3 (of my 4).

Am I missing something?

Thanks

---

### Post by lungdart on 2007-05-14
I don't use the kiba dock, but I do use AWN, and it shows fine on all my desktops. Are you using beryl/compiz? If so try disabling it, and doing a ctrl+alt+backspace to restart your x server, log back in, and restart kiba.

If the problem still persists you can use beryl's "set window attribute" function to have kiba start on viewport -1. This will make it sticky to all view ports.

If you dont use beryl you can get wmctrl to do the same. There may be other ways of doing this, I am not sure, but those are the ways I know of.

Good luck.

---

