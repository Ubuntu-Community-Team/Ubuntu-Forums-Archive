---
title: "Identifying and using non-standard keys"
date: 2009-01-10
forum: General Help
---

### Post by darkfox on 2009-01-10
Key bindings for special keys?

I've reverted to Openbox after a while away, having inherited a slow old laptop.
I use it with a plug-in keyboard and stand:  "Logitech Alto keyboard"
This thing has special keys to control volume and so on.

How can I find out the key value for these special keys?
Once I know this, how do I use them in my Openbox config?

---

### Post by azr on 2009-01-10
To find keycode run
```
xev
```
position your cursor on the window that pops up (ignore output on terminal about mouse movements). Then press the key and note the output in the terminal. 

To set the keycode to another value

```
xmodmap -e "keycode xx = some-key-value-here"
```

where xx is the keycode of the key and an example of some-key-value is Alt_L. (The man page of xmodmap contains some useful examples.)

To see your current keyboard mapping (which will show keycodes and corresp values assigned to keys) type

```
xmodmap -pke 
```


To make these changes permanent you will then have to edit the keyboard map file.

---

