---
title: "dpkg: subprocess post-installation script returned error exit status 135"
date: 2009-04-22
forum: General Help
---

### Post by sanmannor on 2009-04-22
I am running a fresh install of 8.10 i386 downloaded  last night.  
I installed it successfully went to update manager and updated.   
downloded all the updates,  but on installing them it stated 
[I]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
[/I]so I ran  in terminal
**sudo dpkg --configure -a**
 it outputted 
[I]Setting up libc6 (2.8~20080505-0ubuntu9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error
dpkg: subprocess post-installation script returned error exit status 135
^[[C^[[B^[[Dthenor@thenor-laptop:~/Desktop$ 
[/I]
so I looked it up in the forums and saw a few post that might help... but none did.   
any ideas.

---

### Post by stilling on 2009-04-22
> **sanmannor said:**
> I am running a fresh install of 8.10 i386 downloaded  last night.  
I installed it successfully went to update manager and updated.   
downloded all the updates,  but on installing them it stated 
[I]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
[/I]so I ran  in terminal
**sudo dpkg --configure -a**
 it outputted 
[I]Setting up libc6 (2.8~20080505-0ubuntu9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error
dpkg: subprocess post-installation script returned error exit status 135
^[[C^[[B^[[Dthenor@thenor-laptop:~/Desktop$ 
[/I]
so I looked it up in the forums and saw a few post that might help... but none did.   
any ideas.


try this 

sudo apt-get -f install

Help it works

---

### Post by sanmannor on 2009-04-22
ok, tried that, got this 
[I]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. [/I]

---

### Post by stilling on 2009-04-22
sudo dpkg --configure -a
try it again

---

### Post by sanmannor on 2009-04-22
tried that again  typed  
**sudo dpkg --configure -a**

got 

[I]Setting up libc6 (2.8~20080505-0ubuntu9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error
dpkg: subprocess post-installation script returned error exit status 135
thenor@thenor-laptop:~/Desktop$ 
[/I]

---

### Post by stilling on 2009-04-22
ok lets do this 
open synaptic package manager search for libc6 mark for complete removal 
after opne terminal and run sudo apt-get install libc6
tell me what happends

---

### Post by sanmannor on 2009-04-22
can't open synaptic pakage manager,  it gives me the fallowing message 
[I]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/I]

then it closes... is there a way to do it through terminal

---

### Post by stilling on 2009-04-22
try sudo apt-get purge libc6
sudo apt-get install libc6

---

### Post by sanmannor on 2009-04-22
tried 
**sudo apt-get purge libc6**


got  
[I]
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. [/I]
 so I ran 
** sudo dpkg --configure -a**
 got 
[I]Setting up libc6 (2.8~20080505-0ubuntu9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error
dpkg: subprocess post-installation script returned error exit status 135
thenor@thenor-laptop:~/Desktop$ 
[/I]

---

### Post by sanmannor on 2009-04-22
Any help would be appreciated

---

### Post by orlox on 2009-04-22
If libc6 configuring is failing, then something very strange is happening. What you can do, (though I dont know if this could be called a solution, Id say its a risky workaround) is to rename the post installation script. run the following commands on a terminal:

```

cd /var/lib/dpkg/info
sudo mv libc6.postinst libc6.postinst.back
sudo dpkg --configure -a
sudo mv libc6.postinst.back libc6.postinst

```

Tell me if this helps...

---

### Post by sanmannor on 2009-04-22
well it let me finish mostly  updating but still can't do much else still wants me to 
run 
sudo dpkg --configure -a
 it gave me  the fallowing error 
Setting up libc6 (2.8~20080505-0ubuntu9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error
dpkg: subprocess post-installation script returned error exit status 135

---

### Post by orlox on 2009-04-22
Glad it helped.

The thing is, for each package, dpkg (the package manager) has a series of scripts that perform specific configurations, or removal of things, etc... depending on what needs to be done after an specific action with the package (like installation or removal of the package).

When one of the scripts fails for X reason, dpkg tends to break and give this responses that to most people are cryptic...

So, by tricking dpkg and moving the scripts associated with this, it thinks there's actually no configuring to be done, and it doesnt fail...

Of course this is only a workaround, if the script actually has some important configuring to be done, things could get messy on your system.

However, since libc6 should have been installed and configured when you installed you system, reconfiguring after and update might not be so transcendental, but I cant really assure you that.

In any case, you'll have to wait and see if nothing is working funny, I probably expect this not to happen though. But, perhaps, when you get a new update for libc6 this problem might reappear, in which case, youll need to redo this to make the updates work.

---

### Post by sanmannor on 2009-04-22
so it worked temporarily... but now is broken again  
should I re do that script

---

### Post by orlox on 2009-04-22
It wouldnt hurt to try...You can always change it, and try reinstalling the package until it works. Commenting different parts of the script should help you see where the problem is, and if you find something, id reccomend you to submit a bug report at launchpad

---

