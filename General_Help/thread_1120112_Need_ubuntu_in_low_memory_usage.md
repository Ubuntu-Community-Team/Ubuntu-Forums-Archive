---
title: "Need ubuntu in low memory usage"
date: 2009-04-08
forum: General Help
---

### Post by iption on 2009-04-08
Since my wireless on ubuntu is not working I've been using the vmware player to start the ubuntu from windows and to update it from there. This takes a lot of memory, and I would like to know is there a way to start ubuntu from grub in terminal without the GUI. 
I tried searching for the answer, but I didin't understand any of the "runtime" talk. 
Can somebody please tell me a step by step how to do that?

Please note that I need the network manager to work in order to download updates from windows, and normal start of ubuntu when I don't plan to use windows.

---

### Post by pytheas22 on 2009-04-08
If you want to turn off the GUI in Ubuntu, run this command:
```

sudo /etc/init.d/gdm stop
```

You will have to run this command after each boot.  If you want to disable the GUI permanently, run:
```

sudo update-rc.d gdm remove
```

but I wouldn't recommend doing that, because it might cause problems for other services.

Without NetworkManager running (it will be stopped if you kill the GUI), run this command to connect to the Internet:
```

sudo dhclient eth0
```

Also, I bet we could make your wireless card work if you told me the output of the following commands in Ubuntu:
```

lshw -C Network
lspci -nn
uname -rm
```

---

### Post by iption on 2009-04-09
> **pytheas22 said:**
> If you want to turn off the GUI in Ubuntu, run this command:
```

sudo /etc/init.d/gdm stop
```

Without NetworkManager running (it will be stopped if you kill the GUI), run this command to connect to the Internet:
```

sudo dhclient eth0
```

Thanks, this works, but is there a way not to run the GUI and to start the terminal directly from GRUB as an other option to boot.

As for the wireless I tried every single tutorial and how to posted in this forum and more, and it didn't work, and I don't have the nerves to bother with this any more.

---

### Post by kpkeerthi on 2009-04-09
You can choose to boot into "Recovery Mode" and connect to wireless using the plain old command line:
1. [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
2. [http://crunchbang.org/archives/2007/12/18/configure-wireless-on-the-command-line/](http://crunchbang.org/archives/2007/12/18/configure-wireless-on-the-command-line/)

I advice you learn how to use command-line to connect to the internet. It might come handy at times when 'X' breaks.

---

### Post by mb_webguy on 2009-04-09
> **iption said:**
> Thanks, this works, but is there a way not to run the GUI and to start the terminal directly from GRUB as an other option to boot.

Yes, there is a way to [boot into a console from the GRUB menu]("http://ubuntuforums.org/showthread.php?p=6782289#post6782289").

---

### Post by iption on 2009-04-11
> **mb_webguy said:**
> Yes, there is a way to [boot into a console from the GRUB menu]("http://ubuntuforums.org/showthread.php?p=6782289#post6782289").

Thank you, just the thing I needed.
I wonder why didn't I found this thread when I searched fror this... Guess
I was using wrong keywords.

---

