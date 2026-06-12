---
title: "trouble installing codecs"
date: 2005-04-17
forum: Desktop Environments
---

### Post by BiGx5MurF on 2005-04-17
I followed this article [http://www.ubuntulinux.org/wiki/AddingCodecsToTotemHowTo/view?searchterm=install%20codecs](http://www.ubuntulinux.org/wiki/AddingCodecsToTotemHowTo/view?searchterm=install%20codecs)

and everything seemed like it went through as its supposed to.  But I still can't play avi, mpg, or asf files.

Is there something I'm doing wrong?

---

### Post by TravisNewman on 2005-04-18
you are using totem-xine and not totem-gstreamer right? 
apt-get install totem-xine
if you haven't already.

You might also try the standalone xine and see if that helps.

---

### Post by Bob D. on 2005-04-18
As panickedthumb says, totem-xine or stand-alone xine is the way to go. You can check if totem-xine is seeing the codecs by Edit>Preferences from the dropdown menu, then clicking on the 'Add Proprietary Plug ins' button on the General tab.

Bob

---

### Post by BiGx5MurF on 2005-04-19
Thanks for the help guys, but I ended up using this instead to get things working

wget [http://download.ubuntuforums.org/ubuntusetup/ubuntusetup.sh](http://download.ubuntuforums.org/ubuntusetup/ubuntusetup.sh)
sudo sh ubuntusetup.sh

---

