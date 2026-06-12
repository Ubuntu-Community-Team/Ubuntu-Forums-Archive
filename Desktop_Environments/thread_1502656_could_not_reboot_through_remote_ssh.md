---
title: "could not reboot through remote ssh"
date: 2010-06-05
forum: Desktop Environments
---

### Post by chrone on 2010-06-05
i have been encountered this issue since ubuntu hardy 8.04.3, and now after i clean installed to ubuntu lucid 10.04 with the latest update up to june 6, 2010, i still could not reboot via command line in a remote ssh.

is this a bug?

---

### Post by 3Miro on 2010-06-06
> **chrone said:**
> i have been encountered this issue since ubuntu hardy 8.04.3, and now after i clean installed to ubuntu lucid 10.04 with the latest update up to june 6, 2010, i still could not reboot via command line in a remote ssh.

is this a bug?

What command are you using? You should use:
```
sudo shutdown -r now
```

---

### Post by chrone on 2010-06-06
> **3Miro said:**
> What command are you using? You should use:
```
sudo shutdown -r now
```

i used sudo shutdown -r now too, but it didn't work. so i tried with sudo reboot and it didn't work either.

perhaps the command line through remote ssh didn't work on intel S3000AH motherboard. :(

---

