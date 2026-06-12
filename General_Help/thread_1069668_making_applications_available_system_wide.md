---
title: "making applications available system wide"
date: 2009-02-14
forum: General Help
---

### Post by paulgault on 2009-02-14
when i was using 7.10 i could call the makedvd application in a terminal just by typing the relevant command. e.g.

```
makedvd "MyDisc.xml"
```

but now i'm using 8.10 and the above command wont work. i have to put the full path to where mekedvd is in the filesystem for it to work. e.g.

```
/usr/share/tovid/makedvd "MyDisc.xml"
```

it's just a little problem but it's getting a bit annoying! lol

does anyone know how i can make it work like it used to?

i have searched for a solution but i've not had any luck.

thanks,
Paul.

---

### Post by hyper_ch on 2009-02-14
/usr/share/tovid is not in your paths so you can't just call it.

You could create a symlink in /usr/bin that points to the actual makedvd binary.

---

### Post by paulgault on 2009-02-14
I put a symbolic link there as suggested using

```
ln -s /usr/share/tovid/makedvd /usr/bin/makedvd
```

(i needed some help from [here]("http://ubuntuforums.org/showthread.php?t=255573")) and it now works fine.

Thanks hyper_ch!

---

