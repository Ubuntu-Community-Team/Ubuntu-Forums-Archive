---
title: "[SOLVED] changing home directory stops GNOME from starting"
date: 2007-11-02
forum: Desktop Environments
---

### Post by 1212jtraceur on 2007-11-02
I decided to change my username, along with my home directory. I was able to do the first with usermod, but the latter is giving me trouble.

My old username was 'joseph' ($HOME = /home/joseph), and my new is 'frazierj' (currently keeping $HOME = /home/joseph).I tried: ```
sudo usermod --home /home/frazierj -m frazierj
``` However, after I login through gdm, I get a blank screen with only a cursor, which, oddly enough, is responsive.

Is there something I'm missing here? I thought usermod would take care of it...

Thanks,
1212jtraceur

---

### Post by MrFSL on 2007-11-02
The users home can be changed by editing /etc/passwd

Once edited I would probably change the permissions on the home folder using something like:
```
sudo chown -R NewUsername /home/NewUserFolder
```

EDIT: and I would probably execute the above and do the editing from recover mode at boot time.

---

### Post by 1212jtraceur on 2007-11-02
I just tried that. It worked only once, and then it took a while to start and my Firefox extensions weren't working, along with some error window when GNOME started. Do you know of anything else I could do? Right now, I'm symlinking my old directory to my new, but I would like to get it to work properly...

---

### Post by 1212jtraceur on 2007-11-05
Ok, it's working now, by using usermod. It just takes a while. Thanks for the help.

---

