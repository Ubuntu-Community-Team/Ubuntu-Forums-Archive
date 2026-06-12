---
title: "Streaming Video from a networked PC???"
date: 2006-07-26
forum: Desktop Environments
---

### Post by Galactus on 2006-07-26
I installed Ubuntu 6.06 LTS on my HP ze4805us laptop last night. Everything went fairly well, with the exception of setting up my wireless (it took me over an hour to get it working using the command line and NDISWRAPPER). Altogether, everything was set up and working in about 4 hours (included in that time was the install of a new hard drive). 

Anyway, one of the main things I use the laptop for is to view IPTV shows over my home network that I have downloaded onto my desktop. I was able to get to the files on my windows box no problem :D , however I can't get them to stream properly in Ubuntu. 
- VLC won't stream anything over the network.
- Mplayer will stream everything except .mov files, however the play is jerky (it keeps stopping to rebuffer).
- Totem also will stream everything except .mov files, and it too is jerky (same buffer problem).
- I tried just about every player that I could find in the repositiories and nothing worked.

I believe I had kaffeine playing video over my network on another machine (which I've since uninstalled) but that was in a KDE environment and I am now using Gnome on the laptop.

Is there any player that is able to stream video over a home network without the stopping and starting. The convenience of being able to watch my video streamed over the netowrk all over my house (inside and out) is major for me. Without that capability I might have to go back to using Window (DAMN!!!NOOOOOOOOOOOOO - I don't want that!!!!Window = :evil: )

Thanks

---

### Post by simonn on 2006-07-26
install the extra codecs and increase mplayer's cache size (look in man mplayer).

---

### Post by b1g4L on 2006-07-26
Does Linux have any type of networking standard like Windows's Qos Packet scheduler? If so, that might be something to check into.

---

### Post by Galactus on 2006-07-27
Hey Simonn, I installed the extra codecs through Easy Ubuntu. Aside from the fact that VLC won't play any streams from my other PC, the buffer problem seems to only happen when I am using wireless.

Thanks

---

