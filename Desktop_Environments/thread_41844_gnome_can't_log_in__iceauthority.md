---
title: "gnome can't log in / iceauthority"
date: 2005-06-15
forum: Desktop Environments
---

### Post by not_yet on 2005-06-15
greetings,

as the title says, I can't get past the login screen

I take it that its something to do with k3b

the error says -> session lasted less than 10 seconds / unable to read ICEauthority file

I've tried to follow the directions here [http://ubuntuforums.org/showthread.php?t=21319](http://ubuntuforums.org/showthread.php?t=21319)

but when I try and enter  -> sudo chown notyet:notyet.ICEauthority

(notyet being the user name)

I get an error saying not enough args for chown

suggestions??

---

### Post by Xian on 2005-06-15
That format doesn't look right. Try this:

```
$ sudo chown username:username /home/username/.ICEauthority
```

---

### Post by not_yet on 2005-06-15
thanks / that fixed it :)

---

