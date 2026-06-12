---
title: "Updated to 6.06 - And now I can't do anything"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Edward The Bonobo on 2006-06-02
I'e updated to Dapper using the Update Manager.  It seemed to work OK.  Then, as advised,  I had to run apt-get dist-upgrade to get the various packages the upgrade manager doesn't do.  There were a few error messages towards the end and a message to run apt-get update.

But...now I'm stuck.  I can boot in - but I get an error message about the Gnome configuration Daemon.

When I click on Applications (ie to open a Terminal), the menu flashes on and of and doesn't let me select anything.

I got into terminal mode (I can't remember how wou're meant to do it...I held Ctrl+alt and bashed F keys at random).  I tried sudo apt-get update, gave my usual password...and it wasn't accepted.  ](*,) 

Any ideas?

Help would be greatly appreciated.  You don't want me to have to keep using Windows, do you?

---

### Post by Ptero-4 on 2006-06-02
You only need to do ctrl+alt and one of the f keys from f1 up to f6. Hitting that sequence with two or more different f keys will open two or more terminals. Also you can only run one instance of apt at a time. If you try to open two or more instances of apt it will complain about a lock error and won't let you continue.

---

