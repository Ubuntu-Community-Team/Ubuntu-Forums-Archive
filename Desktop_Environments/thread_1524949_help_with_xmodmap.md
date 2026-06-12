---
title: "help with xmodmap"
date: 2010-07-06
forum: Desktop Environments
---

### Post by reakin on 2010-07-06
Hi,

I am trying to use xmodmap to get my keyboard mapped correctly to the symbols on it.  It is a Hungarian Lenovo n200 laptop.

First, I don't know how the access the plus sign.  It is on the bottom right corner key, along with -, _, and *.  Here is what xmodmap tells me about it:

```

keycode  61 = minus underscore slash question asterisk dead_abovedot dead_hook dead_hook

```

I get the asterisk by hitting the win sign, which I have mapped as a 3rd level chooser in the keyboard preferences (options).  I can't get the slash or question mark with this key and I am not sure why they are even displayed as mapped to this key.

Next, I have brightness symbols on F10 and F11, where they should be accessed with the Fn key.  Here is what xmodmap says about these keys:

```

keycode  76 = F10 XF86_Switch_VT_10 F10 XF86_Switch_VT_10
keycode  95 = F11 XF86_Switch_VT_11 F11 XF86_Switch_VT_11

```

When I try to view the output of Fn plus F10 or F11 in xev, there is no output.  I tried replacing the second member of the xmodmap keycode 76 with XF86KbdBrightnessDown, but this doesn't help.

If anyone can give some pointers, thanks. This is the first time I have tried using xmodmap and this has been slowing me down ever since I got this hungarian laptop.

cheers,
Rich

---

