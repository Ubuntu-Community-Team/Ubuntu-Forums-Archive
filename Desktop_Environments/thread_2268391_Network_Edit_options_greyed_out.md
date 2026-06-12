---
title: "Network Edit options greyed out"
date: 2015-03-08
forum: Desktop Environments
---

### Post by Geoff_Lane on 2015-03-08
Folks,

Ubuntu 12.04 Unity Desktop.

Noticed recently that my option to edit network connections in my Unity desktop has been greyed out.

Can't recall when this happened.

Any ideas how to resolve it?

Geffers

---

### Post by fabio27 on 2015-03-13
Same problem here!

Noticed this morning it's been greyed out. Also, the "Disconnect" option under an active connection has been greyed out!
I had two kernels upgrade last 10 days: this may have changed something?

I've searched a little bit and found an approach in [http://askubuntu.com/questions/79546/why-is-the-edit-button-greyed-out-in-network-manager](http://askubuntu.com/questions/79546/why-is-the-edit-button-greyed-out-in-network-manager) . it is rather old (2012) but I'm about to try it anyway, and will post here results.


-f

---

### Post by fabio27 on 2015-03-13
ok, I've tried to change the NetworkManager.conf file and then killed NetworkManager, so that it restarts. 
Nothing changed and the options above are still greyed out and unusable.

Maybe recent kernel updates caused the problem?


-f

---

