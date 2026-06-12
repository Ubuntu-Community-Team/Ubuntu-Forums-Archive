---
title: "Ran updates, Ubuntu 8.04 doesn't boot"
date: 2009-01-28
forum: General Help
---

### Post by Chrisso on 2009-01-28
Hey,

I just installed about a dozen updates this morning through the update manager. The updates ran fine, but next time I turned my computer on, Ubuntu wouldn't load. It gets to the screen with the light brown background and the little circle cursor thing, except it doesn't go anywhere from there. Also, when I close the lid, it doesn't hibernate like it's supposed to. If I hit the power button, but let it go before it shuts down, the screen goes black and it shows me a bunch of text about shutting down, then shuts down properly.

The other kernel options in grub are still there, but don't work either. I can get into recovery mode without problems, but when I tell that to boot normally, the same thing happens. I've already run the dpkg and xfix in the recovery menu (even though I don't know what the second one does...) but that hasn't helped.

It's an HP Pavilion dv9000, if that helps. Also, the updates are fairly recent, since the last time I did updates was only on Monday.

Thanks!

Update: I discovered the Ctrl+Alt+Backspace command, which still works when my computer gets stuck loading the Ubuntu desktop. The first few times I tried it, it switched to a black screen with some text on it about stuff I can't understand, and when I do it a second time, it shuts down the computer. This time, it asked me for my login and password (while switching back and forth from the black screen with text to the brown desktop loading screen). After "logging in" I get this error message on a blue screen:

"The display server has been shut down about 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting for 2 minutes before trying again on display :0."

<sarcasm> This "something bad is going on" business is news to me </sarcasm>

Thanks again

---

