---
title: "Web browser fault and update error"
date: 2010-07-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Picapica on 2010-07-10
Hi
Note: I am an Ubuntu novice!
My Dell mini web browser will not open (spins but then nothing). I think there may be a problem related to an update that didn't finish. When I try to update or add/remove programs, I get an error message that says:
E: dpkg was interrupted, you must manually run 'dpkg -- configure -a' to correct the problem.
E: _cache->open() failed, please report.

I managed to open the terminal and run what is in quotes, I got list of options, none of which seemed like the obvious fix. Help!?
Thank you

---

### Post by mikewhatever on 2010-07-11
The command in quotes should be run with admin privileges.
Try the following one:
```
sudo dpkg -- configure -a
```

---

### Post by Picapica on 2010-07-13
Hi Mikewhatever
Thanks! So I put that code in terminal and it came up with 
Dpkg: need an action option
Plus it gave me options for help codes

I tried to run update manager again and I got the same error message as previously mentioned.
My web browser does not open (spins and then nothing).

To recap, my main problem is that I can't open a web browser. Attempting to update or install or reinstall a web browser fails as mentioned. I don't know the best way to trouble shoot. Dell and Dell/ubuntu support forwarded me here since I don't have a service plan. 

Thanks for trying to help a completely green Ubuntu user! I apologize for being clueless!
Ideas?

---

