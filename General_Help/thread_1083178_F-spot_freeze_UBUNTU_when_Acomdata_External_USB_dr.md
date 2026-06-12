---
title: "F-spot freeze UBUNTU when Acomdata External USB drive is plugged"
date: 2009-02-28
forum: General Help
---

### Post by jocampo on 2009-02-28
Hi

New to the Linux world. Everything seems to be working smoothly but having problems using my external USB drive. Everytime that I plugged my drive, F-spot starts automatically (I believe is scanning the drive) but puts UBUNTU on his knees, can't do anything...only way is killing the F-spot process.

Is anyway to disable that behaviour or is a driver issue? FYI, once killed, I can see and browse data on my external drive.

Thanks in advance,

---

### Post by jocampo on 2009-03-01
please, any input on this? is really annoying...

thanks

---

### Post by jocampo on 2009-03-01
FYI

I fixed it. The problem was Nautilus. I changed Nautilus default behavior of open files with F-spot.

I went to Preferences>Media>Photos>Do nothing

I also unchecked: Browse Media when Inserted

I guess that because the External HD is so big, the scanning process was using all the CPU resources putting UBUNTU on its knees.

Hope this help someone else,

---

