---
title: "Is there a fwbackups debian package?"
date: 2009-04-20
forum: General Help
---

### Post by klepto on 2009-04-20
Hey, 

I heard that fwbackups has a very nice rsync gui. I've been using Image 4 Linux/Sbackup for the longest time. I'd rather use rsync than sbackup. 

Thanks for the help in advance

---

### Post by codeseer on 2009-04-20
fwbackups is ok, but it's really just more beneficial to set yourself up a bash script and cron job it.

You can install from the rpm if you get the rpm package from Synaptic.

---

### Post by klepto on 2009-04-20
I've been testing out "Back in time" and it is a rsync/diff gui which is similar to MacOS's Time Machine. It isn't has great as that but pretty good for a rsync shell. I'll test it out. Any other good rsync gui(s)?

---

### Post by codeseer on 2009-04-20
> **klepto said:**
> I've been testing out "Back in time" and it is a rsync/diff gui which is similar to MacOS's Time Machine. It isn't has great as that but pretty good for a rsync shell. I'll test it out. Any other good rsync gui(s)?

The ones you mentioned are the main ones. I don't think you mentioned 'fly back'. I'm pretty sure all of them except the fwbackups aren't maintained anymore; fwbackups looked the most promising to me anyway. One of them was a summer of code thing from Google.

I've tried out just about every one of them and just got frustrated with it and made a bash shell script and cron jobed it; it's easier than you would think.

---

