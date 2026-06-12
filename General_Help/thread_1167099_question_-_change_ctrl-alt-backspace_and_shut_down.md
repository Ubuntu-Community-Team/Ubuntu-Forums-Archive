---
title: "question - change ctrl-alt-backspace and shut down option"
date: 2009-05-22
forum: General Help
---

### Post by redonwhite on 2009-05-22
Hello,

I was curious if there is a way to change back the keyboard command "Ctrl-Alt-Backspace" for restarting.  Seems to be taking out of the release.  Also is there a way to get rid of the 60 second count down for shutting down the OS.  Before when i hit shut down it would just shut down.  I prefer that.  Thanks for your time.  =)

---

### Post by charliehorse55 on 2009-05-22
To enable the Crtl - Alt - Backspace

```

sudo apt-get install dontzap

dontzap --disable

```

---

### Post by rbc on 2009-05-22
For the shutdown issue, right click on the shutdown/log out/restart icon....choose Preferences, then uncheck "Show confirm dialogs...."

---

### Post by keypox on 2009-05-22
> **charliehorse55 said:**
> To enable the Crtl - Alt - Backspace

```

sudo apt-get install dontzap

dontzap --disable

```



add 

sudo to dontzap --disable
sudo dontzap --disable

thanks alot though, i can't stand not having this feature, x crashes to much.

---

### Post by redonwhite on 2009-05-26
Thank you all for the help!

---

### Post by TekNullOG on 2009-05-26
thanks. this helped. My card isnt supported by ati in 9.04 and now x always crashes. I needed this!

---

