---
title: "Unable to get past login screen since powercut - fixed before by rm a file in ~?"
date: 2011-11-30
forum: Desktop Environments
---

### Post by Dáire Fagan on 2011-11-30
There was a power cut yesterday and Xubuntu 11.04 running Xfce shutdown unexpectedly.

Since this time I have been unable to get past the login screen after entering my password (correctly, with caps lock off etc) because after I do the screen goes black for a second and then asks for the password again, without saying the password was wrong as it would was it.

This problem happened before, and regretfully I did not write down the solution - but the problem was solved - and I remeber because it was so simple - by removing a single file from within my home directory.

I believe the file deleted forced a new session as the previous had become corrupt during a power cut when I was logged in. 

Because of this I did a rm ~/.cache/sessions/*

I then tried shutdown now and the computer tried to shut down but then hung on a black screen with a Xubuntu logo - I removed the hard power after 10 minutes of this.

On attempting to login nothing had changed so I removed the file again but the system reported no such file.

Any ideas?

The file was *possibly *something in .local.

---

### Post by Dáire Fagan on 2011-11-30
Possibly something to do with resetting my profile but not to the point where it deletes everything or I do not recognise things when I log in.

---

### Post by vangop on 2011-11-30
Try the same ```
rm -r ~/.cache/sessions/
``` but from a virtual terminal, not under xubuntu/x.
Just ctrl+alt+f1, login, enter the command and then ```
sudo shutdown -r now
```

---

### Post by Dáire Fagan on 2011-11-30
> **vangop said:**
> Try the same ```
rm -r ~/.cache/sessions/
``` but from a virtual terminal, not under xubuntu/x.
Just ctrl+alt+f1, login, enter the command and then ```
sudo shutdown -r now
```

Thanks, but that's how I was trying it because I was not able to get passed login into x :)

Fixed with:

```
sudo rm ~/.ICEauthority
```

---

