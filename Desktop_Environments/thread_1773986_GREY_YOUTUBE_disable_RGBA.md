---
title: "GREY YOUTUBE/ disable RGBA"
date: 2011-06-02
forum: Desktop Environments
---

### Post by HE_Serenade on 2011-06-02
Hello Ubuntu Community!

I've been messing around with the themes an eye looking stuff and somehow I enabled RGBA on my Ubuntu 10.04 (lucid) and actually I think I messed something there cuz it didn't work at all! Then I noticed that Youtube viedos just game me a grey square instead of the flash player!

I Googlesearched and found [THIS]("http://askubuntu.com/questions/11465/firefox-youtube-flash-player-shows-as-grey-box")

They say it could be the RGBA, and since I've just activated it, thats the main suspect!

I've used the command posted there ```
export XLIB_SKIP_ARGB_VISUALS=1 && firefox
```and everything works great! but I want a permanent solution. 

My OS is 32 bits, using Nvidia GPU and have flash player 100% updated, so it's nothing but RGBA left

How can I remove or disable RGBA??????????

Thanx for reading, and I hope you can help me in this little but annoying matter

---

### Post by hhh on 2011-06-02
It would have been helpful if you had mentioned how you enabled RGBA, but I'll assume you did it with gtk2-module-rgba. If so, see this post, scroll down to Revert all changes...
[http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html](http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html)

---

### Post by HE_Serenade on 2011-06-03
It totally worked!!!!!!!!!!!!!!!!!! 

Thanks a lot M8! :) you're my savior!

---

