---
title: "Synergy  lost connection WARNING: error writing to client &quot;X&quot;"
date: 2009-04-10
forum: General Help
---

### Post by MC_LA on 2009-04-10
I've been using synergy for a while and never had any problems. I recently started having periodic lost connects only on my Ubuntu machine after upgrading to 7.10 and then again on Intrepid 8.10.

I have 3 machines at home: OSX, Ubuntu, and Windows. OSX is my server. Both the Ubuntu and Windows machines connect fine and they both work well. But periodically the Ubuntu machine will lose connection for about 30 seconds and then will automatically reconnect without any issues. The Windows machine never loses connection. This problem happens even if the Windows machine is turned off (which it usually is). 

On the OSX (the synergy server), I see this message when the connection is lost: WARNING: error writing to client "X" , where X is the name of my Ubuntu machine.

This is very annoying, so any suggestions would be greatly appreciated.

---

### Post by MC_LA on 2009-04-18
So I think I figured out the problem. I had a wireless router connected to the same switch as synergy machines. The wireless router works fine and I had no networking problems, but when I turned off this router, my synergy problems went away. It's very strange. Any ideas why ?

---

