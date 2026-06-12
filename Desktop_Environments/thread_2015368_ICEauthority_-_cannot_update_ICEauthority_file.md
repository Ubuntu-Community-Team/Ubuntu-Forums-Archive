---
title: "ICEauthority - cannot update ICEauthority file"
date: 2012-07-03
forum: Desktop Environments
---

### Post by ganna10 on 2012-07-03
Hi there,

I restarted by computer (running Ubuntu 12.04 32bit) after some updates (do not recall what were the updates) and since then I cannot login.  When I try to login, I always get a popup saying: cannot update ICEauthority file /home/jane/.ICEauthority.

I have tried running the suggestions that I have found in these forums but to no avail.. Here is a list of what I have done & the results.

1 - sudo chown jane:jane /home/jane/.ICEauthority
      sudo chmod 644 /home/jane/.ICEauthority
*did not work as same pop up showing when I tried logging in again*

2 - ls -a1 .ICEauthority
*cannot check if this is owned by me as I get the error, ls: cannot access .ICEauthority. No such file or directory.*

Also when I use TTY and login (successfully), there is the message: No directory,  logging in with HOME=/.  I think that this might be related to the problem of the .ICEauthority but I am not sure & I do not know how to fix it.

Thanks a lot for the help in advance,
Jane

---

### Post by ajgreeny on 2012-07-03
Looking at the file on my system it shows with** -rw------- **permissions, ie 600 in octal language, not 644, but I don't think that would make any difference when trying the chmod command.

Try renaming the file from Ctrl+Alt+F1 command line with ```
sudo mv /home/*user*/.ICEauthority /home/*user*/.ICEauthorityOLD
``` which is one answer I have seen mentioned before many times.

Just out of interest, have you made use of **sudo** to start graphical applications instead of **gksu** or **gksudo**, as that can cause this problem.  Srr Root-sudo in my signature for details and explanation of what you should always do.

---

### Post by ganna10 on 2012-07-03
Thanks for the reply.

I renamed the file as mentioned below (no error came up afterwards) but I still get the same ICEauthority popup when I try logging in again.

After reading the Root-sudo link, yes I have opened graphical applications with sudo & not gksudo.  I now know I won't be doing that again! :-)

---

### Post by ganna10 on 2012-07-03
Problem solved!

The home directory was not executable, so the rights were changed so that I could execute it and that fixed the problem.

Thanks.

---

