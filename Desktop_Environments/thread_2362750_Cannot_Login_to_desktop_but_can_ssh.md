---
title: "Cannot Login to desktop but can ssh"
date: 2017-06-01
forum: Desktop Environments
---

### Post by ob2s on 2017-06-01
I only have one user setup on ubuntu 14.04LTS and I can ssh to the system, run sudo, etc, but when I connect a monitor to it, I can bring up a desktop logging in as guest, but when I try to login with the one real user that runs everything, it just circles back to the login as if the password is wrong (it isn't). Can anyone advise me on what is happening and how to fix it  ? 
Thanks

---

### Post by ob2s on 2017-06-01
I created a new user via ssh and can render the desktop, not sure what was breaking the desktop for the one user. Thanks

---

### Post by steeldriver on 2017-06-01
Usually it's an ownership / permissions issue that prevents the session setup from writing to the user's .Xauthority or .ICEauthority file (either of the file(s) themselves or the home dir)

---

