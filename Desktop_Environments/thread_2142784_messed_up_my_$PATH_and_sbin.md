---
title: "messed up my $PATH and /sbin"
date: 2013-05-06
forum: Desktop Environments
---

### Post by linxlimbo on 2013-05-06
While switching from KDE to XFCE i managed to mess up my $PATH (least I believe).  When i enter ```
ifconfig
``` into my terminal i get the error.
```
Command 'ifconfig' is available in '/sbin/ifconfig'
The command could not be located because '/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
ifconfig: command not found
```

when i echo $PATH i get ```
echo $PATH
/usr/local/bin:/usr/bin:/bin:/usr/games
```

so far my googling has found a temp fix ```
export PATH=/sbin:$PATH
```

so far I have reached two questions.  Is this the best method of restoring my /sbin path?  and how do i make it perminant?

---

### Post by papibe on 2013-05-06
Hi linxlimbo.

If you dynamically changed it in a terminal, just close it and open a new one.

If you don't want to close your terminal, try this:
```
source /etc/environment
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by linxlimbo on 2013-05-06
Thanks papibe for the quick reply,
unfortunately when i ```
source /etc/environment 
``` and then quit out of terminal and open a new one the same warning comes up.

---

### Post by papibe on 2013-05-06
I see.

I think you made a permanent change, then.

Do you remember what file did you change?

Could you post the result of this command?
```
grep PATH ~/.*
```
Regards.

---

### Post by linxlimbo on 2013-05-06
this wasn't a recent change so nothing that can be pulled from recent history, i'm not sure if you can find what you're looking for in there.  But here's the outcome of your request
```
/home/user/.bash_history:export PATH=$PATH:/usr/sbin
/home/user/.bash_history:export PATH=$PATH:/usr/sbin:/usr/local/sbin:/usr/local/bin:/usr/bin:/sbin:/bin:/usr/games
/home/user/.bash_history:echo $PATH
/home/user/.bash_history:export PATH=/sbin:$PATH
/home/user/.bash_history:echo $PATH
/home/user/.bash_history:echo $PATH
/home/user/.bash_history:export PATH=/sbin:$PATH
/home/user/.bash_history:export PATH=/sbin:$PATH
/home/user/.bash_history:echo $PATH
/home/user/.bash_history:export PATH=/sbin:$PATH
/home/user/.bash_history:echo $PATH
/home/user/.bash_history:export PATH=/sbin:$PATH
/home/user/.profile:# set PATH so it includes user's private bin if it exists
/home/user/.profile:    PATH="$HOME/bin:$PATH"


```

---

### Post by papibe on 2013-05-06
By any chance did you edit files on /etc?

Could you post the result of this command?
```
grep -i path /etc/bash.bashrc /etc/profile
```
Regards.

---

### Post by linxlimbo on 2013-05-06
that grep results in nothing, big issue?

---

### Post by linxlimbo on 2013-05-06
I just looked into "bash" and came across this article about bash and the order it invokes.
.bashrc exsists, but .bash_profile doesn't.  Is this the issue?  If so, where is echo $PATH pulling from?  because if I perform the same command under root it results in a different answer.

---

### Post by papibe on 2013-05-06
> **linxlimbo said:**
> bash_profile doesn't.  Is this the issue?
Not really.
> **linxlimbo said:**
> I perform the same command under root it results in a different answer.
That sounds like a good thing. I'm guessing you set the changes only for your account and not for the whole system.

Let's compare you bash config files with the base ones. Could you post the result of these 2 commands?
```
diff /etc/skel/.bashrc ~/.bashrc

diff /etc/skel/.profile ~/.profile
```
Regards.

---

### Post by linxlimbo on 2013-05-07
neither of those commands result in anything, does this mean there's no difference? 

Edit: after reading up on this command and doing a quick manual command I realize this is just showing there is no difference between the two files.

---

### Post by linxlimbo on 2013-05-07
Also if I look at my /etc/environment it tells me that /sbin is found within it.  Doesn't this mean that sbin is included in my environment that is originally loaded at login?
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

---

### Post by papibe on 2013-05-07
Yes.

In a system with no mods, you should end up with that path after login. If you have guess account enabled, you may tried login in as guess and check what path you end up with. 

Regards.

---

### Post by linxlimbo on 2013-05-08
I'm also finding that applications are reinstalling themselves to, or are not fully removing themselves when they state they are.  Take for example conky
if i do a purge, autoremove or remove terminal states that conky isn't installed.  But if i restart the computer up pops conky, and I can do a quick locate to see some of the important conky files are back like .conkyrc and /etc/conky.  Does this mean that they are installed to a different location, and when i'm trying to remove them i'm  trying to remove them from a different place then they really are?

---

### Post by linxlimbo on 2013-05-08
oh and made another account, got the same path that my user account has, which is minus the sbin path

---

