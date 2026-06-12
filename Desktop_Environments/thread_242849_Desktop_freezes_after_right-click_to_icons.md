---
title: "Desktop freezes after right-click to icons"
date: 2006-08-24
forum: Desktop Environments
---

### Post by ZiZi on 2006-08-24
My desktop tends to freeze after right-clicking on any of the icons on it. It also disables keyboard output, only mouse is working. I heard it was Kopete's issue, particularly the "Auto-away" feature, so I turned it off. I also read in some forum that Dapper 6.06.1 should fix this issue, but it apparently didn't.

I have all the dapper-updates repos in my sources.list, KDE 3.5.3 with all updates, but it still causes these problems.

Any idea what causes it or how to fix it?

---

### Post by michux on 2006-08-24
> **ZiZi said:**
> My desktop tends to freeze after right-clicking on any of the icons on it. It also disables keyboard output, only mouse is working. I heard it was Kopete's issue, particularly the "Auto-away" feature, so I turned it off. I also read in some forum that Dapper 6.06.1 should fix this issue, but it apparently didn't.

I have all the dapper-updates repos in my sources.list, KDE 3.5.3 with all updates, but it still causes these problems.

Any idea what causes it or how to fix it?

It may be some hardware issue or network-related thing. Check what happens if you disable the network?

```
sudo /etc/init.d/networking stop
```

---

### Post by ZiZi on 2006-08-24
It can be, but I think it has something to do with Kopete, as it is the only icon in the system tray which is not responding (sometimes it even disappears), other network-related apps, such as kwifimanager, do react.

Secondly, I have to note that this behaviour is not regular and happens on a sort of random basis. Sometimes right-clicking the icon is ok, sometimes it freezes the whole desktop.

With my networking down, I wasn't able to reproduce the error. Does it mean anything?

My machine is a HP nc6120 laptop, it has been working with only minor problems so far.

Do you think it would be any good to upgrade to KDE 3.5.4, which was released in the beginning of August?

---

