---
title: "remapping keys on non-english keyboards?"
date: 2006-03-05
forum: Desktop Environments
---

### Post by vdrab on 2006-03-05
hello all,

I have the following situation here... I am using a ibm thinkpad with a japanese keyboard. I don't mind the keys being all weird as I type dvorak anyways, but the one thing that drives me MAD is that the space key is so tiny....  it has two "henkan" keys next to it, RIGHT where you usually hit the space key.  To reach the space key you really have to stretch your thumb, and it doesn't type comfortably at all. 
I use anthy / uim for japanese input anyways , so i want to make those useless henkan keys behave as space keys... and if possible without having to gut my os to do it... (hm... fat chance, i know)

anybody have an idea how to do this?
would be greatly appreciated,
vdrab.

---

### Post by vdrab on 2006-03-06
(bump)

anyone...?

---

### Post by fonggiding on 2006-04-27
I use a Japanese 106 keyboard and I had a similar problem when I switched to dvorak three hours ago. Go dvorak:KS !!! I couldn't use | and "hankaku zenkaku". I solved it by re-mapping the useless keys by

```
xmodmap -pke > Xmodmap.dvorakjp
```

Then I found the | key which happened to be keycode 133 and I added:
backslash bar prolongedsound
in 49 (hankaku zenkaku) I added:
Zenkaku_Hankaku Kanji

Then to finish up I ran
```
xmodmap Xmodmap.dvorakjp
```

It sounds like you have a small keyboard. Mine is a jp106 so for me those keys are 129 and 133. So I suppose you could try:

keycode 129 = space
keycode 130 =
keycode 131 = space

Tell me how that works!

---

