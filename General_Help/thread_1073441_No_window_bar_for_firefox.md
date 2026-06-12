---
title: "No window bar for firefox"
date: 2009-02-18
forum: General Help
---

### Post by Afkpuz on 2009-02-18
So, I went to some website where I was spammed with pop up windows.  It opened up a firefox window that had no top window bar and which covered up my taskbar at the bottom.  Now, every firefox windows has no window bar and covers my taskbar.  I cannot minimize it, move the window, and my firefox window keeps blinking every now and then.  Can anyone help me get firefox back to normal?  I thought I was immune to these kinds of shenanigans in linux.

---

### Post by tombott on 2009-02-18
With Firefox open Press F11, this will put Firefox into Fullscreen mode.
Now press F11 again, and you should get your normal view back.

---

### Post by drs305 on 2009-02-18
I am not sure, but it sounds similar to problems some have had recently. If it's the same problem, hit F11, F11, then unmaximize FF. Close it, then open FF and maximize it to get back to normal window borders.

---

### Post by Afkpuz on 2009-02-18
Yay, thank you both!

---

### Post by olskar on 2009-03-08
Is a bugreport avaible? Using F11 for all eternity is not a solution, it have to be fixed.

---

### Post by Afkpuz on 2009-03-08
Well, I've since reinstalled ubuntu for other reasons and this alleviated the problem.  Plus, isn't this an exploit, not a bug?

---

### Post by Crafty Kisses on 2009-03-08
I've had the same issue but I've solved it. What you need to do is for a temporary fix is press "F11" twice, or for the permanent fix, do the following, go into the Compiz Settings Manager and find "Windows Decorations" add the following line to "Decoration Windows"

```
(any) | class=Firefox
```

Once you've done that close out CCSM, then open CCSM back up again, then change that to:

```
any
```

Then that should solve the problem, it worked flawlessly. If that doesn't work you can always revert back to metacity:
```

metacity --replace
```

I've also found another fix, what you want do to is press F11 twice. Then once you've done that minimize it and resize the window then make it smaller, then close Firefox then reboot it, and it will be back to normal. The issue really only occurs when Firefox crashes and you reboot it, but those are the fixes and I've tested them myself and they do actually work.

---

### Post by yuki86 on 2009-04-02
thanks f11 work for me too

---

