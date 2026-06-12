---
title: "Can you boot without any sort of display adapter?"
date: 2009-11-25
forum: Desktop Environments
---

### Post by spencewah on 2009-11-25
My video card recently died in my Little Ubuntu Home Server That Could and the mobo doesn't have any sort of on-board graphics adapter.  I had it running essentially headless anyway, so this wouldn't change my day-to-day use, but can I still boot up without any sort of graphics hardware present?

Thanks,
-S

---

### Post by Digital Magi on 2009-11-25
In general, yes. It's called a headless server.

Whether your machine can or not I think that depends on your system BIOS. Many will halt and reports errors(beep) if no video adapter is present. Some BIOS do have settings to disable or bypass this to allow boot without video.

You might have to borrow a video card to check and setup your BIOS settings anyway before you can make this work.

Not an expert on this, hopefully someone else will chime in.

---

### Post by spencewah on 2009-11-25
I just gave it a shot and it works perfectly, no beeps or boops!  Thanks.

---

