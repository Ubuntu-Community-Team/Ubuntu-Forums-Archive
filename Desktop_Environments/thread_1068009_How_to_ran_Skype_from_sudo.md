---
title: "How to ran Skype from sudo ?"
date: 2009-02-12
forum: Desktop Environments
---

### Post by _exn_ on 2009-02-12
Hello !

  I have good idea for run closed source applications from sudo, but i have 1 little problem:
  I can't run xwindow applications from other users.
 
  I have try do it like this 
  ```

exn@exn-home:/tmp/skype-2.0.0.72$ sudo -i -u skype
skype@exn-home:~$ /tmp/skype-2.0.0.72/skype
No protocol specified

skype@exn-home:~$ env | grep DISP
DISPLAY=:0.0

 
``` 

 From my (exn) user skype runs fine. Ideas ?

---

### Post by cariboo on 2009-02-12
I have no idea why you would want to run skype as root, but any time you need to run a graphical application as root type Alt-F2 and then enter:

```
gksu skype
```

This will start and run skype as root, any settings will be saved in /root so they won't be available to any other users.

Jim

---

### Post by _exn_ on 2009-02-12
root ? I told what i need run that from sudo.

 Solved, just need change permissions for .Xauthority.

---

### Post by SuperMike on 2010-03-23
I found something interesting. Perhaps you all can pick up the pieces from here and get it to work completely?

I did this at command line:

xhost +

I then did the 'gksudo -u skype /usr/bin/skype' from a desktop launcher, used my local workstation password as supermike, and kapoof I was up and loaded with Skype running under the skype account. I then did a 'ps -ef | grep -i skype' and sure enough saw that it was running under the skype account. It took awhile to load, but then all was well except that it couldn't make calls. It basically couldn't find the pulse audio drivers for some reason. I tried mucking with the sound settings and didn't get anywhere.

Note I'm on Ubuntu 8.04 LTS and using Skype Static 2.1.0.81.

If you can figure out the Pulse Audio step for the skype account, then we can publish a way to get Skype to run under a restricted ID on a computer and not your personal ID.

Also, I tried:

xhost +skype

But it reported that "skype" was not a valid hostname. When I did 'man xhost' it said that I can do +hostname with hostname being a computer or a user. So, this was strange. In the end, I simply opted for 'xhost +', which means (let everyone access to your X desktop). I would have preferred a better option.

---

### Post by srf21c on 2011-01-18
I was able to launch a secondary instance of skype on Ubuntu Maverick 10.10 using the following command:

```
gksu skype-wrapper
```

I did not test the second Skype instance running as root to see if it can successfully interact with pulse-audio while the primary Skype instance is running.

Launching a secondary instance of Skype using another "Desktop User" account type on my system failed however with the "no protocol specified" error. 

```
gksu -u altuser skype-wrapper
```

Now I'm trying to figure out how to grant permissions to the 2nd skype user account to the currently logged in user:

```
XAUTHORITY=/var/run/gdm/auth-for-seth-oVRqMw/database
```

I ran ```
xhost +altuser@myhost
``` and it spit back ```
altuser@myhost being added to access control list
```

Tried running ```
gksu -u altuser skype-wrapper
``` again but it crapped out with the same "No protocol specified" error.

Then I tried ```
xhost +
```
and got
```
access control disabled, clients can connect from any host
```

Now ```
gksu -u altuser skype-wrapper
``` will launch a secondary instance of skype under the non-root "Desktop user" class account.

---

### Post by fraktalek on 2012-06-15
running

```
xhost +
```

is not wise as it turns off access control to X completely.

Instead, try running

```
xhost + SI:localuser:yourusername
```

---

