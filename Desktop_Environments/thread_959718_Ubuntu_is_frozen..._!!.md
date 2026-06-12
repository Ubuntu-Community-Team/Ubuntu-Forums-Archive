---
title: "Ubuntu is frozen... !!"
date: 2008-10-26
forum: Desktop Environments
---

### Post by zachbb on 2008-10-26
My Linux is stuck so I'm on windows..

I restarted Ubuntu and it dosen't work. I don't recall making any big changes to the system last time that I was logged in. What happens is that the applications bar loads at the top of the screen, but none of the icons are clickable. Same with the bar at the bottom. The desktop icons are clickable but when they open (such as when i double click on my 'Terminal' link), a window opens but freezes immediately.

I don't know that much about linux (and I'm making myself sound better than I actually am here!), but I have a feeling that it might be because I tried to install a bluetooth mouse and have it detect at start up (see [this thread]("http://ubuntuforums.org/showthread.php?t=950882")).

So I switched to the text layout using Ctrl-Alt-F2 and typed:

```
hcitool scan
[and it finds the mouse and lists it here]
```

and then I tried to connect to it but get an error:
```
sudo hidd --search
Searching
Connecting to device 00:12:5A:65:94:D6
zach@zach-laptop:^$ [90.926547] 12cap_recv_acldata: Unexpected continuation frame (len 0)
[90.977553] 12cap_recv_acldata: Unexpected continuation frame (len 0)
```


I'm just guessing but maybe this is why it dosent work..

Any ideas on how to fix this?

---

### Post by zachbb on 2008-10-27
can someone please help me with this?

---

