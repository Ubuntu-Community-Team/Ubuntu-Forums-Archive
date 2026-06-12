---
title: "Applications lag when launched"
date: 2008-02-26
forum: Desktop Environments
---

### Post by Gibran on 2008-02-26
Hello everyone,
I am using ubuntu Gutsy and for a while now the applications take several minutes (around 3 minutes) to launch after clicked. There is no high memory or CPU usage, and they work fine once loaded, but this is obviously a big issue for me since not even the file browser is spared. 

I know I am not being too descriptive but there are no other changes I have noticed. Does anyone know what I should do to fix this? Thanks in advance!

---

### Post by Sam Lars on 2008-02-26
Do they take as long from the command line, and is there anything out of the ordinary there?

---

### Post by Gibran on 2008-03-02
Sorry for the delayed response... Yes, they take as long when launched from the command line, and I saw nothing out of the ordinary on it, either.

---

### Post by Acedge on 2008-03-02
What applications are you trying to run, if any in particular?

---

### Post by Gibran on 2008-03-04
Thanks,

Well, the lag also affects the task bar upon startup, where I will only see the empty bar for the better part of a minute or so. About the apps, Amarok, Kopete, Firefox, Nautilus and most programs show an overall delay in response.

Strangely enough, I have noticed the VLC player opens at its normal rate...

---

### Post by Sam Lars on 2008-03-04
Well it sounds like the system is doing something that's causing a delay, that's somehow not using memory or CPU...
Try looking in /var/log/syslog to see if there's some sort of timeout or other out-of-the-ordinary message...

---

