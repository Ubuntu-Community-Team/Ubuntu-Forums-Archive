---
title: "Installing software in ubuntu"
date: 2008-09-06
forum: Desktop Environments
---

### Post by yosarian on 2008-09-06
I have a disk with software for my printer/scanner, but I don't know how to install it. 
I Windows I should double click directly but I know that I have to do something here but I don't know what.
Could someone help me?

---

### Post by PurposeOfReason on 2008-09-06
What is the extension? .tar.gz, .deb etc.

---

### Post by Saint Angeles on 2008-09-06
you have a disk with windows software and you are trying to install it on ubuntu.

thats not necessary... most printers can be automatically added by going to system->administration->printing

---

### Post by yosarian on 2008-09-06
The folder says Linux, that why I think I can install (I know softare for Windows is not going to work)

I have executable files.

And there is an autorun but is not working

---

### Post by Saint Angeles on 2008-09-06
> **yosarian said:**
> The folder says Linux, that why I think I can install (I know softare for Windows is not going to work)

I have executable files.

And there is an autorun but is not working
so theres a .deb file?
or is a a script? (.sh)

---

### Post by yosarian on 2008-09-06
I have an install.sh

---

### Post by sujitkale on 2008-09-06
Try this
**.sh** file is nothing but a shell script. The easiest way to run **.sh** shell script in Linux is as follows:
[B]sh file.sh
bash file.sh[/B]

Another option is set executable permission using chmod command:
**chmod +x file.sh**
Now run **.sh** file as follows: execute
**./file.sh**

---

### Post by yosarian on 2008-09-06
I did sh install.sh
and I got

libstdc++.so.5 (gcc 3.0.x .. 3.3.x) not found, install ... /sbin/ldconfig.real: Can't create temporary cache file /etc/ld.so.cache~: Permission denied
done
libtiff.so.3 not found, install ... /sbin/ldconfig.real: Can't create temporary cache file /etc/ld.so.cache~: Permission denied
done
./i386/install/guiuninstall: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by ad_267 on 2008-09-06
Ok you can probably just link libstdc++ and libtiff to the more recent versions. You also need to run this as root using sudo and entering your password.

In a terminal do:
```

sudo ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.5
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
sudo sh install.sh

```

---

### Post by yosarian on 2008-09-06
> **ad_267 said:**
> Ok you can probably just link libstdc++ and libtiff to the more recent versions. You also need to run this as root using sudo and entering your password.

In a terminal do:
```

sudo ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.5
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
sudo sh install.sh

```

I did work.

Now the printer is working but the system doesn't recognize the scanner. Could you give me any help with that?

---

### Post by ad_267 on 2008-09-06
What make and model is it?

If you do a google search with the model and "Linux" or "Ubuntu" you might find instructions.

---

### Post by yosarian on 2008-09-06
Samsung SCX-4300

---

### Post by ad_267 on 2008-09-06
I'm not sure why that's not working. It looks like the scanner isn't supported by SANE but the Samsung installer should have installed drivers for it.

---

### Post by yosarian on 2008-09-06
I got some help form a web page but still it doesn't work properly

now I have this message
> Details: Failed to execute child process "/opt/Samsung/mfp/bin/Configurator" (Permission denied)

---

### Post by ad_267 on 2008-09-06
Usually that sort of error means you don't have permission to execute that file. Try changing it's file permissions so you can execute it. You can run this from a terminal:

```

sudo chmod a+x /opt/Samsung/mfp/bin/Configurator

```

---

### Post by yosarian on 2008-09-06
> **ad_267 said:**
> Usually that sort of error means you don't have permission to execute that file. Try changing it's file permissions so you can execute it. You can run this from a terminal:

```

sudo chmod a+x /opt/Samsung/mfp/bin/Configurator

```

I did, but still I have in permissions that it is only for root (and I can't change that).
Now when I try to run the help this message appears 
> Failed to execute child process "/opt/Samsung/mfp/bin/shhv" (Permission denied)

And also, when I click on the program nothing happen

---

### Post by ad_267 on 2008-09-06
If you use a+x then that adds execute permissions for all users. Root is the owner, that means only root can edit the file. But any user can execute it. Try doing the same thing for that file and all files in that directory:

```
sudo chmod a+x /opt/Samsung/mfp/bin/*
```

---

### Post by yosarian on 2008-09-06
I did, but now the software it doesn't work (it does nothing). I am going to try to uninstall and install again.

---

