---
title: "GNOME is broken..."
date: 2006-02-12
forum: Desktop Environments
---

### Post by danhm on 2006-02-12
I installed Opera via Synaptic, tried to run it, recieved an error about not having Motif installed, and then my machine locked up. I killed X with ctrl + alt + backspace, and now GNOME gives me an error when I try to log in and goes back to GDM. I'd post the error, but it doesn't stay in my clipboard (is it possible to cut and paste it? I guess I could write it down and then type it out).


Luckily, I had installed Enlightment awhile ago, so I'm using that for now.

---

### Post by Mustard on 2006-02-12
The error message is the vital clue, so as painful as it is to have to type it all out, its pretty important for troubleshooting.

---

### Post by danhm on 2006-02-12
It's all Greek to me...

```

/etc/gdm/PreSession/Default: Registering your system with wtmp and utmp
/etc/gdm/PreSession/Default: running /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "dan"
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid !=0, directory /dev/X will not be created.
_TransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: Transport open failed for pts/ubuntu.
_IceTransMakeAllCOTSServerListener: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/ubuntu:
_IceTransMakeAllCOTSServerListener: failed to open listener for isc
_IceTransSCOOpenServer: Protocol not supported by SCO connection
_IceTransOpen: transport open failed for sco/ubuntu:
_IceTransMakeAllCOTSServerListener: failed to open listener for sco

** (gnome-session:8878): WARNING **L Unable to lock ICE authority file: /home/dan/.ICEauthority
```


Hopefully there are no typos.

---

### Post by danhm on 2006-02-12
This probably isn't good either:

```
bash: /home/dan/.bashrc: Permission denied
dan@ubuntu:~$ ls
ls: reading directory .: Input/output error
```

---

### Post by kaamos on 2006-02-12
[QUOTE=danhm]This probably isn't good either:

```
bash: /home/dan/.bashrc: Permission denied
dan@ubuntu:~$ ls
ls: reading directory .: Input/output error
```[/QUOTE]
Try this
```
sudo chown dan:dan /home/dan -R
```

---

### Post by danhm on 2006-02-12
```
bash: /home/dan/.bashrc: Permission denied
dan@ubuntu:~$ sudo chown dan:dan /home/dan -R
Password:
dan@ubuntu:~$ ls
ls: reading directory .: Input/output error

```


I can view my Gaim logs and play music with amaroK just fine; both the logs and the music are in /home/dan, so I know the partition isn't corrupted.

---

### Post by kaamos on 2006-02-12
Hmm.. try "sudo su" or booting in the recovery mode (chosen in grubs menu) and then use the command above.

---

### Post by angkor on 2006-02-12
[QUOTE=kaamos]Try this
```
sudo chown dan:dan /home/dan -R
```[/QUOTE]

I maybe wrong but shouldn't that be:

sudo chown -R dan:dan /home/dan

---

### Post by danhm on 2006-02-12
Neither command changes the result of trying to show the contents of /home/dan.


Also, when GNOME is loading in recovery mode, I get the attached error message.

---

### Post by Mustard on 2006-02-12
Try this...

Use <ctrl><alt><f1> to switch to text mode. 

Log in and do: 

```
rm .{X,ICE}authority
```

---

### Post by danhm on 2006-02-12
It says:

```
-bash: /home/dan/.bashrc: Permission denied
dan@ubuntu:~$ rm .{X,ICE}authority
rm: cannot remove '.Xauthority": Input/Output error
```


I'm beginning to think that I should just reinstall Ubuntu; my /home is a on a seperate partition, so I won't lose any data or settings, just some programs. I'm a little nervous that I can't display the contents of /home/dan, but amaroK plays all of my music, Firefox knows all of my bookmarks, etc so I know it's still there.

Any tips before I reinstall? What is happening, exactly? Would a reinstall even help? The problem seems to be with things in my /home partition.


Also, thanks for all the help.

---

### Post by Mustard on 2006-02-12
I googled this up...

[http://www.evilducky.net/2006/01/22/ubuntu-linux-wont-load-gnome-desktop/](http://www.evilducky.net/2006/01/22/ubuntu-linux-wont-load-gnome-desktop/)

Quote from the link above...

> Ctrl+Alt+F1 to a console and log in and then:

chown yourusernamehere ~/.ICEAuthority
sudo chmod 777 /home/yourusernamehere/.ICEAuthority
sudo /etc/init.d/gdm restart

Obviously replace yourusernamehere with your login name. Login and you should be good to go!

Another solution suggested from this thread....

[https://lists.ubuntu.com/archives/ubuntu-users/2005-July/042849.html](https://lists.ubuntu.com/archives/ubuntu-users/2005-July/042849.html)

> Just try renaming .ICEauthority to .ICEauthority.bak( using either the
recovery mode or failsafe
terminal ..or press Ctrl+Alt+F2 and logon). Some people have had
problems with .ICEauthority and this is at best a temporary fix. Try
it out and let us know.

---

### Post by danhm on 2006-02-12
I keep getting the Input/Output error, no matter what I try to do to the file.

---

### Post by Mustard on 2006-02-12
Very frustrating....

Your errors are similar to those experienced by others except for that one extra error.  There must be something more seriously wrong with your installation I guess.

---

