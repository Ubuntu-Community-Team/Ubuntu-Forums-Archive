---
title: "Permissions - adesklets - gDesklets"
date: 2005-11-09
forum: Desktop Environments
---

### Post by jimmygoon on 2005-11-09
OKAY!

I got adesklets and gDesklets installed but for me to open them I have to run them with "Sudo" so...

they have the permission of the "sudo-fied" user.

basically, this presents a problem when I goto use firefox or any other external program that these applications launch... they launch them as the sudo user. This is bad because thats the wrong profile!!

Is there anything i can do about that?

---

### Post by invalid on 2005-11-09
What is the error you get that prevents you from running them as a normal user? Perhaps there is just a file that needs permission changing..

Cb

---

### Post by jimmygoon on 2005-11-09
[QUOTE=invalid]What is the error you get that prevents you from running them as a normal user? Perhaps there is just a file that needs permission changing..

Cb[/QUOTE]


```
jimmygoon@ubaptop:~/Desktop/modubar-0.0.1$ ./modubar.py
Traceback (most recent call last):
  File "./modubar.py", line 749, in ?
    Events(dirname(__file__)).pause()
  File "./modubar.py", line 218, in __init__
    adesklets.Events_handler.__init__(self)
  File "/usr/lib/python2.4/site-packages/adesklets/events_handler.py", line 157, in __init__
    self.ready()
  File "./modubar.py", line 235, in ready
    join(self.basedir,'config.txt'))
  File "./modubar.py", line 194, in __init__
    adesklets.ConfigFile.__init__(self,id,filename)
  File "/usr/lib/python2.4/site-packages/adesklets/configfile.py", line 159, in __init__
    self._load_and_save()
  File "/usr/lib/python2.4/site-packages/adesklets/configfile.py", line 179, in _load_and_save
    f = file(self._filename,'w+')
IOError: [Errno 13] Permission denied: './config.txt'
jimmygoon@ubaptop:~/Desktop/modubar-0.0.1$

```

---

### Post by invalid on 2005-11-10
It looks from this that config.txt is your problem. You might try making yourself the owner, and giving permission to read and write to it.

```
sudo chown youruser config.txt
sudo chmod 755 config.txt
```

Cheers,
Cb

---

