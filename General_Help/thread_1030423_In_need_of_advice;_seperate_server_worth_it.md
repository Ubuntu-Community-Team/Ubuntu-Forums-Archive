---
title: "In need of advice; seperate server worth it?"
date: 2009-01-04
forum: General Help
---

### Post by Kain000 on 2009-01-04
Hello everyone

It's good to finally be back home in colorado, My wife and I just returned from Mexico after a grueling 13 hours of delayed flights and layovers. UGH.

anyhow

So My current set up is as follows.


I have one duel core box that I do all my work on and maintain my ipod threw ect. because it's pretty fast and has a very nice display/video card.

On another Pentium 4 box I have a 400 GB disk with all my media.     This box acts as my host to the Xbox 360 in the living room and as a file server for myself and my Dad over in Virginia via SFTP.  

The only other thing I use this box for is I have it configured for Torenting so I can just give it a seed file and let it go to work.   I was running boinc on it for Rosetta at home but it's speed compaired to the output of my duel core box wasn't worth the wattage to be left on.


My question is whether or not you guys thing that it's worth it to have an entirely separate box to handle all this.
My feeling is that as far as security torrenting can be traced back to my router's ip, so there is no benefit to having a separate box, and Internet data transfers such as torrents and sftp shouldn't bog down things to badly.

Right?  I'm not so concerned with the lag on my better box because I don't use it for gaming and thus wouldn't notice the slow down.

other performance wouldn't suffer because of a few server daemons running in the back ground would it?

and last and probably biggest concern was security.   I know that Unix and Linux are all but steel cages and call me worried by windows but the idea of server daemons running on my main rig worries me that if someone could break in and steal my data.  I of course use both my ip tables firewall and the routers firewall and have no windows box's on my network but it's just the little voice you know?


well thank you all for your time to read this now lengthy post.

-sean

---

### Post by underdog512 on 2009-01-04
I would suggest leaving your torrent client on your desktop and then setup an Ubuntu Server box with SFTP installed to share files with your father and Samba installed to share files on your LAN. You would not even need a monitor and keyboard, you could manage the server from your Windows box using ssh.

Then you could just map a drive on your windows box to make saveing files downloaded from your torrent client more streamlined.  

Hope this helps.

---

