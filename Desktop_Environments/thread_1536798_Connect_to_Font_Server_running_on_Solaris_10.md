---
title: "Connect to Font Server running on Solaris 10"
date: 2010-07-22
forum: Desktop Environments
---

### Post by sinha1612 on 2010-07-22
Hi everyone! :)

I have an application running on a Solaris 10 server and I am getting the display on my Ubuntu notebook (10.04 lucid with kernel 2.6.32-23-generic and GNOME 2.30.2). But the problem is the fonts don't display well. So I tried to connect to the font server running on the Solaris server. 

I tried all these variants:
 
xset fp+ tcp/<hostname>:7100
xset fp+ tcp/<hostip>:7100
xset fp+ tcp/<hostname>:/7100
xset fp+ tcp/<hostip>:/7100

But I keep getting this error:
xset:  bad font path element (#23), possible causes are:
    Directory does not exist or has wrong permissions
    Directory missing fonts.dir
    Incorrect font server address or syntax

I verified that the font server is running on the Solaris server this way:
netstat -an | grep 7100

      *.7100               *.*                0      0 49152      0 LISTEN
      *.7100               *.*                0      0 49152      0 LISTEN
      *.7100                            *.*                             0      0 49152      0 LISTEN      
60003e06018 stream-ord 30015330dc0 00000000 /tmp/.font-unix/fs7100                

I have Googled for the last few hours on this without finding an answer. So this is my last resort! Any help will be really appreciated... 

Thanks in advance! :)

[Alternatively, is there some way to install the Solaris fonts on Ubuntu?]

---

### Post by sinha1612 on 2010-07-28
bump :)

---

