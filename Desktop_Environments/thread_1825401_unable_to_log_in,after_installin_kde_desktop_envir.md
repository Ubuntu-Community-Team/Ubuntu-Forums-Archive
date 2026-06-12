---
title: "unable to log in,after installin kde desktop environment"
date: 2011-08-15
forum: Desktop Environments
---

### Post by ganiz on 2011-08-15
hello everyone..i have installed ubuntu  10.10(gnome desktop environment),in my laptop..everythin was workin  well for the past two months...recently,i added kde plasma desktop  environment,via ubuntu software centre..now,when i try to log into  ubuntu,there is an error message stating "gnome power manager have not  been installed correctly.please contact your system administrator",on  the topmost right edge of the screen...i tried various commands like,

sudo apt-get clean
sudo dpkg --configure -a
chmod 0777 /temp
etc.,

but,nothin has solved my problem..many suggested that it may be due to  low drive space..but i cant use the mv commands too..really,i'm so  helpless and its been three days,after usin my laptop..please provide me  with your suggestions,as soon as possible..

thanking u,ganiz...

---

### Post by oldos2er on 2011-08-15
To clear some hard disk space, see this thread: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

Can you boot into recovery mode? If so I would try running ```
apt-get update && apt-get install kdm
``` and see if that allows you to log in.

---

