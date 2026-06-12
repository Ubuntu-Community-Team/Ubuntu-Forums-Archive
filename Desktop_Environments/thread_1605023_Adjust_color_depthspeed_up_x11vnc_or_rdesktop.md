---
title: "Adjust color depth/speed up x11vnc or rdesktop"
date: 2010-10-24
forum: Desktop Environments
---

### Post by juliushibert63 on 2010-10-24
So I've been pulling my hair out the last couple of days trying to find a way to speed up vnc connections from remote machines to my ubuntu machine sitting at home.

As the connection from the ubuntu machine to the internet is shared by a few other people, the amout of upload bandwidth can be limited so actions can be a little slow when performed via vnc. So I'm trying to find a way to speed things up say reduce the color bit depth or even making the entire screen B&W. 

I've tried using the build in rdesktop app on Ubuntu Lucid 10.4 which works great but can't seem to adjust the color depth anywhere and the same with x11vnc. There do seem to be references online to adjusting it but it's not very clear and the only thing I've been able to do is adjust the screen WxH resolution. I've also tried tightvnc. The latter works great as you can specify colordepth via the command line but it wont let me create a vncserver for the currently logged in sessions i.e. :0. Usually this is ok, but occasionally I need to access the ubuntu desktop as though I were exactly sat in front of it. 

Maybe there's another solution to speed up vnc access other than color depth but that seems the most obvious. So is there a way of being able to control screen :0 with a vnc application using a more speedy rate such as adjusting the color depth? Currently I'm accessing the vncserver via an SSH tunnel. Could this be impacting on the speed as well?

---

