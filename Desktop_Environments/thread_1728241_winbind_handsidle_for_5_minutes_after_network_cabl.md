---
title: "winbind hands/idle for 5 minutes after network cable unplugged"
date: 2011-04-13
forum: Desktop Environments
---

### Post by gmoore777 on 2011-04-13
I'm trying to solve a more important winbind issue, but I am going
to start with this oddity that I stumbled upon.

I am on 64-bit LucidLynx Ubuntu 10.04 with latest packages:
   winbind and samba at 2:3.4.7~dfsg-1ubuntu3.5

We are integrated with Active Directory (winbind, etc.)

Everything's been working fine for one year.
(this oddity may have existed for the entire year)

I'm logged in as DOMAIN\first.last.

If I unplug the network cable and leave it unplugged, and
then immediately type any command, such as `wbinfo -t` or
`ls -al`, 
it will take exactly 5 minutes to 5 minutes 30 seconds before
those commands return.

I surmise that winbindd knows that the connection to the 
Domain controller is dead, and either keeps trying to connect
with a tiny wait in between, or just waits for the entire 
5 minutes before it says, 
"ok, I give up, I will use cached credentials now.".

Here are most of the pertinent settings.
I've noted the ones that I recently have added
or changed to try and control this unacceptable
5-minute behaviour. These setting do nothing to
reduce this 5-minute wait.

winbind reconnect delay=3     <-- newly added
winbind cache time=7          <-- newly added
winbind refresh tickets=true  <-- newly added
name cache timeout=0          <-- newly added
allow trusted domains = no
winbind offline logon = true
domain master = no
local master = no
preferred master = no

Anyone have any ideas on how to reduce or eliminate this 5-minute nap?

---

