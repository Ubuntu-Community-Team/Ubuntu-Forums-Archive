---
title: "Trying to run Vendetta Online x64 version, but I get a cute error."
date: 2008-12-16
forum: Gaming &amp; Leisure
---

### Post by Lupusceleri on 2008-12-16
Heyas,

Tried installing Vendetta Online to my Ubuntu Intrepid using the amd64 installer for linux, and followed the guide here: [http://gaming.gwos.org/doku.php/guides:64bit:vendetta_online](http://gaming.gwos.org/doku.php/guides:64bit:vendetta_online)

Buuut, as the topic mentions, I've got an error whenever I attempt to start it, and I made a screenshot of the error.

Yeah I did check permissions, everyone and their dog are allowed to read and write and create and run files from the folder. I also tried running the other things that looked like executables from the folder. I also removed wine as a preferred app to open .rlb and no-extension things with. :)

Any idea what I'm doing wrong?

Thanks,

/Lup.

---

### Post by Achetar on 2008-12-16
Try running the following in a terminal:
```

$ cd .vendeta
$ sudo chmod a+x update.rlb

```

That will make it executable, if it isn't already.

---

### Post by Lupusceleri on 2008-12-18
> **Achetar said:**
> Try running the following in a terminal:
```

$ cd .vendeta
$ sudo chmod a+x update.rlb

```

That will make it executable, if it isn't already.

Thanks, worked without a flaw. :)

---

### Post by chaoswirl on 2009-04-04
I installed it into the right directory.

However I use the ./vendetta command in the terminal to run it and I get a "permission denied" error. There is no Applications menu icon in games and I can't start it from the terminal using the above command. Any ideas?

---

### Post by Vadi on 2009-04-05
Try doing *sudo a+x vendetta* too.

I found their installer to be rather poor-made. It even has a bug that if you don't have a "bin" folder in your home folder (which I don't want to litter with), it'll loop repeatedly or crash.

---

### Post by Perfect Storm on 2009-04-05
The funny thing is that bug have been there for now almost 2 years :popcorn:

---

### Post by Vadi on 2009-04-05
Yeah. One of the reasons why I'm not all hyped about their linux support. (**expects a vendetta fan to refute the point**)

---

