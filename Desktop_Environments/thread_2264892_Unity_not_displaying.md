---
title: "Unity not displaying"
date: 2015-02-10
forum: Desktop Environments
---

### Post by martinojones-2009 on 2015-02-10
Now I don't remeber what I did for this to happen, it was a while ago, and instead of fixing the issue I just installed cinnamon and called it a day because I had homework to do (I'm a college student). I'm perfectly fine with using Cinnamon, I also don't hate Unity, I'm really open to new things; however, I would like to know why this isn't working-- a nice learning experience for me. Now I'm not a pro Linux user, but I'm also not new. So when I try to login to Ubuntu using Unity I'm presented with my desktop... that's it, no Unity dash or any panels. I also cannot ctrl+alt+t for my terminal. I get nothing pressing the super key (aka windows key). I can launch programs I have on my desktop, but that's it. So I switch to tty1 and do a kill all pids under my profile doing "**ps aux | grep (username) | cut -d' ' -f4 | xargs kill**" and then that drops me back to the login screen. So I thought maybe I messed up some configs somewhere, so I "**apt-get remove unity ubuntu-desktop compiz && apt-get autoremove**" and that removed the unity and Ubuntu desktop. I then did "**find / -name unity -type d | xargs rm -rf**" and "**find / -name compiz -type d | xargs rm -rf**"(I know that's dangerous, but I live on the wild side lol). That still didn't work... so I thought maybe there was some other settings under my account, so reinstalled ubuntu-desktop (unity and compiz) and instead I made another user, but that still had the same issue. I'm not sure what's going on, I mean I don't think I'm a complete n00b, but I'm not pro like that.

I of course did some searching around, and have tried a bunch of the suggestions for the past two days, but no luck so far... so please hit me with that one line command and have everything up and running :-)

System:
Ubuntu 14.10 64-bit
Intel i5
Linux kernel: 3.16.0-30
Nvidia driver 346.35 (proprietary because I play games)

---

### Post by martinojones-2009 on 2015-02-11
I didn't think to connect the nvidia driver to the fact Unity wasn't loading, but I have been seeing some other posts recently talking about the same thing, I guess I ddidn't look that hard lol. I didn't see a fix though, does someone know why this isn't working? Even after uninstalling and moving back to an old driver it still odesn't work.

---

