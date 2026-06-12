---
title: "remote desktop from windows into linux? Is it possible?"
date: 2004-11-29
forum: Desktop Environments
---

### Post by Borgmeister on 2004-11-29
Hi, sorry, but another possibly rtfm question, but i have searched google in vain for 2 hours, is it possible to remote desktop into ubuntu from windows? I have successfully remote desktopped into windows from linux using grdesktop, using my domain, but i dont know how to set up a dynamic dns client? for linux, and then, would i be able to use windows remote desktop, or is this a futile excercise?

Thanks once again for you patience

---

### Post by Magneto on 2004-11-29
[QUOTE=Borgmeister]Hi, sorry, but another possibly rtfm question, but i have searched google in vain for 2 hours, is it possible to remote desktop into ubuntu from windows? I have successfully remote desktopped into windows from linux using grdesktop, using my domain, but i dont know how to set up a dynamic dns client? for linux, and then, would i be able to use windows remote desktop, or is this a futile excercise?

Thanks once again for you patience[/QUOTE]
 vnc
exceed
there are many options for a remote X session

---

### Post by randy on 2004-11-30
Turn on vino, it's a vnc server that is listed under Desktop Preferences-> Remote Desktop

---

### Post by jdong on 2004-11-30
google for **xinetd vnc**. Enjoy the results.


Or, for a better setup, consult a FreeNX howto. Most likely you'll have to (1) use Hoary, or (2) compile your own FreeNX, because apparently the Kanotix repository that I based my HOWTO archive off has gone too deep into Debian Sid...

---

### Post by Borgmeister on 2004-12-01
Cheers guys, a couple of other things, not really related, but please help if you can, 

When i boot into ubuntu, on my laptop, it spends a long time 'confguring network', since this is a laptop, this slow process is very irritating, is there any way to speed it up?

Also, is it possible to display films played in totem, on a tv? I tried S-video and i dont think it worked

Once again, i am grateful for your patience

---

### Post by jdodson on 2004-12-01
svideo will work(if you have a svideo out port) and if the driver is setup to handle it in ubuntu.  what kind of video card is it?

---

### Post by Borgmeister on 2004-12-01
Intel Extremly Lame 852GME...

Cheers

---

