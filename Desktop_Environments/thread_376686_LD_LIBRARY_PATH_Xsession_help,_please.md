---
title: "LD_LIBRARY_PATH Xsession help, please"
date: 2007-03-05
forum: Desktop Environments
---

### Post by drfox on 2007-03-05
Please help me get rid of an error message I'm getting after logging into gnome desktop:

X session:unable to launch "LD_LIBRARY_PATH=:/home/myloginname/Julius/bin" X session--- "LD_LIBRARY_PATH=:/home/myloginname/Julius/bin" not found; falling back to default session

Julius was a program I downloaded to view DICOM Xray images; I didn't get it to work right, so I deleted it from my system, but this is what's left.

What do I need to edit to get it out of the LD_LIBRARY_PATH?

Thanks, Larry

---

### Post by linuxpimp on 2007-03-08
> **drfox said:**
> Please help me get rid of an error message I'm getting after logging into gnome desktop:

X session:unable to launch "LD_LIBRARY_PATH=:/home/myloginname/Julius/bin" X session--- "LD_LIBRARY_PATH=:/home/myloginname/Julius/bin" not found; falling back to default session

Julius was a program I downloaded to view DICOM Xray images; I didn't get it to work right, so I deleted it from my system, but this is what's left.

What do I need to edit to get it out of the LD_LIBRARY_PATH?

Thanks, Larry

I'm in the same boat......

Any advice would be great!!

lp

---

### Post by linuxpimp on 2007-03-08
OK so i exported the ld_library_path to /usr/lib

still no go!!

PLEASE HELP!! :-)

The window manager starts up, lets me work for about 10 minutes then crashes!!

After using Linux for 7 years, i am seriousely considering just tanking it and going to a similar FREEBSD based distro....

lp

---

### Post by linuxpimp on 2007-03-08
Ok, i installed Julius,a free medical program and this is the cause.
I removed ~/.profile and all is ok.

lp

---

### Post by drfox on 2007-03-10
> **linuxpimp said:**
> Ok, i installed Julius,a free medical program and this is the cause.
I removed ~/.profile and all is ok.

lp

You're both very kind for having taken the trouble to install Julius and a genius for finding a solution. Thank you very much.

Larry

---

