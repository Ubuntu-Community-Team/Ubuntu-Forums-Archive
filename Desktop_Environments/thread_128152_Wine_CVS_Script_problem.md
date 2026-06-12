---
title: "Wine CVS Script problem"
date: 2006-02-10
forum: Desktop Environments
---

### Post by geo926 on 2006-02-10
Hey guys when trying to install the newest CVS package from wine through the WineCVS.sh script I get the following output eror.

```
-------------------------------------------

Checking out CVS ... May take a while




--------- Error log - file /root/.WineCVS/sources/cvscedega/ErrorLog : ---------/root/.WineCVS/Functions/RunWineCVS: line 736: cvs: command not found


Error in CVS checkout

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)
 
```

Can anyone tell me how to get around this problem? Thankyou!

---

### Post by dcstar on 2006-02-10
[QUOTE=geo926]Hey guys when trying to install the newest CVS package from wine through the WineCVS.sh script I get the following output eror.

```
-------------------------------------------

Checking out CVS ... May take a while




--------- Error log - file /root/.WineCVS/sources/cvscedega/ErrorLog : ---------/root/.WineCVS/Functions/RunWineCVS: line 736: cvs: command not found


Error in CVS checkout

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)
 
```

Can anyone tell me how to get around this problem? Thankyou![/QUOTE]
Do you have the cvs package installed?

---

### Post by geo926 on 2006-02-10
[QUOTE=dcstar]Do you have the cvs package installed?[/QUOTE]

I am not sure If I do....Can i apt-get it?

---

### Post by cdhotfire on 2006-02-10
```

$ sudo apt-get install cvs

```

I think so.

---

### Post by geo926 on 2006-02-11
Hmmm I tried this and even though I seem to get further in the compile I still get stopped with the same error code telling me to try running without parameters, how do I do this?

---

### Post by cdhotfire on 2006-02-11
Eg: **WineCVS.sh**

I guess its like that.

---

### Post by geo926 on 2006-02-11
[QUOTE=cdhotfire]Eg: **WineCVS.sh**

I guess its like that.[/QUOTE]

That's what I have been doing, but is there a way to run without the parameters?:confused:

---

### Post by cdhotfire on 2006-02-11
That is how you run without parameters. :|

Edit: I must tell you that CVS wine is a very problematic cvs, ive tried to install it before with no avail.

---

### Post by cdhotfire on 2006-02-11
```

sudo unlink /usr/bin/gcc
sudo ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc
(now do the compile of cedega)
sudo unlink /usr/bin/gcc
sudo ln-sf /usr/bin/gcc-4.0 /usr/bin/gcc

```

I found this solution, maybe you should try it out.

---

### Post by handy on 2006-02-11
I used the info' on the following link to do a cvscedega compile - install.

No prob's!

[http://doc.gwos.org/index.php/CedegaCVSInstallation](http://doc.gwos.org/index.php/CedegaCVSInstallation)

---

### Post by geo926 on 2006-02-11
[QUOTE=cdhotfire]```

sudo unlink /usr/bin/gcc
sudo ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc
(now do the compile of cedega)
sudo unlink /usr/bin/gcc
sudo ln-sf /usr/bin/gcc-4.0 /usr/bin/gcc

```

I found this solution, maybe you should try it out.[/QUOTE]


I tried this solution and it did not seem to change anything, and when I try to the Eg: WineCVS.sh command It says no such command, How do I execute this command?

---

### Post by geo926 on 2006-02-12
[QUOTE=geo926]I tried this solution and it did not seem to change anything, and when I try to the Eg: WineCVS.sh command It says no such command, How do I execute this command?[/QUOTE]

No ideas?:confused:

---

### Post by geo926 on 2006-02-12
please someone!

---

### Post by cdhotfire on 2006-02-12
The command is sh WineCVS.sh. Eg means example I guess.

Btw, when you tried what I posted, do
```

sudo unlink /usr/bin/gcc
sudo ln -sf /usr/bin/gcc-3.4 /usr/bin/gcc

```

Then do the wine script, and after your done with all do
```

sudo unlink /usr/bin/gcc
sudo ln-sf /usr/bin/gcc-4.0 /usr/bin/gcc

```

---

