---
title: "down them all 1.0 + firefox"
date: 2008-03-03
forum: Desktop Effects &amp; Customization
---

### Post by brunods on 2008-03-03
Hello fellas!

You see, today I upgraded my "down them all" extension and now firefox is crashing!
I didn't report the bug yet cause I'm lazy to fill the forms they require...
But I'm just checking if anyone is getting the same weird thing.
Since the update, if I start firefox from the terminal, it will say "core dump" for the first time, the same for the second and then the third time it'll open the browser...
It's really weird.

Well, hope anyone has some heads up.
Thanks.

---

### Post by Islington on 2008-03-03
what is the output when you run it through a terminal?

---

### Post by t3hi3x on 2008-03-03
```
firefox -safe-mode
```

That will get you where you can uninstall the extension.

---

### Post by santiagoward2000 on 2008-03-03
I installed it too and had no problems with it.

---

### Post by brunods on 2008-03-04
It says:
"Segmentation Fault (core dumped)"

it will output this the first and the second time, and the third it'll open the browser, as I said.

---

### Post by brunods on 2008-03-04
Hey! It's working again!

O used safe-mode and disabled all addons, then I enabled just down them all.
When I restarted the browsert, it showed no errors, and plus, it showed a little popup with down them all info, that I had never seen.
I presume one of my other addons was conflicting with Down Them All and it could not show its license popup.
I already re-enabled all the other addons and everything works perfectly.

Thank you all!

---

