---
title: "Trying to set up ndiswrapper. Terminal seems to freeze."
date: 2006-07-31
forum: Desktop Environments
---

### Post by Oxin on 2006-07-31
Well, the topic pretty much has it covered. I was trying to setup ndiswrapper for a usb wireless adapter and when I try to do almost anything with ndiswrapper now, it seems to freeze. When I say freeze, I mean it stops doing anything until I hit ctrl-c.(I put the asterisks between the command and the output)
sudo ndiswrapper*****************lists usage
sudo ndiswrapper -l**************freezes
sudo modprobe -r wind0502u*******"module not found"
sudo modprobe -r ndiswrapper******freezes
sudo ndiswrapper -i wind0502u*****couldn't copy wind0502u.inf at /usr/sbin/ndiswrapper line 135

I'm still sitting here trying to figure it out but maybe the gurus have a better idea.

PS. Already removed and reinstalled ndiswrapper-utils through synaptic package manager

---

### Post by Dr. Nick on 2006-07-31
have you tried ndisgtk? It is a gui for all them commands, Installable from the universe repo.

have you tried the -e command to remove the driver and start over?

---

### Post by Oxin on 2006-07-31
Tried ndisgtk thinking it would solve all my problems but it seems to freeze too. The window for it shows up with the title but nothing visible in it. Had it up for a few minutes too.

Tried -e command and retried but I get the "couldn't copy" error I listed above.

---

### Post by Dr. Nick on 2006-07-31
weird, have you uninstalled it and then purged it to get rid of the configuration files? Also if the card is usb, have you gotten any other usb items to work?

I had a field day trying to get a wireles usb adaptor working, it turned out my usb was buggy in that kernel version so no usb devices worked

---

### Post by Oxin on 2006-08-01
Well, I just did a super clean removal and reinstall and everything worked until I forced ndisgtk to quit. Now I'm back to where I was before. Maybe I should try again using the Windows 98 drivers since the xp one doesn't want to copy right. I think ndiswrapper stops working because it's still running somewhere on the system and I can't fix it without a reboot. I haven't tried any other usb devices and I really don't intend to. I'm trying to get the wireless adapter installed as sort of a server side project. It's not the end of the world if it won't work but I'll keep trying until I know what's wrong.

---

### Post by Dr. Nick on 2006-08-01
a restart may clear it up some, never seen this before.
may try

sudo killall ndiswrapper

incase it is still running

---

### Post by Oxin on 2006-08-01
Well Dr. Nick, I wish I could say that everything worked like a dream but it didn't. I'm making this post just incase someone else comes searching so that they don't wonder "I would if he ever got it working...". I did 2 reinstalls and even went as far as to compile it on my own and I always ended up in the same spot. Even when it seemed as if everything went fine, it wasn't on the networking list and I checked ifconfig also. Then I tried a few more ndiswrapper inclusive commands and I was back to where I started. At that point, I decided that the easiest solution would be to install Windows Xp, removed unnecesary extras, and install my USB wireless adapter. I wish I could say that Ubuntu could stay but for my new home server, it couldn't achieve the simplest of requirements.

That aside, I must note(as I have in all my other topics) that I will still be running Ubuntu on my main pc and am slowly making the conversion from Windows XP so I only have to boot into it when I have to. Thanks for the help anyhow, Dr. Nick.

---

### Post by Dr. Nick on 2006-08-01
well hopefully it gets better in the upcoming releases. wireless seems to be the biggest problem so far for alot of linux users. I have noticed my wireless expierence get better with time, maybe once edgy is realeased support for your card will be better.

---

