---
title: "IVTV: Can't access tuner after viewing with mplayer"
date: 2006-01-14
forum: General Help
---

### Post by Sureshot324 on 2006-01-14
I have a hauppauge pvr 150 and I have just installed the ivtv drivers.  I can run cat /dev/video0 > test.mpg, let it go for a while, and hit ctrl c, and it successfully makes an mpeg.  I can rerun that command as many times as i want and it still keeps working.

However, if I run mplayer -vo xv /dev/video0, it works the first time, but after I close mplayer it locks up the tuner so i can't view it again, and can't even run the cat command on it anymore until i reboot.  

When the tuner is in this locked state, I get this error when i run cat /dev/video0 > test.mpg:

cat: /dev/video0: Device or resource busy

When i try to view it in mplayer, it prints a lot to the console but i think this is where it goes wrong:

mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

If i try modprobe -r ivtv, i get this: 
FATAL: Module ivtv is in use.

After a reboot it works fine again.  Is there any way to release the tuner and ivtv drivers from this locked state so I can access it again?  Also, is there a way to watch tv in mplayer without locking up the tuner after i close it?

I'm using Ubuntu breezy amd64 and ivtv 0.41

---

### Post by Sureshot324 on 2006-01-19
Found the problem.  Mplayer wasn't terminating properly.  If i do ps -A|grep mplayer to find the process id of mplayer, then kill <that pid>, it works again.

---

### Post by bb002 on 2006-02-21
I know this is old but....

I had this problem too. hitting the esc key to quit seems to make mplayer quit properly. while using the close button doesn't...dunno why but that is my experience. Saved my from doing "killall mplayer" every time i use mplayer.

---

