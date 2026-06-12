---
title: "/home/ permissions problem"
date: 2008-08-24
forum: Desktop Environments
---

### Post by dennismoore1 on 2008-08-24
Recently I accidentaly piped the following command

ls|chmod a+rwx $HOME

DONT EVER DO THAT!

anyway next time i signed in it said that .dmrc should have 644 permissions and that the $HOME folder should belong to the user.

after i made the corrections it said to in a fail safe terminal it said it could not log into Gnome because the $HOME/.ICEauthority file should be writable by all users and its directory should be aswell...

so i did that then it said that $HOME should belong to the user...thats right...it said it again.

so i did this which allows me to log in but gives an annoying error message each time

sudo chmod 644 .dmrc

so what do i do?
its either an annoying error message
or nothing at all
Please help
Thanks

---

### Post by ecolitan on 2008-08-25
I don't exactly understand the prob...

When you set the permissions on your homedir though they should be 700, else you cant get into the dir. 

```

sudo chown `echo $USER`:`echo $USER` `echo $HOME`
sudo chmod 700 `echo $HOME`

```

---

