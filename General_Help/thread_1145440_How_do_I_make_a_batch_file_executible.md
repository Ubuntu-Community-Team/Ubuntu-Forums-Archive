---
title: "How do I make a batch file executible?"
date: 2009-05-01
forum: General Help
---

### Post by kcredden on 2009-05-01
Hey folks: I've been trying to write a simple batch file, and get it to run. But I've yet to get it fixed to be executable. The file is:

#apt-clean

sudo apt-get update
sudo autoremove
sudo purge
sudo autoclean
sudo check

The reason for this, is that after an update, or installing a program though apt-get, programs at times won't run. The indicator sits there and spins for about 20 or so seconds, then nothing. But I found by doing the above, it works. I got tired of having to type all that in, so a simple 1 click (or command) would be great. 

So how can I get this to work? I typed in: 

nano apt-clean
typed in the stuff above
saved it to the /home/kcredden directory
But chmod hasn't worked right.

Any ideas?

Thanks
 
- Kc

using Kubuntu 8.04. (Not upgrading to V9 till it's more debugged.)

---

### Post by wsonar on 2009-05-01
probably need to give it a .sh extention

chmod +x filename

the run it by ./filename

---

### Post by soro2005 on 2009-05-01
first off, I guess you mean sudo apt-get autoremove, etc. Secondly, you'd have to tell the script it should wait for one command to finish, then run the next one. And third, for a well formed script, you need to declare what shell you want to run it in. finally, skip the sudo here and run it with sudo. So this in your script:
```
#!/bin/bash
apt-get update &&
apt-get autoremove &&
apt-get purge &&
apt-get autoclean &&
apt-get check
```
Then make it executable with
```
chmod +x filename
```
Then run it with
```
sudo ./filename
```
Never use sudo if you do not absolutely have to.

---

### Post by egalvan on 2009-05-01
I wrote the following script 

*clean.sh*

the comments are to remind me of what I did,
and where the code came from...

all my scripts are in 

~/bin/

which is another trick I picked up from this forum...
it separates my stuff from everything else.
scripts placed there will be separated from any scripts that come with the original install, or are installed by other software...
and it keeps directories a little cleaner/neater.

I have desktop launchers to run these with just a double-click.

The script must be made executable...


```
#!/bin/bash
## commands to clean drive of excess garbage
## from ubuntu forums
## http://ubuntuforums.org/showthread.php?t=1113381
## 01-april-09

sudo apt-get autoremove

sudo apt-get autoclean

sudo apt-get clean

sudo dpkg --configure -a

```


No, the script is not perfect, or ideal...
it's "quick and dirty", one of the first I wrote for myself...
feel free to adapt, reuse, rewrite, delete, etc.

As for too much sudo, soro2005 may have a point...
I'm still too new to know about that...

ErnestG

---

### Post by lensman3 on 2009-05-01
During testing run the shell script using the following:

sh -xv <shell-script>

The -x will display to the screen each line as it is executed. The -v is verbose.  Generally, just the -x is good enough, though if there are if's and case statements, the verbose will list all statements, but only show those that are executed.  Also the <shell-script> doesn't have to have execute permissions.  The "sh" above can be replace with bash, but if you do a "ls -la /bin/sh" you will notice that "sh" is a soft link to "bash".

Once you set the script to +x, you can also add  to the end of first line of the script "#!/bin/bash"  an -vx.  It will do the same thing as "sh -xv" or "sh -x".

Hope this helps.

---

### Post by kcredden on 2009-05-02
Wow, now that's service! :). Thanks folks, got it running. Saves me a load of headaches. 

- Kc

---

