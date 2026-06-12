---
title: "ls stopped working"
date: 2009-03-07
forum: General Help
---

### Post by charlvj on 2009-03-07
As background info: I have my music on my desktop shared as an nfs share (desktop runs Ubuntu Hardy). I then connect with my laptop (running Intrepid) to my nfs share on the desktop to get the music, which I then play with Rythmbox. it seems to work fine. I have not yet changed my nfs to use tcp and so I have to disable my desktop's firewall so I can connect to the share. I usually restart the firewall as soon as nfs connected. I wasn't sure if that would work, but everything seems to run normally afterwards.

My problem: After a long time (like now it was after a whole CD was played), Rythmbox freezes. So I open a console to kill it, but then killall freezes. I create a new console tab and plan to see if my nfs mount is still working, but ls freezes - but I am not yet in the nfs mount directory. Thinking it might be the nfs mount, I remove my wireless card to force the connection to break, but still ls does not work on any directory. Now I have my card plugged in again and everything seems to be back to normal, except I can't use some of the commands in a console. I thought perhaps it was a hard disk issue, but other things works fine that uses my disk.

Has anybody heard of ls not working?! When I say it doesn't work, I mean I type ls, enter, then nothing happens. Not even Ctrl-C breaks it.

At least some idea of where to start looking would be nice.

Thanks,
Charl

---

### Post by cmnorton on 2009-03-07
I can't imagine the load on the network running music over nfs. I'd stop right there.

As to debugging it, have an x-term (command line open), and enter ps -ef to see what's running that you can kill.

---

