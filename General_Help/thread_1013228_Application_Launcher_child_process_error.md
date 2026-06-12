---
title: "Application Launcher child process error"
date: 2008-12-16
forum: General Help
---

### Post by Waderider on 2008-12-16
I've just successfully installed Cisco VPN on Intrepid for attaching to my University network. Manually typed via terminal....

<sudo /etc/init.d/vpnclient_init start>

...starts the vpnclient and.........

<vpnclient connect AcademicNetwork>

.........gets me the right profile and resultant VPN connection.

I used gedit to create a file with these two lines sequentially. I have then created an application launcher, type "Application in Terminal", pointing to this file. However when I click on the launcher the (blank) terminal opens and I get a separate window saying "There was an error creating the child process for this terminal".

Any help would be greatly appreciated!

---

### Post by Waderider on 2008-12-17
Just in case someone stumbles across this post with the same problem, here's the simple solution.

I ran nautilus <sudo nautilus>, navigated to the script I'd created, selected properties then the permissions tab, and selected "Allow executing file as program".

So it was a permissions error (obviously); a pretty simple one at that!

---

### Post by Redsunz on 2009-02-05
I ran into this error as well "There was an error creating the child process for this terminal"
I was trying to set up multiple copies of folding at home for each of my four cores with shortcuts on the desktop. I figured out it was a bug in the folder mapping line /home/username/.folding/Core 3/fah6 -verbosity
So I took out the space in the folder name "Core 3" and renamed the folder to
/home/username/.folding/Core3/fah6 -verbosity
No more error message. :p

---

### Post by AndresM on 2010-02-21
Similar problem here:

To run Skype I need to type the following on the terminal for the video to run:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype &D
```

So I said to myself, hey I'll just do one of those aplication launches on the top bar, put the skype icon to it and that will be it. 

But I get the child process error and the empty terminal. 

I tried other things like:
```
sudo shutdown 23:00 -h "past your bed time you ubuntu wannabe"
```

And it seems to work.

---

### Post by AndresM on 2010-02-21
Found solution here:

[http://ubuntuforums.org/showthread.php?t=1361679](http://ubuntuforums.org/showthread.php?t=1361679)

it was exactly the same thing.

---

