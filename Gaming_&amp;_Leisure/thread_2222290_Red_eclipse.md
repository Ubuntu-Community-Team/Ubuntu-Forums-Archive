---
title: "Red eclipse"
date: 2014-05-05
forum: Gaming &amp; Leisure
---

### Post by LastDino on 2014-05-05
Well, I downloaded tarball archive from source-forge and went ahead with the process on Red eclipse Wiki.

I got the following error.

> X@X:~/Downloads/redeclipse-1.4$ ./redeclipse.sh
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  153 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x7c
  Serial number of failed request:  132
  Current serial number in output stream:  134


Any ideas? I'm thinking it has something to do with screen resolution settings but I dunno how to tinker with that without starting the game.
I've on board graphics. I've no idea how much it is but I'm guessing around 256Mb?

free command output
> x@x:~$ free
             total       used       free     shared    buffers     cached
Mem:       4097992    1456664    2641328      77128      92368     745500
-/+ buffers/cache:     618796    3479196
Swap:      3997692          0    3997692


If that helps?

---

### Post by qreeves on 2014-05-06
You need to ensure you have a VideoMode entry for the desired mode you wish to set at 60Hz (this is because SDL defaults to that frequency).

You can override the automatic detection on the command line with "-dw" and "-dh". Eg (for 640x480): *./redeclipse.sh -dw640 -dh480*

---

### Post by LastDino on 2014-05-06
> **qreeves said:**
> You need to ensure you have a VideoMode entry for the desired mode you wish to set at 60Hz (this is because SDL defaults to that frequency).

You can override the automatic detection on the command line with "-dw" and "-dh". Eg (for 640x480): *./redeclipse.sh -dw640 -dh480*

It's as easy as that? <_<

It worked perfectly, thanks!

Btw, if it is that easy, I might not trouble you people by making new thread, but I installed ''AssaultCube'' from USC and it is not opening from whisker menu. I dunno how to open it from command line or what is going wrong but it just flickers like Red eclips, probably same issue. How to deal with that?

---

### Post by qreeves on 2014-05-06
I wouldn't know myself sorry, as I don't use Linux. I'm just the Lead Developer for Red Eclipse. You might be able to find more information here: [http://assault.cubers.net/docs/commandline.html]("http://assault.cubers.net/docs/commandline.html")

---

### Post by LastDino on 2014-05-06
> **qreeves said:**
> I wouldn't know myself sorry, as I don't use Linux. I'm just the Lead Developer for Red Eclipse. You might be able to find more information here: [http://assault.cubers.net/docs/commandline.html](http://assault.cubers.net/docs/commandline.html)

:o 
You lurk on ubuntu forums so you could help people like me even though you don't use it? That is some dedication. Nice game too! :popcorn: 

Thank you again, I'll have a look at that link.

---

