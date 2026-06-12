---
title: "clipboard in command line"
date: 2009-02-22
forum: General Help
---

### Post by geo909 on 2009-02-22
Hello,

I was wondering if there is a way to direct something from/to the clipboard from command line.

For example, do something like:
```

cat mylongfile.txt > <clipboard>

```

Any ideas? 

Thanks in advance

---

### Post by fragos on 2009-02-22
I don't know of one but copy and paste do work in the terminal. Select as you normaly would and <shift><Ctrl>C or <shift><Ctrl>V.

---

### Post by kellemes on 2009-02-22
Install xclip..
```
sudo apt-get install xclip
```

```
xclip < mylongfile.txt
```
or
```
cat mylongfile.txt | xclip
```

Edit: [Some more info on xclip]("http://www.debian-administration.org/articles/565")

---

### Post by fragos on 2009-02-22
Thanks -- xclip will be handy to have around.

---

### Post by geo909 on 2009-02-22
Thanks, xclip is what I was looking for!

---

