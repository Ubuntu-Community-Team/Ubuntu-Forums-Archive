---
title: "Cannot move existing HTML link"
date: 2015-09-09
forum: Desktop Environments
---

### Post by BarryD9545 on 2015-09-09
Just upgraded to 15.04, and this problem appeared.

I have placed a couple of HTML links onto my desktop by dragging them from my browser. They dropped into place without issue.

Issue occurs when attempting to move the icon to a new location on the desktop. Rather than move, the new icon is copied.

Any help is appreciated.

---

### Post by brian-mccumber on 2015-09-09
Try holding shift or control and then drag the icon. I am running Ubuntu 14.04, and I tried putting a link on the desktop and when I drag it it moves but when I hold control+drag it makes a copy of it. Maybe your version is opposite. You could also try to drag it using the middle mouse button.

---

### Post by BarryD9545 on 2015-09-09
> **brian-mccumber said:**
> Try holding shift or control and then drag the icon. I am running Ubuntu 14.04, and I tried putting a link on the desktop and when I drag it it moves but when I hold control+drag it makes a copy of it. Maybe your version is opposite. You could also try to drag it using the middle mouse button.

No luck on that one.

Thanks for the thought, though.

---

### Post by brian-mccumber on 2015-09-12
Try holding Alt and dragging it then, I tried that and when I let go of it it pops up a context menu where I can choose to move or copy.

---

### Post by BarryD9545 on 2015-09-15
No luck there either.

---

### Post by BarryD9545 on 2015-09-21
Bump

---

### Post by brian-mccumber on 2015-09-21
I found a bug report about this that affects a total of 3 users. - [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1310864](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1310864)

If you created the links prior to upgrading to 15.04, then try to delete the links and create new ones.

---

### Post by BarryD9545 on 2015-09-22
Still no luck there, either.

---

### Post by BarryD9545 on 2015-10-02
Did a fresh install of 15.04, and them an upgrade to 15.10 (Final Beta).

Still no change.

Saw a post stating upgrading to Nautilus 3.16.2 will solve the problem.  Has anyone tried this?

---

### Post by howefield on 2015-10-02
> **BarryD9545 said:**
> Saw a post stating upgrading to Nautilus 3.16.2 will solve the problem.  Has anyone tried this?

Yep, I can tell you that 3.16.2 works, but cannot say I'd recommend upgrading, the chances of breaking your system is very high.

---

### Post by BarryD9545 on 2015-10-03
That may not have been what I was hoping for.

That may not have been the best news. :|

I did manage to scare up a workaround,though.

This is BubbleUP.desktop, a link to my media server:
```
[Desktop Entry]
Name=BubbleUP
Comment=BubbleUPnP Admin
Exec=/usr/bin/x-www-browser http://192.168.1.3:58050/#main
Icon=/media/barry/Untitled Folder/Pictures/Icons/BubbleUp.png
Terminal=false
Type=Application
Categories=AudioVideo;
```

Then use chmod to make the icon executable.
From a terminal:
```
$ cd Desktop
$ chmod +x BubbleUp.desktop
```

The icon can't be changed via properties, so it's not as easy as pulling the link from the browser....
but it works as far as being able to move an HTML link around on the desktop. which is better.

It wasn't fixed in the final beta of 15.10, but there's always hoping.

---

### Post by BarryD9545 on 2015-11-17
Bump

Latest version (15.10) still has this issue.

Good news is, my workaround is still working.

Anybody seen any advance in the bug?

---

