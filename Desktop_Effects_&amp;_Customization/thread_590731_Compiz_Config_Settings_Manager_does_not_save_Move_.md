---
title: "Compiz Config Settings Manager does not save Move Window settings"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by ajesh on 2007-10-25
CompizConfig Settings Manager does not save the "Move Window" setting in Gutsy.

I have to set this up every time I boot up/log-in. All the other settings (like rotate cube, etc) did get saved and stay set.

I did not have this problem when I had compiz-fusion installed on Fiesty.

Please let me know, if there is a way to save the "Move Window" settings.

Thanks.....

---

### Post by ajesh on 2007-10-26
I solved this in a weird way.

The compiz config file in ~/.config/compiz/compizconfig/Default.ini was being overwritten every time I rebooted the machine. I don't what process overwrites this file or why it was overwriting it.

Anyway, it was removing the move default option. I changed the permissions on the file so that it can't be written anymore. So, now my options are not modified on reboot. However, I have to remember to change the permissions whenever I have to change any option in compiz. This will be annoying.

Let me know if anyone knows the cause of this problem......

Thanks,

---

### Post by jargoman on 2008-01-08
try looking in your log for the words permission denied

```
sudo cat /var/log/messages | grep "permission denied"
```

---

