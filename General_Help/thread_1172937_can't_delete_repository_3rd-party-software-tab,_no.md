---
title: "can't delete repository 3rd-party-software-tab, not in sources.list"
date: 2009-05-29
forum: General Help
---

### Post by hachel on 2009-05-29
hello,
I have some repositories that I don't need any more but I can't get to delete them. When I highlight them in the "third party software"-tab and click delete the delete button goes gray but the line doesn't disappear. I can click it again and click delete as often as I want.
I tried to delete it manually by removing it from /etc/apt/sources.list but it's not in there.

Any help?

thanks

---

### Post by Yellow Pasque on 2009-05-29
Perhaps the sources are in another file in /etc/apt/sources.list.d

---

### Post by hachel on 2009-05-29
ah, thanks, I thought that was a file also and tried to gedit it.
thanks, they were all in there.

---

