---
title: "can't install firefox- apt-get problem?"
date: 2009-06-13
forum: General Help
---

### Post by bartoni on 2009-06-13
Here's my problem :

```
$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
```

Ok, it says there's no firefox, I do as suggested : 

```
$ sudo apt-get install firefox-3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-3.0 is already the newest version.

```

Thinks it's already installed! Huh? 


```
sudo find / -name firefox

```
Nothing.

Tried apt-get update, apt-get autoclean

Please help! How do I install firefox?

---

### Post by QIII on 2009-06-13
Odd.

Just as kind of a graphical double check, does it show up in Synaptic?

---

### Post by synapsys on 2009-06-13
Try installing meta package

```
sudo apt-get install firefox
```

---

### Post by jenkinbr on 2009-06-13
sudo apt-get install --reinstall firefox-3.0

---

### Post by bartoni on 2009-06-13
synaptic had it marked as installed,  clicked reinstall and it worked!

Thanks for your help.

Now struggling with Flash plugin.

---

### Post by jenkinbr on 2009-06-13
> **bartoni said:**
> synaptic had it marked as installed,  clicked reinstall and it worked!

Thanks for your help.

Now struggling with Flash plugin.
Which essentially is the same thing that I posted.

Glad it works for you now. :)

---

### Post by bartoni on 2009-06-13
Didn't see your reply there, yes! -reinstall to the rescue, I'll remember that for next time.

Does anyone know where I should be putting libflashplayer.so? I'm running a slightly old eeexubuntu, running adobe's flash installer has never worked for me in the past, i've had to copy the libflashplayer.so file somewhere (firefox/plugins I'd have thought) in the past to get flash working, but now nowhere seems to work right now.

---

### Post by QIII on 2009-06-13
> **bartoni said:**
> synaptic had it marked as installed,  clicked reinstall and it worked!

Thanks for your help.

Now struggling with Flash plugin.

Well, I'm glad it worked.  Not sure I was saying to reinstall it from there, but I guess I wasn't clear...

The --reinstall switch would have worked from the terminal.

Although Synaptic is great, sometimes using the terminal is instructive.

But I'm glad you got it running.


BTW -- for future reference you can type the following in the terminal

man apt-get

---

### Post by jenkinbr on 2009-06-13
> **bartoni said:**
> Didn't see your reply there, yes! -reinstall to the rescue, I'll remember that for next time.

Does anyone know where I should be putting libflashplayer.so? I'm running a slightly old eeexubuntu, running adobe's flash installer has never worked for me in the past, i've had to copy the libflashplayer.so file somewhere (firefox/plugins I'd have thought) in the past to get flash working, but now nowhere seems to work right now.
Create a new thread for this, as it is a different issue.

---

